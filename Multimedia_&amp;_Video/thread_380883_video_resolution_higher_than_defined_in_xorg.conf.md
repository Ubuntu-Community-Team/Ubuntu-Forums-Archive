---
title: "video resolution higher than defined in xorg.conf"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by meikdahogo on 2007-03-10
Hello all,

I installed the new ati driver using instructions from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).

I did that so that the driver would work with the 17.11 kernel.

I saved my xorg.conf so that my dual screen configuration would not get broken.

I installed the driver, no problem, fglrxinfo gives me the correct information. however, my screen resolution does not work anymore.

I have two HP LP2065 monitors, and in my xorg.conf I have defined 1600x1200 as maximum resolution per monitor. However, when probing somehow it is determined that the best resolution is 1920x1024 and so i get a resolution of 3840x1024.

Now I do not know how to make it clear to Ubuntu that I want the old resolution back. Not that 1920x1024 is not working, but of course letters and icons are pressed together and much higher than they should be, and this does not enhance the readability of my screen.

Any help would be appreciated!

---

### Post by meikdahogo on 2007-03-10
OK, I've figured this one out with the help of some guys on the ubuntu-nl forum on freenode. (thanks JanC)

Check below:

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1600x1200"
	EndSubSection
EndSection

In the SubSection "Display" I had forgotten to define the Modes "1600x1200". Once I added these, a simple CTRL ALT BKSPCE was enough to help me out!

Thanks Jan, I hope somebody else can use this information as well!

---

