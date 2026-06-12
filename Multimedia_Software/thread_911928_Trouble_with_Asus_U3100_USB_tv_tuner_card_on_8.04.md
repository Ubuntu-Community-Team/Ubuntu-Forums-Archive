---
title: "Trouble with Asus U3100 USB tv tuner card on 8.04"
date: 2008-09-06
forum: Multimedia Software
---

### Post by didu on 2008-09-06
Hi guys,

I'm having a lot of trouble getting my new Asus U3100 USB tv tuner card to work on my laptop.

I'm running the AMD64 version of Ubuntu 8.04 with kernel 2.6.24-19-generic.

When I plug the USB tv tuner into my laptop, everything seems normal, and dmesg gives out the following message:

```

[  155.161261] usb 7-3: new high speed USB device using ehci_hcd and address 4
[  155.231102] usb 7-3: configuration #1 chosen from 1 choice
[  155.747500] dib0700: loaded with support for 7 different device-types
[  155.747762] dvb-usb: found a 'ASUS My Cinema U3100 Mini DVBT Tuner' in cold state, will try to load a firmware
[  155.766389] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[  155.976298] dib0700: firmware started successfully.
[  156.097030] dvb-usb: found a 'ASUS My Cinema U3100 Mini DVBT Tuner' in warm state.
[  156.097132] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  156.097310] DVB: registering new adapter (ASUS My Cinema U3100 Mini DVBT Tuner)
[  156.256320] DVB: registering frontend 0 (DiBcom 7000PC)...
[  156.356321] DiB0070: successfully identified
[  156.356504] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-3/input/input14
[  156.382523] dvb-usb: schedule remote query interval to 150 msecs.
[  156.382536] dvb-usb: ASUS My Cinema U3100 Mini DVBT Tuner successfully initialized and connected.
[  156.382824] usbcore: registered new interface driver dvb_usb_dib0700

```

I checked that against the howto on this webpage: [http://www.linuxtv.org/wiki/index.php/Asus_My_Cinema-U3000_Mini](http://www.linuxtv.org/wiki/index.php/Asus_My_Cinema-U3000_Mini) , and it seemed normal.

However, when I run tvtime, it cannot find the tv tuner device.

To further complicate things, I have a builtin camera which is normally at /dev/video0 , so when I run tvtime, it just looks at /dev/video0 and complain that it's not a tv tuner card -- that's fair enough. But where is the device for the tv tuner card?

Furthermore, I followed the instruction on [http://www.linuxtv.org/wiki/index.php/Asus_My_Cinema-U3000_Mini](http://www.linuxtv.org/wiki/index.php/Asus_My_Cinema-U3000_Mini) to v4l-dvb driver. Now, when I reboot the laptop, the /dev/video0 is gone, and I cannot even use my webcam. I used synaptic to reinstall the kernel modules and image, but the /dev/video0 is still missing.

When I plugin the tv tuner, I can see that it creates a directory called /dev/dvb, and a whole bunch of usbdev?.?_ep?? files. But according to tvtime, none of them are a video4linux device.

So, what am I doing wrong? Any help is appreciated!

Thanks a lot in advance. 

-D

---

### Post by didu on 2008-09-06
any ideas? :confused:

---

### Post by mad_gcc on 2008-09-22
> **didu said:**
> any ideas? :confused:

Use Kaffeine instead of Tvtime. Both are very good apps, but Kaffeine does work with usb DVB devices and tvtime don't.

Launch kaffeine and you will see a new icon (digital TV), click on it and try to tune some stations.

It should work.

---

