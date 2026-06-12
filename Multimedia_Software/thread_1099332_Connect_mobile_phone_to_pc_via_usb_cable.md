---
title: "Connect mobile phone to pc via usb cable?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by markg48 on 2009-03-18
just wounderin if there was ubuntu software that would alow me to send messages and transfer files  from cell phone to pc i have software  on windows that allows me to send messages from pc and stuff

---

### Post by khelben1979 on 2009-03-18
Do you know if your Linux system is able to identify that mobile phone once it's inserted in the usb port?

```
lusb
```
will give you the answer to my question. How does it look like?

Also, if that mobile phone supports bluetooth, I think it will be easier. Do you know if it supports bluetooth? I have transferred files with an Nokia 6111 together with a Linux system and in this case it worked perfectly using bluetooth!

---

### Post by markg48 on 2009-03-18
yes it has blue tooth but i dino how to use it ubuntu detects it wen i plug it in trys to use it as a modem lusb doesnt work etha....

---

### Post by khelben1979 on 2009-03-18
Okay, try this instead:
```
sudo lsusb
```

When I used the bluetooth functionality from the mobile phone I used this together with the KDE enviroment (it was on a Debian Etch system). So I would suggest that you use KDE instead of Gnome which is default in Ubuntu to see if it get's easier for you. I can imagine that you might need some KDE applications besides the KDE enviroment itself, also.

---

### Post by blue_shift on 2009-03-18
Surely:
```
lsusb
```

---

### Post by markg48 on 2009-03-18
Bus 004 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Bus 001 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Hippytaff on 2010-10-31
Anyone know about the above, I'm having troubles :-)

---

### Post by syoung27 on 2011-06-08
as am i

---

### Post by nos09 on 2011-06-08
> **Hippytaff said:**
> Anyone know about the above, I'm having troubles :-)

my output of lsusb
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04e8:689e Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

i've successfully configured my phone with ubuntu - gnome, and can use mobile broadband gprs flawlessly !

now my question is : is your phone android based ?

---

### Post by syoung27 on 2011-06-08
mine is not, its a basic flip phone. Samsung Rugby.
i could just boot windows for this to make life simple but i dont want to lol.
just looking to view the memory card on it to format, add new items etc..my comp recognizes it when i run terminal but no applications will at all.

---

### Post by nos09 on 2011-06-08
> **syoung27 said:**
> mine is not, its a basic flip phone. Samsung Rugby.
i could just boot windows for this to make life simple but i dont want to lol.
just looking to view the memory card on it to format, add new items etc..my comp recognizes it when i run terminal but no applications will at all.

does it appears on the side panel of nautilus(file manager) ?!? if so paste the output of the 
```
#fdisk -ls
```

i had a old phone which had the same problem but i was able to mount it manually.. see if that works for you.

---------------------------------------------------------------------------------

okay now i'm going to get some sleep but before that let me explain how to mount drives manually.. if that works for you.

here's the output of my #fdisk -ls

> root@olympians:/home/nos# fdisk -ls

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002637c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12803   102840066   83  Linux
/dev/sda2           12804       14267    11759580   83  Linux
/dev/sda3           14268       15035     6168960   82  Linux swap / Solaris
/dev/sda4   *       15036       19457    35519715   83  Linux

Disk /dev/sdc: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders
Units = cylinders of 3192 * 512 = 1634304 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1204     1920955+   6  FAT16

Disk /dev/sdd: 1 MB, 1048576 bytes
1 heads, 2 sectors/track, 1024 cylinders
Units = cylinders of 2 * 512 = 1024 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

now the /dev/sdc1 is my memory card. so to mount it you have to create a directory firts. 
#mkdir /media/*nameofdir*
then to mount the card :
#mount /dev/sdc1 /media/*nameofdir* 

you can access that by nautilus in your /media folder. 

hope that helps, good night !

---

### Post by syoung27 on 2011-06-08
no it's not there..

---

### Post by Ulysses4ever on 2011-07-22
> *now my question is : is your phone android based ?*
> *mine is not, its a basic flip phone. Samsung Rugby.*

So as mine. Usual cell phone (not smartphone), Samsung S5620 Monte. lsusb shows &#8220;Samsung Electronics Co., Ltd&#8221;, but Nautilus do not show usb mass-storage device.

---

### Post by sandy8925 on 2011-07-22
some phones don't properly expose the inbuilt storage/memory card when connected. i did use one program before. try the instructions by siddhuwarrier here: [http://ubuntuforums.org/archive/index.php/t-915874.html](http://ubuntuforums.org/archive/index.php/t-915874.html)

---

### Post by befana on 2011-07-22
I have no problems with my Nokia E63, but my ZTE Blade with Android 2.2 doesn't want to show on the side panel of nautilus when connected via USB cable. What to do?

---

### Post by Ulysses4ever on 2011-07-29
It turns out that in order to plug in Samsung phone as mass-storage device you should check corresonding option in cell's menu: Settings &#8212; Phone &#8212; PC connection (S5620 Monte; menu items could look slightly different as I see localized version on my native language). I found &#8220;mediaplayer&#8221; option most appropriate.

---

