---
title: "Two Identical Nvidia Video Cards - Only 1 Has Output"
date: 2011-02-20
forum: Multimedia Software
---

### Post by ACMarina on 2011-02-20
I've been working with my brother to help him build a nice little Ubuntu setup after he had some rather nasty spyware cripple his Windows installation.

He's running two Nvidia 8400GS cards.  As I understand it, although each card has three outputs (VGA, DVI, HDMI) we can only run two at a time. No big deal.  He'd like to have one main monitor, one on each side, and then the HDMI out to his TV.  As of right now, we're just working with monitors though in VGA and DVI.

Only one of the cards shows up in the Nvidia Server Settings window, though.  When we run "lspci" it has entries for both cards, but only one of the cards will let us activate the monitors.  So we've got one of the cards showing signal in DVI and VGA, and nothing from the other card.

Interestingly enough, we were able to boot into the crippled install of Windows and bam, all three were up and although they weren't configured, they were usable.  Through the popup windows that spammed us we were able to get it set up just how he wanted, so we're just trying to get Ubuntu to do the same thing for him at this point. Fresh install of 10.10, if it makes any difference.

Thoughts or suggestions?

---

### Post by ACMarina on 2011-02-21
Bump - Somebody's got to have some info here!

---

### Post by tjones00 on 2011-02-22
I had an issue similar to this a couple months ago with 2 nvidia 9800gt cards using ubuntu 10.10 32b kernel pae.

The solution for me was to add "vmalloc=192M" to the command linux part of /etc/default/grub and update grub.

GRUB_CMDLINE_LINUX="vmalloc=192M"

then 

```
sudo update-grub
```

I'm not sure if this will still fix it with the current kernel and version of grub.

---

