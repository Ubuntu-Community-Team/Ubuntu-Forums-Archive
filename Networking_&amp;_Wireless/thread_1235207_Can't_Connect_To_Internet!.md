---
title: "Can't Connect To Internet!"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by ebartolon on 2009-08-08
Can't Connect To Internet on Linux Ubuntu.:(:confused:

---

### Post by Vakman on 2009-08-08
We need more information. Is it a wired or wireless connection? Are what version of Ubuntu are you running? Also please post the output of ```
lspci
``` so we know what hardware you have.

---

### Post by ebartolon on 2009-08-08
i have a wired coonnection and the hard ware is...

---

### Post by ebartolon on 2009-08-08
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:08.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by ebartolon on 2009-08-08
and i have 9.04

---

### Post by ebartolon on 2009-08-08
...

---

### Post by Vakman on 2009-08-08
There is no Ethernet controller listed in lspci. Is the network card that has the Ethernet connection on it a PCI card or are you connecting to the ethernet port directly on the motherboard?

---

### Post by ebartolon on 2009-08-08
motherboard

---

### Post by ebartolon on 2009-08-08
any way you can help me, becasue i se the orange/green light flicker but no internet

---

### Post by Iowan on 2009-08-09
Unless you're just trying to boost your post count, there's no need to start a new post for each sentence. There's even an Edit feature to change existing posts.
**lshw -C network** will also show networking hardware, but probably won't show more than **lspci**. (Might check it anyway).

---

### Post by ebartolon on 2009-08-09
Iowan I got:

*-network DISABLED      

       description: Ethernet interface

       physical id: 3

       logical name: pan0

       serial: 72:12:76:37:f0:00

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by AmerNewbieInDE on 2009-08-09
have you checked that the cable is pluged in? mayyybe try a different cat5 cable

---

### Post by ebartolon on 2009-08-09
:confused::confused::confused::(yes it is connected:lolflag::lolflag: and i tried new cable still nothing

---

### Post by ebartolon on 2009-08-10
help!

---

### Post by ebartolon on 2009-08-10
why did youu just hijack my post.

---

### Post by zkriesse on 2009-08-10
First.....ebartolon....he didn't hijack your post....this is the Ubuntu forums for cryin' out loud....give it a break...second....did you even try to update your computer/do a driver/try wireless? Be more specific man.

---

### Post by Iowan on 2009-08-10
pan0 is likely the "personal area network" (bluetooth).  Anything in there about eth0 or wlan0? You can try **dhclient eth0**, but it will probably return an error.

---

### Post by overdrank on 2009-08-10
> **ebartolon said:**
> why did youu just hijack my post.

> **Zachk18 said:**
> First.....ebartolon....he didn't hijack your post....this is the Ubuntu forums for cryin' out loud....give it a break...second....did you even try to update your computer/do a driver/try wireless? Be more specific man.

I have moved the other post to its own thread and it is not nice to highjack someone else is thread. :)

---

### Post by Iowan on 2009-08-12
Likely now new information, but check **lshw -C network**.

---

### Post by harryhood on 2009-10-15
Same exact problem here, 
tried ifconfig pan0 down
and then did the the same with eth0,
dhclient -r eth0
ifconfig eth0 up
dhclient eth0
After that, still no connection
Works fine in windoze...

---

### Post by sir_cheats_a_lot on 2009-10-15
check your bios settings, if its disabled in your bios it's not even going to be detected in ubuntu.  if it's not disabled it **_*might*_** have a power saving setting that disables it when it goes inactive after so long.

---

