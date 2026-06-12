---
title: "DVD playback not working in Totem or MPlayer"
date: 2008-11-28
forum: Multimedia Software
---

### Post by swr12 on 2008-11-28
Hello,

I have just recently purchased a CD-RW/DVD_+_RW Drive. I am not able to playback commercial DVDs in MPlayer or Totem. When I try to play a DVD in MPlayer I get "ERROR! Seek failed". When I try to play the same DVD in Totem I get "An error occured Internal data flow error." This same DVD plays fine in my standalone DVD player. The drive is a LITEON DH20A4P. The region code is set correctly for where I live. I have installed all the required software (I think) including: the ubuntu restricted software package and the libdvdcss2 package. Is their something I am missing?:confused: 

Any information would be appreciated.

---

### Post by mc4man on 2008-11-28
When you install a new drive it's going to get 1 upped /dev links, even when it's a replacement.
Most players will default to /dev/dvd for dvd movies.

Run ```
sudo lshw -C disk
```
to check what your drives links and device is.

If it isn't /dev/dvd you can make adjustments in each players settings (dev/dvd1, /dev/dvd2, whatever.

If it was a replacement drive then resetting udev/rules.d/70-persistent-cd.rules is a good thing to do.

```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

Leave it looking like this and save and reboot

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

If your new drive was /dev/dvd in lshw and in 70-....rules then there is some other issue that needs to be addressed.

You can safely delete the entries in 70-....rules, they are rewritten upon booting up.

---

