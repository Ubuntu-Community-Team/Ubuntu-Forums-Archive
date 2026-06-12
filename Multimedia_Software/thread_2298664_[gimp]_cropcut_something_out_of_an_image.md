---
title: "[gimp] crop/cut something out of an image"
date: 2015-10-13
forum: Multimedia Software
---

### Post by joe.koenig on 2015-10-13
Hi, y'all.
[CENTER]*                    [ is there  some new aggressive type of board-software that even messes with  innocent non-abusive postings?  It seems to have deleted "duckducking.*." *[/CENTER]

  Please excuse me, but I've been googling and duckducking this.  Still, I can't seem to be able to perform one single, simple task: cut/crop a portion from the middle of an image.

 Not some extraordinarily shaped structure amidst the picture.  Just a portion in the middle the picture.   I.e: Imagine a pictiue.  Divide it into three vertically equally sized parts.  Cut/crop the middle part out and make a new picture of the two remaining fragments.  Sounds pretty easy, right?  (No, "Select -> Invert -> Paste as" doesn't seem to do the trick)



$ cat /etc/*-release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

$ gimp --version
GNU Image Manipulation Program version 2.8.10

Some of the effort I've done:   (among many, many others)
[https://duckduckgo.com/?q=gimp+%22cut+out%22+portion+middle+OR+crop](https://duckduckgo.com/?q=gimp+%22cut+out%22+portion+middle+OR+crop)
[https://www.google.de/search?q=gimp+cut%2Bout%2Bmiddle%2BOR%2Bcrop](https://www.google.de/search?q=gimp+cut%2Bout%2Bmiddle%2BOR%2Bcrop)

---

### Post by sudodus on 2015-10-13
I don't know a dedicated command for this operation, but you can do it stepwise.

1. Mark and copy the top part of the picture. Paste it into a first new gimp window.

2.Mark and copy the bottom part of the picture. Paste it into a second new gimp window.

3. Create a third new gimp window with the appropriate canvas size.

4. Paste the top part and bottom part to the third new gimp window.

It is possible to skip step 1 and step 2 and paste the top and bottom directly into a new gimp window with the appropriate canvas size (but maybe harder to know what canvas size to use). It is also possible to fix the canvas size afterwards.

---

### Post by joe.koenig on 2015-10-13
Well, yeah, that's the usual, tiresome and boring approach.  Been there.  Done that.  That's what I wanted to avoid.  (BTW: I, again, have confused "horizontally" with "vertically".  I'm pretty sure I meant it to be "horizontally" ;-)  Doesn't really matter.)

Thanks
Joe

---

### Post by sudodus on 2015-10-13
If you do it once, do it with gimp, and it should not be that boring.

If you [must] do it many times and with fixed proportions, then don't use gimp.

ImageMagick is a good tool for batch manipulation of images.

[http://www.imagemagick.org](http://www.imagemagick.org)

There are good online tutorials.

---

### Post by shantiq on 2015-10-13
specifically [this]("http://www.imagemagick.org/Usage/crop/") info section in imagemagick howto should be of help maybe

---

### Post by joe.koenig on 2015-10-13
Thanks guys,

 for your everlasting support.
 
 I've pretty much exhausted all of relevant off Imagemagick's tools (without claiming that I haven't missed an option here and there, obviously) " ... convert, montage, transform ... you name it

 [CENTER]*[ Ooops.   I might have misjudged @shantiq's posting.  I'm sorry.  My bad.  I'll reevaluate.  Thanks for your understanding.]*[/CENTER]

---

### Post by joe.koenig on 2015-10-13
Hm, I guess you guys have been right all along. Thanks @sudodus and @shantiq.  There probably is no easy gimp/gui way around this. 

Allow me to share a little Howto I've found on my journey: [http://www.linuxjournal.com/content/slice-and-dice-images-imagemagick](http://www.linuxjournal.com/content/slice-and-dice-images-imagemagick)

> Slice and Dice Images with ImageMagick 
 
 Dec 10, 2008  By Janos Gyerik 
 inHOW-TOs 

You can use the convert command that comes with ImageMagick to extract parts of an image.

You can cut out a 100-pixel-wide chunk from somewhere in the middle of an image:
$ convert -crop 100x+0+0 orig/wrapperbg775.gif slice0.gif
$ convert -crop +200+0 orig/wrapperbg775.gif slice1.gif
$ convert +append slice0.gif slice1.gif wrapperbg675.gif

Note that there was no need to specify the height of the image in any of the above commands. If you need to adjust the height instead of the width, the steps are similar, but use -append instead of +append to paste the slices vertically.

I'm just duplicating/copying in case the link goes down.  Thanks for your understanding, Janos.

Thanks again
Joe

---

### Post by sudodus on 2015-10-13
Beware of our new Image Wizard ;-)

---

### Post by shantiq on 2015-10-13
well Joe i said **maybe** i had never done it before with imagemagick for the specific requirement you needed there [indeed crazy Gimp has not got that function] but you sounded very bright so just pointed the direction and you worked it out ...  Imagemagick is indeed The Dog's Bollox if one has the time and inclination to experiment. you did. kudos ::]]

---

### Post by joe.koenig on 2015-10-13
Image Wizard???  Dog's Bollox??? 
You guys are just pulling my leg/horrn, aren't you?  In case you aren't: Please elaborate (if you feel like doing so)

Cheers
Joe

---

### Post by sudodus on 2015-10-13
It's only a way to wish you good luck with Image Magick :-)

---

### Post by shantiq on 2015-10-13
[:KS]("http://www.urbandictionary.com/define.php?term=Dog%27s+Bollocks")  [The Dog's ...]("http://www.urbandictionary.com/define.php?term=Dog%27s+Bollocks")

---

### Post by howefield on 2015-10-13
And with that, this thread having been asked and answered, is best closed.

---

