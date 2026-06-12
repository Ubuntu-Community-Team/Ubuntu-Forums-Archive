---
title: "Kworld DVB-T USB tuner is working"
date: 2008-05-31
forum: Mythbuntu
---

### Post by JanCeuleers on 2008-05-31
This is an attempt to get the Kworld/ADStech USB DVB-T tuner to be added to the list of known working tuners on help.ubuntu.com

I have this SD tuner working with Mythtv 0.21 / Ubuntu 7.10:

root@fe2:/proc# dmesg | grep DVB
[   51.688141] dvb-usb: found a 'KWorld/ADSTech Instant DVB-T USB2.0' in warm state.
[   51.688461] DVB: registering new adapter (KWorld/ADSTech Instant DVB-T USB2.0).
[   51.689734] DVB: registering frontend 0 (DiBcom 3000M-B DVB-T)...
[   51.690223] input: IR-receiver inside an USB DVB receiver as /class/input/input1
[   51.690278] dvb-usb: KWorld/ADSTech Instant DVB-T USB2.0 successfully initialized and connected.

root@fe2:/proc# lsusb
Bus 004 Device 003: ID 06e1:a334 ADS Technologies, Inc.
[...]

The firmware for this tuner does not come with Ubuntu. It's hard to find on the net but I did manage it. Sorry, but I don't remember where I got it.

root@fe2:/proc# ls -l /lib/firmware/2.6.22-14-generic/dvb-usb-adstech-usb2-02.fw
-rw------- 1 root root 6649 2008-04-28 14:44 /lib/firmware/2.6.22-14-generic/dvb-usb-adstech-usb2-02.fw

---

