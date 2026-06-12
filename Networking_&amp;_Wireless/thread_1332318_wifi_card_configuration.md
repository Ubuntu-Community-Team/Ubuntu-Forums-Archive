---
title: "wifi card configuration"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by hezy00 on 2009-11-20
hello,
how can I config wifi card (edimax ew-7318usg) in bt4 beta and connect to the internet? thanks,
Hezy.

---

### Post by chili555 on 2009-11-20
Perhaps this will help: [http://ubuntuforums.org/showthread.php?t=1326121&highlight=ew-7318usg](http://ubuntuforums.org/showthread.php?t=1326121&highlight=ew-7318usg)

---

### Post by hezy00 on 2009-11-20
hi,
that refers to ubuntu wile I'm trying to use BT4. In the last one, I couldn't even succeed with installing terminal ("Unable to fetch some arcive, maybe run apt-get update or try with --fix missing?" so I'll be..). pls help, thanks again,
Hezy.

---

### Post by chili555 on 2009-11-20
There is no need to install 'terminal.' A terminal emulator or console is undoubtably alreay installed. Konsole, perhaps? Open it and type:```
sudo modprobe rt73usb
iwconfig
```You should have a wireless interface showing.

I am not familiar with 'bt beta.' Is it based on Ubuntu? If so, the commands and process should be very similar.

---

### Post by Iowan on 2009-11-20
> **chili555 said:**
> 
I am not familiar with 'bt beta.' First I thought it was Bluetooth, but then I found another of hezy00's posts that mentioned **Backtrack**. I'm still unfamiliar with it, but found [this]("http://ubuntuforums.org/showthread.php?t=1303718") thread that mentions networking is turned off by default.

---

### Post by hezy00 on 2009-11-21
To chili555,
ok. what do I do afterwards? couse It doesn't seem to connect anywhere. nor to the net. 
hezy.

---

### Post by Bucky Ball on 2009-11-21
Have you tried plugging in an ethernet cable and getting all updates? That may pick up the card and offer you restricted drivers.

System->Administration->Hardware Drivers. Anything there?

---

### Post by chili555 on 2009-11-21
> **hezy00 said:**
> To chili555,
ok. what do I do afterwards? couse It doesn't seem to connect anywhere. nor to the net. 
hezy.Did you first read and try the steps that Iowan pointed out?

---

### Post by hezy00 on 2009-11-23
Hello,
a dirver for usb wifi adapter (edimax ew-7318usg) (comes with the cd) has no setup nor run file. Seems like just a folder with all kind in it. How can I use it for bt3 or 4? Thanks,
Hezy.

---

### Post by coffeecat on 2009-11-23
The driver that comes on the CD is for Windows. Are you wanting to set it up in Ubuntu or Windows? It's not clear - you've used the "other" tag for your post. What is bt3,4?

But if you are using Ubuntu, which release number? Have you clicked on the Network Manager icon to see if your wireless device is working? If you are using Ubuntu and you can't see any networks, open a terminal and post the output of 'lsusb'.

---

### Post by hezy00 on 2009-11-23
You're wright. Sorry for being unclear. 'bt' is BackTrack... I ment that the disc that comes with the device contains dirver for linux, only there's no 'setup' or 'run' file or whatever there's should be to install it (device works properly in ubuntu without installing anything). Thanks again,
Hezy.

---

### Post by hansdown on 2009-11-23
Hi hezy00.

The backtrack forum probably has more people who can help.

[http://forums.remote-exploit.org/](http://forums.remote-exploit.org/)

---

### Post by cariboo on 2009-11-23
Please don't double post on the same subject. I've merged your two threads.

---

### Post by Bucky Ball on 2009-11-23
> **hezy00 said:**
> (device works properly in ubuntu without installing anything).

Why then are you attempting to install the drivers? If the device is working and you manage to install old or obsolete drivers (even from the manufacturer) you could have strange things occur.

If it ain't broke, don't fix it. Forget the CD drivers.

---

