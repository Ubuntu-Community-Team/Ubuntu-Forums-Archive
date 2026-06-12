---
title: "Radeon 7000 resolution problem 8.10"
date: 2008-11-01
forum: Multimedia Software
---

### Post by .zolder on 2008-11-01
Hi,

I just installed 8.10 and now i can't use a 1280x1024 resolution anymore. I could however under 7.10. I went over to amd.com and learned that Ati dropped it's support for the Radeon 7000. The thing is, I don't even know if that's the cause for my problems.

I should mention I'm relatively new to Linux, so besides webtutorials and such I don't have a lot of knowledge when it comes to problemsolving.

What I tried and some info about this config:
```
desktop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)

```(it really is an r7000!)
next, i tried
```
desktop:~$ sudo dpkg-reconfigure xserver-xorg
```
which gave this output:
```
desktop:~$ sudo gedit /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

```

Now, I found this opensource ATI driver tutorial [(click!)](https://help.ubuntu.com/community/RadeonDriver), which says the r7000 is supported by "The open source ATI driver (xserver-xorg-video-ati)". Don't know whether or not I'm using this already... However, at some point the guide says:
```
It should look like this:

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection
```
which obviously isn't the case at all in my situation. This leaves me very uncertain about how to follow the guide, or even whether following or not it is a good idea. Can anyone please help me out a bit?

image fwiw
[img]http://img383.imageshack.us/img383/3563/resolutionsqr1.png[/img]

---

### Post by peakshysteria on 2008-11-01
That might not be the right command you have there (sudo dpkg-reconfigure xserver-xorg). From Ubuntu Hardy Heron 8.04 the right command for changing your xorg is:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

But from 8.10 on I'm not sure you can use this command anymore either since they are phasing this method out.

[markbuntu]("http://ubuntuforums.org/showthread.php?t=794551") says:
>  As far as xorg.conf is concerned, Xorg is in the process of removing xorg.conf entirely. It will not be avialable in future releases of X starting with 7.4. Configuration is being automated with options confined to the drivers themselves and their configuration utilities.

And while we're at it: how did you move from 7.10?

---

### Post by .zolder on 2008-11-01
Thanks for replying. Sadly, using the command you suggested made my xorg.conf look like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
Maybe this is a good thing though, since the apparent phasing out of xorg.conf.. perhaps I should be looking elsewhere
> how did you move from 7.10?
*cough*lost password, fresh install*cough*

---

### Post by peakshysteria on 2008-11-01
fresh install....hm...not sure how to get your card up and running then (most people says clean install is the way to go (even tough I prefer an upgrade myself). Most info on google seem to point to the sad fact that your cards not supported with the latest drivers. But try: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")**Installing the restricted drivers manually **

---

### Post by .zolder on 2008-11-01
I followed the "Installing the restricted drivers "the Ubuntu way" " part of  that guide up to "sudo aticonfig --initial -f "

there, i got this msg:
```
Uninitialised file found, configuring.
Segmentatiefout *<< Segmentation Error*

```

then i tried "Installing the restricted drivers manually"

somewhere, i got this msg:
```
Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (x86_64) first.
Done.
```
When trying to install that, the console says I got the lates dkms build already


I'm at loss. maybe I should upgrade my card with another low performance one that _is_ supported..

---

### Post by jengo on 2008-11-02
i am having the same exact problem man, i really need some help. This resolution is terrible. 

Whats this i hear about Ubuntu not working with radeon 7000? are you kidding me? it works in XP but not ubuntu?

im pretty sure there is a way we can get it to work. somebody plz help!

---

### Post by soxs on 2008-11-02
You may try appendg this to your screenscetion foy our xorg.conf (in case there is allready something alike, replace it)

```
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Defaultdepth	24
```
[COLOR="Red"][SIZE="5"]
NOTE: Make a backup first! This may break graphical login, as I don't know wether 7000er series are 24bits/pixel capable![/SIZE][/COLOR]

---

### Post by jengo on 2008-11-02
can you make a copy of your xorg.conf file so i can see how it is supposed to look? 

thanks.

---

### Post by .zolder on 2008-11-02
soxs! Thanks! I put that in my xorg.conf (looked up an example) and now i'm on 1280x1024!!!

for jengo and probably some others, this is what did the trick:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Defaultdepth	24
EndSection
```
mandatory "remember to backup original" ;)

---

### Post by jengo on 2008-11-02
thank you so much! this fix worked out great! 

thanks guys! :KS

---

