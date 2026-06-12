---
title: "COPIED: Another noob needing help.."
date: 2009-07-14
forum: Mythbuntu
---

### Post by gidsmyth on 2009-07-14
... and finally asking instead of just surfing manuals online.
 
Hi,
 
I'm building (in theory) a Mythbuntu Front/Backend and having just a few difficulties. I have been reading manuals and guides online since February while I work on this and have reinstalled about 20 times trying to get my setup all working. I would appreciate the time and patience of anyone who can get me up and running.
 
I'm using an M2A-VM motherboard with intregrated graphics, and a DVICO Dual Express and its getting a setup that works for both of these that is killing me. I'm a noob to linux, with my only experience being to setup a headless file server and don't know terminal commands. (I'm happy to use them but it takes me forever to figure out what they should be!)
 
Under 8.10 I could install and view all of the Mythbuntu, but it could not (no matter what I did) detect the TV tuners. I read that the drivers were embedded in 9.04 when it came out and so I have been installing 9.04 and 9.10 since then.
In 9.XX the installation goes smoothly, and if I startup and watch the boot script I can quite clearly see it is now finding and installing the TV tuners, but when the mythfrontend starts I have a black screen, with a greyish rectangle in the centre. Tapping on the keys I find that I am able to enter the frontend, but all I get is the highlighting of menu items as I scroll, not the text so I can't configure the mythbuntu at all.
 
I can bring up a 'run program' window which has allowed me to access the desktop and open terminals etc so I have tried installing new graphics drivers, changing resolutions and changing a bunch of stuff. Each time I end up screwing the settings so badly it is easier to re-install than go backwards.
 
Please if anyone can help I will gladly follow any bouncing ball to get to the end, and be most grateful. 
 
Cheers
:p
 
** Note I have started this thread under 'Installations' as well in case it is an Ubuntu issue rather than Mythbuntu. [http://ubuntuforums.org/showthread.php?t=1212830](http://ubuntuforums.org/showthread.php?t=1212830)

---

### Post by issih on 2009-07-14
Just to clarify, are you running mythbuntu itself or mythbuntu installed onto an ubuntu desktop machine?

I have had similar issues with mythbuntu on my box, which were caused by it not playing nicely with compiz, under those circumstances issuing:

```
metacity --replace
```

In a terminal invokes gnome's default window manager, after which, everything worked fine.

I'm fairly certin however, that the actual mythbuntu distribution doesn't come with gnome, and might well not have compiz on, so I do not know whether that is likely to be your solution.

---

### Post by klc5555 on 2009-07-14
Is the graphics card an ATI Radeon?

If it is a Radeon, there's a bug in 9.04.

As a workaround, you should be able start mythfrontend from a command prompt, with:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

If this workaround does it for you, then David Dean shows how to automate it here:

[https://lists.ubuntu.com/archives/ku...ay/074607.html](https://lists.ubuntu.com/archives/ku...ay/074607.html)

---

### Post by gidsmyth on 2009-07-15
Thank you for getting involved
 
**issih **- To clarify I am using the Mythbuntu distro. I think I used the 22 Jun daily build for this latest attempt as I have made enough coasters without getting yesterday's build as well.
 
I'm not quite sure what you are suggesting I do to address the issue - are you saying that in a terminal i should use the code 
 
metacity -- replace
 
?
What does this do and what am I expecting to see different?
 
**klc5555** - The manual for the card indicates it uses ATI Radeon x1250 based graphics so I tried your suggestion. It didn't work, but when I got out the window I noticed it was full of a repeated set of error codes:
 
xerror badmatch
and 
xerror renderbadpicture
 
each with some varied opmajor/minor and resource id codes.
 
:(

---

### Post by klc5555 on 2009-07-15
Still the ATI Radeon bug. One relevant thread is here: [http://swiss.ubuntuforums.org/showthread.php?p=7335482](http://swiss.ubuntuforums.org/showthread.php?p=7335482)

If the command-line workaround does not function for you, the only other current options I know about are either to switch to a reasonably current NVidia GeForce card, which is generally a better option anyway with much better driver support than ATI, or back your Mythbuntu installation down to 8.10 or 8.04.

---

### Post by gidsmyth on 2009-07-16
Progress!!!
 
Ok thanks to the bug link I have managed to get some words when I run the frontend. The problem is that the fonts are VERY distorted (though readable). Unfortunately the link to automate it is giving me a 404 error.
 
Am going to play with some of the appearance settings in the mean time and see if I can setup the backend!

---

### Post by klc5555 on 2009-07-16
> **gidsmyth said:**
> 
 
Ok thanks to the bug link I have managed to get some words when I run the frontend. The problem is that the fonts are VERY distorted (though readable). Unfortunately the link to automate it is giving me a 404 error.
 


Sorry about the dead link. The automation procedure basically involves making a simple one-line script that invokes mythfrontend with the required parameters and substituting this script for the default.

If someone has not beaten me to it by then, I'll provide the accurate information when I get home to my myth machines this evening.

---

### Post by klc5555 on 2009-07-16
The automation procedure is as follows:

The simlink /usr/bin/mythfrontend should be renamed /usr/bin/mythfrontend.old

In a text editor, start a new script "mythfrontend", which will be saved as /usr/bin/mythfrontend

This new script "mythfrontend" has one line, and invokes the simlink now called "mythfrontend.old" with the correct parameters you're using to run your frontend. In my case, this is:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend.old


After this script "mythfrontend" is saved to /usr/bin/mythfrontend then it is made executable: chmod +x /usr/bin/mythfrontend

And it should be fine.

Cheers!

---

### Post by gidsmyth on 2009-07-17
Ah yes of course. Done the same sort of thing with .bat files in windows before. This at least means I can read the frontend text, but bizarrely enough has no effect upon the backend/backend setup (assuming I did it right).
 
Could you please confirm that 
 
XLIB_SKIP_ARGB_VISUALS="1" mythbackend
 
XLIB_SKIP_ARGB_VISUALS="1" mythtv setup
 
are the right terminal commands?
 
Thanks!

---

### Post by klc5555 on 2009-07-17
> **gidsmyth said:**
> Ah yes of course. Done the same sort of thing with .bat files in windows before. This at least means I can read the frontend text, but bizarrely enough has no effect upon the backend/backend setup (assuming I did it right).
 
Could you please confirm that 
 
XLIB_SKIP_ARGB_VISUALS="1" mythbackend
 
XLIB_SKIP_ARGB_VISUALS="1" mythtv setup
 
are the right terminal commands?
 
Thanks!

This workaround is only aimed at mythfrontend. I've used it in frontend-only mythtv machines cursed with ATI Radeon graphics that connect to a remote backend. 

But mythbackend runs as a daemon and does not have a graphical interface. (In the non-Ubuntu world, "root" would start it in the bootup sequence with "mythbackend -d" ) Accordingly it doesn't use a workaround.

If you're having trouble geting text in mythtv-setup (don't forget the hyphen), maybe instead of running it out of a desktop terminal, try running it out of mythfrontend, from myth control centre: when the frontend starts up, go to setup/mythbuntu/mythtvsetup. 

Alternatively, if you have another linux machine with X functioning on it, you could secure-shell into your myth machine and configure the backend remotely: ssh -Y -l [mythtv username] [ip of the myth machine]

and then run mythtv-setup from the remote terminal, bypassing the wonky Radeon graphics on your myth machine.

There are likely other ways also to get the job done.

---

### Post by gidsmyth on 2009-07-17
klc5555, Thank you for all your help. I now have a system that recognises my tuner cards and has somewhat navigable menus.
 
I have successfully automated mythtv and frontend scripts (I had forgotten the '-' in mythtv-setup)
 
I now need to dig out the guide for setting up this tuner card. I think i will have to live with the 'corrupt' graphics until the official fix happens or i get more hardware :( Its usable enough that I'm not going to bother trying a remote interface - at least for the moment.
 
Thanks again, and have a good weekend!

---

### Post by rebootme on 2009-07-29
This worked for me.  Thanks!

---

### Post by gidsmyth on 2009-07-30
Ok so an update: 
 
I downloaded a new daily build of Mythbuntu Karmic, installed that and made the workaround detailed above. Graphics are now perfect.
 
EXCEPT
Can't tune any channels
won't Auto login
 
The login is not an issue as i don't intend tuning off once i get up and running, but the channels thing is crazy.
 
I know the reception is good enough as I have tried plugging the PC into same antenna that digital TV is using.
 
I have increased the timeout in the scan and still nothing.
 
Any suggestions from anyone please?

---

### Post by klc5555 on 2009-07-30
> **gidsmyth said:**
> Ok so an update: 
 
I downloaded a new daily build of Mythbuntu Karmic, installed that and made the workaround detailed above. Graphics are now perfect.
 
EXCEPT
Can't tune any channels
won't Auto login
 
The login is not an issue as i don't intend tuning off once i get up and running, but the channels thing is crazy.
 
I know the reception is good enough as I have tried plugging the PC into same antenna that digital TV is using.
 
I have increased the timeout in the scan and still nothing.
 
Any suggestions from anyone please?

You mean other than "don't expect Alpha/Beta code to work right"? (...oops, sorry...not constructive)

First step is to see whether (when running backend setup again) your tuner cards a) are detected properly b) can run a channel scan, and c) can detect channels and get locks on them.

I suspect "c" (at least) will fail. I don't use your particular Dvico dual express card, but I see that it seems to require both a kernel module (cx88) and particular firmware (XC5000). I suggest that if your card is a) not detected, b)cannot scan, or c)cannot lock when scanning, then it may well be that a)the cx88 module is not loading (for whatever reason) b) is loading, but with the wrong parameters, or c) you do not have the firmware in this new installation, or the firware is not loading correctly. 

A link to the myth page talking about your card is here: [http://www.mythtv.org/wiki/Talk:DViCO_FusionHDTV7_Dual_Express](http://www.mythtv.org/wiki/Talk:DViCO_FusionHDTV7_Dual_Express)

It includes a further link to the firmware page that pertains to the card. (Includes dmesg output to look for to help troubleshoot.)

If your tuner can, however, be detected, scan, and lock, then the problem may be elsewhere.

Good luck!

---

### Post by gidsmyth on 2009-07-31
LOL yes I know that the daily build is perhaps not the smartest thing to do. I keep hoping that the bugs have been fixed - even though its just as likely to be my screw up.
 
My tuner cards are definately detected (ie they are seen in mythbuntu etc...but define properly?)
Mythbuntu is definately trying to do a scan. I also tried using dvbscan and came up with no channels found
I am definately NOT getting channel detection, never mind lock (no signal strength detected whatsoever.)
 
My card is not the DVICO...HDTV7 referred to in your link. I have tried following the process in [http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation](http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation)
 
as this seemed to be closer to my card than the HDTV7, but its quite out of date (circa 2007)
 
I then found it is supposedly working with MythTV
[http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Express](http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Express)
linking to
[http://linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express](http://linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express)
 
In previous iterations I have attempted to follow the instructions at this last link, but due to my nonexistant linux skills I have been unable to figure out what was going wrong. Hence the frequent use of daily builds in the hopes that this 'fix' becomes part of the main release.
 
I'm happy to go back to an earlier release if someone can talk me through the trouble shooting. I bet its something simple like a case sensitive terminal command that I have screwed up.
 
Once again I thank you for your ongoing patience! :)

---

### Post by klc5555 on 2009-07-31
> **gidsmyth said:**
> LOL yes I know that the daily build is perhaps not the smartest thing to do. I keep hoping that the bugs have been fixed - even though its just as likely to be my screw up.
 
My tuner cards are definately detected (ie they are seen in mythbuntu etc...but define properly?)
Mythbuntu is definately trying to do a scan. I also tried using dvbscan and came up with no channels found
I am definately NOT getting channel detection, never mind lock (no signal strength detected whatsoever.)
 
My card is not the DVICO...HDTV7 referred to in your link. I have tried following the process in [http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation](http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation)
 
as this seemed to be closer to my card than the HDTV7, but its quite out of date (circa 2007)
 
I then found it is supposedly working with MythTV
[http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Express](http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Express)
linking to
[http://linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express](http://linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express)
 
In previous iterations I have attempted to follow the instructions at this last link, but due to my nonexistant linux skills I have been unable to figure out what was going wrong. Hence the frequent use of daily builds in the hopes that this 'fix' becomes part of the main release.
 
I'm happy to go back to an earlier release if someone can talk me through the trouble shooting. I bet its something simple like a case sensitive terminal command that I have screwed up.
 
Once again I thank you for your ongoing patience! :)

Well, the first step would appear to be to precisely identify your tuner card. You might want to paste the output of 

lspci -v -s

into a message, and then we can can make sure that the proper driver is loading and the correct firmware is present and loading.

---

### Post by gidsmyth on 2009-07-31
NOTE 
lspci -v -s just gave me the help ?

I know that everything is not required but here it is (smilies inserted at the bit I think is relevant):


sudo lspci -v 
[sudo] password for mythbox: 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 826d
    Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdd00000-fdefffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
    Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fd600000-fd7fffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 826d
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fd900000-fd9fffff
    Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 826d
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8249
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: fdb00000-fdbfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
    Subsystem: ASUSTeK Computer Inc. Device 826d
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at fdef0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at ce00 [size=256]
    Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 2
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel modules: radeon

:P:P
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
    Subsystem: DViCO Corporation Device db78
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Vital Product Data <?>
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [200] Virtual Channel <?>
    Kernel driver in use: cx23885
    Kernel modules: cx23885

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 81aa
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at de00 [size=256]
    Memory at fd9ff000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Vital Product Data <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] Express Endpoint, MSI 00
    Capabilities: [84] Vendor Specific Information <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [12c] Virtual Channel <?>
    Capabilities: [148] Device Serial Number 68-81-ec-10-00-00-00-1a
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8169
    Kernel modules: r8169
--------------------------------------

looks ok to me?

---

### Post by klc5555 on 2009-07-31
Looks OK.

Now, since the card identifies itself as db78 it's probably a FusionHDTV DVB-T of some sort of other? (Gosh, I wish someone who runs one of these cards would chime in...)

So it likely uses the xc3028 firmware (?)

You can likely check what's going on with the firmware by something similar to:

dmesg | grep xc

and see whether anything pertaining to your Dvico firmware is revealed (whether the file is found, or whether it's loading at module load, or is timimg out).

If either of these are the case, then we're likely on to something.

---

### Post by gidsmyth on 2009-07-31
Again this looks ok to me. It is has dual tuners so seeing at the bottom 2 instances of the xc2028 tuner seems right.

Perhaps I'm not using the correct version? how do I check that?

output:

dmesg | grep xc
[    0.168175] pci 0000:01:05.0: reg 20 io port: [0xce00-0xceff]
[    0.168204] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.243787] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.243790] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.243792] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.243795] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.243798] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.243801] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[    0.243803] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[    0.243806] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.243838] system 00:0d: iomem range 0xcd600-0xcffff has been reserved
[    0.248997] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.249077] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    1.027821] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xc
[    1.027823] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xe
[   13.179389] xc2028 1-0061: creating new instance
[   13.179393] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   13.180329] xc2028 2-0061: creating new instance
[   13.180331] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner

---

### Post by klc5555 on 2009-08-01
OK, looking back across your lspci and dmesg output, if I were forced to make a call, I'd have to say that something has gone wrong with your cx88 module load --the card is not being completely or accurately identified.

Compare your spotty lspci output

02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
Subsystem: DViCO Corporation Device db78
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
Capabilities: [40] Express Endpoint, MSI 00
Capabilities: [80] Power Management version 2
Capabilities: [90] Vital Product Data <?>
Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [200] Virtual Channel <?>
Kernel driver in use: cx23885
Kernel modules: cx23885


with the output from a different cx88 Dvico card (from the wiki on the FusionHDTV5 Gold):

Jun 24 15:22:09 pvr cx2388x dvb driver version 0.0.5 loaded
Jun 24 15:22:09 pvr CORE cx88[0]: subsystem: 18ac:d500, board: DViCO FusionHDTV 5 Gold [card=31,autodetected]
Jun 24 15:22:09 pvr TV tuner 64 at 0x1fe, Radio tuner -1 at 0x1fe
Jun 24 15:22:09 pvr ACPI: PCI Interrupt 0000:02:01.2[A] -> GSI 17 (level, low) -> IRQ 209
Jun 24 15:22:09 pvr cx88[0]/2: found at 0000:02:01.2, rev: 5, irq: 209, latency: 32, mmio: 0xe0000000
Jun 24 15:22:09 pvr cx88[0]/2: cx2388x based dvb card
Jun 24 15:22:09 pvr DVB: registering new adapter (cx88[0]).
Jun 24 15:22:09 pvr DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
Jun 24 15:22:09 pvr cx2388x v4l2 driver version 0.0.5 loaded
Jun 24 15:22:09 pvr ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 209
Jun 24 15:22:09 pvr cx88[0]/0: found at 0000:02:01.0, rev: 5, irq: 209, latency: 32, mmio: 0xde000000
Jun 24 15:22:09 pvr tuner 0-0061: chip found @ 0xc2 (cx88[0])
Jun 24 15:22:09 pvr tuner 0-0061: type set to 64 (LG TDVS-H062F/TUA6034)
Jun 24 15:22:09 pvr tda9887 0-0043: chip found @ 0x86 (cx88[0])
Jun 24 15:22:09 pvr cx88[0]/0: registered device video0 [v4l2]
Jun 24 15:22:09 pvr cx88[0]/0: registered device vbi0
Jun 24 15:22:09 pvr cx2388x alsa driver version 0.0.5 loaded
Jun 24 15:22:09 pvr ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 17 (level, low) -> IRQ 209
Jun 24 15:22:09 pvr cx88[0]/1: CX88x/0: ALSA support for cx2388x boards


Unfortunately, I can't go any further because I don't run one of these cards under any version of linux. What I strongly recommend is to start a new thread specifically referencing the Dvico card and cx88 under the 9.10 Alpha, and put your relevant lspci and the dmesg output into it in the hope that either a 9.10 developer, or a few others who use this card on 9.04 or 8.xx will take notice and help out. :(

---

