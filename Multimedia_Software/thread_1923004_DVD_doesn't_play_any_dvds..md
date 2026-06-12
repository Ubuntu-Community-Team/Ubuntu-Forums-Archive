---
title: "DVD doesn't play any dvds."
date: 2012-02-09
forum: Multimedia Software
---

### Post by amrishp on 2012-02-09
Hi to all,
I am having a big problems to make Ubuntu 10.04LTS to play DVD. I have run followings:
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

All went ok and installed perfectly..Rebooted computer and try to play DVD I purchased from store with no luck using vlc, Mplayer, Media Player, Kaffeine. I tried any and all DVD player I can use in Ubuntu bur no luck. Can any one help me please to resolve this? I have SATA DVD drive.

I use code 

sudo lshw -C disk  and got following:

*-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7201S5
       vendor: Optiarc
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1H0E
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

Thank you all in advance.
Amrish

---

### Post by wolfen69 on 2012-02-09
Do you have a different DVD to try?

---

### Post by pmsagdeo on 2012-02-09
Same problem here. Mine are IDE (PATA) DVD drives.  Neither will play DVDs in Totem Movie Player and VLC.  Totem claims I may not have rights to access the file.  Not true. I am the only user of this computer. VLC produces a read error. The Linux Disk Utility claims "NO MEDIA DETECTED". Really! The DVDs play in Windows machine just fine. Strange!!!

Anyone clue as to what is happening will be gratefully acknowledged. 

Thanks. 

Pradip

---

### Post by amrishp on 2012-02-09
> **wolfen69 said:**
> Do you have a different DVD to try?
Hi wolfen69,
Yes, I have tried several DVDs but still it doesn't play and gives all kind of errors. like VLC gives error msg like input doesn't detect /dev/dev or /dev/sr0 and so on not only that but I have wipe out entire hard drive and re-install all different version of Ubuntu and Kubuntu from 10.04 to latest 11.10 with same resuls. surprisingly all these dvds works fine wth Windows on the same computer with same SATA DVD drive!! it seems like simply Ubuntu do not support this drive as as soon as I insert dvd in the drive it keeps spining but doesn't load or mount and without that I can not even add dvd location as a path in to any players.

I hope some one has solution to this.
Thanks,
Amrish

---

### Post by adnon on 2012-02-09
I have the same issue the only thing I can add is that it seems to play regular CD correctly (music, data) but not DVD's, and it doesn't matter if the DVD has just data on it which I wrote on it via a windows machine. It been like that since I installed it (bout a year ago) and when I did originally install the OS I used a DVD with multiple distros on it, but now I can't even read that DVD. 

adnon

---

