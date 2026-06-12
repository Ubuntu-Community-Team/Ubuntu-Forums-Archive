---
title: "how can I turn my desktop into a gif?"
date: 2013-06-27
forum: Multimedia Software
---

### Post by TooFreppaT on 2013-06-27
how can I record my desktop and then turn it into a gif?
I want to make something like these: [http://i.stack.imgur.com/WaYDU.gif](http://i.stack.imgur.com/WaYDU.gif) and [http://i.stack.imgur.com/fgTGz.gif](http://i.stack.imgur.com/fgTGz.gif)
but I want to use zoom for somethings and then zoomout and stuff like that
I have never recorded anything or made a gif or done anything like this before
[http://askubuntu.com/questions/106666/is-there-a-way-to-make-a-file-that-would-run-a-terminal-command-when-you-click-i](http://askubuntu.com/questions/106666/is-there-a-way-to-make-a-file-that-would-run-a-terminal-command-when-you-click-i) this is where I found it from

---

### Post by Toz on 2013-06-27
*Moved to **Multimedia & Video**.*

Have a look at [this link]("http://askubuntu.com/questions/107726/how-to-create-animated-gif-images-of-a-screencast/107735#107735") for instructions.

---

### Post by andrew.46 on 2013-06-28
There is a setting within Gimp that allows you to get a screenshot of various dimensions. Easy then to export the image in whatever format you wish...

---

### Post by TooFreppaT on 2013-06-30
> **Toz said:**
> *Moved to **Multimedia & Video**.*

Have a look at [this link]("http://askubuntu.com/questions/107726/how-to-create-animated-gif-images-of-a-screencast/107735#107735") for instructions.

I followed those instructions but couldn't zoom in, this is the code I used to crop the images before converting them to .gif but you only have to change the extensions to do it afterwards.
```
convert *.jpg -crop _**width**_x_**height**_+_**padding-left**_+_**padding-top**_ *.jpg
```
I used this on a directory with a single image and processed my images one at a time.......lol, but it did what I wanted it to do, it changes the file without generating an output instead it just replaces the file cleanly.
I did try removing the first ***.jpg** for cropping multiple files at once but for some reason I always ended up with one less cropped image compared with the originals, it produces a separate output file for each and renames them all to the last one which wasn't what I wanted it to happen.......I could be mistaken because I did try a number of combinations before settling with for what I put in the codebox.

I found this informations by following a link on [Looking for mass cropping software]("http://askubuntu.com/questions/83829/looking-for-mass-cropping-software/83884#83884") to [imagemagick.org how to crop (using the -crop parameter)]("http://www.imagemagick.org/Usage/crop/"). 

See also:
[LIST]
[*][Command line batch image cropping tool]("http://stackoverflow.com/questions/1893244/command-line-batch-image-cropping-tool") 
[*] [ImageMagick: Batch Crop and Rename Files]("http://nali.org/imagemagick-batch-crop-and-rename-files/") 
[/LIST]

---

### Post by Toz on 2013-06-30
If I'm understanding correctly, that you are trying to crop a number of files simultaneously, try a command like this:
```

for file in *.jpg; do convert -crop widthxheight+padding-left+padding-top "$file"; done
```
...just make sure to replace widthxheight, padding-left, and padding-top with actual values

It will cycle through all of the jpg files one at a time, perform the crop operation overwritting the file.

---

### Post by evilsoup on 2013-06-30
I think you should use mogrify for these things. It's a part of ImageMagick and comes with convert (and uses the same syntax, so most things you read in the convert guides will work with mogrify), but is designed to modify files in-place rather than writing to a separate output file.

```
mogrify -crop widthxheight+padding-left+padding-top ./*.jpg
```

---

### Post by SeijiSensei on 2013-06-30
While mogrify is useful, be sure to back up all the images before you start!

---

### Post by evilsoup on 2013-06-30
> **SeijiSensei said:**
> While mogrify is useful, be sure to back up all the images before you start!

This is definitely good advice, which the OP should follow.

For zooming and other fancy effects: while they certainly can be done at the command-line, I would recommend looking at some graphical video editors. I don't know if any of those available for Linux have the capability (since I video edit on Windows using proprietary software), but if they do the you'll find the visual feedback makes things much easier.

---

### Post by TooFreppaT on 2013-06-30
> **Toz said:**
> If I'm understanding correctly, that you are trying to crop a number of files simultaneously, try a command like this:
```

for file in *.jpg; do convert -crop widthxheight+padding-left+padding-top "$file"; done
```
...just make sure to replace widthxheight, padding-left, and padding-top with actual values

It will cycle through all of the jpg files one at a time, perform the crop operation overwritting the file.I just get a whole bunch of these, one for each file but I will try it next time I restart my computer and change my drivers because I did something with the code I was using before and it gave the same thing the second time I used it but the first time it froze my computer so I think it just broke something. :confused:
```
convert.im6: no images defined `_**filename**_.jpg' @ error/convert.c/ConvertImageCommand/3044.
```


> **evilsoup said:**
> I think you should use mogrify for these  things. It's a part of ImageMagick and comes with convert (and uses the  same syntax, so most things you read in the convert guides will work  with mogrify), but is designed to modify files in-place rather than  writing to a separate output file.

```
mogrify -crop widthxheight+padding-left+padding-top ./*.jpg
```This one worked for me! :D Even 100000+ files and it didn't even crash my computer this time. :guitar:

......unfortunately RecordMyDesktop only has a maximum of only 50 FPS. :(

---

