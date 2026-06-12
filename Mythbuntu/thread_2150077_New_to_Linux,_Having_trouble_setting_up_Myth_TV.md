---
title: "New to Linux, Having trouble setting up Myth TV"
date: 2013-05-30
forum: Mythbuntu
---

### Post by LeighKline on 2013-05-30
Hey all :)

I am totally new to using Linux period, and after some research, decided to wipe our family's 8 year old Windows computer in exchange for Mythbuntu. Well, installation and general setup went like a charm!

However, now I am trying to set up the MythTV for Live TV and Recording (doesn't need to do much else).

My parents are old-school and want it to behave as close to Windows Media Center as possible. Basically, one recording at a time is okay, and even if its needed to switch over to the recording instead of watching Live TV is acceptable.

I'm just... I'm so lost the moment I get into the Back End - coupled with the fact that I can't get Myth TV to come out of Full Screen (I found the windows dimensions, and it will minimize to the corner of the screen 800x600 - but the rest of the screen is just black no matter what else I select).

I need to figure out a tuner card. I can't find anything that seems to want to work. I'm only running the cable into the back of the computer - nothing fancy. But we'd like it to look and record nice.

After that, I'm lost again. I've been at this for several hours.

Anyone willing to take me under your wing and walk me through this? I'm a fast learner, I promise.

EDIT:
Further research leads me to ask -  I'm in America, and documentation I just read over seems to say that MythTV isn't the software to use over here. Can someone clarify?

---

### Post by nickrout on 2013-05-31
LOL most of the mythtv developers are in the US and it is well tuned to the US conditions.

What tuner card do you have?
Where does your TV come from? Cable? Over the Air? FIOS? Satellite? IP over avian carriers?

---

### Post by LeighKline on 2013-05-31
Well, I was hoping so LOL. But everything I've read so far says there's more thorough support for European signals. Glad to be wrong there :P

It's Cable, as in with the cable cable. ;) No box, no satellite, just a cable from the wall to the TV/Comp/Wherever it can pug in to.

I spent over an hour last night trying to figure out how to know what kind of card is in the machine. If you can show me how to find out, it would be appreciated :) Google searches failed me (at least, that was last night, maybe today will be better all around :P)

I'm not opposed to trying a different program/flavor to go for a different program, if it calls for this - but I love the learning process :)

---

### Post by newlinux on 2013-05-31
Do you have anaolog stations left on your cable, or are they all digital? Can your TV tune your stations or do you need a box?

Try showing us the output of
```
lspci -v
```

That may give us an indication of your hardware (including tuner card).

---

### Post by LeighKline on 2013-05-31
Ah that was the command I was looking for! Thank you :)

Like I said, old computer - don't know what half this stuff is :P
```
~# lspci -v00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>


00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [88] Subsystem: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
    Capabilities: [80] Power Management version 2
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel


00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fe00 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at fd00 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fc00 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci_hcd


00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000fbffffff
    Capabilities: [50] Subsystem: Hewlett-Packard Company Device 2a2b


00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, lpc_ich


00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fb00 [size=16]
    Kernel driver in use: ata_piix


00:1f.2 RAID bus controller: Intel Corporation 82801GR/GDH (ICH7R/ICH7DH) SATA Controller [RAID mode] (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at fa00 [size=8]
    I/O ports at f900 [size=4]
    I/O ports at f800 [size=8]
    I/O ports at f700 [size=4]
    I/O ports at f600 [size=16]
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: medium devsel, IRQ 255
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801


01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 0470
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fddf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at de00 [size=256]
    Expansion ROM at fddc0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon


01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary)
    Subsystem: Micro-Star International Co., Ltd. Device 0471
    Flags: fast devsel
    Memory at fdde0000 (64-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00


02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
    Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ef00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci


02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
    Subsystem: Hauppauge computer works Inc. WinTV PVR 150
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ivtv
    Kernel modules: ivtv


02:05.0 Communication controller: LSI Corporation Lucent V.92 Data/Fax Modem
    Subsystem: LSI Corporation Lucent V.92 Data/Fax Modem
    Flags: bus master, medium devsel, latency 32, IRQ 255
    I/O ports at ec00 [size=256]
    Capabilities: [f8] Power Management version 3


02:08.0 Ethernet controller: Intel Corporation NM10/ICH7 Family LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a2b
    Flags: bus master, medium devsel, latency 32, IRQ 20
    Memory at fdefe000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ee00 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: e100
    Kernel modules: e100



```

---

### Post by nickrout on 2013-06-01
The relevant line is ```
02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
    Subsystem: Hauppauge computer works Inc. WinTV PVR 150
``` You have a Hauppauge PVR150 card. It is an analogue tuner with an on board hardware mpeg2 compressor. These used ot be a favourite of mythtv user when analogue was king. 

If your cable has analobue channels, it should work. If it has gone digital you will need a digital card.

---

### Post by LeighKline on 2013-06-01
I think our cable did switch to digital (Time Warner Cable), but Dad believes it was just some channels. I will try this, but haven't gotten it to work yet.

Is this the MPEG 2 encoder tuner card? How do I pick the following input?

---

### Post by bleve on 2013-06-03
First things first.  Now that we have determined your card the next thing to do is check to see if you are getting video that you will be able to record.  If you do the "dmesg" command such as:

$ dmesg  | grep video

You should see video0 is initialized.  

From here you can see if there is video coming into the card:

$ cat /dev/video0 > /tmp/video.ts

Let that run for maybe 30 seconds or so.  Then press CTRL+C.  

You should be able to play the video.ts file with mplayer and see a picture.  If you don't, then there is no reason to keep going with the myth setup.  If you do get video it is a matter of going into mythtv-setup and setting up the capture card, video source and inputs.  There is another step to get scheduling information as well but will wait to hear back how things went with the test above.

---

### Post by nickrout on 2013-06-03
> **bleve said:**
> First things first.  Now that we have determined your card the next thing to do is check to see if you are getting video that you will be able to record.  If you do the "dmesg" command such as:

$ dmesg  | grep video

You should see video0 is initialized.  

From here you can see if there is video coming into the card:

$ cat /dev/video0 > /tmp/video.ts

Let that run for maybe 30 seconds or so.  Then press CTRL+C.  

You should be able to play the video.ts file with mplayer and see a picture.  If you don't, then there is no reason to keep going with the myth setup.  If you do get video it is a matter of going into mythtv-setup and setting up the capture card, video source and inputs.  There is another step to get scheduling information as well but will wait to hear back how things went with the test above.Well except for the fact that you need to set an input for ther card (they normally have a tuner and a composite or s-video input) and if using the tuner you need to actually tune the thing. Then you  might expect to get some video.

It is a long time since I used one of these cards and as far as I am concerned I am in a digital world and they are of historical interest only. However I seems to recall a command-line program called v4l2-ctl or similar. If it isn't installed, it is in v4l-utils.

---

### Post by bleve on 2013-06-03
> Well except for the fact that you need to set an input for ther card  (they normally have a tuner and a composite or s-video input) and if  using the tuner you need to actually tune the thing. Then you  might  expect to get some video.

It is a long time since I used one of these cards and as far as I am  concerned I am in a digital world and they are of historical interest  only. However I seems to recall a command-line program called v4l2-ctl  or similar. If it isn't installed, it is in v4l-utils. 				

You are probably be right here.  Maybe a better test would be to hookup a TV directly to the cable line and see if it gets basic channels.  Mine does and I have Time Warner cable but it may not be the same everywhere.  It has been a while since I have had to do this kind of testing, although I do use a PVR-350 as one of my inputs connected to the basic cable.  I have always had luck just setting it up in the setup.

---

### Post by LeighKline on 2013-06-03
Well, we have many TV's hooked up to our cable, and we get both basic and digital channels (the ##-## channels, if I understand correctly), but nothing over 70-something. So I'm very much assuming it works :P

Alright, output from the first command:
```
[    0.281834] pci 0000:01:00.0: Boot video device[   22.069662] Linux video capture interface: v2.00
[   22.732731] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   22.732809] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   22.732919] ivtv0: Registered device video24 for encoder PCM (320 kB)

```

Ran the second, figured out how to play it. The moment it opened, I got a "totem requires an additional plugin to decode this file" box. 
MPEG-2 System Stream demuxer
I let that install whatever it wanted.
That streamed 2 seconds of a 34 second clip, got a picture :). It was of our "bulletin board channel".

I love progress! Now what?

PS - thank you so much for your patient tutelage - I am loving learning this system!

---

### Post by bleve on 2013-06-03
Now you need to run mythtv-setup and configure everything.  You will need something to deal with guide data.  I use schedules direct and pay the yearly fee.  Once you have that setup you go through the menus on mythtv-setup.

---

### Post by LeighKline on 2013-06-03
This is where I'm lost again. I have tried. I set only one tuner card - MPEG-2. However, for picking up channels, I cannot get Dad to pay for the DVR we could have for 15$ a month. There's no way I'm going to get him to commit to a paid service guide instead. He's gonna say "we used to get this for free, why not now".

I tried to go with the "no grab" - we know our channels by heart. But I can't get a single channel scan to pick up anything, no matter what I try. I've also tried the Transmitted Guide Only, with the same results. Is there any way to just have the cable without downloading any guide?  If I'm reading this right, I'm stuck at "Please add a channel" for the default channel, which won't work in the front end at all.

EDIT:
Yep just ran it past him, and his answer: "if someone wants to pay for it." :P Stinks to know your parents so well :P

I have been trying to scan for channels, using different settings, and now it just kicks me out of the backend as soon as I hit next to start the scan. Probably calling for a system restart. I was using the NTCS (going from memory, not sure if that's the right order or letters), but again, not sure how to tell if that's correct.

---

### Post by nickrout on 2013-06-04
FFS schedules direct is dirt cheap and has the best guide data on the planet. Just do it.

---

### Post by LeighKline on 2013-06-04
I may end up doing that out of my own pocket :P

Will this solve the issue of not finding channels while scanning? Am I correct in using the NTSC signal, or should it be PAL?

---

### Post by tgm4883 on 2013-06-04
Schedules Direct (SD) has a 7 day free trial, and after that it's $25/year, so a pretty good price. I'm unsure of the scanning abilities of mythtv (I know it was broken at one point) as I just always pull the info from SD. We still don't really know what kind of card you have, or what you set it up as in mythtv. Can you post the output of 'lspci'

---

### Post by bleve on 2013-06-04
I think we have figured out that the card is a PVR-150 and yes if you have schedules direct account with a listing source picked out when you fetch the channels when creating the input for the tuner card you will get the channel information from schedules direct.

---

