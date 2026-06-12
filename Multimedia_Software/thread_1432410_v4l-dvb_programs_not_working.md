---
title: "v4l-dvb programs not working"
date: 2010-03-17
forum: Multimedia Software
---

### Post by as009988 on 2010-03-17
None of the tv viewing programs work, ether they crash or don't produce a stream. 

I am sure the drivers are installed. The card is autodetected as a  WinTV-HVR-1270. From what I have read on other post the 1250 r4 detects as a 1270

My system;
asus m2n-sli
GeForce 7600 GS
Hauppauge WinTV-HVR-1250 r4
Hauppauge WinTV-PVR-500 (working)
Hauppauge Impact VCB (working)

Ubuntu 9.10 amd64
v4l-dvb mercurial installed Mar 11 2010
me-tv-1.1.2
Kaffeine 1.0-pre2
linuxtv-dvb-apps-1.?

Kaffeine see's a device LGDT3305, will not scan

me-tv produces glibmm-ERROR **:
    unhandled exception (type unknown) in signal handler
 X Error of failed request:  BadDrawable (invalid Pixmap or Window     parameter)
  Major opcode of failed request:  143 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Resource id in failed request:  0x320007e
  Serial number of failed request:  404
  Current serial number in output stream:  405
 Aborted

Installed WindowsXP media center dual boot
  WinTV-HVR-1250 digital cable working
  WinTV-HVR-1250 analog cable working
  everthing else working


back to basics, czap
 $ czap -r -H -n 3 
 using...adapter0...demux0
reading channels from file....
 3 103.4 4:669000000:QAM_256:69:72:4
ERROR: cannot parse service data

I'm at a loss???????

---

### Post by wkulecz on 2010-03-18
Can your TV viewer apps get a image through composite or S-video inputs? say from a VCR or DVD player.

I've been unsuccessful with the Hauppauge 950Q and HVR-1950 DTV devices, although both work great in Windows 7 and I can use the S-Video or Composite inputs in Ubuntu 9.10.

Try installing the linux-firmware-nonfree package, it fixed an issue with the default driver in 9.10 for the 950Q but still can't get the ATSC tuner to work for either device.  Not a major issue for me as I got the thing to capture NTSC tapes and live video over composite input.

---

### Post by as009988 on 2010-03-19
I have the fimware.
v4l-cx23885-avcore-01.fw, v4l-cx23885-enc.fw and are in /lib/firmware

As for for s-video,  I need a /dev/videox device for that, I don't have this. My card only has /dev/dvb/adapter0 frontend0, demux0,,,  devices

Yes this card has a analog tuner, Support for (Tuner Model: NXP 18271C2)  is not in the drivers yet.

---

### Post by as009988 on 2010-03-23
OK I have done some looking around/re installing/ retesting
 same results.
czap produces "ERROR: cannot parse service data"
 
I found a channels-conf in the, dvb-apps/util/szap/channels-conf/dvb-c build folder.
The lines are formated like this;

CNBC:394000000:INVERSION_OFF:6900000:FEC_NONE:QAM_64:510:520
DLF-Köln:394000000:INVERSION_OFF:6900000:FEC_NONE:QAM_64:0:810

My channels.conf is formated like this ;

4e_id 7:369000000:QAM_256:0:74:7
5e_id 11:483000000:QAM_256:64:65:11

both of these are for cable tv.

Is mine formated wrong?

---

