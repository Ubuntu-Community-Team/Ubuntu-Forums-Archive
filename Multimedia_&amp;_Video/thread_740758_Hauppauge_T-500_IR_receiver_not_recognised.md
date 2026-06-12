---
title: "Hauppauge T-500 IR receiver not recognised"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by parvaman on 2008-03-31
Hello,
I'm new to Ubuntu + MythTV so I'd appreciate some pointers from anyone. I have set up a MythTV system running Gutsy 7.10 and have installed a Hauppauge Nova T-500 Dual DVB-T tuner for Freeview reception in the UK. I got the card up and running using the MythTV wiki guide at [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI).
The only problem is that the IR Receiver in the card does not seem to be recognised

The information from “dmesg | grep DVB” should be something like…
…
[ 34.224298] DVB: registering frontend 1 (DiBcom 3000MC/P)…
[ 34.787147] input: IR-receiver inside an USB DVB receiver as /class/input/input4
[ 34.787308] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.

…but I don’t get the “…input: IR-receiver…” row when I grep, so therefore cannot get the Hauppauge remote working.

Anyone seen this sort of error before and knows how to get the IR-Receiver recognised? I'm using firmware dvb-usb-dib0700-1.10.fw.

---

