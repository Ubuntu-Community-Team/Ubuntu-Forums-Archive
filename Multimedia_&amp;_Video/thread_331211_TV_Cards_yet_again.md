---
title: "TV Cards yet again"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by greatgoo on 2007-01-04
I am working on getting a ATI TV card to work in my Linux Box.  I have read the various postings I could find here, tried the various fixes, crashed the box four times, rebuilt it three times and saved it the last time.  I am getting better, but still have a lot to learn.

When I look at the system log, either through Gnome or using dmesg, I see the card is identified as a Connexant based card, but it is not recognised.  There is then a list of common cards one could use use with the insmod command, card=#.  The man page for insmod says modprobe is better.  TV Now and the v4l project talk about patching the module ... on and on and on.

First what I am looking for is a better understanding of hardware detection.  How the kernal decides what to do when a piece of hardware is found.  Anyone got a link to that?

Next I would like to better understand the module process.  How about a link to that.

Finally, when I tried the insmod command or the modprobe command to set the card number to 4, no module is found.  Playing with the various module possibilities for Connexant, none of those modules are found, hence my above request for kernal knowledge. Has anyone got any ideas on that? 

David Davis
Toledo, OR 97391

---

### Post by 64mgb on 2007-01-04
I can't help you with the links to documentation...I'm looking for some of them myself.  As for the driver and getting the card to work, have you looked at IVTV?

ivtvdriver.org

Rich

---

### Post by superm1 on 2007-01-04
> **64mgb said:**
> I can't help you with the links to documentation...I'm looking for some of them myself.  As for the driver and getting the card to work, have you looked at IVTV?

ivtvdriver.org

Rich
Although IVTV card do use conexant chipsets, AFAIK IVTV hasn't supported anything beyond the Hauppauge cards and a few other obscure cards.

The cheapo ATI TV wonder cards typically use a bttv framegrabber driver.
The nicer TV wonder PRO cards use one of the conexant modules, but this should be loaded for you automatically on the latest Ubuntu kernels.

I wouldn't be a good person to explain exactly how the hotplug/udev system works, i'm just appreciative it does :)

So back on topic, what ATI card is this?  Particularly, what is the output of ```
lspci
```

---

### Post by greatgoo on 2007-01-05
So back on topic, what ATI card is this? Particularly, what is the output of lspci

ATI TV Wonder 200

lspci

00:00.0 Host bridge: Gammagraphx, Inc. Unknown device 000e (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:02.0 CardBus bridge: Texas Instruments PCI1420
02:02.1 CardBus bridge: Texas Instruments PCI1420
02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:06.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

And since you asked, from dmesg  :mrgreen: 

[17179592.528000] cx88[0]: Your board isn't known (yet) to the driver.  You can
[17179592.528000] cx88[0]: try to pick one of the existing card configs via
[17179592.528000] cx88[0]: card=<n> insmod option.  Updating to the latest
[17179592.528000] cx88[0]: version might help as well.
[17179592.528000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[17179592.528000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[17179592.528000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[17179592.528000] cx88[0]:    card=2 -> GDI Black Gold
[17179592.528000] cx88[0]:    card=3 -> PixelView
[17179592.528000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[17179592.528000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[17179592.528000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)

<snip>

[17179592.528000] CORE cx88[0]: subsystem: 1002:00f9, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179592.528000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[17179592.820000] cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 209, latency: 32, mmio: 0xee000000
[17179592.888000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179592.888000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179592.928000] cx88[0]/0: registered device video0 [v4l2]
[17179592.928000] cx88[0]/0: registered device vbi0
[17179592.928000] tuner 0-0060: tuner type not set

---

### Post by superm1 on 2007-01-05
> **greatgoo said:**
> So back on topic, what ATI card is this? Particularly, what is the output of lspci

ATI TV Wonder 200

lspci

00:00.0 Host bridge: Gammagraphx, Inc. Unknown device 000e (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:02.0 CardBus bridge: Texas Instruments PCI1420
02:02.1 CardBus bridge: Texas Instruments PCI1420
02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:06.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

And since you asked, from dmesg  :mrgreen: 

[17179592.528000] cx88[0]: Your board isn't known (yet) to the driver.  You can
[17179592.528000] cx88[0]: try to pick one of the existing card configs via
[17179592.528000] cx88[0]: card=<n> insmod option.  Updating to the latest
[17179592.528000] cx88[0]: version might help as well.
[17179592.528000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[17179592.528000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[17179592.528000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[17179592.528000] cx88[0]:    card=2 -> GDI Black Gold
[17179592.528000] cx88[0]:    card=3 -> PixelView
[17179592.528000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[17179592.528000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[17179592.528000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)

<snip>

[17179592.528000] CORE cx88[0]: subsystem: 1002:00f9, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179592.528000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[17179592.820000] cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 209, latency: 32, mmio: 0xee000000
[17179592.888000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179592.888000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179592.928000] cx88[0]/0: registered device video0 [v4l2]
[17179592.928000] cx88[0]/0: registered device vbi0
[17179592.928000] tuner 0-0060: tuner type not set
You would have the most luck i'd think setting the card to emulate a ATI TV Wonder pro.  I haven't seen anything directly indicating this cards functionality from a short google search, but I think thats what the card bases its hardware from.

1) So remove the cx88xx driver (or whatever the module is).
```
sudo rmmod cx88xx
```
2) Edit /etc/modprobe.d/options.  Add a line for options about he card.  So if the module name was indeed cx88xx it would be:
```
 options cx88xx card=4
```
3) Reload the module with the forced card type.  If the module was named cx88xx:
```
sudo modprobe cx88xx
```

No guarantees this will work for you, but its definitely worth a shot.

---

### Post by greatgoo on 2007-01-05
> **superm1 said:**
> You would have the most luck i'd think setting the card to emulate a ATI TV Wonder pro.  I haven't seen anything directly indicating this cards functionality from a short google search, but I think thats what the card bases its hardware from.

1) So remove the cx88xx driver (or whatever the module is).
```
sudo rmmod cx88xx
```
2) Edit /etc/modprobe.d/options.  Add a line for options about he card.  So if the module name was indeed cx88xx it would be:
```
 options cx88xx card=4
```
3) Reload the module with the forced card type.  If the module was named cx88xx:
```
sudo modprobe cx88xx
```

No guarantees this will work for you, but its definitely worth a shot.

And so went my thoughts also.  Initially I did not understand modules and options and so I stumbled around for a bit.  Read the man page a few times and cursed.  All this before I came to this forum.  I determined the module was called cx8800. I am still not sure this is true but it was a workable hypothesis.  I could never make the insmod or modprobe sequence work.  Hence my search for hidden knowledge.  Which BTB:  Thanks for the bit about the options file.  Just finding where stuff is adds another wrinkle to my brain.

SO!

I am running from root right now, no need for the sudo.  Here is the clip from the term window ..

root@greatgoo-desktop:~# modprobe cx8800
FATAL: Error inserting cx8800 (/lib/modules/2.6.17-10-generic/kernel/drivers/media/video/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@greatgoo-desktop:~# dmesg

<snipped>

[17179595.128000] NET: Registered protocol family 17
[17179603.508000] eth0: no IPv6 routers present
[17187728.976000] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[17187896.020000] cx8800: Unknown parameter `card'
root@greatgoo-desktop:~# 

Here is the options file ..

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# ATI TV Wonder force card configuration 4
options cx8800 card=4

Thanks for the help and tips on how some of this works, much appreciated.

David Davis
Toledo, OR 97391

---

### Post by 64mgb on 2007-01-05
I don't see any source code for cx8800, so I can't go in to check what parameters it expects.  But I do see that module cx88 expects a parameter called "card" and the ATI TV Wonder Pro is card 4, as superm1 suggested.

Rich

---

### Post by greatgoo on 2007-01-05
> **64mgb said:**
> I don't see any source code for cx8800, so I can't go in to check what parameters it expects.  But I do see that module cx88 expects a parameter called "card" and the ATI TV Wonder Pro is card 4, as superm1 suggested.

Rich

Did you get that info from one of my earlier posts?  Always looking for more information.

Based on your suggestion, I modified the line in the options file to read cx88

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# ATI TV Wonder force card configuration 4
options cx88 card=4

and tried the modprobe again with that as the module ..  no luck.

root@greatgoo-desktop:~# modprobe cx88  
FATAL: Module cx88 not found.
root@greatgoo-desktop:~#        

David Davis
Toledo, OR 97391

---

### Post by greatgoo on 2007-01-05
> **64mgb said:**
> I don't see any source code for cx8800, so I can't go in to check what parameters it expects.  But I do see that module cx88 expects a parameter called "card" and the ATI TV Wonder Pro is card 4, as superm1 suggested.

Rich

AH HA!!!!

cx88xx is the module.  A quick command line modprobe did not fail as the others had.  So I reset the options parameter to cx88xx and rebooted the machine.  Here is the dmesg

[17179596.456000] CORE cx88[0]: subsystem: 1002:00f9, board: ATI TV Wonder Pro [card=4,insmod option]
[17179596.456000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179596.532000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179596.684000] cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 209, latency: 32, mmio: 0xee000000
[17179596.716000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179596.716000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179596.716000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[17179596.792000] cx88[0]/0: registered device video0 [v4l2]
[17179596.792000] cx88[0]/0: registered device vbi0

It look like the TV tuner may be found, the radio tuner probably has a different module.  I will go look.  

Thank you all for the help so far.  I will let you know what I find.

David Davis
Toledo, OR 97391

---

### Post by superm1 on 2007-01-06
> **greatgoo said:**
> AH HA!!!!

cx88xx is the module.  A quick command line modprobe did not fail as the others had.  So I reset the options parameter to cx88xx and rebooted the machine.  Here is the dmesg

[17179596.456000] CORE cx88[0]: subsystem: 1002:00f9, board: ATI TV Wonder Pro [card=4,insmod option]
[17179596.456000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179596.532000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179596.684000] cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 209, latency: 32, mmio: 0xee000000
[17179596.716000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179596.716000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179596.716000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[17179596.792000] cx88[0]/0: registered device video0 [v4l2]
[17179596.792000] cx88[0]/0: registered device vbi0

It look like the TV tuner may be found, the radio tuner probably has a different module.  I will go look.  

Thank you all for the help so far.  I will let you know what I find.

David Davis
Toledo, OR 97391
Well TV modules is the more important one anyhow right? :D

Does the TV one work?

---

### Post by greatgoo on 2007-01-07
> **superm1 said:**
> Well TV modules is the more important one anyhow right? :D

Does the TV one work?

Ahhhhh, No!

I am using Edgy Eft and there are other fish to fry.  Something in the updates is eating my video configuration and giving me a black screen, no X.  I am trying to figure out what is doing it, so the TV Card is on the back burner right now.  BUT! from this thread ..

[http://www.ubuntuforums.org/showthread.php?t=332261](http://www.ubuntuforums.org/showthread.php?t=332261)

I find this ..


Code:

cd /etc/modprobe.d/ 
sudo echo "options cx88xx card=4 tuner=44" > cx88xx 
modprobe -r cx8800 
modprobe cx8800


Which he said does work.

David Davis
Toledo, OR 97391

---

### Post by greatgoo on 2007-01-12
Well, I made it all work, with lots of help from here.

The card works well, sans the radio receiver, and TVTime is killer app.  I had to use Ubuntu 6.6 to make it work because my old video card would not work with 6.10.

Everything that worked is here.

David Davis
Toledco, OR 97391

---

