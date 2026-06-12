---
title: "Hauppauge WinTV Nova-T (USB)"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Tk0680 on 2007-04-05
Edit: It seems that there are two Hauppauge products that go by the above name - one is a USB stick, the other is more of a box that sits on your desk. While they have the same name, it appears that they are set up differently as far as software goes. I'm using the stick.

I'm tearing my hair out on this one.

I have the above bit of kit, but cannot get Ubuntu (Edgy: 2.6.17-11-generic) to recognise it. I'll try to pre-empt all of the questions people might ask below ...

Log (immediately after the stick is plugged in):
```
rich@humphrey-l:~$ tail /var/log/messages | grep usb
Apr  5 18:09:20 humphrey-l kernel: [17179644.208000] usb 1-5: new high speed USB device using ehci_hcd and address 5
Apr  5 18:09:20 humphrey-l kernel: [17179644.344000] usb 1-5: configuration #1 chosen from 1 choice
```

lsusb:
```
rich@humphrey-l:~$ lsusb
Bus 003 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 005: ID 2040:7060 Hauppauge** 
Bus 001 Device 001: ID 0000:0000
```

Firmware:
```
rich@humphrey-l:~$ ls /lib/firmware | grep dvb
dvb-fe-tda10046.fw
dvb-usb-nova-t-usb2-02.fw
```

The firmware is also in the kernel's own firmware directory.

I can't find a guide anywhere that tells me to do anything more than I've already done, but I really want this working. Everything is up to date, everything's been restarted, still no luck.

Any help whatsoever would be oh so appreciated.

---

### Post by Toertel on 2007-04-27
The required driver modules (*dib0700* and *dvb-usb*) are already part of the kernel. What is left is the firmware. Download [**linuxtv-firmwaretar.bz2**]("http://www.omskakas.se/wp-content/uploads/2007/01/linuxtv-firmwaretar.bz2") ([**article**]("http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html/firmware-files-for-various-tv-tuners-under-linux/")), unpack it and copy dvb-usb-dib0700-01.fw to /lib/firmware. Now plug in the DVB-T stick and *dmesg* should show the following:

```
[ 6157.876000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 6158.008000] usb 5-2: configuration #1 chosen from 1 choice
[ 6158.008000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 6158.016000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[ 6158.192000] dib0700: firmware started successfully.
[ 6158.696000] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[ 6158.696000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 6158.696000] DVB: registering new adapter (Hauppauge Nova-T Stick).
[ 6158.888000] **WARNING** I2C adapter driver [DiBX000 tuner I2C bus] forgot to specify physical device; fix it!
[ 6158.912000] DVB: registering frontend 0 (DiBcom 7000PC)...
[ 6159.180000] MT2060: successfully identified (IF1 = 1220)
[ 6159.644000] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
```

Now you can watch DVB-T TV using e.g. Kaffeine (install kaffeine and libxine1-ffmpeg).

Alternative way to firmware through script in Linux kernel sources I haven't tried yet: [http://ubuntuforums.org/showthread.php?t=421110](http://ubuntuforums.org/showthread.php?t=421110)

---

### Post by tombott on 2007-12-13
Cheers for this worked a treat for my USB WinTV card under Gutsy.

---

