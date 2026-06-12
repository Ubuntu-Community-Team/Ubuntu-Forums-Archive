---
title: "[Hardy] latest ati fglrx (8.5) drivers"
date: 2008-05-22
forum: Multimedia Software
---

### Post by excogitation on 2008-05-22
8.6 available:

[fglrx-amdcccle_8.501-0ubuntu1_i386.deb](http://www.filefactory.com/file/a8a2dd)
[fglrx-installer_8.501-0ubuntu1_i386.changes](http://www.filefactory.com/file/1c0891)
[fglrx-kernel-source_8.501-0ubuntu1_i386.deb](http://www.filefactory.com/file/682fe2)
[xorg-driver-fglrx_8.501-0ubuntu1_i386.deb](http://www.filefactory.com/file/f8ef45)
[xorg-driver-fglrx-dev_8.501-0ubuntu1_i386.deb](http://www.filefactory.com/file/f1c0dc)

if you run into the libGL.so.1 error
> sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

--- previous post ---
So I guess you've already seen it (isn't rss nice?):
[ati-driver-installer-8-5-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run")

If by any chance someone is looking for the *.deb's
(built using ./ati-driver-installer-8-5-x86.x86_64.run --buildpkg ubuntu/hardy)

[LIST]
[*] [fglrx-amdcccle_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/dc1df3) of size 5.133 MB

[*] [fglrx-installer_8.493-0ubuntu1_i386.changes](http://www.filefactory.com/file/4e07a3) of size 1.153 KB
[*][fglrx-kernel-source_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/a2733c) of size 1.215 MB
[*][xorg-driver-fglrx_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/5b64cd) of size 7.633 MB
[*][xorg-driver-fglrx-dev_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/a2734a) of size 39.789 KB
[/LIST]
[URL="https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat85-inst.html"]
Official install instructions are here.[/URL]
[New Features and Resolved issues can be found here.]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html#194695")

---

### Post by Exershio on 2008-05-22
downloading it now. let's see how this one works.

---

### Post by excogitation on 2008-05-22
I don't know what you expect... I can't tell a difference 
- then again you know what's been changed if you look at the "changelog".

---

### Post by bebox on 2008-05-26
> **excogitation said:**
> So I guess you've already seen it (isn't rss nice?):
[ati-driver-installer-8-5-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run")

If by any chance someone is looking for the *.deb's
(built using ./ati-driver-installer-8-5-x86.x86_64.run --buildpkg ubuntu/hardy)

[LIST]
[*] [fglrx-amdcccle_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/dc1df3) of size 5.133 MB

[*] [fglrx-installer_8.493-0ubuntu1_i386.changes](http://www.filefactory.com/file/4e07a3) of size 1.153 KB
[*][fglrx-kernel-source_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/a2733c) of size 1.215 MB
[*][xorg-driver-fglrx_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/5b64cd) of size 7.633 MB
[*][xorg-driver-fglrx-dev_8.493-0ubuntu1_i386.deb](http://www.filefactory.com/file/a2734a) of size 39.789 KB
[/LIST]
[URL="https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat85-inst.html"]
Official install instructions are here.[/URL]
[New Features and Resolved issues can be found here.]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html#194695")

are this deb's also for 64-bit ubuntu?

---

### Post by bebox on 2008-05-26
> **bebox said:**
> are this deb's also for 64-bit ubuntu?

they are not...has anybody 64-bit debs?

---

### Post by excogitation on 2008-05-26
I think you only have to run
./ati-driver-installer-8-5-x86.x86_64.run --buildpkg ubuntu/hardy
on your system to get those generated.

---

### Post by bebox on 2008-05-27
> **excogitation said:**
> I think you only have to run
./ati-driver-installer-8-5-x86.x86_64.run --buildpkg ubuntu/hardy
on your system to get those generated.

yes i tried that but it was not working..i had some errors..i fixed it now.

---

### Post by Stuk on 2008-05-27
Despite having the restricted fglrx driver enabled, my fglrxinfo always said Mesa was in use.

Does this update fix this problem? I saw an Ubuntu fglrx update was rolled out this morning, but nothing changed :(

Stu

---

### Post by excogitation on 2008-05-27
Did you enable "System -> Administration -> Hardware Drivers -> Ati ... driver"?

---

### Post by Stuk on 2008-05-28
Yep. Sorry, that's what I meant by "having the restricted fglrx driver enabled".

I've tried disable > restart > enable >restart etc. but I have a feeling it's something more fundamental than that.

---

### Post by excogitation on 2008-05-28
> **Stuk said:**
> Despite having the restricted fglrx driver enabled, my fglrxinfo always said Mesa was in use.

Does this update fix this problem? I saw an Ubuntu fglrx update was rolled out this morning, but nothing changed :(

Stu

I guess it's not really the driver's fault (could be wrong here) - so an update probably won't change anything.

Anyways - I don't know how to get it working on your machine.

---

### Post by zgornel on 2008-05-28
> **Stuk said:**
> Yep. Sorry, that's what I meant by "having the restricted fglrx driver enabled".

I've tried disable > restart > enable >restart etc. but I have a feeling it's something more fundamental than that.

Actually, that needs to be disabled if you want to run the drivers from the AMD site (catalyst 8.5). Please check here : [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) . Also, another thing that need to be known, if you revert back to older versions from 8.5, you might have problems in getting the kernel to recognize fglrx.ko because starting from 8.5 the driver uses dkms (dynamic kernel module support).
To check whether you have a good installation (after you install the debs or run the installer): 
```
sudo modprobe fglrx
```
If you get an error that the module is not found, search for fglrx.ko in /lib/modules/<kernel-version> and if it is there, manually insert it. Then restart the X server (ALT+CTRL+Backspace). Run ```
fglrxinfo
``` and if no 'Mesa' appears than it's all ok ;)

---

### Post by excogitation on 2008-05-28
> **zgornel said:**
> Actually, that needs to be disabled if you want to run the drivers from the AMD site (catalyst 8.5).

Well... that's not true
> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7537 Release


---

### Post by zgornel on 2008-05-29
Could you check the file: /etc/default/linux-restricted-modules-common to see if fglrx is disabled ?  Might be that it works the same if it is enabled.

---

### Post by excogitation on 2008-05-29
[URL="http://pastebin.com/m4f7cb0cc"]/etc/default/linux-restricted-modules-common
[/URL]

---

### Post by zgornel on 2008-05-30
> **excogitation said:**
> [URL="http://pastebin.com/m4f7cb0cc"]/etc/default/linux-restricted-modules-common
[/URL]

Well, it seems that it works also without adding it to the blocked restricted modules !

---

### Post by Fenris_rising on 2008-06-01
hi all
ive just tried doing this. ive been messing with my graphic drivers for days now. i managed to create the .deb files and installed them then after using the --initial command i turned on the restricted drivers and restarted. well i got a screen up ok but it was stretched in hieght and seemed compressed in width though it fitted the screen. i couldnt see the top bar but was able to blindly mouse to turn off the restricted drivers so im back to a normal screen. should i have had the restricted drivers turned on before creating the .deb files? i did get an error with the --initial command (cant remember what it said) when it was writting to the xorg.conf.
any pointers will be gratefully recieved. im running a X300 radeon pcie card.

---

### Post by sim-value on 2008-06-04
you would have just needed to set your Resolution ...

---

### Post by Fenris_rising on 2008-06-04
did that thanks! so what have i gained........bugger all! infact my keyboard now thinks its symbols are every where except on the correct keys. 
despite the restricted drivers being switched on ive lost the normal and extra options for the desktop (the screen goes white) and having disabled the restricted drivers rebooted enabled them and rebooted i still have the white screen if i try to enable normal or extra. infact i even seem to have 1 mesa 7.0.3-vr2 running now. what do i do now please???? heres my zorg.conf. ive corrected the keyboard back to uk. fglrxinfo gives.

```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
```


```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP L1740 LCD Flat Panel Monitor"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by sim-value on 2008-06-04
Well... in your xorg.conf it says you use "ati" driver not fglrx ...

Oh and BTW i didnt say it will work it doesnt work on my PC only that the Resolution is normal again !

---

### Post by Fenris_rising on 2008-06-04
hi there, noooooo not blaming you m8. currently think that was a failsafe xorg. gawd ive buggered it now cpu running at 100% windows crawling up the screen bugger bugger bugger! i need to do something to get back to the good file!

---

### Post by sim-value on 2008-06-05
ok ... interesting Result i never had that ... anyway ....

just do  sudo dpkg-reconfigure -phigh xserver-xorg then you are gonna have a generic xorg.conf then you can do aticonfig --initial -f and then nano /etc/X11/xorg.conf and here > SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection


add Resolution 1024x768 or whatever your resolution ist ....
And then either 
a) it works
b) it works but you still have mesa as renderer
c) The  man in black are going to fetch you ..

---

### Post by Fenris_rising on 2008-06-05
hi there

did that got the mesa drivers back .....yuck.......slow slow slow. i did my favorite and reinstalled the whole system lololol.

---

### Post by excogitation on 2008-06-18
reinstalling a system must still be in a lot of peoples heads from the win98/bluescreen aera.

I've even moved my XP install cross 2 laptops and never needed to install fresh.

Don't you have better things to do with your time?

Anyways new drivers are out.

---

### Post by markbuntu on 2008-06-18
The only way I ever got rid of the mesa drivers was with a reinstall.

Anyway, the proper way to install the 8.5 driver is here:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I don't know about other guides but this one works for sure and covers all the bases.
If you want to tweak the driver for maximum performance you can go here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

These tweaks make a huge difference in speed and cpu loading, etc. be sure to thank djdoo if they help you.

If you have a newer card and a fast cpu you can fool around with the TextureVideo setting to get rid of flickering in windowed videos and best full screen play.

---

