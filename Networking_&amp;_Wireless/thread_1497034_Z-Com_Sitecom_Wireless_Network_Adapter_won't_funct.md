---
title: "Z-Com Sitecom Wireless Network Adapter won't function."
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by murderslastcrow on 2010-05-30
Device 003: ID 0cde:0008 Z-Com Sitecom Wireless Network Adapter 100G+ WL-125, listed under lsusb in the terminal, is a USB wireless adapter I received in the mail this evening for my new dual-core super destructive doomsday machine computer I recently bought and installed Ubuntu on. Not much use to my master plan when it's hard-wired, though, since I plan to move it around occasionally and don't have the means or permission to move an ethernet cord to it.

So, I plug it in- no option to enable wireless, nothing. No proprietary hardware drivers offered.

So, I snoop around, and someone says they've loaded it with ndiswrapper and blacklisted the alternate driver, p54usb. So, I proceed to install ndiswrapper and load the inf file from the CD that came with my adapter. Only problem is, I'm on 64-bit, and ndiswrapper needs a 64-bit version of the driver to work, not the one on the CD. So I load the one in the Vista folder just in case it's 64-bit, since most computers shipping with Vista were. However, I don't believe this is the case, since it didn't work.

Of course, I updated initramfs with "sudo update-initramfs -k all -u" after blacklisting. No result.

So, I took p54usb off the blacklist, updated initramfs again, and I've been looking for how p54usb can support my adapter. However, I've come up short. I'd really like to get this working, since the shipping took forever, and I guess I was foolish to think just any adapter would work since all I'd tried before brought up wireless connections as soon as I plugged them in.

If anyone knows of a 64-bit driver for ndiswrapper that would work in this situation, or how to get p54usb working for this specific device, I would be extremely grateful. If this is not possible, I'm just going to buy a different one, since there's no way up giving up 64-bit just for WIRELESS.

---

### Post by murderslastcrow on 2010-05-30
K, so I used dmesg to find out which firmware it was requesting, downloaded to proper directory and renamed, and restarted the p54usb module.

And still, nothing. Also, dmesg still says it's requesting the firmware that I've downloaded using the instructions provided on this page. [http://wiki.debian.org/prism54#p54usb](http://wiki.debian.org/prism54#p54usb)


Dmesg output for now:

[I][  213.901318] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  214.061740] usb 1-4: firmware: requesting isl3887usb
[  214.067126] usb 1-4: (p54usb) cannot load firmware isl3887usb (-2)!
[  214.067137] usb 1-4: firmware: requesting isl3887usb_bare
[  214.073775] p54usb: probe of 1-4:1.0 failed with error -2
[  214.073841] usbcore: registered new interface driver p54usb[/I]

---

### Post by murderslastcrow on 2010-05-30
I suspect that the directory it wants me to create in Debian isn't the one I should be placing it in in Ubuntu. I'll have to check up on that in the morning, since I can't really bother with this at the moment. Please offer helpful suggestions if you can.

---

### Post by murderslastcrow on 2010-05-30
I was too lazy to go to sleep, and it turns out I was right. Just needed to move the firmware to /lib/firmware and the currently kernel folder (just to be safe), sudo modprobe -r p54usb, sudo modprobe p54usb, and now wireless just works.

Great, I think this is the third forum post where I've solved my own problem. How embarrassing.

---

### Post by Acerane on 2010-08-13
Please, can you explain exactly what you did ? I have the same problem and I have not found the solution yet :(

---

