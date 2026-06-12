---
title: "Twinhan USB remote not work after 10.01"
date: 2010-06-16
forum: Multimedia Software
---

### Post by emaydubya on 2010-06-16
I've had a Twinhan DVB remote control for many years. It's been fantastic. BEEN.
After 10.01, buttons longer work except for Volume Up and Down which didn't do this before.

I had a party over the weekend and it was such a freaking huge pain to have to go to the pc to switch tracks etc when the week before I could use my remote. ( I know.. I'm venting again)

The Twinhan USB remote, shows up as a keyboard so I've never had to configure it. NEVER. And that's been what's so awesome till now.

This thread is the same problem but I'm not allowed to post a reply there.
[http://ubuntuforums.org/showthread.php?t=1452636&highlight=twinhan+remote](http://ubuntuforums.org/showthread.php?t=1452636&highlight=twinhan+remote)

I'm guessing that some development has gone on there that has broken it. Either the kernel or Ubuntu. Who knows? So I'll add this to the list that used to work but don't now.

Any ideas... I guess not. Chalk it down to Linux's advancement.

---

### Post by ikb_meats on 2010-06-23
TL;DR - Try reverting 2.6.32's twinhan-related USBHID patch.

Wall of text version:

I ran into this problem last night; until I came across a couple forum posts like this one, I'd just assumed that the remote had died due to neglect...

From what I can work out, a USB hid driver specifically for twinhan USB HIDs was added in 2.6.32, and the USB IDs for these devices are blacklisted in the main usbhid driver.  Accordingly, I'd assume it's this new driver that's the cause of the issues.

I've reverted the patch in question in a local copy of the kernel source and rebuilt the various USB HID modules, usbhid.ko now finds the twinhan IR sensor again, but I'm not at home to test it right now.  That said, given that previous Ubuntu releases would let me type on a text console with the remote and Lucid presently doesn't, I'm going to work on the assumption that it _IS_ the HID driver changes that have caused the issue, and not anything related to HAL/udev/etc (which is the only major change I can think of which might break something like this.)

Edit: to elaborate, I suspect there's a handful of different twinhan sensor/remote combos, of which the 2.6.32 changes are useful for some, and they all use the same USB ID (0x62530100).  From what I can work out, the hid-twinhan module does some kind of alternate mapping to the button presses, some of which may not necessarily correspond with all remotes.  This is all conjecture, though, I could be completely talking out of my hat.

Edit 2: Home from work, remote is operational with the 2.6.31-style usbhid module.  I'm not 100% clear on what purpose the change had, but it's definitely not good with at least SOME Twinhan remote/sensor combos.

---

### Post by blu_zee on 2012-01-25
Yes, I just tried getting my old twinhan remote going again too and ran into the same issue.  Looked at the source for hid-twinhan and it looks like a totally different remote. That driver makes my remote useless.  

Quick possible solution instead of reversing the patch and recompiling the driver is to blacklist usbhid and use usbkbd instead. The remote works like it did before. If you need usbhid for other devices that may be a problem. I had success loading usbkbd first and then usbhid after but I don't know if the two are really suppose to be loaded at the same time or not. 

I don't know why this driver was necessary as it wasn't difficult to remap the hot key shortcuts to match the buttons on the remote to work with most programs.  It would be nice if the author of hid-twinhan could remap his buttons in user space rather than break other peoples remotes.

---

