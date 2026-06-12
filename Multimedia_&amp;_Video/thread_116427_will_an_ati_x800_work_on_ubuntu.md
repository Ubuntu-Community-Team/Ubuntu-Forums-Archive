---
title: "will an ati x800 work on ubuntu"
date: 2006-01-12
forum: Multimedia &amp; Video
---

### Post by kakashi on 2006-01-12
i am about to buy[ this card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814127176"):D . i WILL be using ubuntu on it so i thought i'd find out how well it would work. also the one of the reviews says that i  should not buy an ati card for linux.:???: 
 
what do you ppl think.

---

### Post by nilly on 2006-01-12
[QUOTE=kakashi]i am about to buy[ this card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814127176"):D . i WILL be using ubuntu on it so i thought i'd find out how well it would work. also the one of the reviews says that i  should not buy an ati card for linux.:???: 
 
what do you ppl think.[/QUOTE]

Dont.. go with nvidia instead..

(the short answer)

---

### Post by micjustmic on 2006-01-12
Meh, I'm using an ATi X700 Pro.

I think nVidia gets driver updates out faster, but the ATi drivers seem to work just fine.

I've heard horror stories about ATi cards, I won't go into them, but I've had nothing but good things with mine.

Mic

---

### Post by nadir.ita on 2006-01-12
[QUOTE=kakashi]i am about to buy[ this card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814127176"):D . i WILL be using ubuntu on it so i thought i'd find out how well it would work. also the one of the reviews says that i  should not buy an ati card for linux.:???: 
 
what do you ppl think.[/QUOTE]

hello... i have bought an ati x800 gto and installed ubuntu 5.10 one hour ago. actually im using X without evident problems (*) but i've not installed ati proprietary drivers yet and - sincerely - im too tired for accomplish the job now :-? so, for a desktop usage the board seems ok, for advanced 3d... not personally tested.

BTW... memory modules are not cooled (in my board, a sapphire, the cooler in the upper side covers the elements WITHOUT touching them - for maximum heat (SHAME!!)) so i strongly advise you to buy some heat sinks (e.g. [http://www.sharkoon.com/enghtml/fans_heatsink.htm](http://www.sharkoon.com/enghtml/fans_heatsink.htm)) and a serious fan. these boards dont seem to be built to resist longer than the warranty. im wondering why :rolleyes: 

if ill succeed installing the latest ati drivers and play cs:s il provide feedback, anyway in this period im really really busy. cu and good night...

(*) except this step: in /etc/X11/xorg.conf:

change:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 Pro (R480)"
	**Driver		"ati"**
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
EndSection

to:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 Pro (R480)"
	**Driver		"radeon"**
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
EndSection

---

### Post by nilly on 2006-01-12
Sure X800 works perfecly in 2d desktop... i own a X800XL 512MB.. it works wonders in amazing 2dimensional.. but who would by a X800 for its amazing 2d features!!??

As for fglrx 3d.. it wont work whatever i try.. could be some other hardware aka nforce4 etc that interfere.. i would bet nvidia would be a safer bet... im gonna try borrowing a newer type pci-e nvidia card to try on my machine..

Anyway.. ati will mess you up sooner or later.. nvidia driver are more stable even in windows..

EDIT: btw nadir looks like you got yourself a X850.

---

### Post by kakashi on 2006-01-12
thanks for the info. i suppose then i can get it. hope you succeed in 3d as well (cedega). i'll still wait for more info though.

---

### Post by Zeroedout on 2006-01-13
If I absolutly had to grab a graphics card right now, I would get an Nvidia (and I really dislike Nvidia for my own reasons). Ati's linux driver is nowhere near as good as it's windows driver, and the plain fact is that Nvidia's linux driver is MUCH more complete. Historically, Nividia has always had much better linux support. Ontop of that, there are some games in cedega that refuse to run with an ATI card, for example the gta series. I don't have much cash right now, and i'll really start saving up when ATI has a better working linux driver, however, I suggest you go with Nvidia. That's not to say that the ati drivers are pure shit, they're not bad, but they are not as good as they could be, though they get better all the time.

---

### Post by nadir.ita on 2006-01-14
[QUOTE=nilly]
EDIT: btw nadir looks like you got yourself a X850.
[/QUOTE]

its a x800 gto, isnt it very close to the x800? (im not an expert :confused: )

anyway, if this can help, ive suceeded in installing original ati 8.20.8 drivers following an how-to ([http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers))

```

nadir@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

nadir@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
5656 frames in 5.0 seconds = 1131.200 FPS
6329 frames in 5.0 seconds = 1265.800 FPS
6517 frames in 5.0 seconds = 1303.400 FPS
6503 frames in 5.0 seconds = 1300.600 FPS
6514 frames in 5.0 seconds = 1302.800 FPS

```

---

### Post by newuser111 on 2006-01-14
even though nvidia drivers are better (faster, more updated etc) ati drivers will work for your card

it depends if you are going to do gaming in linux or windows, ati drivers work fine for me in most games, but expect lower framerates than equivalent nvidia cards

its a shame because ati have been making linux drivers for a long time now, but have yet to produce really quality drivers compared to the windows ones, even their windows drivers are questionable now, using lots of ms .net

---

### Post by kakashi on 2006-01-14
[QUOTE=nadir.ita]its a x800 gto, isnt it very close to the x800? (im not an expert :confused: )

anyway, if this can help, ive suceeded in installing original ati 8.20.8 drivers following an how-to ([http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers))

```

nadir@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

nadir@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
5656 frames in 5.0 seconds = 1131.200 FPS
6329 frames in 5.0 seconds = 1265.800 FPS
6517 frames in 5.0 seconds = 1303.400 FPS
6503 frames in 5.0 seconds = 1300.600 FPS
6514 frames in 5.0 seconds = 1302.800 FPS

```[/QUOTE]

i was also going to buy a x800gto too untill i posted here. the x800gto is a lower end version and SOME have a x850 chip with only 12 pipelines enabled. you can unlock the rest and have a full x850.

---

### Post by nadir.ita on 2006-01-17
[QUOTE=kakashi]i was also going to buy a x800gto too untill i posted here. the x800gto is a lower end version and SOME have a x850 chip with only 12 pipelines enabled. you can unlock the rest and have a full x850.[/QUOTE]

:-\" thx

---

### Post by majkmil on 2006-01-29
Hi, In glxgears Iget this.

mark@ubuntu:~$ glxgears
9801 frames in 5.0 seconds = 1960.033 FPS
26217 frames in 5.0 seconds = 5243.392 FPS
26981 frames in 5.0 seconds = 5396.017 FPS
26992 frames in 5.0 seconds = 5398.271 FPS
26994 frames in 5.0 seconds = 5398.795 FPS
26957 frames in 5.0 seconds = 5391.213 FPS
26965 frames in 5.0 seconds = 5392.930 FPS

This is on a ATI 9600, Is this right? I usually get in the 1900 FPS range. Here are my drivers.


mark@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5582 (8.21.7)

Don't get me wrong I am happy with these numbers but I was wondering what others are getting.

---

### Post by Kieffer87 on 2006-02-05
I dont feel like reading the whole thread, but I have an Saphire ati x800 with the fglrx drivers. 3d works perfectly

---

### Post by kakashi on 2006-02-06
well a bought a x800gt. i have not yet tried fglrx (computer having issues with install winxp) but vesa seems to work. is there any card vesa can't run

---

### Post by daradib on 2006-10-21
I have X800. There was a slight problem (X won't load), but it can be fixed:
New topic:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

