# forvorbiscomment

This is a script that interactively creates metadata for all of the .ogg files in a directory.

You should make sure the file called "forvorbiscomment" is executable with `chmod +x forvorbiscomment`.

You can also feel free to put this script in your $PATH.

Feel free to fork this repository if you want to make changes (i.e., to make it work for other file types with a different program like an id3 tagger).

## Dependencies
- vorbis-tools (or whatever package provides vorbiscomment in your distro)
- bash (will probably not work with other shells)

## Notes

- The default values work specifically for an "mp3-style" directory structure of "Artist Name"/"Album Name"/File. Make sure to call the script with the --interactive option if you do not have this because it will put undesirable values for those variables if you do not. This is because the default options are programmed to look at the parent directory name for the album name, and the one above that for the artist name.

- Calling the script with --defaults and --interactive conflicts and will not work.

- The script must be called in a directory with .ogg files and will not work for other file types without tweaking.

- If the files you are running the script on were obtained by using yt-dlp, they will have brackets like [...] on the end of your file name. Passing the --yt-format option to the script will automatically trim this out of the file name if you use the default options or interactively choose to have the title of the track be the file name, but it will also trim out the last field (space-separated phrase, including words, parentheses, brackets, etc.) if it detects brackets. So, if the files were *not* obtained with those brackets and your title should have other brackets in it, **do not** use the -y option.

## Usage
```
forvorbiscomment [arguments]
Valid arguments are:
-d, --defaults		| Use the default values of the script (default option, conflicts with --interactive)
-h, --help		| Print these options
-i, --interactive	| Manually define values for metadata; choose which values are global and local to each file (conflicts with defaults)
-y, --yt-format		| If files were downloaded with yt-dlp, automatically trims the bracket part out of the track name. Does nothing if used with --interactive or with a file that does not have this. However, if you set this option and the file name ends in [...] or [...].ogg it will cut out those brackets (be careful!)
```
