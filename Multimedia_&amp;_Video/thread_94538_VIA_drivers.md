---
title: "VIA drivers"
date: 2005-11-24
forum: Multimedia &amp; Video
---

### Post by sp_ubuntulinux on 2005-11-24
Are there anydrivers for a VIA graphics card? I tried dpkg-reconfigure xserver-xorg but that didn't work. :confused: :confused: :confused: :???: :???: :???:

---

### Post by Teroedni on 2005-11-24
what via card?? is it an integrated your talking about?


if you dont know do this

write in terminal```
sudo lshw
```

---

### Post by sp_ubuntulinux on 2005-11-24
This is the output that i got-
*-display
                description: VGA compatible controller
                product: VT8378 [S3 UniChrome] Integrated Video
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dbffffff iomemory:dc000000-dcffffff irq:11

Yes, it is an integrated card. :D

---

### Post by jvictor on 2005-11-24
PLz run a search on S3 Unichrome pro drivers , u will get the soln

---

### Post by Teroedni on 2005-11-28
did you get it to work?

If you did could you add a [solved] to the thread name?
Thanks:)

---

### Post by sp_ubuntulinux on 2005-11-28
I'm sorry. i just can't seem to figure out how to work this. I can't find any drivers on the net for ubuntu. :(

---

### Post by binks on 2005-11-28
[http://ubuntuforums.org/showthread.php?t=76037&highlight=S3+Unichrome+pro+drivers](http://ubuntuforums.org/showthread.php?t=76037&highlight=S3+Unichrome+pro+drivers)

see replay #6 m8

---

### Post by ivor on 2005-11-28
Initial breezy debs can be found at: [http://www.openchrome.org](http://www.openchrome.org).
cheers.

---

### Post by jeremyk on 2005-11-28
Once you have installed the drivers found at [www.openchrome.org](www.openchrome.org), what are you supposed to do to make it work?

Cheers

---

### Post by RaNd.Gr on 2005-12-21
After a lot of tries ...

Download [http://dri.freedesktop.org/snapshots/via-20051220-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/via-20051220-linux.i386.tar.bz2)
then I installed my new kernel (AMD) 

sudo apt-get install linux-image-2.6.12-10-k7
sudo apt-get install linux-headers-2.6.12-10-k7
sudo apt-get install linux-restricted-modules-2.6.12-10-k7

then I tried /via-20051220-linux.i386/sh install.sh

and ...

root@pc0:~# glxinfo
name of display: :0.0
__driCreateNewScreen_20050727 - succeeded
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI

---

