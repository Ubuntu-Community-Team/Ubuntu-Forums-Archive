---
title: "Imagemagick Location help please"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by drhiii on 2007-07-04
I've searched the internet, the forums, and also searched the hard drive file system to find out the following...

I have installed Gallery2.  And netpbm, gd, Imagemagick.  The first two are located in the setup for Gallery2.  I cannot however find out the location of Imagemagick to configure it inside Gallery2.  Imagemagick *is* installed, I know that.  I just dunno where to point the G2 config screen to find it.

Help anyway?

---

### Post by moore.bryan on 2007-07-04
*did you try a ```
locate imagemagick
``` into the terminal?*

---

### Post by david_2001 on 2007-07-04
The ImageMagick binaries (convert, display etc.) are in /usr/bin.

---

### Post by drhiii on 2007-07-05
> **moore.bryan said:**
> *did you try a ```
locate imagemagick
``` into the terminal?*


Therein lies my quandry.  As follows:

>>  apt-get install imagemagick
Reading package lists... Done
Building dependency tree... Done
imagemagick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I reissue the install command to make triple triple sure.... 

Then, as another poster said, it is located in /usr/bin, so I do a locate with a grep of bin and the result is...

locate imagemagick | fgrep -i bin
/usr/share/doc/imagemagick/www/binary-releases.html


So it is not located in /usr/bin.

This is why I am perplexed.   I will keep searching for a solution.... reason for it is it converts a RAW image file type that I use, otherwise netpbm would work fine.

Sigh...

Tx for the responses.   If anyone has other ideas, please yell back...

---

### Post by moore.bryan on 2007-07-05
> **drhiii said:**
> Therein lies my quandry.  As follows:

>>  apt-get install imagemagick
Reading package lists... Done
Building dependency tree... Done
imagemagick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

[i]have you tried a reinstall?
```
sudo aptitude reinstall imagemagick
```
[/i]

---

### Post by mcduck on 2007-07-05
I suppose your problem is that Imagemagick is not a program, but a collection of programs instead. So there's no executable called 'imagemagick', instead you'll find ones called 'convert' and 'mogrify' etc..

If I remeber right most of Imagemagick stuff is in /usr/share/imagemagick, and the executables for tools in /usr/bin

---

### Post by david_2001 on 2007-07-05
> **mcduck said:**
> I suppose your problem is that Imagemagick is not a program, but a collection of programs instead. So there's no executable called 'imagemagick', instead you'll find ones called 'convert' and 'mogrify' etc..

If I remeber right most of Imagemagick stuff is in /usr/share/imagemagick, and the executables for tools in /usr/bin

They ([http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)) are definitely all installed in /usr/bin but it seems that this fact is not entirely believable ;-)

---

