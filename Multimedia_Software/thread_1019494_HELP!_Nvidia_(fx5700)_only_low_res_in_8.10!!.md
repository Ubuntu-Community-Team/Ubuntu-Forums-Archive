---
title: "HELP! Nvidia (fx5700) only low res in 8.10!!"
date: 2008-12-23
forum: Multimedia Software
---

### Post by Shlomir on 2008-12-23
This is driving me nuts and I really need it fixed!

Since upgrading to Ubuntu 8.10 and installing the Nvidia driver I can olny get 640x480 resolution graphics, and I think the problem is in my xorg settings. This is my problem history so far...

1. I have an Nvidia fx5700 card and upgraded to Ubuntu 8.10, previous 8.04 worked fine, 100%!

2. I installed driver 173.14.12 using envy.

3. I have tried dpkg-reconfigure xserver-xorg, displayconfig-gtk and xfix which just reinstalls the generic Ubuntu driver that kills the Nvidia one but gives you 800x600 res!

I think the problem is in my xorg, here it is, can someone please recommend what extra strings will give me high res??

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by mplexus on 2008-12-23
try adding those bold lines

Section "Screen"
	Identifier	"Default Screen"
**        Device          "Default Device"**
	DefaultDepth	24
[B]        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"
        EndSubSection
[/B]
EndSection

---

### Post by Shlomir on 2008-12-24
Yes I tired this but didn't make any difference, still 640x480 the max res.

Are you sure it's the right entries in xorg.conf?

This is getting very frustrating, as I had everything nice in 8.04!!

AAaarrggghhh@#$%$#@!!

---

### Post by coolethan on 2008-12-24
step 1: calm the frick down
step 2: click this link
step 3: enjoy Ubuntu 8.10 the way it should be enjoyed



[http://ubuntuforums.org/showthread.php?t=1019044&page=3]("http://ubuntuforums.org/showthread.php?t=1019044&page=3")

---

### Post by Shlomir on 2008-12-24
> **coolethan said:**
> step 1: calm the frick down
step 2: click this link
step 3: enjoy Ubuntu 8.10 the way it should be enjoyed



[http://ubuntuforums.org/showthread.php?t=1019044&page=3]("http://ubuntuforums.org/showthread.php?t=1019044&page=3")

Not very much help there...I mean, where are the strings to add to xorg to get the extra resolutions, no mention of what section and what values to add...

BUMP!!

---

### Post by coolethan on 2008-12-24
you should only have to adjust the resolution values. wherever you see 800x600 put in the resolution you want. should work. if you still have your 8.04 disc you might want to try running that live and as it was working 100% as you say, you should be able to find the xorg.conf file on the live disc and copy it and place it into the X11 file in 8.10. you need to be root to do that however.

---

### Post by Shlomir on 2009-01-01
I fond a fix..It was a xorg.ini field, but buggered if I remember where on the Internerd I found it!

HNY!

---

