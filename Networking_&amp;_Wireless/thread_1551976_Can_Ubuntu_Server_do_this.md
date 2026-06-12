---
title: "Can Ubuntu Server do this?"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by purvis on 2010-08-13
I currently have 9 computers, 2 gaming systems, 5 U-Verse set top boxes, and 5 smart phones connected to my home network. 1 of the computers is running W7 and was purchased specifically to function as a server for all of my other devices to be able to send and receive files (primarily pictures, videos, music, and text) and share them with the other devices in my home, and perform back ups. I discovered that on most of the devices I cannot consistently access the W7 machine and the U-Verse boxes don't recognize it all. If I installed Ubuntu Server on this computer would I be able to share the files and back up my other computers to it? What about the U-Verse boxes? Would they be able to see the music, pictures, and videos?

---

### Post by cj.surrusco on 2010-08-13
Well I don't know what type of protocol that U-Verse uses, but Ubuntu server has many file sharing options. I would guess that U-Verse uses UPnP, but I can't say for sure. UPnP is available with Ubuntu server along with FTP, SFTP and SMB.

With all of those options, you should be able to set up sharing with all of your devices, you just need to check what type of connection each device requires.

---

