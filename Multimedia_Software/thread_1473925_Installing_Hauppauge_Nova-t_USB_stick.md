---
title: "Installing Hauppauge Nova-t USB stick"
date: 2010-05-05
forum: Multimedia Software
---

### Post by ice cold on 2010-05-05
I need some very hand holding help in getting my WinTV Nova-t stick working with TVTime on Lucid Lynx.

I've copied the firmware file dvb-usb0700-1.20.fw to /lib/firmware

lsusb shows:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 003: ID 2040:7070 Hauppauge Nova-T Stick 3
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and dmesg | grep dvb shows:
[   17.417534] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   17.417540] usb 1-4: firmware: requesting dvb-usb-dib0700-1.20.fw
[   17.444496] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   18.164061] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   18.164134] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.643771] dvb-usb: schedule remote query interval to 50 msecs.
[   18.643776] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   18.644159] usbcore: registered new interface driver dvb_usb_dib0700

which all looks good.  

Running TV Time from the command line gives:

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/mark/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Segmentation fault

This message previously said 'Cannot open capture device /dev/video0: Permission denied', or something to that effect, but /dev/video0 at least existed.  I tried adding my username to the video group but now /dev/video0 doesn't even exist

Can someone help me please!

---

### Post by xc3RnbFO8P on 2010-05-06
Try **Kaffeine** or **ME-Tv**.

---

### Post by ice cold on 2010-05-15
Cool, thanks, they both worked.  Handling as /dev/dvb/adaptor0 seems the better way to go :-)

---

