---
title: "ipod will not mount properly"
date: 2010-07-16
forum: Multimedia Software
---

### Post by meanmrmustard on 2010-07-16
A friend gave me an ipod shuffle, the first ipod I've actually tried to use.
When I plug it in two instances show up in 'places' - it seems it has two mount points.
When I unmount one it then shows as a USB mass storage device - the other tells me that it must have been mounted from the command line but won't unmount even at the cli.

I've tried gparted but it crashes when trying to create a new volume label or making a new partition. GTKpod also won't seem to affect it.

It does have the apple directories on it and gtkpod shows tracks there but when I try to play the music, the light flashes green and amber alternatively but will not play.

What do I have to do to clear this thing of all data/music?

---

### Post by coolcaseley67 on 2010-07-16
hi 
 
what version is your ubuntu ?

---

### Post by meanmrmustard on 2010-07-16
> **coolcaseley67 said:**
> hi 
 
what version is your ubuntu ?

hello!
This is a Hardy Heron machine.

---

### Post by coolcaseley67 on 2010-07-17
hi 


-from ubuntu 10.04 it works out of the box !  


- in Hardy Heron you will  have to jailbreak(which you've been trying ) [https://help.ubuntu.com/community/PortableDevices/iPhone ]("https://help.ubuntu.com/community/PortableDevices/iPhone")



-** Maybe upgrade to ubuntu 10.04 ?**

---

### Post by meanmrmustard on 2010-07-19
> **coolcaseley67 said:**
> hi 


-from ubuntu 10.04 it works out of the box !  


- in Hardy Heron you will  have to jailbreak(which you've been trying ) [https://help.ubuntu.com/community/PortableDevices/iPhone ]("https://help.ubuntu.com/community/PortableDevices/iPhone")



-** Maybe upgrade to ubuntu 10.04 ?**

I put 10.04 on my laptop and it mounted the ipod OK but trying to install rockbox fails. It told me that it didn't recognize the partition table and that it may not be an ipod.
Creating a new partition table with gparted only made matters worse - it now does not mount and gparted says it is ignoring /dev/sdc (hard drives in the machine are sda and sdb) because it has a logical sector size of 2048 bytes and it only supports 512 bytes for the sector size.
This is a second generation shuffle with firmware v1.0.4

I've just connected the ipod to my Windows 7 box and it told me it wanted to reset to factory defaults so I could add music from my library. I allowed this, then tried installing rockbox again (on 10.04) but it again could not read the partition table "may not be an ipod" was the message)

---

