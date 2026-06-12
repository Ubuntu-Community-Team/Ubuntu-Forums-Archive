---
title: "Enabling Atheros AR9285 card on Toshiba NB205 from UNBR"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by audiorevolution on 2009-07-24
I just bought a Toshiba NB205-N310. I hurried home and immediately booted from a usb drive Ubuntu Netbook Remix. Unfortunately, I did not know that the NB205 ships with the Atheros AR9285 wireless card disabled, and that it must be enabled in XP (simply by pressing FN+f8 ) or Ubuntu will not recognize it. In my initial haste, I wiped the HDD clean of XP, without seeing any need to make an image backup - until now.

Now I cannot find a way to enable my wireless card, and I'm asking you for help. I have an acquired image of XP Home, but it's not the one shipped with the NB205. If I wrote this to my usb drive, and reinstalled XP (*shudder*), would I be able to enable my card with those two simple buttons?

Or can anyone else figure out another way to enable the card without wiping off Ubuntu?

---

### Post by dimeotane on 2009-07-24
My deepest sympathies! 

It would have been best to dd image the HD to a backup hard drive first upon unboxing.   

I'd check the Toshiba website for wireless drivers for the notebook... you could try installing those in a new installation of windows and see if it will turn on the wireless before returning to Ubuntu.

---

### Post by audiorevolution on 2009-07-24
Yeah, I wish I dded the HDD first - a lesson I won't soon forget.

Unfortunately, I'm not sure how to make a usb key bootable for installing XP.  Up until now I've only ever owned macs, so I've never done a full install of XP on my own.  dding the image to the key didn't allow it to be bootable on my NB205, and unfortunately the only tools I can find for making it bootable only run on windows.  Any advice?

---

### Post by audiorevolution on 2009-07-25
As for reinstalling windows to activate the card: I erased my pendrive, and selected "MS-FAT" as its file structure in reformatting, partitioning it entirely as freespace.  I then dded the XP Pro image I have onto the pen drive - but when I boot from it, it loads PXE2.1, but then immediately fails to locate an DHCP signal, despite my ethernet cable being plugged in.

I know I'm a noob, but can anyone suggest a way to achieve this?

---

### Post by LookTJ on 2009-07-25
Try installing this
```

sudo apt-get install linux-backports-modules-jaunty
```
If it doesn't install, make sure you are hard wired :)

---

### Post by audiorevolution on 2009-07-25
linux-backports-modules-jaunty is already the newest version, and does not affect my disabled card at all.

---

### Post by LookTJ on 2009-07-25
Did you check the restricted manager as well?

---

### Post by LookTJ on 2009-07-25
[http://ubuntuforums.org/showthread.php?t=1201551](http://ubuntuforums.org/showthread.php?t=1201551)

This same guy is having the same wireless issues.

perhaps it's a bug? I'd check with launchpad

More research: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.28/+bug/399983](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.28/+bug/399983)

---

