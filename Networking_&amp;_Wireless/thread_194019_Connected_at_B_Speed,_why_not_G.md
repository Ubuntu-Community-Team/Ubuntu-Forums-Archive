---
title: "Connected at B Speed, why not G???"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by GmAz on 2006-06-10
My wifi card has the Atheros 5212 chipset on it and it works great.  I lost it when I updated the NVidia drivers and madwifi put it back in perfectly.  The problem is that it connects at B speeds (11 mbps).  I would like it to connect at 54 mbps.  I know the internet speed won't be affected, but I do sometimes transfer files back and forth between my laptop and desktop and would like the speed.  Thanks!

---

### Post by GarBhaD on 2006-08-14
I have the same problem as you. I have a laptop and a desktop, both with a 802.11g speed PCMCIA/PCI card with atheros chips. Both computers use Ubuntu 6.06.
Does anyone know why is this happening? iwconfig states that speed is 48-54Mbps, but transfer only reaches 1.2MB/s at most (which is 802.11b speed).
Please help.

---

### Post by GarBhaD on 2006-10-29
I tried transferring files with different protocols (ftp, ssh, nfs...), but I always got 1MB/s at most.
I just installed ubuntu 6.10 in **one** of my computers (desktop PC) and the transfer speed doubled!!
Does this mean that there was a problem with the previous drivers? Is there a way to get 4-6MB/s over wifi in Linux? Please, help!

---

### Post by GarBhaD on 2006-10-31
In the end, speed did not double itself. There seems to be an issue with the System Monitor, who reports 2MB/s when in fact I'm only receiving 1MB/s :(

---

### Post by GarBhaD on 2006-11-10
I finally installed windows in both computers and tried a file transfer using the official drivers of the wireless cards, and I barely got 1.5MB/s. So in the end, there was no problem with ubuntu at all: it's just that wifi sucks :P And I have a really good signal! What a let down. At least, I hope this can be of help to somebody else...

---

