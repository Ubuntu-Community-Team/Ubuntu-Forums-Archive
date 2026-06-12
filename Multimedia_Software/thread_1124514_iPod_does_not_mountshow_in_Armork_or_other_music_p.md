---
title: "iPod does not mount/show in Armork or other music player"
date: 2009-04-13
forum: Multimedia Software
---

### Post by sheelagh on 2009-04-13
[FONT="Arial"]Hi

I have just brought an iPod Touch 2G (v 2.2.1), however my Ubuntu (started with 8.10, now upgraded to 9.04) does not seem to recognizes my iPod. When I connect it through the USB cable (iPod is Jailbroken and does not screen lock) it shows on the desktop with a camera icon and the name ”Apple, Inc. Ipod”, asking if I will open it with F-Spot. It does not show in /media.
It does not show either when running iTunes in WINE, however I mounts fine on a windows machine.

I would like to use Amarok as I is my primary media player in Ubuntu. Currently I run Amarok 2, but the iPod would not mount either in v1.x.x when setting it up through the device menu. Furthermore, I have tried Rythmbox and various other applications recommended, but none seems to recognize the iPod. Therefore it must be a packaged problem in Ubuntu it self – my suspicion is towards libgpod files, but they seem OK and up to date! 

Anyone – what is the problem? I have searched and searched for a possible solution but have not found the right one yet – can anyone help? 

Thanks. [/FONT]

---

### Post by LostMagix on 2009-04-15
I dont think the 2nd gen ipod is supported just yet, unless you want to try and jail break it (I dont suggest it)

---

### Post by Jimmynemo2 on 2009-04-15
Sorry to be the one to tell you, but there is no way currently to use the ipod touch 2g with ubuntu without jailbreaking it.

On the other hand, if you jailbreak it, it can sync wirelessly (actually the only way to sync, but you can drag and drop files to play, which is cool, though slow)

So yeah, to use mine, I found out how to jailbreak and did that- relitively easy, but also your only choice. Sorry

---

### Post by SuperSonic4 on 2009-04-15
from the OP: "iPod is Jailbroken and does not screen lock"

What happens if you do ```
sudo fdisk -l
``` (lower case L not a 1 (one))

---

### Post by Jimmynemo2 on 2009-04-15
Sorry i missed that in the original post.

Lets see- unplug it, stop trying to sync with the cable. Not needed.

grab your jailbroken ipod, open cydia
on home page, scroll down to "copying files to/from Device" and "openssh access how to"

once you are connected and set up according to what those say, you can (in ubuntu), click places, then connect to server, then change type to ssh, and it'll show up mounted under computer. Then you drag and drop song files over, and use pwnplayer (available in cydia) to play files as dragged over (you cant get them to show up in the official player as they arent in the song database that the usb cable allows to be created).


Also, here are the links that got me to where I am to use mine in Ubuntu:

[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

---

### Post by WildeBeest on 2009-04-17
I have the same problem as the OP.

I can do everything jimmynemo2 suggested, but I would like to be able to sync with amarok and gtkpod.

People on here say they have done it, but how?

---

