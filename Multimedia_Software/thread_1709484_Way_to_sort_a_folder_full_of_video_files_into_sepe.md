---
title: "Way to sort a folder full of video files into seperate folders"
date: 2011-03-18
forum: Multimedia Software
---

### Post by Jombib on 2011-03-18
Sorry if this is a duplicate, have just spent the last hour searching forums and google but might have missed something obvious.

I have a massive collection of movies in .avi, .rmvb and mkv format, all these files are currently just thrown into one big folder of files. I was wondering if there was a way I could use some kind of script to go through the folder and  make a new folder within it for every video file (using the name of the video file) and move the video file into its respective folder.

For example if there is a video file named "the_hangover.avi" it would make a folder called "The_Hangover" and move "the_hangover.avi" into it.

There are currently about 1000 video files to sort and I am not looking forward to doing it manually if this is not possible.

Many Thanks for all your help, my Ubuntu journey would not have been possible so far without you.

---

### Post by sisco311 on 2011-03-18
In bash you can try something like:
```

cd /path/to/dir

shopt -s nullglob
for file in *.{avi,rmvb,mkv}
do
  directory="${file%.*}"             # remove file extension 
  directory="${directory//_/ }"      # replace underscores with spaces

  darr=( $directory )
  darr="${darr[@]^}"                 # capitalize the directory name

  [color=green]echo[/color] mkdir -p -- "$darr"           # create the directory; 
  [color=green]echo[/color] mv -b -- "$file" "$darr"      # move the file to the directory
  [color=green]echo[/color]
done

```

The [color=green]echo[/color] commands are just for testing, remove them to actually move the file.

---

### Post by aeiah on 2011-03-18
python, for the hell of it:
```

import os, shutil

dir = sys.argv[1]

if dir[-1] != '/':
        dir = dir+'/'


# for every file in the directory
for file in os.listdir(dir):
        #create new directory name from filename
        newDir = file.rsplit('.',1)[0]

        #capitalise, if you really want it
        newDir = newDir.title()
        
        #make new directory
        os.mkdir(dir+newDir)

        #move file into new directory
        shutil.move(dir+file, dir+newDir+file)

```

script takes one argument, the directory you want to process. this is untested so test it first, but really i just did this due to boredom, the bash implementation will do the same

---

### Post by Jombib on 2011-03-18
Thanks aeiah! That has actually just saved me about a weeks work. Just one question though, I've noticed that any files with "{}" "[]" or "()" were not moved, I'm guessing these are symbols that confused the script due to them having some other purpose

Thanks again though, I really appreciate it

---

### Post by pt123 on 2011-05-20
a little update on the bash script by me to move handle cd1 & cd2 at the end of the filename, as well as moving .srt subtitle files into the directory.

```

#!/bin/bash

cd "/media/path_to_working_folder"
pwd

shopt -s nullglob
for file in *.{avi,rmvb,mkv,ogm,mp4}
do
  directory="${file%.*}"             # remove file extension 
  directory="${directory//_/ }"      # replace underscores with spaces

 darr=${directory}
 
 darr="${darr/ cd1}"
 darr="${darr/ cd2}"
 darr="${darr/ CD1}"
 darr="${darr/ CD2}"
 srt="${file%.*}.srt"
 #echo "$srt"

  echo "$darr"
  mkdir -p -- "$darr"           # create the directory; 
  mv -i -- "$file" "$darr"      # move the file to the directory

	if [ -f "$srt" ]
	then
	 	mv -i -- "$srt" "$darr"      # move the srt file to the directory
	fi
 
done

```

---

