---
title: "Ralink RT2501: Very poor connection in Karmic"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Geoff Leopard on 2009-11-03
Hi

My laptop's wireless (lsusb shows a Ralink RT2501) worked fine in 9.04, but 9.10 sees a huge drop in signal strength. The card works, but only if I am within around 6 feet of the router; any further away and I lose the connection. I have tried both 32 and 64 bit installs with the same problem. The Jaunty live CD works fine, so it's not the card or the router.

The wireless light was off after the installs and needed to be switched on using the hardware, which hasn't happened in previous Ubuntu installs. I don't know if that is significant.

I will have to move back to Jaunty if I can't get this sorted out, which isn't the end of the world. Karmic is looking great apart from this.

Many thanks in advance for any advice.

---

### Post by kgbudge on 2009-11-20
I'm seeing something very similar. Under Hardy 8.04 LTS on my Dell Inspiron 530 desktop PC, my card works fine, being detected by the wireless manager as:

Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
RaLink RT2561/RT61 802.11g PCI

and I get good connectivity. It continued to work fine under 8.10 and 9.04, but when I tried to update to Karmic 9.10, the update hiccuped halfway through. After that, I found that my network connectivity stank. I could connect reliably to my wireless access point: Typing the stereotypical 192.168.0.1 into my browser address box immediately brought up the control panel for the router. However, all other sites were, at best, very slow to load and, at worst, completely inaccessible. My mail was also completely inaccessible. It was always the same sites I couldn't reach; those I could, were a bit faster when accessed repeatedly.

I burned a Karmic 9.10 disk yesterday (20 Nov 2009) and ran it as LiveCD. The problem was still there, so it wasn't a corruption of my configuration files on my hard disk.

I had to reinstall Hardy 8.04 LTS on my system. (Fortunately I had the wit to thoroughly back up before trying to update to Karmic.) Everything is working great now, so it's not my hardware.

It looks very much like something went wrong with the RaLink RT61 wireless card drivers between 9.04 and 9.10.

---

### Post by mhgsys on 2010-02-23
Same problem here;

EDIT: I just got the drivers from the xp partition I've just installed as dual boot. (drivers were on my recovery cd, installed it in windows)
(Hey , I paid for the damn windows right...>) 

Anyway; 
**I used ndisgtk to install the inf file.** 

**_And my problem is fixed._**
Ralink Technology, Corp. RT2501USB Wireless Adapter working like a charm again.

 Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Geoff Leopard on 2010-02-23
Just to say that Debian Squeeze has the same issue, so it's something upstream...

---

