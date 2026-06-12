---
title: "Problems with Music Player on Ubuntu 7.11"
date: 2009-07-21
forum: Multimedia Software
---

### Post by Ant01 on 2009-07-21
I have been running Rhythmbox for a while now using a NFTS removable hard drive as the storage for my music. Lately the player has been loosing the index of the songs so I had to reload the directory. Sometimes I can't find the removable disc and I have to reboot Ubuntu. I then uninstalled Rhythmbox and tried to reinstall it but somehow it says it can't find the necessary files. 

I've tried using Amarok but am having the same problems. I am not sure if the Ubuntu is corrupt, or if the windows removable disk is having problems or some other software problems. 

Please can someone advise before I make a total mess of things..:(

---

### Post by ajgreeny on 2009-07-21
I suspect the music player, whichever one you use, may loose the removable drive files and folders if the disk sometimes mounts as a different /media folder, as can happen with usb disks, or even internal disks, if they are mounted in a different order to normal and can therefore change from /media/disk to media/disk1 or even /media/disk2.  The only way that you can avoid this happening, that I'm aware of is to label your ntfs partition, which is probably most easily done with gparted.  It will then always mount as /media/label.

---

### Post by Ant01 on 2009-07-22
Thanks for the help I managed to fix the problem using ntsfsfix to fix the mount, I hope it stays that way.

I still am having the problem reinstalling rhutmbox, when I synaptic package manager to upgrade I get the following error;
926225123365

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.2-0ubuntu4_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.2-0ubuntu4_i386.deb)
  404 Not Found
Please help as amarok doesn't seem to be working properly or I don't know how to use it...

---

### Post by ajgreeny on 2009-07-22
I assume you mean ubuntu 7.10, as there was never a 7.11 version, but whatever, that version of ubuntu is no longer supported, though I think it is still possible to get packages from archived repos. somewhere on the web, though a search has not come up with anything useful.

However, it would be worth upgrading to a newer version of ubuntu, I think, and suggest 9.04 is the best yet version, for me, at any rate.

---

