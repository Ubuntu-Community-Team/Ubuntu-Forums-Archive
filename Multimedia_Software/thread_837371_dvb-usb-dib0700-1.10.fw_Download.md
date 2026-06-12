---
title: "dvb-usb-dib0700-1.10.fw Download"
date: 2008-06-22
forum: Multimedia Software
---

### Post by jeffhills on 2008-06-22
Following a rebuild of my Mythbox (following a RAM failure) neither of my Hauppauge Nova T500's will work (A Leadtech card is still fine). I seem to have lost the Firmware. The problem now is the site [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw)
has been unavailable for 2 days. Does anybody else have the same problem, or is there another way of getting the firmware? 
Jeff

---

### Post by Riverside on 2008-06-22
Same issue for me.  I am trying to obtain the firmware to get a Hauppauge Nova-T Stick working using the instructions at:

[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

However:

```
anthony@gutsy:~$ dmesg | grep dvb
[   24.829178] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   24.863199] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-1.10.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   24.863236] usbcore: registered new interface driver dvb_usb_dib0700
[  722.094513] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[  722.104578] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-1.10.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
```

So, I am also following the instructions at:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

And am trying to obtain the dvb-usb-dib0700-1.10.fw firmware.

As you mention though, the only download link I have been able to find (the one at the above URL) is unavailable (actually unreachable, having checked) at present.

This appears to be a regularly recurring issue:

[http://ubuntuforums.org/archive/index.php/t-586826.html](http://ubuntuforums.org/archive/index.php/t-586826.html)

Ideally, given the popularity of the Hauppauge Nova-T Stick, it would be beneficial if the community could arrange to also host the firmware file for download on a server with better and more consistent availability.

---

### Post by Riverside on 2008-06-22
Now resolved:

[http://ubuntuforums.org/showpost.php?p=5241978&postcount=8](http://ubuntuforums.org/showpost.php?p=5241978&postcount=8)

---

