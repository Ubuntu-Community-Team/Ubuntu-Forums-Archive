---
title: "DeVeDe Produces Distorted Audio"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2007-06-25
If you read the reference post below, a lot of users are haveing distorted auito with DeVeDe.

[http://ubuntuforums.org/showthread.php?t=369585&highlight=devede+feisty]("http://ubuntuforums.org/showthread.php?t=369585&highlight=devede+feisty")

The problem must be with the Mplayer or codec, but what is the fix, or when will it be fixed?

---

### Post by wildkarde on 2007-06-25
There is a fix.

Download this
[Fix for x86]("http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2")

[Fix for 64bit]("http://www.rastersoft.com/descargas/mplayer_fixed_64.tar.bz2")

```
This file contains the Mplayer/Mencoder versions from Ubuntu Edgy.
Due to a bug in the Feisty version, DeVeDe is unusable with them,
and the lastest Mplayer/Mencoder versions from the SVN has some
troubles with PAL. Since this old version worked fine, I decided
to distribute this "patch" for people who wants to use DeVeDe.


HOW TO INSTALL IT

First, install Mplayer and Mencoder for Ubuntu Feisty as usual, and
be sure to uninstall the old mplayer-cvs-2007-04-11-0-i386.deb
package (it has the PAL problem).

When both packages are installed, just run the "install.sh" script
from a command line using sudo:

          sudo ./install.sh

It will replace the Feisty executables of Mplayer and Mencoder (1.0Pre1)
with the Edgy versions (0.99Pre8).


CONTACTING THE AUTHOR

Sergio Costas
raster@rastersoft.com
http://www.rastersoft.com
```

---

### Post by jlr4u on 2007-06-25
Thank You!

The install.sh script worked find.

---

### Post by Goodson1974 on 2007-06-30
Hi

I've tried the fix and Devede now works perfectly once more :p

Now i don't seem to be able to play any .avi video files!

I'm getting error messages in Totem like: -

Video codec 'DivX 5' is not handled. You might need to install additional plugins to be able to play some types of movies

and

Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies

These were playing fine before, and i haven't removed them to my knowledge!

Any ideas how to get around this?

Cheers

---

### Post by kspn on 2007-06-30
The Audio fix worked a treat :D

Now I just cannot get it actually display the entire DVD image on the screen (it cuts the bottom/top off the image)

This is quite annoying as that is where the subtitles are :???:

Any Ideas? (I have tried Pal/Ntsc formats, no difference)

---

### Post by 4Foot on 2007-07-13
> **wildkarde said:**
> There is a fix.

Download this
[Fix for x86]("http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2")

[Fix for 64bit]("http://www.rastersoft.com/descargas/mplayer_fixed_64.tar.bz2")

```
This file contains the Mplayer/Mencoder versions from Ubuntu Edgy.
Due to a bug in the Feisty version, DeVeDe is unusable with them,
and the lastest Mplayer/Mencoder versions from the SVN has some
troubles with PAL. Since this old version worked fine, I decided
to distribute this "patch" for people who wants to use DeVeDe.


HOW TO INSTALL IT

First, install Mplayer and Mencoder for Ubuntu Feisty as usual, and
be sure to uninstall the old mplayer-cvs-2007-04-11-0-i386.deb
package (it has the PAL problem).

When both packages are installed, just run the "install.sh" script
from a command line using sudo:

          sudo ./install.sh

It will replace the Feisty executables of Mplayer and Mencoder (1.0Pre1)
with the Edgy versions (0.99Pre8).


CONTACTING THE AUTHOR

Sergio Costas
raster@rastersoft.com
http://www.rastersoft.com
```

I don't want to sound like a complete dummy but "sudo ./install.sh " does absolutely nothing for me when I try to run it in a terminal window but tell me that I am stupid and no such program/file/anything exists.

Do I have to do it in some specific directory? Do I have to include something about mencoder or mplayer files and their locations? 

I am trying hard to love Ubu but sometimes when those of you who are trying to be helpful, (and I really appreciate your efforts)  resort to geek-speak you tend to leave out some important, but too obvious to you, elements of the command line stuff that you throw around.

This isn't a harsh complaint, just a plea for a little more noob friendly advice. I like DeVeDe a lot and was very happy using it before the last kernel update. Now I have downloaded a newer version, which is stuck in a usr/bin file that won't let me delete it and tried to reload the official version 3 times and I really want to follow the advice above but 'sudo ./install.sh " just ain't getting me there.

Other then the obvious advice that I take a couple of months to teach myself all there is to know about linux command line protocols and operands so that I can take advantage of this temp fix is there any other advice that anyone can give about installing these older ver of mencoder and mplayer. And how do I get root privileges to delete the stuck version of Devede?

I started out with CPM and the first versions of DOS so I am not afraid of a command line but my gray matter seems to be a little bit slower on the uptake these days and I could use a little bit more info.

Thanks for your patience and help.

4Foot

---

### Post by maxjivi05 on 2007-07-13
Try sudo sh ./install.sh

---

### Post by kelvin spratt on 2007-07-13
You can also download a patch from the DeVeDe site it gives you full  instructions of how to apply it.

---

### Post by maxjivi05 on 2007-07-13
Ok, I applied this patch that you all linked... I'm still having the Very same AUdio issues... I can't get the audio to work with DeVeDe... I've been using Avidemux and ManDVD :/ anyone know how to fix it?

---

### Post by 4Foot on 2007-07-16
> **maxjivi05 said:**
> Try sudo sh ./install.sh

Thank you maxjivi05. That worked for me and I am very happy to report that my copy of DeVeDe is now working perfectly.

The problem I was having is that, while it may seem obvious to linux veterans, I did not know that you could open a terminal in a specific folder. While trying to figure out how to use the excellent file manager from PCman I found a menu item which allowed me to open the terminal in the folder where the particular 'sh" file was located with the mencoder and mplayer files that I had downloaded from the DeVeDe developers site.

As soon as I opened that up and ran the above script, the terminal reported back that the mplayer and mencoder files had been downgraded. I then tested DeVeDe and it worked just fine. I love that prog.

I am very grateful for the help. Thank you all.

4Foot

PS: Now if I could only figure out what "rar is not in your path" means when I try to unrar a rar'ed folder. :)

---

