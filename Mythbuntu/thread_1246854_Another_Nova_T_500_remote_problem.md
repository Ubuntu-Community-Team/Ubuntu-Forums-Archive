---
title: "Another Nova T 500 remote problem"
date: 2009-08-22
forum: Mythbuntu
---

### Post by tonycollinet on 2009-08-22
SOLVED - See [http://ubuntuforums.org/showpost.php?p=8081685&postcount=6](http://ubuntuforums.org/showpost.php?p=8081685&postcount=6)


****************************************
Now tearing my hair out. 
1 - it was not working.
2 - I went through a fix process, going to 1.1 firmware, and compiling/installing the v4l latest drivers. After this it worked, showing up both in the device list, and in dmesg.

Since then it has stopped working (I suspect an update has broken it). It was not appearing in the devices ( cat /proc/bus/input/devices ) nor was there any reference in dmesg.

What have I done so far:
double checked fw version is 1.10
recompiled/installed the latest V4l drivers.
Gone through all the config files as described in:
[http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote](http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote)
(all these are the steps I went through to get it to work last time)

Now I have an entry in devices - but there is still nothing in dmesg, and the remote doesn't work.

Thanks for any help

***********cat /proc/bus/input/devices************

I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:05:09.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:05:09.2/usb2/2-1/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=3
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffd
******************************

*******dmesg | grep dvb*******
[    9.807003] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    9.807010] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    9.943872] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   10.664031] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   10.664214] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.085776] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.425404] dvb-usb: schedule remote query interval to 50 msecs.
[   11.425412] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   11.425627] usbcore: registered new interface driver dvb_usb_dib0700
**************************************

---

