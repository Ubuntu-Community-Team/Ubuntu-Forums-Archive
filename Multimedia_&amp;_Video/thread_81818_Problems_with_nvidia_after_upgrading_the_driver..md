---
title: "Problems with nvidia after upgrading the driver."
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by syrex2 on 2005-10-25
Hello all :-) 
I've been upgrading my nvidia driver (with apt-get) and now I'm having freezing    apps and blank screen after a few minutes.
This problem also happend to me when I used kubuntu.

I heard about other people with the same problems with similar display card (nvidia 6xxx).

So i'm asking what is the latest nvidia driver in apt-get,and what the version in Ubuntu Breezy Badger 5.10 (that works fine for me) ?

anyone else heard about this problem?



(nvidia gigabyte 6600 gt)

thanking you in advance :-)

---

### Post by syrex2 on 2005-10-27
up

---

### Post by jamin_l on 2005-10-27
Ok I'm going to jump in here as well.

Currently running Breezy Badger. Kernel (I believe those are the results from "uname -r" in a term): 2.6.12-9-686
I have nvidia-kernel-common V. 1.0.7667+1 installed.

I have just upgraded the graphics card from an nVidia GeForce 4MX to an nVidia GeForce 6600GT AGP/VGA card.
I haven't experienced it myself, but husband reports instability in X after upgrading.

Questions:
Is this the "nv" driver I have installed on the nvidia ones? (I recall reading on nvnews.net that there are two different versions.)
Which version of the drivers is recommended?
Is there a problem that my xorg.conf file is still showing my graphics card as the GeForce 4MX or do I need to edit this manually?

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
```

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	<Description of display modes edited out to save space>
EndSection
```

Should I attempt to install the drivers here? [http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)

I also saw this [earlier thread for Hoary](http://ubuntuforums.org/showthread.php?t=57368&highlight=6600gt), but decided to ask first if the instructions would be invalid as I'm now running Breezy or if I should follow them.

Generic computer specifications:
Athlon XP 1800 (I cannot recall the clockspeed right now)
*new* nVidia GeForce 6600GT AGP8x / VGA
*old - not plugged in* nVidia GeForce 4MX
768 MB RAM

Okay, I think that's enough questions for now. Thank you in advance for any assistance provided.

---

### Post by remmurd on 2005-10-27
I'm new to Linux but have managed to install Ubuntu and get it running with an Nvidia MX4000 but had trouble with the S-video output to TV...

So, I began installing the Nvidia driver from the Nvidia web site and during install made a change to the xorg.conf file.

Basically added (#) to one line and changed the driver name from "nv" to "nvidia".

After making said changes, have not been able to log back into Ubuntu Desktop.  Get as far as the boot load then stuck at command line.

My question is this:
            How do I edit and save the "xorg.conf" file from the command line so I'll be able to get back to where I started?

Thanks in advance to anyone who can help.

---

### Post by syrex2 on 2005-11-09
Up please...

:( :( :( :( :(

---

### Post by sfink01 on 2005-11-09
I also had issues with nVidia drivers locking up my system running games through OpenGL.  They would run for a while then hard lock the system.  The drivers 7667 and 7676 were the problem.  I rolled back to 7174 and everything is fine.

I compiled the 7174 manually only to find it in Synaptic later, it's called nvidia-glx-legacy.

Try that.

Steve

---

### Post by syrex2 on 2005-11-09
ok,I'll thanks.

---

### Post by syrex2 on 2005-11-13
Works perfect,thanks :P

---

### Post by syrex2 on 2005-11-13
problems are back :-\

another suggestion?

---

### Post by syrex2 on 2005-11-18
a:???: :???: :???: :???: :???: :???:

---

### Post by Teroedni on 2005-11-18
Can you be a little more specific .Which apps?

---

### Post by syrex2 on 2005-11-18
[QUOTE=Teroedni]Can you be a little more specific .Which apps?[/QUOTE]

All the apps,it's starting with one and goes to anther,after a few minutes all the the Window manger is getting white...
Sometimes after the software is getting white is working regular after moving to another software and back to the first 1...

Maybe it's gnome?

Thanks.

---

### Post by Teroedni on 2005-11-18
What hardware do you got
How strong cpu 
How much ram
Sound card and the others

---

### Post by syrex2 on 2005-11-18
[QUOTE=Teroedni]What hardware do you got
How strong cpu 
How much ram
Sound card and the others[/QUOTE]

AMD Athlon(tm) 64 Processor 3000+
Gigabyte GA-K8N Pro-SLI 
Realtek AC97 Audio (sound card OB)
Twinmos 512MB x2 DDR-SDRAM ( PC3200U 2.5-3-3-8 ) 
NVIDIA GeForce 6600 GT Gigabyte x16 128MB 
WD 40 GB 7200

---

### Post by tseliot on 2005-11-19
[QUOTE=jamin_l]Ok I'm going to jump in here as well.

Currently running Breezy Badger. Kernel (I believe those are the results from "uname -r" in a term): 2.6.12-9-686
I have nvidia-kernel-common V. 1.0.7667+1 installed.

I have just upgraded the graphics card from an nVidia GeForce 4MX to an nVidia GeForce 6600GT AGP/VGA card.
I haven't experienced it myself, but husband reports instability in X after upgrading.

Questions:
Is this the "nv" driver I have installed on the nvidia ones? (I recall reading on nvnews.net that there are two different versions.)
Which version of the drivers is recommended?
Is there a problem that my xorg.conf file is still showing my graphics card as the GeForce 4MX or do I need to edit this manually?

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
```

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	<Description of display modes edited out to save space>
EndSection
```

Should I attempt to install the drivers here? [http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)

I also saw this [earlier thread for Hoary](http://ubuntuforums.org/showthread.php?t=57368&highlight=6600gt), but decided to ask first if the instructions would be invalid as I'm now running Breezy or if I should follow them.

Generic computer specifications:
Athlon XP 1800 (I cannot recall the clockspeed right now)
*new* nVidia GeForce 6600GT AGP8x / VGA
*old - not plugged in* nVidia GeForce 4MX
768 MB RAM

Okay, I think that's enough questions for now. Thank you in advance for any assistance provided.[/QUOTE]

First off I made a new guide for Breezy [HOWTO: Latest NVIDIA drivers]("http://ubuntuforums.org/showthread.php?t=75074")

If you have changed your graphic card you can type:

```
sudo dpkg-reconfigure xserver-xorg
```

If you don't know how to answer the other questions you can use the suggested answers (which will work) by pressing ENTER (without typing anything).

---

### Post by tseliot on 2005-11-19
[QUOTE=syrex2]Hello all :-) 
I've been upgrading my nvidia driver (with apt-get) and now I'm having freezing    apps and blank screen after a few minutes.
This problem also happend to me when I used kubuntu.

I heard about other people with the same problems with similar display card (nvidia 6xxx).

So i'm asking what is the latest nvidia driver in apt-get,and what the version in Ubuntu Breezy Badger 5.10 (that works fine for me) ?

anyone else heard about this problem?[/QUOTE]


sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file (DO NOT add the blue line now):

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

[COLOR="Red"]If it doesn't solve the problem add the Blue line[/COLOR]

---

### Post by wadeall on 2005-11-26
I'm new to Liux (as of yesterday) so cannot give any answers but seem to be suffering from the same problem (after being loged on Ubunto for 10-15 minutes my screen will freeze or the screen will start to fill with white and balck lines.  Ive got a XFX nvidea Geforce 6600GT videeo card so it sounds as though this could be the problem.

Wade:(

---

### Post by pedroleouf on 2005-11-26
Just to say that when you install the nvidia driver (apt-get install nvidia-glx) you must edit your xorg.conf and in the Module section, comments theese lines:
```
Load    "GLcore"
Load    "dri"
``` and add ```
Load    "glx"
``` After, in the Device section of your video card, replace the line ```
Driver    "nv"
``` by this one: ```
Driver    "nvidia"
``` 
Perhaps it could help you. Sorry if not

---

### Post by Teroedni on 2005-11-27
Could you post your xorg and xorg.log files?


Also have you overclocked your card ?
Thanks:)

---

### Post by bonbon64 on 2006-01-16
hi this my first post here, just installed ubuntu 5.10 -- 2.6.12-10-386 not to long ago everything went fine exept it keeps hard locking all that moves is the curser i have installed the latist nvidia drivers NVIDIA-Linux-x86-1.0-8178-pkg1, i even did a clean install to see if i could stop it happening

added my xorg log
and xorg.conf

any ideas

ben

athlon xp amd 2400+, gigabyte k7 mobo, gforce 6600 128mb,

---

