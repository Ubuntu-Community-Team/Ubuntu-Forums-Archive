---
title: "Sharing Disk Drive on Ubuntu with Windows XP"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by unckybob on 2008-12-13
I'm running Windows XP on my laptop. My laptop is particularly convenient to use as a DVD player. It's convenient to be able to put it wherever I want. Unfortunately my disk drive is broken and it may take some time to get a replacement. I'm trying to play it on my Ubuntu machine over the network. I installed Samba and I managed to share it on the Ubuntu machine at /media/cdrom0. My DVD player on the laptop software has an option to use a DVD from a folder. So I use it using Network Places. 

In the "Open" box it comes up as: 

"cdrom0 on Dell-Ubuntu server (Samba,Ubuntu) (Dell-ubuntu)". 

Anyway once I've selected it, in an error box it says: 

"The selected folder does not have valid DVD content." 

Please help.

---

### Post by superprash2003 on 2008-12-13
is the cd rom browseable from the network?? does it have read only permission//or write as well/??does it ask for password?

---

### Post by unckybob on 2008-12-13
I can browse the drive from the Windows machine. It is read only. I doesn't ask for any password.

---

### Post by superprash2003 on 2008-12-14
firstly im not sure if your software would allow access from a netowrk shared folder.. as it is designed to read from a CD/DVD drive and not a network folder. both of them do behave differently.. although you could try giving that folder write permissions and then trying..

---

