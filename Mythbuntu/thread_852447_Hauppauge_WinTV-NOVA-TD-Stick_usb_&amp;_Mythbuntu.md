---
title: "Hauppauge WinTV-NOVA-TD-Stick usb &amp; Mythbuntu"
date: 2008-07-07
forum: Mythbuntu
---

### Post by gianpiero on 2008-07-07
Hello!
I bought this dvb usb because I want to use it under Mythbuntu, I known it work under linux:[http://http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick#Drivers]("http://http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick#Drivers").
The dmesg | grep dvb is:
```
 dmesg | grep dvb
[  179.269512] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in cold state, will try to load a firmware
[  179.353782] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[  180.064391] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in warm state.
[  180.064504] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  180.554848] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  180.943913] dvb-usb: schedule remote query interval to 150 msecs.
[  180.943926] dvb-usb: Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity successfully initialized and connected.
[  180.944492] usbcore: registered new interface driver dvb_usb_dib0700

```

But I receive: "Error was encountered while displaying video".

Someone  knows some specific wiki for my dvb??:confused:

Another question:
I can't use some keys of my remote control (model: hauppauge A415 OH/s 1-1), I can use the directions keys, the volume keys, but I can't use "ok" key, "play" key,..
WHY?:confused:
Someone knows some specific /etc/lirc/lircd.conf and /etc/lirc/hardware.conf for my remote control. I think it would be work as a usb keyboard. (Why these keys aren't work?)

Thank you very much, I'm sorry for my bad English.

---

