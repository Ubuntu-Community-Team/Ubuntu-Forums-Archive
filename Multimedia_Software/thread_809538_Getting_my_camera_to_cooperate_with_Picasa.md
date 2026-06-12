---
title: "Getting my camera to cooperate with Picasa"
date: 2008-05-27
forum: Multimedia Software
---

### Post by id4abel on 2008-05-27
The fact that my camera names files IMG_1966.JPG and Picasa shows them as 1 of 314 was driving me crazy. I modified a Pearl script that renames the camera filenames to 1.jpg, 2.jpg, 3.jpg ... which is saving me a lot of suffering.  Now someone can say, "photo 231 is a little dark" and my 231.jpg is now the same file rather than the IMG_3187.JPG that my camera decided was a good idea. 

To use this script, save the lines below into a text file that has the extension of .pl (as in rename.pl or picasanumbers.pl or whatever you prefer) 

#!/usr/bin/perl



$iteration=1;



foreach my $file (`ls *.JPG`) {

    chop($file);

    system("mv $file $iteration.jpg;");

    $iteration++;

    }


Once the file is saved, drop a copy in the same directory as the camera files you will upload to Picasa. Use the script by first opening Terminal. Use the cd command to change your directory. Finally enter ./rename.pl to start the script.

---

### Post by K.Mandla on 2008-05-29
Moved to Multimedia and Video.

---

