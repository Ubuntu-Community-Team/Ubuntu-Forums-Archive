---
title: "USB DVB-T cant find any channels"
date: 2013-02-21
forum: Multimedia Software
---

### Post by Thee on 2013-02-21
Hey

Got a USB DVB-T tuner, which is supported by the Kernel, installed the firmware from a guide I found here on the forums, all good, as you can see:

```

dmesg |grep it913x
[   26.187128] it913x: Chip Version=02 Chip Type=9135
[   26.187498] it913x: Firmware Version 52953344
[   26.187873] it913x: Dual mode=0 Tuner Type=38
[   26.187874] it913x: Unknown tuner ID applying default 0x60
[   26.355615] it913x-fe: ADF table value	:00
[   26.359435] it913x-fe: Crystal Frequency :12000000 Adc Frequency :20250000 ADC X2: 01
[   26.394994] it913x-fe: Tuner LNA type :60
[   26.879510] Registered IR keymap rc-it913x-v1
[   26.879641] it913x: DEV registering device driver
[   26.879661] usbcore: registered new interface driver it913x
[ 4942.583145] it913x: Chip Version=02 Chip Type=9135
[ 4942.583518] it913x: Firmware Version 52953344
[ 4942.583892] it913x: Dual mode=0 Tuner Type=38
[ 4942.583893] it913x: Unknown tuner ID applying default 0x60
[ 4942.584776] it913x-fe: ADF table value	:00
[ 4942.588509] it913x-fe: Crystal Frequency :12000000 Adc Frequency :20250000 ADC X2: 01
[ 4942.624069] it913x-fe: Tuner LNA type :60
[ 4942.757262] Registered IR keymap rc-it913x-v1
[ 4942.757336] it913x: DEV registering device driver

```

My problem is that I cant find any channels, with any app, tried MeTV, w_scan and Kaffeine. None can get any channels. Actually, w_scan stops at some point with an error. I even installed official drivers and software in Windows and there it couldn't find anything either.

Now, I'm not using an antenna, I have Cable (DVB-C) hooked to a receiver, which has a RF out, from which you can get about 30+ analog channels with DVB-T settings.

I know this because I tried to scan using my TV, with the following settings, country=Germany, source=DVB-T, Scan for analog channels=Yes. And it finds 30+ analog channels, also, an old CRT TV finds the same channels.

This should work, so why can't this tuner find any channels?

---

### Post by howefield on 2013-02-21
It is probably something completely different, but I have to change the transmitter data contained within the default scan files, eg for kaffeine the file is ~/.kde/share/apps/kaffeine/scanfile.dvb

Might be worth checking it is scanning with robust data.

---

### Post by Thee on 2013-02-21
Well I don't really know what I should change there...

---

### Post by howefield on 2013-02-21
Which transmitter are you served by ?

---

### Post by Thee on 2013-02-21
If you mean the receiver, it's this one:
[http://www.amazon.de/TechnoTrend-TT-micro-C274-Kabelreceiver-UnityMedia/dp/B001QF3IFC](http://www.amazon.de/TechnoTrend-TT-micro-C274-Kabelreceiver-UnityMedia/dp/B001QF3IFC)

---

### Post by Thee on 2013-02-21
Ok, I figured it out. I cant use a DVB-T card to get analog TV channels. These zillion standards are gonna ruin us someday :)

So, I think I should get a DVB-C card to be able to receive digital channels, or a analog TV card to be able to receive analog TV channels. Or something that has both...

In any case, someone knows something like that thats not very expansive and works on Linux?

---

### Post by mazinoz on 2013-06-08
Have you checked you have installed v4l programs as well as enabled v4l  in the kernel?

---

