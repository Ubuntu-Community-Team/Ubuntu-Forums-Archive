---
title: "Mp3 player..."
date: 2006-01-25
forum: Multimedia &amp; Video
---

### Post by christhemonkey on 2006-01-25
My Mp3 player/USB memory stick normally works fine in ubuntu.

But earlier today, when i tried to copy files onto it to put on my windoze machine, it told me that i didnt have permission to write to it.

Tryed to change the permissions, but it said that it could not do because the device was read only! 

And then after that it just refused to let me write to the USB stick at all.:( 
Had to borrow my brothers in the end. Any ideas?

---

### Post by localzuk on 2006-01-25
Not to be a smart-arse but does your device have a switch on it which can be used to lock it? I have had this problem in the past.

Also, you may like to take a look in /etc/fstab and look for /dev/sdaX (X being either not there or a number). If there is a 'ro' in that line then it is only allowed to mount as read only. Change it to 'rw' and re-mount the disk.

---

### Post by christhemonkey on 2006-01-26
The hold switch wasnt on, and my fstab has always been set to rw.
It has worked in the past, but just randomely decided it didnt want to yday!

---

### Post by Bandit on 2006-01-26
Have you tried to chown of the usb stick directory?
Try that and see if it helps.
Cheers,
Joey

---

### Post by christhemonkey on 2006-01-26
Says this device is read only.:S

---

### Post by aysiu on 2006-01-26
What filesystem does your MP3 player use? FAT16? FAT32? NTFS?

---

### Post by christhemonkey on 2006-01-26
er, not sure. But it is usable in windows.
Probs one of the FAT ones methinks?

How does one go about checking this?

---

### Post by aysiu on 2006-01-26
[QUOTE=christhemonkey]er, not sure. But it is usable in windows.
Probs one of the FAT ones methinks?

How does one go about checking this?[/QUOTE] Boot up Ubuntu. Plug in the MP3 player. Then go to Applications > Accessories > Terminal and type ```
sudo fdisk -l
``` It'll probably be at the bottom... /dev/sda1 or /dev/sde1

---

### Post by christhemonkey on 2006-01-28
il let you know...!

---

### Post by christhemonkey on 2006-02-01
twas FAT32, but am on breezy now and hasnt played up since.

---

