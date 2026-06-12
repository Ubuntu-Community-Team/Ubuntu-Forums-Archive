---
title: "File Sorting"
date: 2013-06-21
forum: Multimedia Software
---

### Post by olnik on 2013-06-21
Basically, numerous hard drive problems led me to recover all of the photos on one of my hard drives in to a folder named 'JPG', which contained every image of that format on my computer. Which just so happened to be half a million files. This amount of files is too big for my computer to handle and consequently I am unable to even open the file easily (it takes hours) and even when it opens it's far too laggy to organise. Even then it would be such a tedious job I'd probably find myself doing it for days, if not weeks. 

All the images I need are from a certain camera, I was looking in to something about meta-data of images and I checked the meta-data of one image from the camera and it still contained all the information, however the file name had been changed, so all the images are unorganised. 

I was wonering if anyone knew how to write a script which would sort through this folder and copy the images taken by a specific camera to a different folder? I know you can do it by file size but as there is such a variety of images I don't believe that method would be plausible. Also, if anybody has a script which can search through the same folder for a picture with exact dimensions I would also very much appreciate that. 

Thanks in advance, James

---

### Post by TheFu on 2013-06-21
I don't have a script to do what you want, but I have modified a web gallery to look at the EXIF data and display that.  **exiftool** is probably what you need to know to get started.

If you make an attempt at the script, others are more likely to help.  [http://www.sno.phy.queensu.ca/~phil/exiftool/](http://www.sno.phy.queensu.ca/~phil/exiftool/) might help or might be everything you need. I dunno.

---

### Post by olnik on 2013-06-21
TheFu, thanks, I looked at that recently and I find out how to read all the exif data but as far as the script goes I am clueless. If I knew where to start, to start one, believe me I would. But honestly, I would have no idea where to start. 

If anybody would take the time to write a script for this it would be very much appreciated.

---

### Post by TheFu on 2013-06-22
> **olnik said:**
> TheFu, thanks, I looked at that recently and I find out how to read all the exif data but as far as the script goes I am clueless. If I knew where to start, to start one, believe me I would. But honestly, I would have no idea where to start. 

If anybody would take the time to write a script for this it would be very much appreciated.

Understood.  If I have some time, I'll try to hack something together. A script is just commands that you would normally type stored into a file. Of course, we can use loops and IF checks, but the basic idea of a script being commands that you would type into a terminal holds - especially when you are starting out.

Perhaps this will get you started:
```
$ exiftool  252.jpg  |grep 'Camera Model Name'
```
Camera Model Name               : Canon PowerShot ELPH 300HS

So if we store a list of every photo file into a text file ....  ```
ls *.jpg > J.txt 
```now we can iterate over that list in our code and don't have to re-read the directory more than once (to create the J.txt file).
If we are looking for a specific camera model .... mine is a "ELPH 300HS" I can either move or rename all the files with that inside the exif data. the pseudo-code would be this:

```
# Loop over all the image files in J.txt
# using exiftool, look for files with "Canon PowerShot ELPH 300HS" in the camera model.
#     If found, rename the file by prepending "PowerShot-" to the name.
#     otherwise, ignore the file.

```
Simple.  When the script finishes, every file that I want will start with "PowerShot-" and will be easy to separate from all the other files.  Of course, I'd **make a 100% backup of the directory first - before I ever tried running the script. **

Now I just need to learn how to do each of those small steps in the language I use - bash in this case.  The Advanced Bash Scripting Guide has never let me down: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

BTW, I always write pseudo-code as code comments before I begin, so I don't get lost along the way if I need to step away.

```

#!/bin/bash

# Loop over all the image files in J.txt
for ARG in `cat J.txt`
do

   # using exiftool, look for files with "Canon PowerShot ELPH 300HS" in the camera model.
   #  use the man pages for commands to see which options simplify the output
   IS_PS = `exiftool -S $ARG | grep -c "Canon PowerShot ELPH 300HS" `

   #     If found,  - the grep -c returns a count of times something is found
   if [[ $IS_PS -ne 0 ]] 
   then
      # rename the file by prepending "PowerShot-" to the name.   - notice that this line doesn't do anything.
      echo mv $ARG  "PowerShot-$ARG"
   fi 

   #     otherwise, ignore the file.

done

```
I haven't tested this complete script, but it should be close to working.  Might be small issues with the count returned by grep or the loop control reading a line at a time in the file. If the file names have spaces or special characters, that could be an issue too.  I find it is easier to always name files a specific way on my system, so I never need worry about those potential problems.

BTW, inside the EXIF data should be the original file name that the camera created. That could be useful. It might be good to grab the timestamp and make that part of the filename so photos are displayed in order.

Anyway, this should get you close, if not all the way there.  Certainly there are 100 other ways to accomplish this - some will be better.

---

### Post by evilsoup on 2013-06-22
If there are millions of files in the directory, you'll run into bash's maximum number of arguments ('*.jpg' will be expanded to every .jpg in the directory). You'll need to use find instead. Something like:

```

find . -type f -name '*.jpg' > files.txt

```

This will print one file per line.

You would also be better off using a 'while read' loop -- in this case, 'for' will break on any file containing spaces in its name

```

while read ARG; do
  #exiftool stuff, as in TheFu's script, should go here
done < files.txt

```

It's also possible to pipe the output of find straight into 'while read'; the version below uses nullbyte as the delimiter, which means that even filenames containing newlines will be handled correctly (nullbyte is one of the two characters that cannot be in a legal *nix filename, the other being forward-slash). This script will place files in directories named after the model of the camera, as determined by exiftool:

```

#! /usr/bin/env bash
find . -type f -name '*.jpg' -print0 | while read -d $'\0' i; do
##  get the name of the model -- the sed part
##  finds a line beginning with 'Model:'
##  (for sed, '^' means 'the beginning of the line')
##  and then strips off the 'Model; ' part,
##  leaving only the model of the camera
  model=$(exiftool -S "$i" | sed -n '/^Model:/s/Model: //p')
##  tests to see if a directory named for the camera model
##  already exists; if it doesn't, then creates it with mkdir:
  [[ -d "$model" ]] || mkdir "$model"
##  tests that "$model" isn't empty, and then moves
##  the file into the "$model" directory
##  (if "$model" is empty, then there was no exifdata
##  about what model of camera was used)
  [[ "$model" != '' ]] && mv "$i" "$model"/
done
exit 0

```

As for your other question: the width of the image is listed by exiftool (with the '-S' option) with the key 'XResolution', and the height with 'YResolution'. You get them within a script like so:

```

width=$(exiftool -S "$file" | sed -n '/^XResolution/s/.*://p')
height=$(exiftool -S "$file" | sed -n '/^YResolution/s/.*://p')

```

...and then you can test to see if they match whatever arbitrary resolution you want. Here is an example:

```

[[ $width$height == 300300 ]] && echo "The resolution is 300x300 pixels"

```

---

