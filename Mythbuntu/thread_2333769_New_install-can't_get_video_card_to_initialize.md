---
title: "New install-can't get video card to initialize"
date: 2016-08-12
forum: Mythbuntu
---

### Post by pottzie on 2016-08-12
This is a fresh install of Mythbuntu 14, with a Hauppauge 950q that has worked on Mythbuntu 12 for a couple of years. I've set the backend as well as I can figure, and haven't made the card connect to the operating system. The card shows as [DVB:/dev/dvb/adapter0/frontend0]

Video sources is blank, just shows (New Video Source), and I only use Myth to watch broadcast TV.  Input connections shows [DVB:/dev/dvb/adapter0/frontend0] (DVBInput > (None)    Storage directories shows 'Default,' with a header of /var/lib/mythtv/recordings/

when I exit, it wants to fill mythdatabase, and I've answered yes and no, with no difference.  I can't make the Hauppauge "light up," there's a yellow light that turns on and indicates it's been turned on by the software and functioning, and I haven't found a way to do that

---

### Post by pottzie on 2016-08-14
Made a bit of progress, although I still can't wake the card in Myth. This helped;    [https://ubuntuforums.org/showthread.php?t=2225748](https://ubuntuforums.org/showthread.php?t=2225748)

 [COLOR=#000000]Download the extra firmware file from: [/COLOR][http://kernellabs.com/firmware/xc5000/](http://kernellabs.com/firmware/xc5000/)

[COLOR=#000000]cp dvb-fe-xc5000c-4.1.30.7.fw /lib/firmware[/COLOR]

[COLOR=#000000]/lib/firmware/dvb-fe-xc5000-1.6.114.fw[/COLOR]
[COLOR=#000000]/lib/firmware/dvb-fe-xc5000c-4.1.30.7.fw[/COLOR]

[COLOR=#000000]w_scan -ft -c US -X > ~/channels.conf

I got to see it scan channels, and then list them. Still can't make it work in Myth 

[/COLOR]https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q

---

### Post by uteck on 2016-08-17
Looking at this page:
[https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

It seems that the only the file you downloaded is needed:
> 
After an application open the device the first time, the module will load the firmware. You will see:
xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
i2c-adapter i2c-2: firmware: requesting dvb-fe-xc5000-1.1.fw
xc5000: firmware read 12332 bytes.
xc5000: firmware upload

Try removing dvb-fe-xc5000c-4.1.30.7.fw and rebooting to see if was loading the wrong firmware.

---

