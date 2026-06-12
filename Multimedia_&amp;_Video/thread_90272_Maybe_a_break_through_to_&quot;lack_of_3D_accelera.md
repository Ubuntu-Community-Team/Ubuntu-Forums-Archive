---
title: "Maybe a break through to &quot;lack of 3D acceleration&quot; problem"
date: 2005-11-14
forum: Multimedia &amp; Video
---

### Post by ilans on 2005-11-14
Hello
 
I wrote a lot in this forum about my problem: lack of 3d acceleration (on ATI RADEON 9550 - The card didn't recognize by the kernel...)

After a lot of investigation I made another test:
I installed a different card:  ATI RADEON 9600 PRO
I did a fresh installation of breezy, install the fglrx drivers and... still get
Mesa project: [www.mesa3d.org](www.mesa3d.org) (now lspci bring no "unknows device" messages)

I investigate the error message again and I have still the same problem.

My new suggestion to explore:
Mybe my  Internal AGP card (Intel D865GBV) cause the driver/kernel
to load additional module that cause the problem.

Did anyone else have the same problem with the same configuration (internal AGT card)??

---

### Post by Kyral on 2005-11-14
Wait you have onboard video?(Unfamilier with that AGP Card, just need to make sure)

---

### Post by Biased turkey on 2005-11-14
If you installed an ATI Radeon AGP video board, don't you have to desable the onboard integrated Intel video in the BIOS ?

---

### Post by ilans on 2005-11-14
Yes I have additional onboard AGP card.
I don't use it and I can't disable it (the bios don't have any option to disable the internal agp card).

code:
lsmod |grep fglrx
fglrx                 245412  0
agpgart                32328  2 fglrx,intel_agp

*******************************************************************************
The intel_agp is the onboard apg chipset (called "intel extreem graphics")
*******************************************************************************
code:
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

****************************************************************************************************
Now with this new card (9600 pro instead of 9550) the kernel recognize the card but ...
******************************************************************************************************

code:
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by daller on 2005-11-14
Maybe this is all wrong, but isn't that what this is for?

Option "UseInternalAGPGART" "no"

...in the /etc/X11/xorg.conf

---

### Post by daller on 2005-11-14
[QUOTE=ilans]
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/QUOTE]

Did you change "ati" into "fglrx" in the device section of "/etc/X11/xorg.conf" ???

---

### Post by daller on 2005-11-14
This is my device section

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9700 (RV350 NF)"
        Driver          "fglrx"
        Option          "UseInternalAGPGart" "no"
        BusID           "PCI:1:0:0"
EndSection

```

and I get this:

```
daniel@medion:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 TX Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

The 9600/9700 mixup is due to overclocking...

---

### Post by ilans on 2005-11-14
[QUOTE=daller]Did you change "ati" into "fglrx" in the device section of "/etc/X11/xorg.conf" ???[/QUOTE]

Yes, It is in fglrx - as is supposed to be

---

### Post by ilans on 2005-11-14
[QUOTE=daller]Maybe this is all wrong, but isn't that what this is for?

Option "UseInternalAGPGART" "no"

...in the /etc/X11/xorg.conf[/QUOTE]

I added this line, then restart X, but still have the same problem (Mesa)

---

### Post by daller on 2005-11-14
[QUOTE=ilans]I added this line, then restart X, but still have the same problem (Mesa)[/QUOTE]


Well, my fault...

It should be:

Option "UseInternalAGPGart" "no"

instead of:

Option "UseInternalAGPGART" "no"

...I have no idea, if it means anything...

do you have this package installed?

sudo apt-get install linux-restricted-modules-$(uname -r)

---

### Post by ilans on 2005-11-17
Well... 45 days without 3D acceleration...
Here is all of the logs from my system

---

### Post by mlomker on 2005-11-17
I found a number of threads online and they all point to your system board.  The BIOS is reporting the wrong information to the driver.  If you've already updated your BIOS to the latest version then [try this thread.]("http://www.rage3d.com/board/showthread.php?t=33831753")

---

### Post by ilans on 2005-11-17
o.k.
Finally I am sure what cause my annoying symptom (lack of 3d acceleration):
I have internal AGP chipset (on the motherboard - that is not in use) and I have
the ATI radeon 9600 pro card (I have no choice in my bios to disable the onboard VGA card)

reconfigure xorg.conf (by choosing next,next...) configure the card as:
PCI:1:0.0
I am sure that this pci is referring to the onboard chip, BUT how
can I know what is the bus id of my ATI RADEON 9600 PRO card? :confused: 

Here is the output of dpkg reconfigure xserver-xorg:

Users of PowerPC machines, and users of any computer with multiple video
 &#9474; devices, should specify the BusID of the video card in an accepted       
 &#9474; bus-specific format.                                                      
 &#9474;                                                                           
 &#9474; Examples:                                                               
 &#9474;                                                                           
 &#9474;  ISA:1                                                                   
 &#9474;  PCI:0:16:0                                                               
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 
 &#9474;                                                                           
 &#9474;                                                                           
 &#9474; For users of multi-head setups, this option will configure only one of   
 &#9474; the heads.  Further configuration will have to be done manually in the X  
 &#9474; server configuration file, /etc/X11/xorg.conf.

---

### Post by mlomker on 2005-11-17
I don't think that's it because lspci reported your card as 1:00.

```

mlomker@mlomkernote:~/$ sudo lspci -v
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA])
        Subsystem: Uniwill Computer Corp: Unknown device 2324
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c800 [size=256]
        Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at feac0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

```

and:

```

mlomker@mlomkernote:~/$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xf0000000 (3840MB), size= 128MB: write-combining, count=8
reg02: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=1

```

---

### Post by ilans on 2005-11-17
Code:
lspci -v


0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] (prog-if 00 [VGA])
	Subsystem: Giga-byte Technology: Unknown device 4022
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at a800 [size=256]
	Memory at ff820000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at ff800000 [disabled] [size=128K]
	Capabilities: [58] AGP version 3.0
	Capabilities: [50] Power Management version 2

0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
	Subsystem: Giga-byte Technology: Unknown device 4023
	Flags: bus master, 66MHz, medium devsel, latency 32
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at ff830000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2

Code:
cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1

Why I get only 1 line ?:confused:

---

### Post by mlomker on 2005-11-17
[QUOTE=ilans]reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1
Why I get only 1 line ?:confused:[/QUOTE]

I don't know, but I assume it is your system board since you've already tried two cards.  You should really post this on the rage3d forum.

---

### Post by DarkDancer on 2006-01-01
Do you have the user manual for yout mothre board? Chances are if there is no choice for it in the bios you can disable the on-booard video with a jumper.

---

