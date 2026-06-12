---
title: "Problem with shares (All types)"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by hexdream on 2009-11-06
Hey all,


I have a bit of an odd issue connecting to shares using Karmic :frown:

I have two servers running Ubuntu Jaunty server. They have both Samba and NFS shares running. 

Internet works perfectly on my Karmic install, and I can access SAMBA shares perfectly **_if_** I dual boot into windows 7 (Used only for games if you are wondering). I can also access my Jaunty shares using other Jaunty systems such as my laptop.

On my Karmic machine/install:

I mount a share (successfully)
I can see the shares at whichever mountpoint I use.
I can see the folders of the share.
If I click on **empty** folders on the share, they open up (Not displaying content as they are empty).
If I click on folders with a very small number of files/folders in them, I can sometimes see the files, but can not open them. If I try open any file of any size in the share, Nautilus (2.28.1) effectively locks up. The same happens when I try access large folders. Attempting to navigate the shares at the command line also locks the command line)

This problem occurs with every type of share that I try. I have tried NFS, SAMBA and SSHFS, so I do not believe the problem lies on the server side, and I  do not believe the issue is with my network card.

Issue is also the same if I mount manually, via FSTAB, or browse using smb://server IP address in nautilus.

Does anyone have any suggestions? I'm hitting a bit of a brick wall here ](*,)

---

### Post by hexdream on 2009-11-08
Anybody? ):P

---

### Post by hexdream on 2009-11-13
OK, problem solved. Despite being able to browse the internet through it, seems there was an issue with the network card. 

Problem resolved with a small hammer, and a replacement network card. :D

---

