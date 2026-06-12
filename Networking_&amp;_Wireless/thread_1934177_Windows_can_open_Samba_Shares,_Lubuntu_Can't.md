---
title: "Windows can open Samba Shares, Lubuntu Can't"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by whell on 2012-03-01
Here's a question from a Linux novice:

I have two laptops running Lubuntu 11.10.  One is acting as a "server".  I have a Windows 7 PC and another laptop running Lubuntu 11.10 acting as "clients".  Attached to the server laptop is a Seagate 2 TB hard drive that I want to share with the two clients.  All the computers are in a home network environment, and the Win 7 PC and Lubuntu client are connected wirelessly.

I've successfully set up the Windows 7 PC so that it has read/write access via samba to the USB hard drive attached to the server.  I've had no luck so far getting the Lubuntu client laptop to access the USB hard drive.  

Can anyone give me any pointers on this?

---

### Post by collisionystm on 2012-03-01
> **whell said:**
> Here's a question from a Linux novice:

I have two laptops running Lubuntu 11.10.  One is acting as a "server".  I have a Windows 7 PC and another laptop running Lubuntu 11.10 acting as "clients".  Attached to the server laptop is a Seagate 2 TB hard drive that I want to share with the two clients.  All the computers are in a home network environment, and the Win 7 PC and Lubuntu client are connected wirelessly.

I've successfully set up the Windows 7 PC so that it has read/write access via samba to the USB hard drive attached to the server.  I've had no luck so far getting the Lubuntu client laptop to access the USB hard drive.  

Can anyone give me any pointers on this?

The first question would be, how did you do it? What steps have you taken so far? Did you actually edit samba or did you just right click on a folder and hit SHARE

---

### Post by whell on 2012-03-01
Yeah, I guess that would help to know!  :redface:

On the server laptop, I opened share-admin from a terminal window and set up the shared folder on the USB hard drive.  When I go to the Windows 7 PC, I can go to the Networking folder.  I see a network icon for my Lubuntu server (called Musicbox).  I can click on the icon, and it opens a folder with my shared folders inside.

How can I access this shared folder from my client Lubuntu laptop?

---

### Post by SteveDee on 2012-03-02
> **whell said:**
> ...How can I access this shared folder from my client Lubuntu laptop?

Look here: [http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba](http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba)

---

### Post by whell on 2012-03-02
Thanks.  I'll give this a try over the weekend.

---

