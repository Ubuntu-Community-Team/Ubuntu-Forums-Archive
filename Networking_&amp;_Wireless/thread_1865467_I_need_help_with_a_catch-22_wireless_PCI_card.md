---
title: "I need help with a catch-22 wireless PCI card"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by S2UIRR3L on 2011-10-20
Hi all - Need some help with a catch 22...

First off, I'm using Maverick 10.10. I downloaded it and installed it when I had a hard wired connection to the internet. These days, there's only wireless and leaching with my neighbor's permission. I pay half his cable bill, and use half his service (wi-fi).

I just bought an internal wireless PCI card and need to download some sort of firmware to make it work, but I can't down load it because the wireless is not working...?

I have my laptop which has it's own built in wireless and had no issues installing Jaunty 9.04 so I left it as it is (why fix it if it ain't broken?).

THE BIG QUESTION

**Is there a way that I can download all the firmwares and drivers ect needed using my laptop, then transfer them to my tower via USB thumb drive?**

On my tower, this is what I clicked to look into things:
**SYSTEM>ADMINISTRATION>ADDITIONAL DRIVERS**

After making some noise and searching for a few seconds, it returned this:
**[http://us.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43legacy-installer_4.178.10.4-4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43legacy-installer_4.178.10.4-4_all.deb)**

I copied the ".deb" file that I downloaded with my laptop and transferred it to my tower via USB thumb drive. Maybe I did it wrong... I don't know?

Please, if there's a way that I can use my laptop to download the files and then transfer them to my tower, will someone please help me with a few instructions or a "how-to".

Ubuntu Forums has never failed me and again, I thank everyone who contributes to helping newbies like my self to make my Linux experience that much more enjoyable.

THANKS
-Squirrel

---

### Post by wildmanne39 on 2011-10-20
Hi, it depends on the wireless card you have from looking at that deb file I guess you have a broadcom car, but I like to make sure and I like to know the model of the card so please post the results of:
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by S2UIRR3L on 2011-10-21
I tried two things... the first one didn't look like something you can use, so I tried a second command and that showed something a little better... I think? Here are both results copied directly from both terminal windows:








---------- THIS IS THE 1ST RESULT ----------

inuyasha@inuyasha-desktop:~$ lspci -nnk l grep -iA2 net
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of A2
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
inuyasha@inuyasha-desktop:~$ 

---------- END OF 1ST RESULT ----------










---------- THIS IS THE 2ND RESULT ----------

inuyasha@inuyasha-desktop:~$ lspci -nnk
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge [1106:3116]
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091]
    Kernel modules: shpchp
00:08.0 USB Controller [0c03]: ALi Corporation Device [10b9:5227] (rev 03)
    Subsystem: ALi Corporation Device [10b9:5227]
00:08.1 USB Controller [0c03]: ALi Corporation Device [10b9:5227] (rev 03)
    Subsystem: ALi Corporation Device [10b9:5227]
00:08.2 USB Controller [0c03]: ALi Corporation Device [10b9:5227] (rev 03)
    Subsystem: ALi Corporation Device [10b9:5227]
00:08.3 USB Controller [0c03]: ALi Corporation M5229 IDE [10b9:5229] (rev 01)
    Subsystem: ALi Corporation M5229 IDE [10b9:5229]
    Kernel modules: pata_ali
00:09.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02)
    Subsystem: Microsoft Corporation Wireless PCI Adapter MN-730 [1414:0004]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
00:0a.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
    Subsystem: Diamond Multimedia Systems Device [1092:0160]
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233A ISA Bridge [1106:3147]
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel modules: i2c-viapro, via-ircc
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: pata_via
    Kernel modules: pata_via
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: uhci_hcd
00:11.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: uhci_hcd
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 40)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx
01:00.0 VGA compatible controller [0300]: S3 Inc. VT8375 [ProSavage8 KM266/KL266] [5333:8d04]
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel modules: savagefb
inuyasha@inuyasha-desktop:~$ 

---------- END OF 2ND RESULT ----------









I hope I did the right thing(s) and I hope this helps you to help me. I appreciate everything you're trying - THANKS A MILLION!!!

---

### Post by wildmanne39 on 2011-10-22
Hi, just copy and paste the command into the terminal, it is only one command.
Thank you

---

### Post by S2UIRR3L on 2011-10-25
This is what I got for entering that command:






inuyasha@inuyasha-desktop:~$ lspci -nnk | grep -iA2 net
00:09.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02)
    Subsystem: Microsoft Corporation Wireless PCI Adapter MN-730 [1414:0004]
    Kernel driver in use: b43-pci-bridge
--
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9022]
    Kernel driver in use: 8139too
inuyasha@inuyasha-desktop:~$ 








When all this is solved, I wonder if the same fix will work with Jaunty Jackalope?
Thanks again for being so patient with me. It's very much appreciated!

---

### Post by wildmanne39 on 2011-10-25
Hi, this should work.

Down load the b43 zip file to your usb device then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Run this commands one line at a time.
Thank you

---

### Post by BHEJU on 2011-10-25
Let me suggest something different.
Go to store and get a USB wireless card. Most of the new ones are supported by default. 
Connect to internet. Get your drivers for the other card. And return the USB one.

Cheers,

---

### Post by S2UIRR3L on 2011-10-25
LOL - I tried that, but Belkin doesn't like Linux very much. I wound up buying 50-ft. of CAT-5 instead. But that when I had my own internet connection. My location doesn't get cable anymore and I'm SOO not paying all that money for Verizon Fios. I offered my neighbor a few dollars every month and he's letting me leach off of his Verizon wi-fi. Besides that, if I learn a lesson here on the forums the "hard" way, I can always pass this info to someone else on the forums, the same way I learned it. This is why I love the forums.

Thanks a million for the suggestions. Every piece of information gained here is very valuable. One day, I'd like to use Linux only. I'm not much of am MMO gamer, so I should have no issues with it. But I'd like to learn as much as I can first. You know, look before you leap? lol

Thanks again everyone - Cheers!

---

### Post by S2UIRR3L on 2011-11-03
Sorry I didn't reply again sooner... been busy.

I tried downloading that zip file and tried installing with terminal, but it didn't work. I'm sure it's something that I did. It said something like "file already exists" and just wouldn't do anything after that...?

It's irreverent now that the kids spilled about 2-liters of chocolate milk in the tower lol. I wound up recycling it and the kids' father bought me the Fujitsu that I had my eye on to compensate me for it.

Should I mark this as SOLVED, since my issue is solved... in a sense lol. Thank you for all your efforts and trying to help me. Even tho my neighbor's kids destroyed my old computer, I appreciate everything lol.

 Cheers!
-Squirrel

---

### Post by wildmanne39 on 2011-11-03
Hi, if you want to mark it solved you can other wise given that outcome leave it as it is.
Thank you

---

### Post by S2UIRR3L on 2011-11-04
Thank you wildmanne39 ------ I'll mark it as solved because I'm sure the code that you've provided will work for someone.

---

