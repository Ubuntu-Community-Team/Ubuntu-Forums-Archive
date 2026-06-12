---
title: "Mythtv and pcHD5500"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by stinkypudding on 2007-06-27
I have an HD5500 that was working great up until about a week, which I believe coincided with a kernal update to 2.6.20-16. Now my capture card isn't working.

When I do a dmesg |grep dvb, here is the output:

ryanr@ubuntu:~$ dmesg |grep dvb
[ 17.040000] cx2388x dvb driver version 0.0.6 loaded
[ 17.040000] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 17.040000] cx88[0]/2: cx2388x based dvb card
ryanr@ubuntu:~$ dmesg |grep cx88
[ 15.576000] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected]
[ 15.668000] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[ 15.724000] cx88[0]/0: found at 0000:00:0f.0, rev: 5, irq: 21, latency: 20, mmio: 0xfa000000
[ 16.008000] tuner 0-0043: chip found @ 0x86 (cx88[0])
[ 16.012000] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[ 16.020000] cx88[0]/0: registered device video0 [v4l2]
[ 16.020000] cx88[0]/0: registered device vbi0
[ 16.684000] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[ 17.000000] cx88[0]/2: cx2388x 8802 Driver Manager
[ 17.000000] cx88[0]/2: found at 0000:00:0f.2, rev: 5, irq: 21, latency: 64, mmio: 0xf8000000
[ 17.040000] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 17.040000] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[ 17.040000] cx88[0]/2: cx2388x based dvb card
[ 17.416000] DVB: registering new adapter (cx88[0])

And when I grep cx88, here is the output:

ryanr@ubuntu:~$ dmesg |grep cx88
[ 15.576000] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected]
[ 15.668000] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[ 15.724000] cx88[0]/0: found at 0000:00:0f.0, rev: 5, irq: 21, latency: 20, mmio: 0xfa000000
[ 16.008000] tuner 0-0043: chip found @ 0x86 (cx88[0])
[ 16.012000] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[ 16.020000] cx88[0]/0: registered device video0 [v4l2]
[ 16.020000] cx88[0]/0: registered device vbi0
[ 16.684000] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[ 17.000000] cx88[0]/2: cx2388x 8802 Driver Manager
[ 17.000000] cx88[0]/2: found at 0000:00:0f.2, rev: 5, irq: 21, latency: 64, mmio: 0xf8000000
[ 17.040000] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 17.040000] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[ 17.040000] cx88[0]/2: cx2388x based dvb card
[ 17.416000] DVB: registering new adapter (cx88[0])

When I enter mythtv-setup, my card fails to open, when I select DVB v3(which I believe is correct) or pcHDTV.

Can someone help?

---

### Post by Afkpuz on 2008-02-08
```
sudo gedit /etc/modules

```

Add this to the bottom of the file on its own line

```
cx88-dvb
```


Reboot and select "DVB DTV capture card(v3.x)" in mythtv setup.  Should work.  More details here

[http://wiki.linuxmce.org/index.php/PcHDTV_HD5500](http://wiki.linuxmce.org/index.php/PcHDTV_HD5500)

It's written for linuxmce which is based on kde, so change don't use kate.  Use gedit.

---

