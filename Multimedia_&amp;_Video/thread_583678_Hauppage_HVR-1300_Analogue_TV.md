---
title: "Hauppage HVR-1300 Analogue TV"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by josno on 2007-10-20
I've been trying to get my WinTV HVR-1300 to work in Ubuntu since I moved house - before, DVB worked fine but as far as I can tell there's no DVB where I am (or at least I can't find any - Stockland Hill, Exeter, UK anyone?). 

Analogue works fine in Windows (though the reception's a bit dodgy) but I can't get it to work in Ubuntu at all. After I first tried it in Windows, tvtime-scanner picked up the four channels and I could use it fine (although I don't think there was any sound) but now not even the video will work. My composite input works fine however. Anyone have any suggestions?

---

### Post by kstam on 2007-11-07
Same problem here...
I have the same card. In Windows working fine both Analogue and DVB. In Ubuntu everything seems to be fine. Modules are loaded... cx88, cx88-blackbird, cx88-dbb, cx88-alsa... No error messages in dmesg... registers devices for analogue /dev/video0 (framegraber), /dev/radio0, /dev/vbi0, /dev/video1 (mpeg2 stream for analogue TV) and /dev/adaper0 for DVB-T.
I installed MythTV and I can configure all the inputs (Analogue for both /dev/video0 for the uncompressed and /dev/video1 as an mpeg2 card and digital for DVB-T), but when I try to search for chanels seems to work fine, but don't find any channel for the analogue TV (for both /dev/video0 and /dev/video1). For the DVB-T works fine and tunes on the four channels in my region. I can watch fine in mythtv the digital channels, no problem there... but no analogue TV.
As in my region (Greece) most channels are analogue and only four digital I have to have it working otherwise there is no use of it.
I tried building and installing the latest modules from linuxtv and seemed to have worked fine... but same results. I don't know though if I have the correct firmware for the card... though in dmesg seems to be loading fine... I tried searching on the internet for them and downloaded the latest from ivtv that I read are the correct (are they??) but still the same. I copied them in /lib/firmware/2.6... is it the correct place??? Still I say again that dmesg don't complain about the firmware....
I read here:
[www.ganymede.ch/2007/09/05/mythtv-with-wintv-hvr-1300](www.ganymede.ch/2007/09/05/mythtv-with-wintv-hvr-1300)
that for a person the same card was working out of the box in arch linux... Is it a bug in Ubuntu??
I 'm using a fresh install of Gutsy...
Please any suggestion would be much helpfull and appreciated. I 'm newbie.. but I 'm trying to learn and understand... and really want this to work and go to Ubuntu completely.
Thanks in advance

---

