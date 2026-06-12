---
title: "Orinoco Silver PCMCIA card doesn't work in lucid"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by fmouse on 2010-10-05
I have a Lucent Orinoco Silver PCMCIA network card that's been solid and reliable in Ubunto Feisty and Hardy on my Dell D600 laptop, however I recently upgraded Lucid and nothing I do gets the card up and running.  Fortunately, I've managed to do some jiggery-pokery with the firmware for the built-in Broadcom card and have it working fairly well, however I'd like to get the Orinoco card working again since it has some features, such as an external antenna jack, which aren't available otherwise.

The box is running linux kernel 2.6.32-25-generic.  The card has, I think, a Prism2 chipset (the model on it is PC24E-H-FC).  "iwlist eth1 scan" correctly identifies the wi-fi signal characteristics and shows a respectable signal level of -52dBm, however "iwconfig eth1" shows an incorrect frequency and "None" for an access point.  Using iwconfig I can finagle the parameters on the connection pretty much into compliance with what they should be, but still get link quality of 0/70 and a signal level of -122dBm.  "lsmod|grep orinoco" shows:
```
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
pcmcia                 30784  1 orinoco_cs
cfg80211              126496  3 orinoco,b43legacy,mac80211
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
```
I've tried disabling the Broadcom card (b43legacy module) but nothing I do brings my old Lucent/Orinoco card online or enables it to pass traffic.

Has anyone else had this problem and know of a solution?

---

### Post by maxslimmer on 2012-01-20
I'm running into this situation with xubuntu on 11.10. Just getting started looking for a solution so I'll post back when I know more.

---

