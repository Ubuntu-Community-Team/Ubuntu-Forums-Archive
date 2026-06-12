---
title: "skystar 2 is not working after update to kramic"
date: 2009-11-02
forum: Multimedia Software
---

### Post by netlord on 2009-11-02
hi there

can anyone help me? i´min trouble with an skystar 2-card which is not longer working after updating to karmic.

ubuntu seems to recognise the card itself
> chriss@solaris:~/script$ dmesg | grep SkyStar
[   21.770227] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
chriss@solaris:~/script$ dmesg | grep b2c2
[   20.882639] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   20.889415] b2c2_flexcop_pci 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[   20.931820] b2c2-flexcop: MAC address = 00:d0:d7:13:19:68
[   21.770155] b2c2-flexcop: found 'ST STV0299 DVB-S' .
[   21.770227] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

> chriss@solaris:~/script$ ls /dev/dvb/adapter0 -ali
insgesamt 0
6617 drwxr-xr-x  2 root root     120 2009-11-02 15:40 .
6616 drwxr-xr-x  3 root root      60 2009-11-02 15:40 ..
6621 crw-rw----  1 root video 212, 6 2009-11-02 15:40 ca0
6619 crw-rw----+ 1 root video 212, 4 2009-11-02 15:40 demux0
6620 crw-rw----+ 1 root video 212, 5 2009-11-02 15:40 dvr0
6618 crw-rw----+ 1 root video 212, 3 2009-11-02 15:40 frontend0


but neither kaffeine or me-tv seems to recognise the device, so its isn´t working.

i already set up the card using this this wiki: [http://wiki.ubuntuusers.de/B2C2](http://wiki.ubuntuusers.de/B2C2), but....

anyone an idea?

thx

---

### Post by netlord on 2009-11-04
hi

is there no help with this problem?
really?

*edit*

there seems to be a problem with the demux-device.
when i´m trying to use me-tv there is an error:

04.11.2009 18:23:06: Frequency 12551500, Symbol rate 22000000, FEC 5, polarisation 1
04.11.2009 18:23:06: Tuning to transponder at 12551500 Hz
04.11.2009 18:23:06: Exception: Öffnen des Demux-Geräts fehlgeschlagen: No such device
04.11.2009 18:23:06: Failed to tune to transponder at 12551500 Hz


the demux-device is created, according to the wiki, like this: 

mknod -m 0660 demux0 c 212 4

is this wrong?
how can i find out if its wrong or right?

---

