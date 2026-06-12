---
title: "Trying to get dual monitors to become one"
date: 2014-12-22
forum: Multimedia Software
---

### Post by afrohippie82 on 2014-12-22
Hello all I have installed an older ATI radeon x1300 256 mb video card to my system when installed it works fine I didn't have to down load drivers it just worked. The problem is I cant get the dual monitors to run as one Monitor, They both show the same thing. I'm using a splitter that goes from Dvi to two vga's both monitors are made by the same company and the same size, except one has a dvi port and the other doesn't. I went to this [page]("http://help.ubuntu.com/community/RadeonDriver") to troubleshoot but only found a few things that looked promising 1. my video card was supported. 2. Alot of useful information  3. code that might help me diagnose my problem. The problem is that I don't know how to interpret the data in some of the code not all of it. I was hoping I could get some help on the information found and what I could do to fix my issues. I also have noticed that my mouse moves somewhat slower why is this? FYI I have also upgrade my power supply  to handle the card and any other add ons it now has double the power that it came with from the factory.

Thanks in advance for your help.

The code that I ran is as follows**[SIZE=2]:[/SIZE]**

 ```
[SIZE=2][FONT=arial]
[/FONT][/SIZE][SIZE=2][FONT=arial]**lspci -nn | grep VGA**[/FONT][/SIZE]
[SIZE=2][FONT=arial]01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146][/FONT][/SIZE]

```

```
  ** dmesg | egrep 'drm|radeon'**
 [   32.383454] [drm] Initialized drm 1.1.0 20060810
 [   33.303579] [drm] radeon kernel modesetting enabled.
 [   33.307898] radeon 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 18
 [   33.310168] [drm] initializing kernel modesetting (RV515 0x1002:0x7146 0x1002:0x2342).
 [   33.310194] [drm] register mmio base: 0xFDEF0000
 [   33.310196] [drm] register mmio size: 65536
 [   33.311063] [drm] Generation 2 PCI interface, using max accessible memory
 [   33.311072] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
 [   33.311076] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
 [   33.311532] [drm] Detected VRAM RAM=256M, BAR=256M
 [   33.311536] [drm] RAM width 64bits DDR
 [   33.314190] [drm] radeon: 256M of VRAM memory ready
 [   33.314193] [drm] radeon: 512M of GTT memory ready.
 [   33.314223] [drm] GART: num cpu pages 131072, num gpu pages 131072
 [   33.414369] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
 [   33.431049] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
 [   33.431232] radeon 0000:01:00.0: WB enabled
 [   33.431238] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000000 and cpu addr 0xffcc3000
 [   33.431242] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
 [   33.431279] [drm] Driver supports precise vblank timestamp query.
 [   33.431391] [drm] radeon: irq initialized.
 [   33.431421] [drm] Loading R500 Microcode
 [   34.083938]  [<f8bbeb90>] ? rs600_irq_process+0x4e0/0x660 [radeon]
 [   34.084163] [<f8badf30>] radeon_driver_irq_handler_kms [radeon]
 [   34.338404] [drm] radeon: ring at 0x0000000010001000
 [   34.338445] [drm] ring test succeeded in 9 usecs
 [   34.382195] [drm] ib test succeeded in 0 usecs
 [   34.382796] [drm] Radeon Display Connectors
 [   34.382799] [drm] Connector 0:
 [   34.382801] [drm]   DVI-I-1
 [   34.382803] [drm]   HPD1
 [   34.382806] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
 [   34.382808] [drm]   Encoders:
 [   34.382810] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
 [   34.382812] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
 [   34.382814] [drm] Connector 1:
 [   34.382816] [drm]   SVIDEO-1
 [   34.382817] [drm]   Encoders:
 [   34.382819] [drm]     TV1: INTERNAL_KLDSCP_DAC2
 [   34.450937] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 221
 [   34.835996] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 221
 [   35.060202] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 221
 [   35.206950] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 221
 [   35.207467] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
 [   35.207471] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   37.022314] [drm] fb mappable at 0xD00C0000
 [   37.022320] [drm] vram apper at 0xD0000000
 [   37.022322] [drm] size 3145728
 [   37.022324] [drm] fb depth is 24
 [   37.022326] [drm]    pitch is 4096
 [   37.022574] fbcon: radeondrmfb (fb0) is primary device
 [   37.132171] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
 [   37.132174] radeon 0000:01:00.0: registered panic notifier
 [   37.139756] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
 [   38.034774] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   53.284842] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   56.012298] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   56.575826] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   68.937973] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   76.742436] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   79.526514] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   83.282641] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [   93.655539] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [  114.893039] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [  129.664103] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
 [  181.996285] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID


```


```
   [B]sudo apt-get install
mesa-utils[/B] 
LIBGL_DEBUG=verbose glxinfo eading package
lists... Done Building dependency
tree       
Reading state
information... Done The following NEW
packages will be installed:   mesa-utils 0 upgraded, 1 newly
installed, 0 to remove and 0 not upgraded. Need to get 32.0 kB
of archives. After this
operation, 118 kB of additional disk space will be used. Get:1
http://us.archive.ubuntu.com/ubuntu/ trusty/universe mesa-utils i386
8.1.0-2 [32.0 kB] Fetched 32.0 kB in
0s (52.5 kB/s) debconf: unable to
initialize frontend: Dialog debconf: (Dialog
frontend requires a screen at least 13 lines tall and 31 columns
wide.) debconf: falling
back to frontend: Readline Selecting
previously unselected package mesa-utils. (Reading database
... 215905 files and directories currently installed.) Preparing to unpack
.../mesa-utils_8.1.0-2_i386.deb ... Unpacking
mesa-utils (8.1.0-2) ... Processing triggers
for man-db (2.6.7.1-1ubuntu1) ... Setting up
mesa-utils (8.1.0-2) ... 


```

Any help would be appreciated.

---

### Post by Bucky Ball on 2014-12-22
To do this I'm imagining you are going to need two video outputs from the card (or two cards). Don't see how the one vid output from one card is going to be capable of giving two signals to two separate monitors (as you want different things on each monitor, not a mirror image). :-k

Anyway, I use a laptop with a monitor attached via VGA. I use arandr to configure them, and one of the options is to create one big screen (you can also do one above the other, side by side, etc.). Arandr is in the repositories. Give that a try. Good luck.

---

### Post by afrohippie82 on 2014-12-23
Has anyone tried [arandr]("https://apps.ubuntu.com/cat/applications/precise/arandr/") if so did it help you gain an extended monitor like I'm trying to do

---

### Post by Bucky Ball on 2014-12-23
> **afrohippie82 said:**
> Has anyone tried [arandr]("https://apps.ubuntu.com/cat/applications/precise/arandr/") if so did it help you gain an extended monitor like I'm trying to do

Yes. See my last post. Probably best to just try it and find out if it works for you.

---

### Post by afrohippie82 on 2014-12-23
well i have a svideo adapter to vga and boy does the picture suck it looks like Black and white on the svideo side and like hd  on the vga side arandr worked great as far as a placement tool lol wish it could do something about this lack of color in this display. I sure hope a better video card will do a  better job and not give me these results. I get an extended display but boy does it look like crap. Thanks for the help bucky ball any ideas on a cheap better video card.

---

