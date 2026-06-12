---
title: "unable to use wireless on 10.4"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by Kaorichan2009 on 2010-11-01
I have a wireless connection through my laptop's BCM4312. But I cannot get it to work at all not sure if i dont have the drivers and it grays out enable wireless... Do i have to get a different card?

The card is installed now its saying that the wireless is disabled? How to get around that?

---

### Post by Kaorichan2009 on 2010-11-01
i tried something else
```
rfkill unblock all
```
but it says permission denied.
how to get around it?

---

### Post by Enigmapond on 2010-11-01
Right-click on the network icon on top and make sure it's enabled. If it is then go to System/Administration/Hardware Drivers and see if the Broadcom driver is enabled...you will need a connection to the internet if not and it will download the driver.

---

### Post by chili555 on 2010-11-01
Most Broadcom cards require firmware. Since it is proprietary, it is not installed by default. If you can get a wired ethernet connection, you can go to System > Administration > Hardware Drivers. You will be offered Broadcom drivers, the firmware package, actually.> it says permission denied.Preface the command with sudo. *rfkill *is probably not the problem; firmware is.

---

### Post by Kaorichan2009 on 2010-11-01
computer flopped and now i cant boot into ubuntu need reinstall. Should i just get 10.10?

---

### Post by chili555 on 2010-11-01
I recommend 10.10. I use it on 3 computers and it's solid. Post back if we can help.

---

### Post by Kaorichan2009 on 2010-11-01
Better check for blank dvds then. haha.

---

### Post by Kaorichan2009 on 2010-11-02
Alright 10.10 is loaded. now how to change the screen to widescreen mode and to install the wireless...

---

### Post by Kaorichan2009 on 2010-11-02
now it wont install. System error comes up when i wanna install the drivers.
Nevermind it works! Finally!!

---

### Post by Kaorichan2009 on 2010-11-02
> **chili555 said:**
> Most Broadcom cards require firmware. Since it is proprietary, it is not installed by default. If you can get a wired ethernet connection, you can go to System > Administration > Hardware Drivers. You will be offered Broadcom drivers, the firmware package, actually.Preface the command with sudo. *rfkill *is probably not the problem; firmware is.

This worked. I forgot the sudo command Thanks~

---

### Post by chili555 on 2010-11-02
Glad it's working. Have fun!

---

