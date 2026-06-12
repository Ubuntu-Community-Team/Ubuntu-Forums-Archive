---
title: "How best to batch shrink JPEG file size (not pixels) to a given number of KBs?"
date: 2011-04-03
forum: Multimedia Software
---

### Post by rocksockdoc on 2011-04-03
What is the best way to shrink JPG file size **to a given number,** e.g., ~100KB without significantly changing the pixel dimensions, color, or dpi resolution.

On Windows, I had no problem (using Irfanview freeware with the right plugin) shrinking JPEG files to 'around' a given file size (e.g., 100KB) simply at the click of a checkbox. The results were 'around' the desired file size (usually plus or minus something like 10% to 20%), which was an attempt at the software to do the best it could using a variety of selectable filters. (Irfanview will even automatically 'ignore' files that are already below the file size set limit & with another checkbox, it will strip out the EXIF header & thumbnail information).

However, on Ubuntu, I can't seem to figure out what's best to shrink JPG file size to around a given number.

Of course I resize to the desired pixel dimensions first (e.g., using the RESIZE feature of Nautilus to resize to 640x480 pixels or "convert * -strip -auto-orient -resize 640x480 -quality 75 *.jpg); but, once the pixel dimensions are set, I no longer want to change dimensions to get the file size down ... but sometimes I still need to reduce the file size closer to a given desired file size for a large directory of photos.

Certainly ImageMagick has a "resize" option, but that option resizes the pixel dimension, which is NOT what is needed here:

```

convert -resize 50% -quality 80 input.jpg output.jpg
```Of course, with trial and error on the "-quality" setting, one can 'approximate' what is needed:
```

mogrify -format jpg -quality 75 -resize "640x480>" -strip *

```But, without trial and error approaches for potentially hundreds of photos at a time, what's the best way to shrink a directory of photos to (around) a given file size in KB (plus or minus 10% or 20%) simply by specifying the desired target file size?

---

### Post by rocksockdoc on 2011-04-23
Update: I gave up on trying to find any Ubuntu utility to resize digital pictures to a given file size (in kilobytes).

For now, I'll just use the Ubuntu Software Center > nautilus extension to mass resize or rotate images" instead.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189811&stc=1&d=1303590517[/IMG]

---

### Post by rocksockdoc on 2011-09-03
Ever since I posted this (as yet unanswered question), I've been manually converting files to smaller sizes using the Nautilus GUI extension to resize photos:
```
sudo apt-get install nautilus-image-converter
```[IMG]http://i.stack.imgur.com/6yFBF.png[/IMG]
When batch operation is needed, I use ImageMagick for batch resizing operations:

```

sudo apt-get install imagemagick
convert -resize 640x480 -quality 90 input.jpg output.jpg

```or 
```

mogrify -resize 640×480! *.jpg

```Note: This will resize all to 640*480 pixels.
The bang (!) tells it to force the aspect ratio.

or 
```

mogrify *.jpg -quality 75 -resize "640x480>" *
Note: The ">" at the end makes images smaller but 'not' larger.

``` However ... 

This still doesn't set the final file size (in kilobytes).

---

### Post by aura7 on 2011-09-03
Irfan View has nice image conversion features with lot of customization too. Try installing it using wine and use batch resize option in Irfan View.

---

### Post by aeronutt on 2011-09-03
I don't believe nautilus-image-converter works in the most recent versions of nautilus/ubuntu.

---

### Post by rocksockdoc on 2011-09-05
> **aura7 said:**
> Irfan View has nice image conversion features 

I agree that Irfanview, on Windows, is the golden standard.

Not only can it batch shrink to a pre-determined file size (e.g., 100 KBytes), but, it does so in an intelligent manner that allows the file to be larger or smaller if it can't get there.

There appears to be no similar equivalent functionality in Ubuntu, unfortunately.

---

### Post by WasMeHere on 2011-09-05
> **rocksockdoc said:**
> 
When batch operation is needed, I use ImageMagick for batch resizing operations:

```

sudo apt-get install imagemagick
convert -resize 640x480 -quality 90 input.jpg output.jpg

```or 
```

mogrify -resize 640×480! *.jpg

```Note: This will resize all to 640*480 pixels.
The bang (!) tells it to force the aspect ratio.

or 
```

mogrify *.jpg -quality 75 -resize "640x480>" *
Note: The ">" at the end makes images smaller but 'not' larger.

``` However ... 

This still doesn't set the final file size (in kilobytes).

Hello rocksockdoc,

1. I don't understand why you want to set the final size in kilobytes. I am satisfied to set the quality and size in pixels (imagemagick options -quality and -resize), because that way the visual quality of the picture is controlled (allowing more kilobytes to a complicated picture). The average size of many pictures can be predicted well enough (to fit in a limited space).

2. Irfanview works well for me with Wine in Ubuntu. I use it very seldom nowadays, but it is certainly a good option.

3. By the way, I use jhead for lossless rotation of pictures.
```
jhead -autorot
```

/olle

---

### Post by rocksockdoc on 2011-09-05
> **Olle Wiklund said:**
> I don't understand why you want to set the final size in kilobytes. 

It's a good question.

I'm 'spoiled' by the wonderful features of the Irfanview freeware ... so much so that I haven't really figured out if these so nice and so easy to use features are really necessary.

For example, to set the file size to, say, 100KB (using a RIOT plugin, whatever that is), is as simple as checking a checkbox. 

So, in practice, since I email ten at a time and I wish to limit my email size to less than a GB, I usually set the following three items in batch Irfanview operations as my default ... and I leave it at that:

[LIST]
[*]Shrink pixel size to 640x480 pixels
[*]Shrink JPEG quality to something around 85% or so (& auto-apply sharpening)
[*]Shrink file size to something around 100 to 200KB or so
[/LIST]
Now, your question of whether there is value in that third setting, is one I can't really answer. In effect, the first two get the file size down from 5 GB to something on the order of a hundred to two hundred KB anyway ... but I use the third for good measure.

It seems to work - but - I can't answer the question of whether it's actually necessary. 

**Maybe someone who knows the RIOT plugin can tell us more about the value of shrinking down to a specified file size (give or take)?**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201546&stc=1&d=1315236512[/IMG]
> **Olle Wiklund said:**
> The average size of many pictures can be predicted well enough (to fit in a limited space).

In practice, this is true (for the most part).

> **Olle Wiklund said:**
> Irfanview works well for me with Wine 

As a general rule, I first try to REPLACE Windoze features with Ubuntu ... w/o resorting to Wine. 

IMHO, the day Wine becomes no longer necessary to easily do the things we need to do, is the first day that Ubuntu (and any other Linux) will finally become 'user friendly' functional. 

> **Olle Wiklund said:**
> I use jhead for lossless rotation of pictures

Thanks. There are ten things I do (doesn't everyone?) with pictures that I am desperately trying to get Ubuntu to do easily ...

Here, for the record, are my attempts to reproduce, on Ubuntu, what Irfanview seems to do with aplomb on Windoze: 
* [**Stringing commands together to manage typical digital photo operations**]("http://ubuntuforums.org/showthread.php?t=1839153")             

> **rocksockdoc said:**
> Can those more knowledgeable than I help me improve the to-be-written script described below?

My ten typical digital photo operations, in preparation for mailing to  friends & family, which I presume are somewhat ubiquitous, are the  following:

[LIST=1]
[*]I create an empty directory on the hard disk drive titled by date
[LIST]
[*]e.g., mkdir /data/pic/20110904
[*]Note: I should make this automatically figure out the date from the 'date' command.
[/LIST]
 
[*]I copy the flash card JPG contents to the hard disk drive
[LIST]
[*]e.g., mv /media/NIKON D5000/DCIM/100D5000 /data/pic/20110904/big
[*]Note: I'm not sure if the Nikon flash card folder will always be the same name or not.
[/LIST]
 
[*]I rotate the large JPG files according to EXIF orientation tags
[LIST]
[*]e.g., exiftran -ai *.JPG
[*]or, jhead -autorot *.JPG
[/LIST]
 
[*]I rename the large JPG files based on EXIF date & time data
[LIST]
[*]e.g., for i in $(ls *.JPG); do exiv2 -r '%Y%m%d-%H%M%S-:basename:' rename $i; done
[*]Note: This creates file names of the format: 20110904-141904-DSC_1001.JPG
[*]I should probably figure out how to get rid of the "DSC_" part as it adds no value.
[/LIST]
 
[*]I create a directory to hold the shrunken JPG files (suitable for mailing out)
[LIST]
[*]e.g., mkdir /data/pic/20110904/small
[/LIST]
 
[*]I shrink the JPG files to 640x480 pixels at any desired % quality (and/or to about 100KB in size)
[LIST]
[*]for f in *.JPG; do convert -resize 640x480 -quality 90 $f ../small/shrunk_$f; done
[*]This creates file names of the format: shrunk_20110904-141904-DSC_1001.JPG
[*]Note: I can't figure out how to ensure they will be smaller than a certain file size.
[/LIST]
 
[*]I add a white caption plate of about 100 pixels wide for later captioning
[LIST]
[*]e.g., for f in *.JPG; do convert $f -bordercolor white -gravity south -splice 0x100 $f; done
[*]Note: This bottom captioning plate must be added only after auto-rotation.
[/LIST]
 
[*]I create a common set of sub folders for mailing purposes
[LIST]
[*]e.g., mkdir 20110904/small/{family,friends}
[/LIST]
 
[*]I step through the small picture set selecting the best photos to copy to the to-be-emailed subfolders
[LIST]
[*]e.g.,  feh *.JPG -F --cycle-once --action1 "cp %f ./family/%n" --action2 "cp  %f ./friends/%n" --action3 "cp %f ./family/%n; cp %f ./friends/%n"
[*]As I view each picture in turn:
[LIST]
[*]Space bar advances to the next photo
[*]Backspace repeats the previous photo
[*]1 copies the file to the 'family' subfolder
[*]2 copies the file to the 'friends' subfolder
[*]3 copies the file to both the friends and family subfolders
[*]Control + delete will delete the current file
[/LIST]
 
[/LIST]
 
[*]I caption the pictures, ad hoc, for that personal touch in the results.
[LIST]
[*]e.g., for f in *.JPG; do kolourpaint $f; done
[*]Note:  I caption and annotate each picture, as needed, & then save the new  file & close kolourpaint (whereupon the next file pops up in  kolourpaint, to repeat the process).
[/LIST]
 
[/LIST]
I'm not a  programmer so, before I string these ten commands into a single script,  may I ask for advice from those of you more experienced than I in these  scripting matters?

[COLOR=DarkRed]** So far, nobody has provided any advice on the above question ... but I hope someone does as the results will be published back here so that everyone can do these most-common ten steps just as easily on Ubuntu as we can already do on Windoze.**[/COLOR]

---

### Post by WasMeHere on 2011-09-25
Thank you rocksockdoc,

for your long and informative answer. I use digikam to manage and tag my pictures, gimp to edit them, imagemagick and jhead for batch processing. But I have not at all your high ambitions to manage my pictures. I hope that you find some friends here in the forum to exchange methods with you in order to migrate completely to linux.

Best regards
Olle

---

### Post by WasMeHere on 2011-09-26
> I should probably figure out how to get rid of the "DSC_" part as it adds no value.

In bash you can use ${i/string/} as in the following example
```
olle@April-2008:~$ typeset greeting='Hello DSC_World'
olle@April-2008:~$ echo $greeting 
Hello DSC_World
olle@April-2008:~$ echo ${greeting/DSC_/} 
Hello World
olle@April-2008:~$ 
```

---

### Post by Thav on 2011-09-26
I found this paper abstract on predicting the size of a JPEG after resizing and changing quality factor published by the IEEE Computer Society.
[Very Low Cost Algorithms for Predicting the File Size of JPEG Images Subject to Changes of Quality Factor and Scaling ]("http://www.computer.org/portal/web/csdl/doi/10.1109/DCC.2008.85")

They give a sample table in the abstract, but you'd have to get a hold of the full paper for the others. It sounds like if a few percent error was acceptable that may work out for you, and then you could write a script that runs the formula and calls ImageMagick to resize to the dimensions and quality that you want. This assumes you're going from JPEG to JPEG, but there may be similar work out there for RAW to JPEG.

---

### Post by WasMeHere on 2011-09-27
In order to learn shell programming, I suggest that you search for 'bash tutorial' in your browser. This way I found the following links, which might help you in different ways. You will find more, including what you need with good examples of small shell-scripts.

[U][http://linuxconfig.org/Bash_scripting_Tutorial]("http://linuxconfig.org/Bash_scripting_Tutorial")
[http://www.hypexr.org/bash_tutorial.php]("http://www.hypexr.org/bash_tutorial.php")
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")[/U]

Have fun
Olle

---

### Post by aeiah on 2011-09-27
```
convert -define jpeg:extent=100kb input.jpg output.jpg
```

[http://www.imagemagick.org/Usage/formats/#jpg_write](http://www.imagemagick.org/Usage/formats/#jpg_write)

---

### Post by volks65 on 2012-10-04
try [http://converseen.sourceforge.net/](http://converseen.sourceforge.net/)

---

### Post by lud on 2013-06-15
Hi,

perhaps [jpegoptim]("http://freecode.com/projects/jpegoptim") would be worth trying? I believe from version 1.3.0 it has the -S / --size option to set target size for output.

Although I use it only with the --max attribute to set maximum quality of the optimized pirctures, the -S / --size option might be way forward...you can write a simple vash script to automate this task for you.

---

### Post by oldos2er on 2013-06-15
Old thread closed.

---

