---
title: "Why does my nvidia card hate me?"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by whaevr on 2008-03-02
So heres my sob story, I'm going to use as many pictures here as I can and provide as much information as I can because frankly I'm sick of these not working.

Heres my computer setup, my motherboard has an onboard intel graphics chip. Although I do have an nvidia geforce 6800 card. 

Heres a picture of them in Ubuntu
[IMG]http://i116.photobucket.com/albums/o26/photos_r_me/desktop.jpg[/IMG]

So heres the start of my problems, my system uses the nvidia card to boot up. I pretty much don't use the Intel card anymore- at all. So when I downloaded the Ubuntu cd and poped it in and selected the first option, Ubuntu starts to load. Then all a sudden the loading bar goes crazy and it like split in 3 and gets all pixelated and just stops.

So I restart comp, and try in safe graphics mode....same thing. Now here I'm going to skip hours of trying random things I did, including redownloading Ubuntu twice, etc etc.
Finally I figure out that I needed to use the Intel card in order to get Ubuntu to load- even in safe graphics mode.So first I set Bios to boot with Intel, then I go to the back of my computer unscrew the blue cable from the nivida slot and then screw it into the Intel slot.

Cool, Ubuntu starts in normal mode, I install it and restart. Boot into Ubuntu just fine with a high resolution and everything, Ubuntu informs me that there is restricted drivers that I have to install. I click it, its for my nvidia card. Fine, I installed it and rebooted. Now I go back into Ubuntu (still on Intel) and the resolution is like 800x600 instead of 1280x1024.

So now Ubuntu tells me its in safe graphics mode, I hit configure (never logged in Ubuntu yet) and messed with the options there and thought I had it set to use the nvidia card. So I restart Ubuntu, change Bios to boot on nvidia, turn off computer put the blue cable back into the nvidia slot, and turn it back on.

Go back into Ubuntu...and now it won't start. So now I change Bios, change cable, and reinstall Ubuntu. Here I am now ignoring the restricted driver notice, on my Intel card. 

So heres the million dollar question thats caused me hours of problems/misery:
WHY CAN'T I USE MY NVIDIA CARD?

Heres what I think could be the problem:

1. I could have not properly set the screen to use the nivida card after the reboot. 
So..
I was hoping someone here could tell me exactly how to set the screen to use the nvidia card, and completely ignore the Intel one.Again heres the picture of them Ubuntu
[IMG]http://i116.photobucket.com/albums/o26/photos_r_me/desktop.jpg[/IMG]

2. I'm almost positive that I don't have an nvidia 6800, I thought it was 6200 or something...I can boot into windows and check it really quick. I don't know if that makes a difference or not...

So...help me kick windows once and for all and provide some insight! 

Don't do it for me...do it for the fact that if I get this to work there'll be one less windows computer in the world..:)

---

### Post by Whiffle on 2008-03-02
Have you tried disabling the intel card in bios?

---

### Post by whaevr on 2008-03-02
No I haven't, I'll try it, but before I do, would that be the only card displayed in the Screens and Graphics menu?

---

### Post by Whiffle on 2008-03-02
I'm not quite sure what you mean.  The idea is that if you turn off the intel card in bios then the bios won't even allow the operating system to use it, so the only one the OS would see is the nvidia one, which would then be the only one displayed in screens and graphics.

---

### Post by whaevr on 2008-03-02
I mean this menu here:
[img]http://i116.photobucket.com/albums/o26/photos_r_me/desktop.jpg[/img]
So your saying I should download the restricted drivers, disable the intel card, then boot into Ubuntu.

---

### Post by Whiffle on 2008-03-02
I think that would work, yes.

---

### Post by whaevr on 2008-03-02
Alright here goes nothing. Hopefully this works,,

---

### Post by whaevr on 2008-03-02
I installed the restricted drivers and rebooted then..

All right I don't know how to disable the onboard card in the bios, all I could select  was whether  to use it on boot so I switched boot to pci, stuck cable in nvida's slot and Ubuntu wouldn't start >.<

So I switched boot to Intel, stuck cable in Intel slot, and then Ubuntu would start.

BUT

Now I'm in Ubuntu with a ridiculous screen res that won't go higher than 800x600.

If theres any spelling mistakes forgive me because the font looks like .5 right now -.-

Help..

Edit: the only things I could disable were on board audio, two things about LAN, and 1349. I tried disabling 1349 as I don't know what it is..and using nvidia to boot and Ubuntu still froze.

---

### Post by whaevr on 2008-03-02
Now I tried booting with Bios on Intel but cable in nvidia, Ubuntu loaded, but it wouldn't use my card to display. I had to put the cable in the Intel slot for it to show.

Argh :mad:

---

### Post by sanddgroper on 2008-03-03
Hi
Is the Nvidia card in an AGP slot or is it PCIe or is it just in a pci slot.
Does your bios have any ability to select AGP or PCIe
1394 is to do with importing video from camcorders and the like.
Also if you post the out put of you xorg.conf file might tell us something.
Thats /etc/X11/xorg.conf.

Cheers
Sandy

---

### Post by whaevr on 2008-03-03
The Nvidia card is in a PCI slot.

No my Bios doesn't have that ability because:
 
A: I don't have a PCIe slot on my mobo I know this for sure.
B: I'm guessing I don't have an AGP slot either.

I'll post the contents of that file in a minute or so.

Alright here's the contents of the file you requested:

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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
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

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1152x864@75"	"1280x1024@75"	"1024x768@60"	"1280x960@60"	"1024x768@70"	"1280x1024@60"	"1024x768@75"	"1280x960@75"	"832x624@75"	"1400x1050@60"	"800x600@60"	"1400x1050@75"	"800x600@75"	"1600x1200@65"	"800x600@72"	"1600x1200@60"	"800x600@56"	"1792x1344@60"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

I also have a file in this folder called default-display-manager
Could this be edited to make it use Nvidia...?

One last thing..I reinstalled Ubuntu since yesterday, and I'm using Intel graphics chip, and I haven't installed the restricted Drivers yet, so I could have a normal up screen res again...I don't know if this effects what you wanted to see in this file or not, but just thought I'd let you know.

---

### Post by sanddgroper on 2008-03-04
Hi Whaevr
Yes it just tells me you are using the onboard card.
If you have no AGP or PCIe slots it must be an old board.
Do you have the manual for the board you may need to move
jumpers on the board to disable the onboard graphics.
I would guess that untill you disable the onboard graphics
you will not be able to get the Nvidia card to work.
Could you just give us the computer type the cpu speed and the
ram you have on your machine.

Cheers
Sandy

---

### Post by sanddgroper on 2008-03-04
Hi Whaevr
> I also have a file in this folder called default-display-manager
Could this be edited to make it use Nvidia...?
I would not think so.

Cheers
Sandy

---

### Post by whaevr on 2008-03-04
Sure here's all I know about my computer.

Its an HP Pavillion a1133w, I have 2.9Gb of Ram because I recently purchased 2Gb off newegg. As for CPU I have a Pentium 4 that runs at 3.00Ghz.

I have saved **all** the manuals and what not that came with the computer. So I suppose the manual should be here somewhere...

Although I don't know what you mean by moving jumpers around to disable the chip..

---

### Post by sanddgroper on 2008-03-04
Hi
Dont worry about jumpers I thought your computer might be older
than what it is.
Does your computer support an addon graphics card.
I had a quick look at the spec's of your computer and the only
thing it says is the computer has 2 PCI slots no mention of AGP
or PCIe
So are you limited to the onboard graphics card.

Cheers
Sandy

---

### Post by whaevr on 2008-03-04
No I'm not limited to the onboard chip, I've used this Nvidia card in Windows for a while but everytime I try to set Bios to use it on load Ubuntu won't even load. It freezes.

Your right about my board for the most part it actually has 3 PCI slots but it probably listed 2 because it came with a modem card in it, although I don't use it anymore so I removed it.

---

### Post by sanddgroper on 2008-03-05
Hi Whaevr
Ok the nvidia board works in your machine so I am running out of
ideas.
You could try having a look at the following files to see if they show any errors.
dmesg
messages
syslog
when loading the nvidia driver.
A check of the nvidia site indicates to me that the card you have was only produced
as a PCI Express(PCIe) or AGP.So I would suggest that the slots you have are actually
PCIe but I know nothing about HP computers and it does not get your problem solved.
Have reread your posts and can only think Ubuntu for what ever reason does not want
to play with your graphics card.
Do you have any live cd of linux other than Ubuntu you can boot off to see if other distro's
will work with your nvidia card.
Sorry you cant get this to work.

Cheers
SAndy

---

### Post by whaevr on 2008-03-05
Well when I do lspci it tells me I have a 6200, not a 6800 like it shows in the screens and graphics menu.

Output:
```

02:04.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

I'm positive its a 6200, and not a 6800. I went and checked in Windows to make sure. This would also explain why you found on the Nvidia site that its a PCIe card, because you most likely looked up 6800, because that's what I listed before.

Hopefully this new information can help you fix my problem...

Edit:
So can I change the card model in screens and graphics to a different model...? I think Ubuntu is crashing because its looking for a PCIe card and its not finding one..

Edit:Edit:
Sorry for the late reply =P was busy today.

---

### Post by sanddgroper on 2008-03-06
Hi whaevr
We gotta stop metting like this.:lolflag:
Ok if it is a 6200 then you probably need the nvidia glx driver from
synaptic.
That should be an AGP card but after what you have said I could
not guess whats in your HP box.

Cheers
Sandy

---

### Post by whaevr on 2008-03-06
Ok I downloaded and installed the package you told me to get off synaptic...how do I make Ubuntu use the nvidia card and not the Intel chip...because looking at the screens and graphics menu does nothing..

Edit:
I was hoping you could tell me how to set the xorg.conf file to use my card, at the moment I'm trying it figure it out...

---

### Post by whaevr on 2008-03-06
Edit:
Soon as I get the Boardname filled, I'm also going to blacklist my intel chip because I found a similar, almost exact problem with an integrated intel chip and an nvidia card, and adding
```

#blacklist intel onboard drivers
blacklist agpgart
blacklist intel_agp

```
to /etc/modprobe.d/blacklist fixed his problem, all he had to do was reconfigure xorg.conf to use his nvidia card, and it worked fine.

So...**in theory** that should work for me...

HUGE EDIT:
OMG I DID IT. I added the lines above ^ then did just followed a restricted drivers install, rebooted, changed boot from Onboard to PCI in Bios, then had to do "dpkg-reconfigure xserver-xorg" once Ubuntu rebooted because xserver crashed, I just used all the settings that were already filled in for me. I only changed the name from Intel..blah blah blah to 
"Nvidia Geforce 6200"

The rest of the time I just pressed ok =D 

If ANYONE has ANY problems with their video card and has an Intel chip in their mobo I _highly recommend_ doing the above!

---

