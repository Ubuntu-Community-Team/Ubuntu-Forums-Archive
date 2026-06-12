---
title: "Updated Nvidia driver, now nothing works"
date: 2013-12-28
forum: Multimedia Software
---

### Post by crazypj10 on 2013-12-28
Hi all, 
Tried search various terms but can't find a decent answer. probably because I'm using wrong search parameters?
Sorry if this has been covered previously, I was running Ubuntu 12.04 LTS without any problems with Nvidia card and 3.04 Nvidia driver
This morning, after normal  update I checked for new video drivers and found update to 3.19 was available and tested so I activated it.
Now, I cannot get Ubuntu to boot.
Tried booting with fail safe video driver, still no luck, gets to end of first screen and says video test (failed) I forget exact wording but can look it up if required
Selected earlier version which just seems to have made things worse (and still no boot)
I have live CD but don't want to lose everything I've done in the last few months by nuking original installation and re-installing 
Will it be possible to use CD to remove Nvidia driver somehow and install generic driver?
I haven't tried boot repair yet either

---

### Post by crazypj10 on 2013-12-29
OK, did a LOT of searching around, ended up downloading Boot repair Disc and burning a copy on laptop.
It said everything was repaired and to re-boot computer
Well,it wasn't repaired and the Windows XP option was also missing so I'm back to using Ubuntu Live disc
As computer is booting into 12.04 there is a small cursor at top left corner of screen blinking away to show something is happening.
 When it reaches fault everything stops and I have a long list of processes that were started with this line as fail
*Starting load fallback graphics device                      [fail]
The boot repair disc gave this message in case it didn't work
[http://paste.ubuntu.com/6655507/](http://paste.ubuntu.com/6655507/)
 I had an idea I could find the Nvidia drivers in root and remove them, but, I couldn't find the any video drivers (when logged on as root)
I'm now completely stumped
WOW, I just opened the link, there is a ton of information I don't understand

---

### Post by Bucky Ball on 2013-12-29
Well, you have grub installed on three disk drives. That is going to cause a LOT of confusion. 

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
```

You appear to have XP installed on two hard drives (sda and sdb), unsure about the NTFS partition on sdc1, and Ubuntu installed in an extended partition on the third drive (sdc6).

What setup are you hoping to have at the end of all this? You want a dual-boot with Windows? Do you have personal data on here anywhere that you wish to save before going any further? If so, I would boot from a LiveDVD and back it up to an external drive now.

Straight up: it's a mess in there! :-k

If you can boot into Ubuntu, open a terminal and:

```
sudo update-grub
```

Restart. Any different?

If not:

```
sudo grub-install /dev/sda
```

Reboot. But if boot repair didn't fix, this may not either.

---

### Post by crazypj10 on 2013-12-29
I had a hard drive fail and got a bit paranoid so when I bought a new one I copied the entire contents to it. I've now removed it from computer. 
I was using spare as spare, mainly for pictures and video from Go-Pro, plus various pictures that have been scanned from 1970's~80's
I'm using live CD now, I'll pull everything off that I want to save then start over. Reminds me of the 'good old days' of Win 95 :redface:
The Boot Repair Disc added grub the second time I used it, I didn't know it would mess with all the drives

---

### Post by crazypj10 on 2013-12-29
Won't boot to anything
I've removed all the drives, checked them by connecting to laptop with adapters, repaired Windows file system (although it is still 'broken') and re-fitted only one
I'll try the boot repair again and add grup to the one I have fitted.
I know the initial problem was caused by the Nvidia driver update, the others were me trying to 'fix' it after doing bunch of searching.
I'm using Ubuntu live disc again at present, I don't know if I can use the code you posted to instal grub back onto hard drive but I'll find out
Get error  sudo: grub: command not found
Is this because I'm using live disc?

---

### Post by Bucky Ball on 2013-12-29
This doesn't work from the livecd?

```
sudo grub-install /dev/sda
```

---

### Post by crazypj10 on 2013-12-30
Still doesn't work. I found file with Nvidia 319 driver but cant delete it
Also has 319 update (can't delete or edit that either)
I tried logging in as root then use terminal but I just don't know what to type to remove the latest driver and force system to use early driver
I'll run the boot repair disc again as that will give more information.
OK, I'm pretty sure It should be sda6, the earlier sda is the Windows partition
'new' boot repair listing
http:// paste.ubuntu.com/6661423/

---

### Post by crazypj10 on 2013-12-30
Found an old Seagate Baracuda 20 gig EIDE drive and installed Ubuntu on that for now

---

