---
title: "ATI Radeon Xpress 200M"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by jamieplucinski on 2006-10-27
Hi. I am having some problems with getting my graphics card to work under Ubuntu.

My graphics card is an ATI Radeon Xpress 200M PCI-Express card on a Compaq Presario R4225CA laptop. LSPCI lists the card as:
```
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

```

LSPCI -n lists my card as a:
```
01:05.0 0300: 1002:5955
```

I have tried every howto I can find to get my card working with 3d acceleration, but os far all attempts end with Ubuntu displaying a completely black screen after starting up (right before GDM should load). No X-Server errors are displayed, and the only way I can get back into Ubuntu is to boot into recovery mode and restore my /etc/X11/xorg.conf backup file.

I have tried manually going into the configuration file and changing my driver from ati to fglrx, aticonfig --initial and then the overlay=Xv bits too. Nothing works.

Right now fglrxinfo dumps the following:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

And my xorg.conf device section contains the following:
```
Section "Device"
	Identifier	"ATI Radeon Xpress 200M"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection
```

I would be extremely grateful is someone could help me out here; I really want to ditch Windows for Linux but I can't stand to spend the rest of my computing life with a system that can't even run my screen saver or any of the 3D games out there...

Thanks in advance,
Jamie :confused:

PS: I am using Edgy Eft i386, uname -r dumps:
```
2.6.17-10-generic
```

---

### Post by nbound on 2006-10-27
Same problem here... tried many things all to no avail... the fglrx module wont even load. its strange though as this card has worked fine in both breezy and dapper with fglrx :(

---

### Post by jamieplucinski on 2006-10-27
> **nbound said:**
> Same problem here... tried many things all to no avail... the fglrx module wont even load. its strange though as this card has worked fine in both breezy and dapper with fglrx :(

You're doing better than me, I haven't been able to get my graphics card working properly on any linux distro since I got it... ](*,)

---

### Post by nbhaskar on 2006-10-28
> **jamieplucinski said:**
> You're doing better than me, I haven't been able to get my graphics card working properly on any linux distro since I got it... ](*,)

I haven't tried this in Eft but I had problems with my ATI X700 card in Dapper Drake and I got it to work by changing my xorg.conf to say the following

```
Section "Device"
	Identifier	"ATI Radeon Xpress 200M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection
```

Hope this helps you guys, let me know the results. I'm in the process of installing Eft and will let you know of the results.

---

### Post by jamieplucinski on 2006-10-28
> **nbhaskar said:**
> I haven't tried this in Eft but I had problems with my ATI X700 card in Dapper Drake and I got it to work by changing my xorg.conf to say the following

```
Section "Device"
	Identifier	"ATI Radeon Xpress 200M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection
```

Hope this helps you guys, let me know the results. I'm in the process of installing Eft and will let you know of the results.

No difference for me :( I'm back on XP for now (dual-boot). Hopefully someone finds a solution soon otherwise I'll have to go back to windows *spits* full time. :(

---

### Post by it-monkey on 2006-10-28
Same here, nothing but black screen after boot no matter which howto and guide I have followed *cries*

---

### Post by jamieplucinski on 2006-10-28
> **it-monkey said:**
> Same here, nothing but black screen after boot no matter which howto and guide I have followed *cries*

Hmmm... thank the ubuntu gods I'm not alone in this, but a solution doesn't seem to be coming out... yet. I'm not sure if it's the ATI drivers that suck, or somewhere along the line resources have been mapped to our cards thinking it's a PCI card instead of a PCI Express.

Gigantic Virtual Cookie for anyone who can help us solve this :)

---

### Post by nbound on 2006-10-28
> **it-monkey said:**
> Same here, nothing but black screen after boot no matter which howto and guide I have followed *cries*

heh, mine doesnt even load fglrx, it just sits there with the stock "ati" drivers :(

---

### Post by LoCusF on 2006-10-28
Hi!

I have a solution that might help the black screen at startup. I had the same problem with the ATI fglrx drivers, it seems that a BIOS setting is messing up with the display driver's memory. So you have to set the memory in UMA and SIDEPORT to 128 MB. Consult your laptop's BIOS program on how to set it. I have gotten a working fglrx but not using DRI.

---

### Post by nbound on 2006-10-28
I FIGURED IT OUT!!!!

download the "linux-restricted-modules-generic" package

i checked the xorg logs... and it seemed the kernel driver (one of the restricted modules) wasnt loading! so i checked the restricted modules... and none (other than common) was installed... i tried it... rebooted and YAY it worked!

I didnt have to do the UMA fix above either (luckily coz i cant :P)

---

### Post by jamieplucinski on 2006-10-28
> **nbound said:**
> I FIGURED IT OUT!!!!

download the "linux-restricted-modules-generic" package

i checked the xorg logs... and it seemed the kernel driver (one of the restricted modules) wasnt loading! so i checked the restricted modules... and none (other than common) was installed... i tried it... rebooted and YAY it worked!

I didnt have to do the UMA fix above either (luckily coz i cant :P)

Hmm, I tried the sideport method and had the restricted modules thing installed too. Could you please post a list of all of the commands you used to get it running please?

Thanks,
Jamie :D

---

### Post by nbound on 2006-10-28
i already had a failed install setup in my xorg... (instead it would load the open source drivers instead of fglrx)

all i did was install the module stated then reboot

and i came back with 3d accel :D

---

### Post by LoCusF on 2006-10-28
> i already had a failed install setup in my xorg... (instead it would load the open source drivers instead of fglrx)

all i did was install the module stated then reboot

and i came back with 3d accel

What?

I removed xorg-driver-fglrx and installed the linux-restricted-modules-generic package. No result on amd64. ](*,)

---

### Post by nbound on 2006-10-28
no keep fglrx fully installed AND run restricted modules

---

### Post by jamieplucinski on 2006-10-28
> **nbound said:**
> no keep fglrx fully installed AND run restricted modules

I already had the restricted modules installed, but still no difference. Could you post your /etc/X11/xorg.conf please?

---

### Post by LoCusF on 2006-10-28
> 
I already had the restricted modules installed, but still no difference. Could you post your /etc/X11/xorg.conf please?


Yeah post that. I have both packages now, with composite disabled in xorg.conf and now I get a really really garbled screen :)

---

### Post by LoCusF on 2006-10-28
> **LoCusF said:**
> Yeah post that. I have both packages now, with composite disabled in xorg.conf and now I get a really really garbled screen :)

Hmm. now I enabled the display adapter to use only UMA memory and now the whole thing works :o :o

---

### Post by jamieplucinski on 2006-10-28
> **LoCusF said:**
> Hmm. now I enabled the display adapter to use only UMA memory and now the whole thing works :o :o

Hmmm... so we have to dump the built-in memory on the card, then re-allocate system ram to the card to be able to use it under linux as we can already under Windows with no fuss... surely there's stupidity afoot in someone's source code...](*,)

---

### Post by LoCusF on 2006-10-28
> **jamieplucinski said:**
> Hmmm... so we have to dump the built-in memory on the card, then re-allocate system ram to the card to be able to use it under linux as we can already under Windows with no fuss... surely there's stupidity afoot in someone's source code...](*,)

Yeah tell me about it :)

---

### Post by jamieplucinski on 2006-10-28
> **LoCusF said:**
> Yeah tell me about it :)

Looks like my Ubuntu partitions will be erased and filled with Windows by the end of the weekend if nothing crops up, sorry, nothing **sensible** pops up. What the hell is the point of having a GPU running from system memory with it's own dedicated memory sitting unused, aside from being a huge hit to performance, it's also something incredibly stupid to expect people to do. Not a lot of people have the option in their BIOS to change the memory allocation for their GPU, so ATI must a) Have become pompous incredibly stupid p*i*ks or b) Spend all their time smoking weed.

](*,) ](*,) ](*,) ](*,)

---

### Post by nbound on 2006-10-28
My working xorg.conf

Module section:
```
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection
```

Video section
```
Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768"
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "false"
EndSection

```

tested with 600fps in glxgears:D

Anyone having any luck?

---

### Post by skatedawe on 2006-10-28
I installed edgy eft from fresh install & followed this method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually)

 it worked! I've been sitting all this day to fix this. 
 
 Here's  my xorg.conf

 ```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

If you got ati 200m and got strange flicker problem, change in bios to 128mb ram for graphic and follow the guide at the link.

---

### Post by nbound on 2006-10-28
Looks the same setup as mine, nice,  i didnt get the flicker problem with mine even though its only set to 32mb ram

---

### Post by jamieplucinski on 2006-10-28
With mine set to the use dedicated ram I was left with a black screen, after setting it to 128MB of my system RAM it worked again... but I'll be buggered if I am going to have 896MB of RAM and leave the 128MB sitting idle on the card. I'm going to try some different combinations of Sideport and DMA memory, if I can loose 32MB of system RAM instead it won't be so bad.

Any idea on how we can get full usage without having to loose a bunch of memory?

---

### Post by jamieplucinski on 2006-10-28
No good. Only works with sideport off and UMA/DMA set to 128MB on my system, even though my card is reported as working with the drivers.

What I am wondering is, are the drivers limited to the official ATI boards? I have an ATI chip, but a HP/Compaq custom board (as usually happens on laptops) so I am wondering if my problem stems from that? Maybe it's trying to access the memory via an incorrect address on the board, and since it's not the board it's expecting, the drivers fail.

---

### Post by nbound on 2006-10-28
Nah im using a compaq notebook too... my card doesnt have ANY onboard memory... which is probably why i dont get the probs u do... all mine is shared with the system

---

### Post by jamieplucinski on 2006-10-28
Hmmm. I have 1024MB (1GB) of system RAM and 128MB on the card. I have the option of using only the dedicated memory on the card, using both memory on the card and 32MB, 64MB, or 128MB of system RAM, or using 32MB, 64MB, or 128MB of system ram and not using the dedicated memory at all.

I think this is why I am having so many problems.

---

### Post by jamieplucinski on 2006-10-29
If enough people are experiencing this, is there a way we could open a bounty on it (doubtful since the drivers are closed), or put some pressure on ATI to give some decent support for us?

---

### Post by nbhaskar on 2006-10-29
I had this working in breezy, thanks to Gabor. When I changed "ati" to "radeon" in the Device section of xorg.conf file, the system should boot up. Hope this helps you guys.

:)

---

### Post by nbhaskar on 2006-10-29
I did install edgy on my machine and in fact I'm typing this from my machine logged on edgy.

I did have to change the Device section to say, "radeon" instead of "ati".

---

### Post by nbound on 2006-10-29
radeon is just another opensource driver isnt it? fglrx is the 3d accel one

---

### Post by jamieplucinski on 2006-10-29
> **nbhaskar said:**
> I did install edgy on my machine and in fact I'm typing this from my machine logged on edgy.

I did have to change the Device section to say, "radeon" instead of "ati".

I tried this, same as before, no 3d acceleration, so I am going back to the fglrx driver... having to loose the memory again.

---

### Post by aroswald1977 on 2006-10-31
> **nbound said:**
> I FIGURED IT OUT!!!!

download the "linux-restricted-modules-generic" package

i checked the xorg logs... and it seemed the kernel driver (one of the restricted modules) wasnt loading! so i checked the restricted modules... and none (other than common) was installed... i tried it... rebooted and YAY it worked!

I didnt have to do the UMA fix above either (luckily coz i cant :P)

What distro are you using, and could you please tell me exactly what you did, and how, in plain noobie english, so I can try the same?

where or what repo do I need to go to download that package?

---

### Post by nbound on 2006-10-31
> **aroswald1977 said:**
> What distro are you using, and could you please tell me exactly what you did, and how, in plain noobie english, so I can try the same?

where or what repo do I need to go to download that package?

Its in one of the ubuntu default ones

Im using Ubuntu Edgy 6.10 (x86)

I installed the abovementioned packaged... and then followed the guide in the wiki here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a)

Hope that helps :)

---

### Post by d-E-a-D on 2006-11-14
Hi, i have a 200m and my problem is that when i change my xorg.conf with 
Section “Extensions”

Option “Composite” “0&#8243;

EndSection
I only get a blank screen at startup, and if i turn it off i only get
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I've tried all that you people say in the forum like change sideport and uma... things like that, nothing worked.

I was using dapper with ati 8.24 drivers and it worked good using this guide: [http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m](http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m)

Does anyone can solve my problem? 
thanks

---

### Post by msdark on 2007-12-30
try with the latest driver from the ati oficial website...
these driver works for me
the version is 8.433.1 o 7.2 (the new numeration).
These driver support AIGLX and work very fine with Compiz Fusion
you dont' have to put nothing about composite extension on your /etc/X11/xorg.conf file

That's all... try it

---

### Post by Dr.Vista on 2008-01-05
I cannot use Desktop effects on my pc! I get this error message "The Composite Extension Not available". I don't know what happened! How do I check if my graphics card is the problem?I have the same card you guys have! I have a compaq notebook too! Here is a thread about that.

[http://ubuntuforums.org/showthread.php?t=658703](http://ubuntuforums.org/showthread.php?t=658703)

---

### Post by hx129 on 2008-01-06
You should enable composite extension in your /etc/X11/xorg.conf.(if you are using AIGLX instead of Xgl)

Section "Extensions"
        Option          "Composite"     "1"
EndSection

---

### Post by hx129 on 2008-01-06
Well, just a quick question. Do you have any problem using mplayer under 8.443 driver?
In my case, it doesn't work unless under full screen mode.

---

### Post by Kat of Zion on 2008-01-22
Yeah, I have been getting very laggy graphics in trying ot run portal.  GLXgears works beautifully EXCEPT  if we put the glxgears window right above our lower desktop panel.  Basically when you hover your mouse over the trashcan, the informational bubble that appears in the KDE interface upon hovering your mouse over starts bogging glxgears down.  Its almost as if glxgears dislikes running 2D stuff atop its 3D.

Any ideas?   We are still looking for the latest 200m drivers (32 bit).

---

