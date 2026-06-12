---
title: "Script for batch photo conversion and resizing"
date: 2015-02-02
forum: Multimedia Software
---

### Post by andrewsc0 on 2015-02-02
Hello,
 I'm trying to get into a more professional workflow as a photographer using linux and I was wondering if anyone could help me make a script (and how to run it) that could simplify my process?

What I would like to create is a script that when ran would do the following to all of the images in the folder the script is directed at:

1. renames all of the NEFs (Nikon raw file) in a folder to something of my choosing
2. converts a copy to JPG
3. resizes JPGs to a certain pixel length (usually 2048 pixels) on the long end (even if it is the horizontal or vertical end) of each photo 
Bonus option:
4. Adds a watermark? This isn't that important to me right now, but in the future it will be. 

Two things have to happen:
The original NEF files can't be touched and
the JPG and the NEF that it came from have to have the same name.

I've been messing around with the first three things and gotten them to work in one way or another using the following three programs:
pyrenamer (though I've only used the gui version and not terminal for this one)
imagemagick
ufraw

The following has worked to some (though not the best) degree of success:


ufraw-batch --out-type=jpeg --out-path=./jpg ./*.NEF
or
ufraw-batch –out-type=jpeg –out-path=./ ./*.NEF


Outputs the NEFs files into PPM (could not understand why it output as ppm and not jpg)
But, then I could then run

convert *.ppm image%d.jpg

Then I could resize them with a bastardized version of the following two lines that I cannot remember right now
convert '*.jpg[200x]' resized%03d.png
and 
convert image.jpg -resize "100>" newimage.jpg


However it only resized the horizontal axis. It also renamed the images...


If you out there could offer your know how to help me make a more efficient and better version that does all of the above in one step I would greatly appreciate it! Thanks in advance.

---

### Post by mooreted on 2015-02-03
Image Magick is an amazing tool. It takes a bit to learn, and I haven't used it for awhile, but it will do all of that and more:

[http://www.imagemagick.org/](http://www.imagemagick.org/)

Some examples:

[http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

I had a friend that wanted all the pics on his website to have full size photos with thumbnails. Image Magick let me resize all the pictures and create thumbnails in one command.

---

### Post by mooreted on 2015-02-03
Doing some research. I would write the script for you, but I don't trust my scripting skills. But maybe I can give you an idea of the direction to take:

For request 1. mogrify might be what you're looking for:

Ex: mogrify -shave 240x0 -resize 96x72 -path xyz *.jpg

For request 2. mogrify again

Ex: mogrify    -format jpg   *.png

Looks like mogrify for request 3. as well

Ex:  mogrify -resize 256x256 *.jpg

Here are some suggestions for watermarking:

[http://www.imagemagick.org/Usage/annotating/#wmark_image](http://www.imagemagick.org/Usage/annotating/#wmark_image)

---

### Post by andrewsc0 on 2015-02-03
so you are dead on for request 2 and 3. Thank you for the help so far, this is definitely the right direction!

The command for 2. 
    mogrify -format jpg *.NEF
makes a jpg for each NEF file and for 3.
    mogrify -resize 2048x2048 *.jpg
resizes each photo to a maximum length of 2048 on which ever (horizontal or vertical) end is longest.

as for adding a watermark the command
     composite -dissolve 40 -gravity South \Watermark.tif *.jpg -alpha Set w.jpg

works but it has a few errors that I can't seem to figure out
1. it only adds the watermark to the first image
2. it has to rename the image, keeping it the same name does not result in a watermarked image. (I would be ok with it "destroying" the original jpg and not making a copy)
3. It doesn't quite center the watermark so that it cuts off the front edge of the watermark. Not sure how to center it better, or make sure it resizes for every photo. 

Finally for the first renaming step, 
I'm having trouble finding a command line renamer that I understand.   I use pyrenamer all the time and love it, but I would like to add a forget it and forget it approach to renaming the files. 
Traditionally what I'll have is 50 or so NEF files that are named things like 

MIH_056.NEF
MIH_0110.NEF
MIH_1355.NEF

and I would like to rename them something sequential

SubjectsNAME_001.NEF
SubjectsNAME_002.NEF
SubjectsNAME_003.NEF  


Any simple directions on how to do that via command line would be appreciated.

---

### Post by mooreted on 2015-02-03
Yeah, most of the instructions out there want to use sed and ack or a do/while loop. The problem is, they don't really explain what each step does and I never do any scripting unless I know what each step means.

The Thunar file manager has a bulk rename.

---

### Post by andrewsc0 on 2015-02-03
so I found that 
```
find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" %04d.NEF\n", $0, a++ }' | bash
```
will rename the files as I want!
```
[COLOR=#000000]mogrify -format jpg *.NEF[/COLOR]
```
will make a jpg of the nef (I'm wondering if I could output this to a new/different folder)
```
[COLOR=#000000]mogrify -resize 2048x2048 *.jpg[/COLOR]
```
will resize the image as I want it to be resized

Now if I could just fix the watermark problems and turn all that into one script somehow..

---

### Post by mooreted on 2015-02-03
Awesome, at least you are 99% there.

---

### Post by FakeOutdoorsman on 2015-02-03
> **andrewsc0 said:**
> I'm wondering if I could output this to a new/different folder

You can use [-path](http://www.imagemagick.org/script/command-line-options.php?#path).

---

### Post by andrewsc0 on 2015-02-04
Thank you FakeOutdoorsman for that piece of info:

So what I would want a script to do at this point is:
```

find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" SubjectName_%04d.NEF\n", $0, a++ }' | bash
mkdir jpgs
[COLOR=#333333][FONT=Lucida Grande]mogrify -path fullpath2/jpgs [/FONT][/COLOR]-format jpg *.NEF
cd fullpath/jpgs
mogrify -resize 2048x2048 *.jpg
```

as for adding the watermark, using gravity center and resizing the watermark file has fixed the location problems, also it keeps the names correct (I think that was a silly error on my part) however I still can't get it to do more than one image. 
For some reason -dissolve is not recognized by mogrify... this is the error it produces: mogrify.im6: unrecognized option `-dissolve' @ error/mogrify.c/MogrifyImageCommand/4460.
when I run
```
mogrify composite -dissolve 40 -gravity center Fullpath/Watermark.tif *.jpg -alpha Set *.jpg
```

so if I can figure out how to get the watermark added to multiple images at a time and then make everything into a script I'd have exactly what I need.

Using the draw command instead of composite I have gotten the watermark to work on all images in the directory and instead of messing with dissolve I just changed the opacity of the watermark itself, so the following works.

```
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Fullpath2/Watermark.tif'" *.jpg
``` 

so I just need to turn the following commands into a script I can point at a directory and run.. **How do I do that?**
(obviously ***SubjectName*** and ***Fullpath2*** need to be replaced as needed.)

```

find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" SubjectName_%04d.NEF\n", $0, a++ }' | bash
mkdir jpgs
mogrify -path Fullpath2/jpgs -format jpg *.NEF
cd Fullpath2/jpgs
mogrify -resize 2048x2048 *.jpg
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Fullpath2/Watermark.tif'" *.jpg

```

Thank you mooreted, for setting me off in the right direction!

also I started another thread in another forum, hoping it would get more eyes if any future internet searchers find this information useful [http://ubuntuforums.org/showthread.php?t=2263962](http://ubuntuforums.org/showthread.php?t=2263962)

---

### Post by FakeOutdoorsman on 2015-02-05
You can probably use one mogrify command to do all three of your current commands and therefore prevent the reduction of quality loss due to the multiple generations of lossy encoding.

---

### Post by mooreted on 2015-02-05
> **andrewsc0 said:**
> Thank you FakeOutdoorsman for that piece of info:

So what I would want a script to do at this point is:
```

find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" SubjectName_%04d.NEF\n", $0, a++ }' | bash
mkdir jpgs
[COLOR=#333333][FONT=Lucida Grande]mogrify -path fullpath2/jpgs [/FONT][/COLOR]-format jpg *.NEF
cd fullpath/jpgs
mogrify -resize 2048x2048 *.jpg
```

as for adding the watermark, using gravity center and resizing the watermark file has fixed the location problems, also it keeps the names correct (I think that was a silly error on my part) however I still can't get it to do more than one image. 
For some reason -dissolve is not recognized by mogrify... this is the error it produces: mogrify.im6: unrecognized option `-dissolve' @ error/mogrify.c/MogrifyImageCommand/4460.
when I run
```
mogrify composite -dissolve 40 -gravity center Fullpath/Watermark.tif *.jpg -alpha Set *.jpg
```

so if I can figure out how to get the watermark added to multiple images at a time and then make everything into a script I'd have exactly what I need.

Using the draw command instead of composite I have gotten the watermark to work on all images in the directory and instead of messing with dissolve I just changed the opacity of the watermark itself, so the following works.

```
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Fullpath2/Watermark.tif'" *.jpg
``` 

so I just need to turn the following commands into a script I can point at a directory and run.. **How do I do that?**
(obviously ***SubjectName*** and ***Fullpath2*** need to be replaced as needed.)

```

find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" SubjectName_%04d.NEF\n", $0, a++ }' | bash
mkdir jpgs
mogrify -path Fullpath2/jpgs -format jpg *.NEF
cd Fullpath2/jpgs
mogrify -resize 2048x2048 *.jpg
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Fullpath2/Watermark.tif'" *.jpg

```

Thank you mooreted, for setting me off in the right direction!

also I started another thread in another forum, hoping it would get more eyes if any future internet searchers find this information useful [http://ubuntuforums.org/showthread.php?t=2263962](http://ubuntuforums.org/showthread.php?t=2263962)


You're welcome. Happy to help.

---

