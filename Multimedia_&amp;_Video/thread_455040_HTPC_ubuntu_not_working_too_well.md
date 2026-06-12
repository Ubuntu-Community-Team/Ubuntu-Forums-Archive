---
title: "HTPC ubuntu not working too well"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Dark Damo on 2007-05-26
I seem to have hit a snag following the wiki [here](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend).

I am up to backend configuration capture card. 

I set it to pcHDTV DTV capture card (w/v4l drivers)

video devices: /dev/video0
DVICO FusionHDTV DVB-T Plus [cx8800]
Signal timeout: 500
tuning timeout: 2000
Default input S-video (Only other is composite)

Now video sources:

name: lol
XMLTV: Tramsmitted guide only
channel frequency table: Australia


Now when i go to scan for channels it keeps scanning ASTC or something and keeps timing out picking up 0 channels. I want it to scan DVB-T not ASTC. How can i change it to DVB?

Also, i shut it down but how do i get back into myth tv config?

Thanks in advance.

---

### Post by Dark Damo on 2007-05-26
bump, please help me.

---

### Post by h6w on 2007-06-26
I have a similar problem.   If you disable mythtv with 
```
sudo /etc/init.d/mythtv stop
```
and then do a
```
scan /usr/share/doc//dvb-utils/examples/scan/dvb-t/au-Melbourne
```
(replacing au-Melbourne with your location.

Do you get a 'tuning failed' message?

---

