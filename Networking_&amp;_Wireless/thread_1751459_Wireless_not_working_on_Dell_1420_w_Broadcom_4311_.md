---
title: "Wireless not working on Dell 1420 w/ Broadcom 4311 Card"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by dgellerup on 2011-05-06
I have been reading threads and trying all kinds of things to get the wireless internet to work on my laptop to no avail. I am brand new to Linux and could really use some help.

Here is my problem:
When I click on the "Networks" icon in the upper right of the top taskbar, it doesn't show wireless networks at all. It only shows "Wired Networks, auto Etho (my ethernet connection), disconnect, VPN connections, enable networking (which is checked), information, and edit connections." This happened after I tried to fix the problem that I had before, in which it had a blacked-out option for wireless that said "Device Not Ready (Firmware Missing)." I'm pretty sure I downloaded and installed the b43 cutter, because I typed in the code exactly how it was described in other threads, but still no luck. I even successfully installed the broadcom STA driver and activated it but still it doesn't work.
I downloaded the most recent version of Ubuntu which I believe is 11.04? this week (May 1, 2011).


When I run 
lspci -v | less

I get:

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: Dell Wireless 1390 WLAN Mini-Card
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: wl, ssb


Any help on this would be much appreciated

---

### Post by garvinrick4 on 2011-05-06
I do not have a machine with broadcom cards but this seems like the link for you:

[[ubuntu] Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1604868")

---

### Post by bkratz on 2011-05-06
I think you will be interested in this thread.

[http://ubuntuforums.org/showthread.php?t=1741865](http://ubuntuforums.org/showthread.php?t=1741865)

---

### Post by BertN45 on 2011-05-06
I have the same wifi card: 
[LIST=1]
[*] Deactivate the Broadcom STA driver using "Additional Drivers"
[*] Start the Synaptic Package Manager and type b43 in the filter box.
[*] Mark the firmware-b43-installer and the b43-fwcutter for installation and Apply.
[/LIST]"

That is all and it should start your wifi, it did start my BCM4311 on my Dell 1521.

---

### Post by dgellerup on 2011-05-07
Thanks, Bert. Apparently the cutter was already installed/activated, I just had to get the STA out of the way. Anyways, wireless is working now, thanks a bunch guys

---

