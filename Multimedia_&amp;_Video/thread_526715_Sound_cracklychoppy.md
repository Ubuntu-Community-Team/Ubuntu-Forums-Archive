---
title: "Sound crackly/choppy"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Scooter7 on 2007-08-15
Hi, I'm having problem with my sound in Ubuntu.

I use Ubuntu 7.04.

Here is my sound information:

> Vendor: Intel Corporation
Device: 82801G (ICH7 Family) High Definition Audio
Bus Type: PCI


My problem is this:

When playing music, the sound seems kind of crackly.   And this explanation may seem odd, but the vocals (if any) sound as though the singers have something caught in their throat - kind of gargled, I suppose.

I don't have this problem when playing video, or when system sounds play.   I do get it when running things in programs such as Visual Boy Advance or zsnes - it's worse in these cases.

Perhaps I should mention that when I first installed Ubuntu, I had no sound at all - I had to modify /boot/grub/menu.lst to look like this (I added acpi=off):

> title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=728bff65-13f3-4cf9-b94a-84c26ce4ec86 ro quiet splash acpi=off
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

I asked someone I know who also uses Ubuntu, and he has the exact same chipset, yet didn't have these problems.

Any suggestions?

---

### Post by Kapre on 2007-08-15
Did you try changing the sound preference?

Go to System --- Preference ------Sound Playback 

Toggle the settings till you find your preferred sound. Hope this helps.

K

---

### Post by Scooter7 on 2007-08-15
Well, I don't know why, but changing it from 'default' to 'ALSA' fixed it, even though I had already tried that... thanks, Kapre!

-edit-

Odd, it seems that now I can only run one program that uses sound at a time.

Visual Boy Advance won't start if XMMS is open, and when XMMS is open pidgin's sounds don't play...

Looks like I'm back at Step 1.

---

