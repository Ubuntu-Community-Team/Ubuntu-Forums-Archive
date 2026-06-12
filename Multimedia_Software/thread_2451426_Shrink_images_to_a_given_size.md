---
title: "Shrink images to a given size"
date: 2020-10-04
forum: Multimedia Software
---

### Post by gipsyshadow on 2020-10-04
I'm running ubuntu 18.04 and I'm searching a sw to resize images to a given size, eg. 250kb, 1.5mb and so on. I need this sw to be able to cut an image for first and then shrink it to a given size. Of course I don't mean "dimensions" for size but its "weight" in kb or mb.

---

### Post by Holger_Gehrke on 2020-10-04
The ImageMagick tools can try to do this - at least for jpeg and webp. Usually they are a few percentage points off the desired file size. See [https://imagemagick.org/script/formats.php](https://imagemagick.org/script/formats.php) for details.

Holger

---

### Post by gipsyshadow on 2020-10-04
Thanks for your suggestion. Please let me ask a very newbie question: how to get it with its GUI? I've tried to "call" it by command line but nothing were found, then I've seen there're 3 packages installed with that name in mu ubuntu: imagemagick, imagemagick-6-common, imagemagick-6.q16. What to do now?

---

### Post by Holger_Gehrke on 2020-10-04
ImageMagick is made up of several tools: animate, compare, composite, conjure, convert, display, identify, import, mogrify, montage and stream. While the 'display' command can be seen as a kind of GUI to ImageMagick,  the tools are meant to be used on the command line and have lots (and  lots and lots and ... ) of options that can be combined in many  interesting ways to get almost any result imaginable. I usually call it  the 'Photoshop of the command line'. All of these tools have pages in the manual (so 'man convert' will give you a short overview of the convert tool) and there's more extensive documentation in the package imagemagick-6-doc which will install to /usr/share/doc/imagemagick-6-common/html or you could go to [http://www.imagemagick.org](http://www.imagemagick.org) .

```

convert original.jpg -define jpeg:extent=128kb new.jpg

```
will read 'original.jpg' and write to 'new.jpg' while trying to compress to a size around 128kb.

The advantage of the command line for jobs like these is the ability to use shell scripting to create complex workflows that can then be executed with just one command.

For example this
```

for i in *.JPG ; do a=$(stat --printf=%s "$i") ; if [ $a -gt 1000000 -a $a -lt 2000000 ] ; then convert "$i" -define jpeg:extent=512kb "${i%%.JPG}-sml.jpg"; fi ;done

```
will convert all files in the current working directory with names ending in '.JPG' that have a size between 1000000 and 2000000 Bytes keeping the converted file size around 512kb and give the converted files names created by removing '.JPG' from the end of the name and appending '-sml.jpg'.

Holger

---

### Post by gipsyshadow on 2020-10-05
Very interesting stuff about imagemagick, it's a powerful tool for sure. Now I'd like to show you something I've just found on the web: [jpegoptim]("https://www.omgubuntu.co.uk/2016/03/how-to-optimize-jpeg-command-line-linux").
> 
The app also lets you reduce a jpg to a specific size.

Do you know it? If yes, what do you think about it? I'd like to try it BUT I wonder if I can get a GUI. It seems you can get "trimage" as GUI in ubu repos BUT I've just seen its dependencies and there're entries like "python:any" and I'm afraid it will install very heavy stuff in my OS because I'm sure I haven't anything installed dealing with python and I'd like to avoid to install that only for this job. Can you confirm my concern?

---

### Post by Holger_Gehrke on 2020-10-05
I don't know that program. And I actually can't confirm your concern since on Ubuntu 18.04 Python is installed by default both in version 2.7 (for compatibility with older scripts) and version 3.6 (as python3) because many parts of the system are written in Python. You could try a simulation of the installation with 'apt install --dry-run trimage' after setting up the PPA for it. This should tell you what exactly would be downloaded and how much.

Holger

---

### Post by T6&amp;sfpER35% on 2020-10-05
i just use GIMP

---

### Post by Holger_Gehrke on 2020-10-05
> **3nd said:**
> i just use GIMP

That will work for a few images, few being defined by your personal threshold of boredom. Also you can't just tell it 'make this image 500kb', you have to fiddle with the image quality factor until you get the right size. Once you have to do this for all the larger images on a photography website to make space for new images, you'll see the wisdom of automation ...

Holger

---

### Post by gipsyshadow on 2020-10-07
I've just tried imagemagick using your command
```

convert XYZ.jpg -define jpeg:extent=128kb new.jpg

```
and I'm very confused. I tell you my problem. Consider the images present in [jpegoptim]("https://www.omgubuntu.co.uk/2016/03/how-to-optimize-jpeg-command-line-linux") page, the cat in particular. If I run imagemagick with your command and the input image is one of my photos taken by my camera (circa 1.8-3.5MB, circa 4500x3500 pixels) the output pic is horrible, let's say like [this]("https://149366088.v2.pressablecdn.com/wp-content/uploads/2016/03/cookie.jpg"). The result changes just a little few if I firstly resize my photo dimensions @50%, and that for ALL my photos. If I get a quite big image from the web, let's take [this]("https://i2.yuki.la/8/4b/46f954b1a6403f91e445de3b6e6da7b7d310e6aae93f486140c298720792b4b8.jpg") 2.3mb 4000x3000pixels girl, the result is perfect, and that for ALL web pics like that (I mean quite big) tried until now. WHY?

---

### Post by Holger_Gehrke on 2020-10-07
JPEG is lossy. The smaller the file, the bigger the loss of detail / image quality. If I run that girl's face image through convert to get a 128kb image the result is far from perfect, especially if comparing details at full resolution. Running 'identify -format "%Q\n" girl128k.jpg' tells me it has a quality factor of 13, the original had a quality of 94 (the quality factor runs from 1 to 100 (higher is better) but is not a percentage, AFAIK). The ruined cat-image has a q-factor of **1**. Reducing the amount of data to a quarter by scaling it by 50% horizontally and vertically obviously gives better quality; if I do 'convert girl.jpg -resize 2000x1500+0+0 -define jpeg:extent=128kb girl-rs-sml.jpg' I get a file of 125kb with a q of 59. Acceptable quality is generally said to be around q=75; if I run 'convert girl.jpg -quality 75 girl75.jpg' the resulting image is about 750kb and looks okay if viewed at full resolution. As to why the images from your camera generally come out of conversion looking horrible I can't tell but it probably has to do with the image content. JPEG compression does very well with images that have soft gradients and is notoriously bad for sharp contrasts along straight lines.

So in general I'd check the q of the images to shrink and I'd generally not try to go lower than 1/3 of the file size.

Holger

---

### Post by gipsyshadow on 2020-10-08
Thanks for your explanation, now I see what went wrong: I checked all my photos converted by your command and their quality were 1.

Now I'd like to tell you my "goal", I mean my reason to search a tool able to do what I told in my 1st post. I've joined many forums where there're KBs limits about posted images, eg. 25kb, 125kb, 900kb and so on. Whenever I want to post a pic, maybe a detail cut off from a photo of mine, I have to pick my photo, cut a part of it and then my "odyssey" begins because I spend a lot of time resizing/scaling its dimensions, in other words I manually try to OPTIMIZE the point between the minimum loss of data/resolution and its weight (Kbs) to fit the forum's limits.

That said, what can you suggest me to spend less time possible to get my goal with my pics? Though I use imagemagick with the "convert" option I firstly have to optimize the best quality for that specific image conversion, so it's a mess again for me.

---

### Post by Holger_Gehrke on 2020-10-08
Since this is an interactive situation for a single image or a low number of images, 3nd's idea of just using GiMP for it is actually really good.

I'd do a rectangular selection for the area of interest, then 'Image'->'Crop to Selection' to cut the image to just the part I want to post. Next I'd scale it ('Image'->'Scale Image') to keep it's dimensions below whatever threshold the forum might have (if there is no such limit, I might skip this step). Finally 'File' -> 'Export as', set path and name. After that you get a form to set various format-specific options. Set 'Show preview in image window' on, you won't get a file size shown in the form otherwise. You can open the advanced options and remove the thumbnail, EXIF and xmp-metadata (those take a few kb). Now if you change the slider for quality you'll get a preview in the image window (as a separate layer; you can switch between preview and original image for comparison by clicking on the eye in front of the layer name in the Layers dock)  and a file-size in the form. If you can't get an image of acceptable quality with a small enough size, abort the export, scale the image down and try export again. I rarely post images, but when I do this takes less time to do than to explain.

Holger

---

