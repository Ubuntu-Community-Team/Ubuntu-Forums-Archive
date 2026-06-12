---
title: "Videomate U100 USB DVB - driver?"
date: 2008-07-19
forum: Multimedia Software
---

### Post by jwatsonoz on 2008-07-19
Hi,

Attempting to get a Videomate U100 DVB USB stick to work. I have managed to get Hardy to recognize it by compiling and installing the following linuxtv project:

[http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2)

However, it does not communicate with the tuner properly i.e. no channels are found. Stick works with windows - so I'm having to dance with the devil until I get this fixed.

Can anybody help?

thanks,
Jason

---

### Post by xc3RnbFO8P on 2008-07-19
In terminal:
> lsusb
show the output.

---

### Post by jwatsonoz on 2008-07-24
Hi, thanks for your message. The stick is registered just fine its the driver isn't working i.e. allowing communication with the tuner chip. (see output from dmesg and kaffeine below)

lsusb
-----
Bus 003 Device 004: ID 185b:0100 Compro 

dmesg | grep dvb
----------------
[   47.022999] dvb-usb: found a 'VideoMate TV U100' in warm state.
[   47.023009] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   47.053546] dvb-usb: schedule remote query interval to 300 msecs.
[   47.053555] dvb-usb: VideoMate TV U100 successfully initialized and connected.
[   47.053580] usbcore: registered new interface driver dvb_usb_rtd2831u


The stick is recognised when I start Kaffeine, but does not tune in. Sample from terminal whilst attempting to tune (it does the same for all frequencies):
...............

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Using DVB device 0:0 "Realtek RTL2831 DVB-T"
tuning DVB-T to 585625000 Hz
inv:2 bw:1 fecH:2 fecL:9 mod:3 tm:1 gi:2 hier:0
...............

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Transponders: 5
dvbsi: The end :)
Channels found: 0

Has anybody got a working driver for the videomate u100? Are there plans to create one? thanks :)

---

### Post by jwatsonoz on 2008-07-31
Hi again

Where do I repost this to get help?

thanks,
Jason

---

### Post by Tristan85 on 2010-07-16
i have the same tuner card.... you have any luck with it.. cause i havent.

---

