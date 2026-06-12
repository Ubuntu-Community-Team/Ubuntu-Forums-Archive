---
title: "What's the best (i.e., quickest and easiest) program to manually crop digital photos"
date: 2010-09-08
forum: Multimedia Software
---

### Post by rocksockdoc on 2010-09-08
I'm new to Ubuntu 10.04 (having come over from the PC world) where I often need to manually resize a picture.

In Windoze, you simply pop up Irfanview which loads in a split second and then you simply sweep out the area to crop and you hit control + Y (to crop) and control + s (to save) and voila, the picture is cropped and saved.

**[COLOR=DarkRed]What's the best (i.e., quickest and easiest) program to manually crop digital photos using Ubuntu 10.04?[/COLOR]**

[SIZE=1]*Note: I've tried Gimp 2.6 (slow as a dog), Inkscape 0.47 (even slower than the Gimp & much less intuitive for cropping), KolourPaint 4.4.2 (segmentation fault every time), Krita (crashes every time), Xara Xtreme 0.7 (unintuitive crop), Xfig 3.2 (doesn't seem to work on JPEGs), Xpaint 2.8.13 (highly unintuitive crop), etc.*[/SIZE]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168851&stc=1&d=1283945014[/IMG]

---

### Post by M93 on 2010-09-08
F-spot is not slow and its not bad

---

### Post by Rasa1111 on 2010-09-08
> **M93 said:**
> F-spot is not slow and its not bad

Right.
  GIMP is good to crop photos with,
 but F-spot seems to be quicker to open. 

Another, really easy way,

 Is to use the screenshot tool. 

So, say you have a photo open in image viewer, 
 You could simply go to Applications> Accessories> Take Screenshot~
Choose "select area to grab" Then hit the "take screenshot" button,
then just drag your cursor from where you want to start the crop, to where you want to end it. 

Once you select an area, just save it , and you have a new image of only the area you selected. 

 No program needed to be opened at all.

 Screenshots of the process~

(and damn, that's allot of graphics programs!) :lol:

---

### Post by cchhrriiss121212 on 2010-09-08
Viewnoir is really easy and light too. Just open the image with it, then go to Image>Crop.

---

### Post by rocksockdoc on 2010-09-09
> **Rasa1111 said:**
> GIMP is good to crop photos with, but F-spot seems to be quicker to open. 

Perfect! "F-Spot 0.6.1.5" is not only a LOT quicker to come up than "The Gimp 2.6.8" but, it takes far fewer actions to crop a screenshot with F-Spot than with The Gimp. 

> use the screenshot toolNice! That "Applications->Accessories->Take Screenshot" tool works better than KSnapshot ([which crashes every time]("http://ubuntuforums.org/showthread.php?t=1571540")); but it seems to only save PNG files.

**[COLOR=DarkRed]Can "Take Screenshot" be coerced into saving GIF files instead of PNG files?[/COLOR]**

> **Rasa1111 said:**
> (and damn, that's allot of graphics programs!) 

**I'm simply trying to annotate screenshots as easily as possible.**

For that, I need only the following:
- Ability to screenshot and save as a GIF (does "Take Screenshot" save as GIF?)
- Crop (looks like F-Spot crops nicely if the screenshot needs to be further cropped)
- Text (Gimp texts just OK but Gimp is slow as a dog)
- Draw arrows (Gimp stinks at drawing arrows)
- Draw open "boxes" or "ellipses" ([Gimp stinks at drawing boxes and ellipses]("http://ubuntuforums.org/showthread.php?t=1086589"))
- Scale/resize the final result to 640x480 (Gimp does this job nicely)

So far, these are the programs I've tried:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169002&stc=1&d=1284076007[/IMG]

---

### Post by rocksockdoc on 2010-09-09
> **cchhrriiss121212 said:**
> Viewnoir is really easy and light too. Just open the image with it, then go to Image>Crop.

Weird.

Viewnoir has NEVER been mentioned (apparently) on the Ubuntu forums here; and it's not in the Ubuntu Software Center on Ubuntu 10.04. 

???

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169007&stc=1&d=1284077035[/IMG]

---

### Post by Rasa1111 on 2010-09-09
cool, glad it helped. 

Im not sure if "take screenshot" can be set to save as GIF. 

 But, Have you seen "**Shutter**" yet? 

You can save in whatever format you want,
and you can also edit the screenshots, right in the app. 

[http://www.ubuntugeek.com/shutter-featureful-screenshot-tool.html](http://www.ubuntugeek.com/shutter-featureful-screenshot-tool.html)

It allows you to~
> **take a screenshot of your complete desktop, a rectangular area or capture a website**
take screenshot directly or with a specified delay time
save the screenshots to a specified directory and name them in a convenient way(using special wild-cards)
Shutter is fully integrated into the Gnome Desktop (TrayIcon etc.)
generate thumbnails directly when you are taking a screenshot **and set a size level in %**
Shutter session collection
keep track of all screenshots during session
copy screeners to clipboard
print screenshots
delete screenshots
rename your file
upload your files directly to Image-Hosters , retrieve all the needed links and share them with others
**edit your screenshots directly using the embedded drawing tool**

 Sounds like it may have all you need?
all in this one app.

 Here's a video of it also.
[http://www.youtube.com/watch?v=ZpU_yLFhkU8](http://www.youtube.com/watch?v=ZpU_yLFhkU8)

 and a few more links on **Shutter**.
[http://www.howtogeek.com/howto/6720/shutter-is-a-state-of-art-screenshot-tool-for-ubuntu/](http://www.howtogeek.com/howto/6720/shutter-is-a-state-of-art-screenshot-tool-for-ubuntu/)
[http://www.waytoubuntu.com/2010/01/shutter-excelent-screenshot-application.html](http://www.waytoubuntu.com/2010/01/shutter-excelent-screenshot-application.html)
[http://ubuntuguide.net/take-and-edit-screenshots-in-ubuntu-using-shutter](http://ubuntuguide.net/take-and-edit-screenshots-in-ubuntu-using-shutter)

 Cheers. <3

---

### Post by Dex73 on 2010-09-09
Shutter is sweet for screen shots. If the photo is already on the screen you can highlight it and save only what you highlighted in a separate file. It's a screenshot/crop tool all in one, and like Rasa1111 was getting at it's loaded with options and after you open it once it gets really fast!

---

### Post by Rasa1111 on 2010-09-09
> **Dex73 said:**
> Shutter is sweet for screen shots. If the photo is already on the screen you can highlight it and save only what you highlighted in a separate file. It's a screenshot/crop tool all in one. Just something to think about.

Yeah i just learned about it right before my previous post. 
I remember reading something on it awhile ago.. 
but never looked into it until a few minutes ago. 
It does look sweet. 

 How is it's speed?
i mean, Does it hog resources?
and does it open quickly?

 thanks.

---

### Post by nechus on 2010-09-09
I use IrfanView a lot under Wine. I prepared an icon for it:
[http://www.glowfoto.com/static_image/09-222054L/4193/png/09/2010/img4/glowfoto](http://www.glowfoto.com/static_image/09-222054L/4193/png/09/2010/img4/glowfoto)

---

### Post by rocksockdoc on 2010-09-10
> **Rasa1111 said:**
> How is it's speed?.

Both "Applications->Accessories->Shutter" and "Applications->Accessories->Take Screenshot" are new to me. 

Shutter opens up slower than "Take Screenshot" and requires more steps; but seems to have a richer set of preferences. For example, while "Take Screenshot" will only save a PNG, Shutter gives you the choice of "bmp", "jpg", or "png" (sadly, GIF is not an option).

Shutter also allows you to subsequently automatically open up the results in F-Spot or The Gimp. 

Shutter has more features than "Take Screenshot" except it's a lot slower than "Take Screenshot". 

Still, it's a very nice find ... and I might find myself using it even though it's slower, if for no other reason than it opens up more easily for the next editing step in my screenshot editor.

---

### Post by rocksockdoc on 2010-09-10
Just so you know, the overall goal is for a usable screenshot annotation program on ubuntu.

Screenshots and cropping are just the start! 

The next three requisites are circles, texting, and arrows.

**GOLDEN STANDARD:**

The best program for ad-hoc screenshot annotation is, unfortunately under WINE, namely Paint.NET.

[LIST]
[*]You simply draw your circles & type your caption starting at the cursor (that's it)
[LIST]
[*]It's WYSIWYG so there's no uselessly annoying additional temporary text-editing box  **[COLOR=DarkRed]<== biggie![/COLOR]**
[*]No need to draw a uselessly redundant bounding box **[COLOR=DarkRed]<== biggie![/COLOR]**
[*]It's easy to switch colors & fonts & sizes while typing
[/LIST]
 
[*]You simply draw the endpoints of the arrow (and it takes care of the rest automagically)
[LIST]
[*]It's trivially easy & powerful to have multiple curves in the line of the arrow! **[COLOR=DarkRed]<<==biggie![/COLOR]**
[*]It's easy to preset the arrow endpoint shapes and to change them on the fly  **[COLOR=DarkRed]<== biggie![/COLOR]**
[*]It's easy to set variously spaced dotted lines & thicknesses for your arrow shafts
[/LIST]
[/LIST]
Unfortunately:

[LIST]
[*]Paint.NET, like Irfanview, is only available on Ubuntu under WINE **[COLOR=DarkRed]<== biggie![/COLOR]**
[/LIST]
 I've researched ALL the known Ubunto native drawing programs - and all  fail (miserably in some cases) to meet a simple standard of easy  circles, fast captions, and decent arrows.

**FORUM  REFERENCES:**
- [What's a good curved ARROW drawing tool in Ubuntu (similar to Paint.NET on Windoze)?]("http://ubuntuforums.org/showthread.php?t=1575505")
- [What's the best (i.e., quickest and easiest) program to manually crop digital photos]("http://ubuntuforums.org/showthread.php?t=1570447")
- [How to batch add 200 white canvas pixels to rotated JPEG bottom edge]("http://ubuntuforums.org/showthread.php?t=1720281")
- [How do YOU scroll through hundreds of photos & move good ones to a separate folder?]("http://ubuntuforums.org/showthread.php?t=1625745")
- [Is there an extension to "Eye of Gnome" to RENAME or DELETE pictures while viewing?]("http://ubuntuforums.org/showthread.php?t=1737710")
- [How best to rename all JPEGs in a folder by EXIF date & time stamp]("http://ubuntuforums.org/showthread.php?t=1694592")
- [Why does my first bash script work - but also elicit Kolourpaint errors?]("http://ubuntuforums.org/showthread.php?t=1752506")
etc.

---

### Post by cchhrriiss121212 on 2010-09-10
> **rocksockdoc said:**
> Weird.

Viewnoir has NEVER been mentioned (apparently) on the Ubuntu forums here; and it's not in the Ubuntu Software Center on Ubuntu 10.04. 

???


Thats my fault as I misspelled it, its actually Viewnior.

---

### Post by M93 on 2010-09-10
[viewnior]("http://xsisqox.github.com/Viewnior/about.html")

---

### Post by Dex73 on 2010-09-13
> **rocksockdoc said:**
> Both "Applications->Accessories->Shutter" and "Applications->Accessories->Take Screenshot" are new to me. 

Shutter opens up slower than "Take Screenshot" and requires more steps; but seems to have a richer set of preferences. For example, while "Take Screenshot" will only save a PNG, Shutter gives you the choice of "bmp", "jpg", or "png" (sadly, GIF is not an option).

Shutter also allows you to subsequently automatically open up the results in F-Spot or The Gimp. 

Shutter has more features than "Take Screenshot" except it's a lot slower than "Take Screenshot". 

Still, it's a very nice find ... and I might find myself using it even though it's slower, if for no other reason than it opens up more easily for the next editing step in my screenshot editor.

You can leave Shutter in the tray. Then it will start up instantly. Just don't quit it. Unfortunately this get's screwed up when your forced to restart.

---

### Post by lordppm on 2010-09-13
You can try with Shotwell or use online photo editor "Picnik" from [www.picnik.com](www.picnik.com)

---

