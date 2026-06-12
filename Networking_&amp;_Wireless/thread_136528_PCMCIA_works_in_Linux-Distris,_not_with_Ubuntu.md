---
title: "PCMCIA works in Linux-Distris, not with Ubuntu?"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by eraserhead on 2006-02-26
Hi! 

To get my old IBM 600x connected to the world out there I bought a "TDK Pro Digital" PCMCIA-card. While the support of this card is officially unknown, I got it to work with Vector Linux (Slackware-based Distri) and with Suse by adding the following lines into my /etc/pcmcia/config-file after running a cardctl ident:
         card  "TDK", "Pro Digital LAN+GSM"
           manfid 0x021b, 0x0202
           bind "pcnet_cs"

BUT, unfortunately this does not work with Ubuntu!!!!

Is there anyone out there who can help me, please??


Thanks in advance!!

---

