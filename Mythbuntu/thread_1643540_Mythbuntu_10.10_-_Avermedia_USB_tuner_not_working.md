---
title: "Mythbuntu 10.10 - Avermedia USB tuner not working"
date: 2010-12-12
forum: Mythbuntu
---

### Post by map7 on 2010-12-12
I've just upgraded my system from Mythbuntu 9.04 to 10.10 with a fresh install, but now my Avermedia USB tuner doesn't seem to work.

Here are the details of the tuner:
AverMedia Volar USB	  
Device from lsusb:      07ca:b808
Device in Mythtv setup:	DiBcom 7000MA/MB/PA/PB MCSubtype

I can still boot into my old system on a separate partition (same disk) and it works, then without changing any cables or location of the USB tuner I reboot to Mythbuntu 10.10 and it doesn't work.

Mythbuntu 10.10 is able to detect the device but when I go to 'Watch TV' it will not lock onto a station even though it reports to have over 70% signal strength and is using a proven antenna setup (cable, booster, etc).

I do have another card in my Mythtv setup and have done the station scan with that card. If I try and scan with the Avermedia tuner it doesn't find any stations.

On this website it says that it should have support since 2.6.20
[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB3000M-B_USB1.1_DVB-T_devices](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB3000M-B_USB1.1_DVB-T_devices)

Do I have to compile some new drivers or something?

---

### Post by thatguruguy on 2010-12-12
You can try the following:

[http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto]("http://www.wi-bw.tfh-wildau.de/%7Epboettch/home/index.php?site=dvb-usb-howto")

---

### Post by map7 on 2010-12-13
Just tried that with the following commands:
```
$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ make CONFIG_DVB_FIREDTV:=n
$ sudo make install
$ sudo reboot

```
and still have the same problem. Here is what I get in my messages when booting:

```
Dec 13 23:29:05 marvin kernel: [   13.479311] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in cold state, will try to load a firmware
Dec 13 23:29:05 marvin kernel: [   13.482724] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
Dec 13 23:29:05 marvin kernel: [   13.557397] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
Dec 13 23:29:05 marvin kernel: [   13.693148] dib0700: firmware started successfully.
Dec 13 23:29:05 marvin kernel: [   14.200379] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in warm state.
Dec 13 23:29:05 marvin kernel: [   14.200503] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Dec 13 23:29:05 marvin kernel: [   14.200875] DVB: registering new adapter (AVerMedia AVerTV DVB-T Volar)
Dec 13 23:29:06 marvin kernel: [   14.553652] DVB: registering adapter 2 frontend 0 (DiBcom 7000MA/MB/PA/PB/MC)...
Dec 13 23:29:06 marvin kernel: [   14.562268] MT2060: successfully identified (IF1 = 1220)
Dec 13 23:29:06 marvin kernel: [   15.091252] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/input/input9
Dec 13 23:29:06 marvin kernel: [   15.091394] dvb-usb: schedule remote query interval to 50 msecs.
Dec 13 23:29:06 marvin kernel: [   15.091403] dvb-usb: AVerMedia AVerTV DVB-T Volar successfully initialized and connected.
Dec 13 23:29:06 marvin kernel: [   15.092663] usbcore: registered new interface driver dvb_usb_dib0700
```


I'm getting this error in my mythbackend.log where adapter2/frontend0 is my AverMedia Volar USB stick.
```

                        eno: Device or resource busy (16)
2010-12-13 23:30:36.784 DVBChan(15:/dev/dvb/adapter2/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2010-12-13 23:30:36.867 DVBChan(15:/dev/dvb/adapter2/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2010-12-13 23:30:36.942 DVBChan(15:/dev/dvb/adapter2/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2010-12-13 23:30:37.025 DVBChan(15:/dev/dvb/adapter2/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2010-12-13 23:30:37.125 DVBChan(15:/dev/dvb/adapter2/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2010-12-13 23:30:37.250 DVBChan(15:/dev/dvb/adapter2/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2010-12-13 23:30:37.283 DVBChan(15:/dev/dvb/adapter2/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
```

---

### Post by thatguruguy on 2010-12-13
It sounds like something else is grabbing your tuner.

You may want to open backend setup and make sure that  "Use DVB card for active EIT scan" is not checked for that tuner.  For me, at least, having that option checked caused problems.

I don't know much about the tuner you're using, frankly.  Are you using it as a digital tuner, analog tuner, or both?  Have you checked it under other programs?  For instance, MeTV works with digital tuners, and tvtime works with analog tuners.  You may want to see if it works with those programs, so we can get an idea of the extent to which this is a mythtv problem.

---

### Post by Vojta01 on 2011-01-16
Hi, were you able to solve this issue? It seems that it is already reported as bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/654791](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/654791)
I am having the same issue, but with Winfast leadtek DTV dongle, which seems to be using the same firmware.

---

### Post by map7 on 2011-01-16
No I still don't have my tuner working. I haven't had time to spend on this issue at the moment.

---

