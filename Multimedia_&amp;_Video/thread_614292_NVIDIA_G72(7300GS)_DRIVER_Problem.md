---
title: "NVIDIA G72(7300GS) DRIVER Problem"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by ryrene on 2007-11-15
Hello... I have just received my cd of ubunto and i decided to install it yesterday. Everything went perfectly well until i started to configure the video settings. My video card is nvidia gforce g72(7300). The  video card can't be enabled and the video settings reverts back to its default (as if  there is no video card). What should i do? Im just a new user. Pls help.. Tnx

---

### Post by Qwerty_ on 2007-11-16
Hi Ryrene, have you tried to install the restricted drivers?

System>Administration>Restricted Drivers Manager.

---

### Post by ryrene on 2007-11-16
yep, i tried to enable the driver but it says that nvidia-glx-new can't be found.. does it come with the cd or do you need to download it from the internet?? tnx for the reply ^^

---

### Post by erginemr on 2007-11-16
Hello and Welcome to Ubuntu Forums!

To be able to download and install nvidia-glx-new, you may need to enable other repositories too, which is done via Synaptic -> Settings -> Repositories. Have a look at the scheenshots that I have attached and you will understand.

Also, I advise you to install "compizconfig-settings-manager" (3rd and 4th screenshots) after you install NVIDIA drivers, which will allow you to customize Compiz-Fusion effects to your liking.

Welcome Again!

---

### Post by erginemr on 2007-11-16
Here are the screenshots that I have promised...

---

### Post by erginemr on 2007-11-16
Finally: Never ever think of installing NVIDIA drivers from their site. If you follow that path, you will need to reinstall it each time you update your kernel. (Ubuntu developers release kernel updates periodically via the Update Manager.)

I have seen a lot of people on the forums having done that, who later on had to deal with kernal incompatibility issues. In a nutshell, the best and safest way is to install it via Ubuntu repositories.

---

### Post by Buster_Merryfield on 2008-05-10
I have some problem with me ubuntu also... When i do what ever u said... I have that special effect thingy and its all great... But my max screen resolution is just 640x480px?! What can i do about that?!

Please help... I really like ubuntu and i don't want to get back to wind****

---

### Post by erginemr on 2008-05-10
Welcome to Ubuntu! No promises but I'll do my best.

First, can you please post the output of a few diagnostic commands from the terminal:

1. What is your monitor brand and type (CRT, wide-screen)? Or if laptop, your laptop brand? What is your monitor's natural resolution?

2. Your video card (although you have already stated as NVidia 7300GS, anyway, just to make sure that your system recognizes it):
```
lspci | grep -i vga
```

3. Whether you have 3D enabled:
```
**glxinfo** | grep -i direct
```

4. The contents of your graphics configuration file:
```
gedit /etc/X11/xorg.conf
```

5. Which driver package have you installed? nvidia-glx-new?

---

### Post by Buster_Merryfield on 2008-05-10
1st of all tnx for replying and spendig your time with me.
2nd tnx for welcoming, i allways wanted to install some kind of linux on my comp, but i never had mine. And i want to learn how to use its potentials and to learn how to customize it and stuff like that. Now i got my own computer, and this is my 1st touch with linux...
Ubuntu is quite easy to install and pretty much fast... That is my 1st imressions...
Back to the problem...

I have 3.6 processor, 7300gs nvidia, 2gig ddr2 ram in dual mode... And ASUS wide screen with his native resolution of 1680x1050 60hz

When i installed Ubuntu, i had only two possible screen resolutions: 800x600 and 640x480.
The sound was working, and all that stuff... Except the graphic card... I downloaded some drivers from nVidia site. And it worked. I mean i had all those special effects stuff BUT then i had only one resolution 640x480.
Then i fallowed your previous instructions and got the same thing.

So... Here is the thing that u wanted...

```
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

```

i now disabled 3d mode, but i know how to enable it but here is the second stuff

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

3rd without that #intro stuff
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

1st i did not know where to type all those commands :D I'm a total noob here... But i'm learing! :D

TNX ONCE AGAIN! Milan

---

### Post by Buster_Merryfield on 2008-05-10
One more question. What about all those updates?! Should i install them all?! I have blinking icon and showing me that i have 59 updates available...

And one more thing... I installed Ubuntu from windows... And i selected 10gigs of space for Ubuntu. I still see D: partition (the one with Ubuntu) and i still see files on D: But from Ubuntu... I can only see C: partition with windows... I can't see D:    Why is that?!


Thanks

---

### Post by erginemr on 2008-05-11
> **Buster_Merryfield said:**
> One more question. What about all those updates?! Should i install them all?! I have blinking icon and showing me that i have 59 updates available...

And one more thing... I installed Ubuntu from windows... And i selected 10gigs of space for Ubuntu. I still see D: partition (the one with Ubuntu) and i still see files on D: But from Ubuntu... I can only see C: partition with windows... I can't see D:    Why is that?!

Thanks

You are most welcome. Don't worry, we all started as noobs. You will be a Linux Pro in no time. :)

Yes, you should install all updates, including the one for Compiz, which will supposedly put an end to the hard freeze/hang problems of many users of Hardy. Hardy is a pretty fresh new system and these updates will surely iron some of its hard edges.

Do not forget your problem with the D: partition, and put it forward again later on please. But for the time being, let's put that one aside and focus on the resolution problem...

---

### Post by erginemr on 2008-05-11
Here is my X config file (I have NVidia GeForce 4 MX):
```
# <some comments here>

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
[B][COLOR="#ff0000"]	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
        SubSection      "Display"
            Depth       24
            Modes       "1024x768_75" "800x600_75" "640x480_75"
        EndSubSection
[/COLOR][/B]EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

[B][COLOR="Red"]Section "Module"
	Load		"glx"
EndSection[/COLOR][/B]
```

**(1) **Please first take a copy of this file with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
```
and then, edit it with:
```
gksudo gedit /etc/X11/xorg.conf
```
and add the lines in red to yours, with one exception:
Your modes line should read:
```

**[COLOR="Red"]            Modes       "1680x1050_60" "1280x800_60"[/COLOR]**

```
instead.

**(2) **By the way, my apologies but the command before I gave you had a typo, the correct one to check whether glx (3-D) is enabled is:
```
glxinfo | grep -i direct
```

**(3)** Restart your X server with Ctrl+Alt+BackSpace. Do you now get 1680x1050?

**(4)** Otherwise, you can restore your previous settings with:
```
sudo cp /etc/X11/xorg.conf.working /etc/X11/xorg.conf
```
and install nvidia-settings with:
```
sudo aptitude install nvidia-settings
```
This is a tool by NVidia to adjust several settings for your graphics. It will put a launcher under Main Menu -> Applications -> System or you can run it with: 
```
Alt+F2 -> gksudo nvidia-settings
```

Please try the 1680x1050 resolution there, and allow it to write the new settings when asked.

Good Luck!.. [-o<

---

### Post by Buster_Merryfield on 2008-05-11
I have do what ever you told me... But still i have no higher resolutions 
then 640x480... This is my xorg.conf file now:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050_60"	"1280x800_60"
	EndSubSection
	
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

But I can't see any other resolutions then 640x480 and 320x240... And from that nvidia stuff either... What can i do now?! 
p.s. i enabled 3d stuff before i did anything...
```
direct rendering: Yes

```

One funny thing is... When i disable 3D... I have a choice between 800x600 and 640x480. But when i enable 3D i have only 640x480 and 320x240... LolZ.... Tnx for reading this long post and tnx for trying to help me.

\/ Peace

---

### Post by erginemr on 2008-05-11
I am sorry that it didn't work out as expected. 

Now that you have your backup already, please try this one:
[http://ubuntuforums.org/showpost.php?p=4583023&postcount=4](http://ubuntuforums.org/showpost.php?p=4583023&postcount=4)
Item #5, that involves using dpkg-reconfigure from the console.

If this doesn't work either, I'll ask you to install and run EnvyNG to install and configure the driver from the NVidia web site: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

These two testimonies also point to the use of EnvyNG:
[http://ubuntuforums.org/showpost.php?p=2210973&postcount=176](http://ubuntuforums.org/showpost.php?p=2210973&postcount=176)
[http://ubuntuforums.org/showpost.php?p=4904865&postcount=414](http://ubuntuforums.org/showpost.php?p=4904865&postcount=414)

which you should resort to if the above steps don't do any good.

---

### Post by erginemr on 2008-05-11
This line:
```
Option		"UseFBDev"	"true"
```
is strange to me. Does commenting out that one with:
```
**#** Option		"UseFBDev"	"true"
```
make any difference?

From Google:
> [I]DESCRIPTION
       fbdevhw  provides functions for talking to a framebuffer device.  It is
       os-specific.  It is a submodule used by other video drivers.  A fbdevhw
       module is currently available for 1 framebuffer devices.

       fbdev(4x)  is a non-accelerated driver which runs on top of the fbdevhw
       module.  fbdevhw can be used by other  drivers  too,  this  is  usually
       activated with `Option "UseFBDev"' in the device section.[/I]

I think you should try disabling / deleting this line.

---

### Post by Buster_Merryfield on 2008-05-11
Why Ubuntu always restore to NOT 3D option after reboot?! Anytime i reboot... It turns back to the previous state?!

---

### Post by erginemr on 2008-05-11
> **Buster_Merryfield said:**
> Why Ubuntu always restore to NOT 3D option after reboot?! Anytime i reboot... It turns back to the previous state?!

You should disable 3-D (Compiz) once and for all, that is; until you solve your resolution problem. I'd say, forget about it. Let's cope with it the Cartesian way: one by one.

---

### Post by Buster_Merryfield on 2008-05-11
I disabled that 3D stuff... And i'm confused now a little bit... I dunno why i can't see other resolutions after i added that "modes" thingy...

Anyway... I will install fresh copy of Ubuntu and then post here again.... To be shure that i did everything right.. 

Peace and tnx once again for helping me!


Milan

---

