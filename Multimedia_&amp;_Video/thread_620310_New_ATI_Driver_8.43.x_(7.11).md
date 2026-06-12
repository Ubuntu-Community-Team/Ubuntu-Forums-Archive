---
title: "New ATI Driver 8.43.x (7.11)"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by kshane on 2007-11-22
Has any body else installed the ATI driver released yesterday (8.43.x - (7.11)?  I just installed it a few minutes ago.  I don't see a whole lot of difference so far.  I'm running an ATI Radeon X1650 and using the Compiz from the Ubuntu repositories.  I still can't use smooth scrolling in Firefox.

Kevin

---

### Post by acoustibop on 2007-11-22
How did you install it, Kevin?

---

### Post by Melcar on 2007-11-22
Nothing seems to have changed for me.  Compiz + AIGLX is still practically unusable.

---

### Post by kshane on 2007-11-22
> **acoustibop said:**
> How did you install it, Kevin?

```

sudo sh ./ati-driver-installer-7-11-x86.x86_64.run

```

Went in very smoothly...

Kevin

---

### Post by kshane on 2007-11-22
> **Melcar said:**
> Nothing seems to have changed for me.  Compiz + AIGLX is still practically unusable.

About the same here.  Glxgears is running faster, though.  I'm getting 300-400 fps more than before.

```

kevin@enigma:~$ glxgears
17882 frames in 5.0 seconds = 3576.389 FPS
18083 frames in 5.0 seconds = 3616.581 FPS
18134 frames in 5.0 seconds = 3626.796 FPS
18096 frames in 5.0 seconds = 3619.057 FPS
18113 frames in 5.0 seconds = 3622.575 FPS

```

I'm still playing around with things to see how it goes.  If I run into anything "new", I'll post it.

Kevin

---

### Post by adarkenigma on 2007-11-22
so these drivers are bad as last ones? xgl is still better?

---

### Post by yavor_bg on 2007-11-23
I'm new Linux user.
I'm with Ubuntu 7.10 and Radeon9800XT . I try to install new Ati driver. 
I run code:
```
sudo sh ./ati-driver-installer-7-11-x86.x86_64.run
```
and after installation complete I restart my system.
When I try to run ATI Catalyst Control Center I get this message: 
[http://img406.imageshack.us/my.php?image=screenshotsb3.jpg](http://img406.imageshack.us/my.php?image=screenshotsb3.jpg)

---

### Post by Ber P on 2007-11-23
I've just managed to install it. As others already posted, it seems that there are no improvements from 8.42. Same FPS, and still very poor performance with Compiz. 

Hope the next one is better....:neutral:

---

### Post by kshane on 2007-11-23
> **Ber P said:**
> I've just managed to install it. As others already posted, it seems that there are no improvements from 8.42. Same FPS, and still very poor performance with Compiz. 

Hope the next one is better....:neutral:

Yes, I agree.  I see a little bit better frame rate, but it's still buggy.

Kevin

---

### Post by kshane on 2007-11-23
> **adarkenigma said:**
> so these drivers are bad as last ones? xgl is still better?

I'm keeping the new one (7.11) installed.  Like I said, it's buggy, but I can still do everything I do and run AIGLX for Compiz, and Compiz works better for me with AIGLX as opposed to XGL

I, too, hope the next release is better.  It seems from my readings that this release had more to do with specific issues with the newer ATI cards.  Got my fingers crossed on the next release...

Kevin

---

### Post by kshane on 2007-11-23
> **yavor_bg said:**
> I'm new Linux user.
I'm with Ubuntu 7.10 and Radeon9800XT . I try to install new Ati driver. 
I run code:
```
sudo sh ./ati-driver-installer-7-11-x86.x86_64.run
```
and after installation complete I restart my system.
When I try to run ATI Catalyst Control Center I get this message: 
[http://img406.imageshack.us/my.php?image=screenshotsb3.jpg](http://img406.imageshack.us/my.php?image=screenshotsb3.jpg)

I believe the fix for you is to run the following in a terminal:
```

aticonfig --initial

```

---

### Post by RemmyLee on 2007-11-23
I've got them installed and I can see a very noticable difference in gaming.

Both Quake 3 Arena and Quake 4 run faster. Q3A, with full anti-aliasing and anisotropic, runs absolutely perfect.

I'm not in to the whole flashy desktop thing myself, but the OpenGL support is getting better with each release.

---

### Post by yavor_bg on 2007-11-23
when I run the following in a terminal:
```
aticonfig --initial
```

I received this message:
```
yavor@yavor-desktop:~$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
yavor@yavor-desktop:~$ 
```

What this mean?:(

---

### Post by stunner on 2007-11-23
[http://ubuntuforums.org/showpost.php?p=3336554&postcount=3]("http://ubuntuforums.org/showpost.php?p=3336554&postcount=3")

---

### Post by kshane on 2007-11-23
> **yavor_bg said:**
> when I run the following in a terminal:
```
aticonfig --initial
```

I received this message:
```
yavor@yavor-desktop:~$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
yavor@yavor-desktop:~$ 
```

What this mean?:(

Post your /etc/X11/xorg.conf and the ouput from fglrxinfo

Kevin

---

### Post by Hero of Time on 2007-11-23
What is the best course to install this version? Is it best to remove previous fglrx packages, then reboot and install this one via CLI, or can it be installed on top of the currently installed version?

Also, how can I see on what video mode Compiz-Fusion is running (xgl or aiglx)?

---

### Post by acoustibop on 2007-11-23
> **yavor_bg said:**
> when I run the following in a terminal:
```
aticonfig --initial
```

I received this message:
```
yavor@yavor-desktop:~$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
yavor@yavor-desktop:~$ 
```

What this mean?:(

Try
```
sudo aticonfig --initial
```

---

### Post by yavor_bg on 2007-11-23
Here is my /etc/X11/xorg.conf post and the ouput from fglrxinfo:
Is there anything wrong?:confused:

```
yavor@yavor-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

```

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SDM-E96D"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Monitor    "SDM-E96D"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

What do you think about this with the new Ati driver on my 9800XT?
I think it is very bad result.
```
yavor@yavor-desktop:~$ glxgears
1466 frames in 5.2 seconds = 279.282 FPS
1469 frames in 5.2 seconds = 280.237 FPS
1469 frames in 5.2 seconds = 283.958 FPS
1469 frames in 5.3 seconds = 279.709 FPS
1469 frames in 5.3 seconds = 279.416 FPS

```

---

### Post by Hero of Time on 2007-11-23
Your driver isn't installed correctly. You still have the Mesa driver, which does function, but not properly. Try to install the driver again. If needed, remove the old packages first via Synaptic and install the driver manually from CLI.

---

### Post by sanraj83 on 2007-11-23
Hi, 

  I have a ati x300 on a Thinkpad T43. I use the following script from sabriah posted in [http://www.phoronix.com/forums/showthread.php?t=6583&page=9](http://www.phoronix.com/forums/showthread.php?t=6583&page=9)

Script:

[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

 I would just download the script, press cntr+alt+f1 and get to the terminal. Then change it into a executable as root, then just run it. It did all the magic and I had the latest driver installed. 

sudo chmod +x ./install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh

To get Xv working, just type 

sudo aticonfig --overlay-type=Xv in a  terminal and restart your system. 

My laptop runs fine and I can use the inbuilt compositor in XFCE4 with no troubles on a Dual head mode. 

But adding the  AIGLX section seems to create problems.

Section "ServerLayout"
    Option "AIGLX" "True"
EndSection

-- R

---

### Post by guris on 2007-11-23
WTF? I just installed this drivers and they are slower than .42, I have 200m card and before it was like 1500fps and now its only 1200 .  I am NOT happy :(
However the brighness and colors are better that in old drivers, but they are slower, at least on my pc. It's sad. :(

---

### Post by Yellow Pasque on 2007-11-24
I installed them, but still got the same screen corruption as I did with the last release (using 690G/X1250). AIGLX performance was improved though, so it seems they're making progress on the newer cards.

Anyway, I can't stand the screen corruption, so I went back to 8.40.4

---

### Post by Casual Fan on 2007-11-24
Does the newest driver fix the suspend/hibernate issues that folks with ATI cards have been having?

---

### Post by Melcar on 2007-11-24
> **Casual Fan said:**
> Does the newest driver fix the suspend/hibernate issues that folks with ATI cards have been having?


I think nvidia drivers have a similar issue also.  Anyway, these new drivers don't really do anything for me; performance is still good (no increase/decreases from the previous version), the random screen corruption at the corners of the screen and around the mouse is still present, running Compiz still messes with full screen opengl applications, and screen tearing in full screen 3d apps. is still present.

---

### Post by Lagos on 2007-11-25
for anyone that thinks the new driver is slower...  type "fglrxinfo" in the console. if it says Mesa, then your install didnt work correctly and you are stuck with the generic mesa driver.

---

### Post by macaholic on 2007-11-25
I'd just like to point out, installing just by running the .run file is the probably the worst way to go about installing these drivers. You would be much better off following [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") instead.
Yes these drivers are still bad under AIGLX, but they aren't terrible (for me anyway), I get
```
48963 frames in 5.0 seconds = 9792.529 FPS
54156 frames in 5.0 seconds = 10831.103 FPS
46084 frames in 5.0 seconds = 9216.718 FPS

``` 
when running glxgears, still compiz performance is bad. :( But have no fear, things will improve.

---

### Post by guris on 2007-11-25
**macaholic**

Thank you for the link. I'm gonna try it now. 
According to fglrxinfo I have latest drivers now, but I'm not sure they are properly installed.  I have integrated mobile ati 1150 chip. It's not very powerfull, however,  I can play UT2004 and Quake A3 without a lag . I'm not saying that this is bad drivers, but Copmpiz and suspend still doesn't work and ugly black brick sometimes appears on the screen, and its quite annoying. I guess the only way is to recompile kernel to use SLAB to use full of this driver's potenial. But I'm afraid to break something. I really like  suspend to work on my laptop.  Later I will try it maybe.

---

### Post by mamlouk on 2007-11-25
> **yavor_bg said:**
> Here is my /etc/X11/xorg.conf post and the ouput from fglrxinfo:
Is there anything wrong?:confused:
First as someone said earlier, try ```
sudo aticonfig --initial
```
If that didn't fix it, I have noticed that you have 2 devices in you xorg.conf. First one works on the ATI open source driver (ati), and the second works on the ATI Proprietary driver (fglrx). Try commenting the open source ati one. Also, copy the BusID part from the ati driver and paste it in the fglrx. So, you xorg.conf should have: ```
#Section "Device"
	#Identifier  "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	#Driver      "ati"
	#BusID       "PCI:1:0:0"
#EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection
```
Only remember to backup your original xorg.conf file so that you can go back to it any time.

Now, here's my situation. I had 8.42.3 installed, with compiz running on it, but only on my 2.6.22-14-generic kernel. I has happy 7.11 was released because it will work on my 2.6.23 kernel. I installed it as per [cchtml](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide), when I rebooted my screen wouldn't go any higher than 1024x768. I read on the forums about re-running the .run file, and I did, rebooted and got my resolution back, compiz, and everything. However, when I fglrxinfo, I get: ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.1.7059 Release
``` But when I run glxinfo | grep direct, I get ```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
``` Any ideas?

---

### Post by Dynar on 2007-11-26
I still need a driver for my ATi Radeon 9550. I've tried almost anything. I can't play a single game at the moment. If I can get it running that is.. such as Quake 3. I got it updated and everything, just no OpenGL. Guess I'll be stuck with those Mesa drivers.

I do however got myself some Eye-candy, it's the only thing I can really improve.

---

### Post by kshane on 2007-12-03
After playing with the new driver, I have decided to keep it, but I have removed Compiz.  It slows my system way down and really does no functional good.  Like I posted earlier, I'm looking forward to the next release.  I would dearly love to run Compiz and my games with no hassles or need for tweaking the system.  

Fingers crossed!

Kevin

---

### Post by kthijs on 2007-12-05
This ati driver works pretty good for me I guess. glxgears gets me:

26216 frames in 5.0 seconds = 5243.095 FPS
26257 frames in 5.0 seconds = 5251.261 FPS
26233 frames in 5.0 seconds = 5246.576 FPS
26100 frames in 5.0 seconds = 5219.927 FPS

My card is an ati mobility radeon x700. I haven't tried any games though.

---

### Post by Sef on 2007-12-05
> After playing with the new driver, I have decided to keep it, but I have removed Compiz. It slows my system way down and really does no functional good. Like I posted earlier, I'm looking forward to the next release. I would dearly love to run Compiz and my games with no hassles or need for tweaking the system.


How much ram do you have?   What is your motherboard and CPU?

---

### Post by X-dark on 2007-12-07
Did somebody manage to install this driver with the realtime kernel and Ubuntu 64bits ?

---

### Post by Yellow Pasque on 2007-12-07
> **Sef said:**
> How much ram do you have?   What is your motherboard and CPU?
My experience with Compiz was similar. I have a 2.5GHz X2 4800 and 2GB DDR2-667 (dual channel). My video is the integrated X1250 (690G chipset mobo). My machine should have plenty of power to slice through the desktop effects, but instead, they were laggy and consumed a lot of CPU.

And yes, I had fglrx set up properly to use the vid card/direct rendering and not Mesa. Ironically, the desktop effects worked perfectly in the LiveCD when I had my X300 card (used it in another build).

I can live without the effects, so it's not a big deal to me, but some people seem really attached to them.

---

### Post by nasov on 2007-12-09
I experience the same problem as mamolouk... anyone else?

glxgears crashes X
fglrxinfo does the same but then i throws me back to the login screen.
after another login when i type fglrxinfo i get the proper ATI x1300 info

any ideas anyone?

im about to install DRi from dri.freedesktop.org

if ill suceed i'll post if not i'll post as well.

---

### Post by dark_harmonics on 2007-12-10
I'm having an issue where running a single-head system works fine but running a dual-head system returns an error that has says something about "glibc double free or corruption" and then has a core dump. This really throws a wrench into amy dual-head system. Its so nice to have dual screens. At least with the old, open source drivers I could utilize the separate screens (if not as fast).

---

