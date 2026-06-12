---
title: "Can't get the tuner working"
date: 2009-01-16
forum: Mythbuntu
---

### Post by cartisdm on 2009-01-16
I can't seem to get my mythbuntu installation configured.  I have the hauppauge WinTV HRV 1600 tuner.  I have followed the 8.10 installation guide to the letter but when I try to watch TV nothing happens.

I'm only running Mythbuntu on this single desktop so it's got the backend and frontend installation and no unusual configuration.  Can someone please help me out

---

### Post by bwang on 2009-01-16
Try this page: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

---

### Post by cartisdm on 2009-01-16
I tried doing the compile but after the "make" command it ran for about 15 minutes, I don't know if that's normal or not.  I think I got some errors too.  Then doing the last step where I was supposed to get a certain output I got this output:

```
$ dmesg | grep cx18
[   13.543956] cx18:  Start initialization, version 1.0.0
[   15.947970] cx18-0: Initializing card #0
[   15.947976] cx18-0: Autodetected Hauppauge card
[   15.948350] cx18 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[   15.948366] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   15.951518] cx18-0: cx23418 revision 01010000 (B)
[   16.240774] cx18-0: Autodetected Hauppauge HVR-1600
[   16.240778] cx18-0: VBI is not yet supported
[   16.507869] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   16.507904] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   16.598266] cx18-0: Disabled encoder IDX device
[   16.598465] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   16.598471] DVB: registering new adapter (cx18)
[   16.726894] cx18-0: DVB Frontend registered
[   16.726954] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   16.727008] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   16.727014] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   16.753340] cx18:  End initialization
[   38.696284] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   39.419921] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   39.426254] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   40.664943] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
```

---

### Post by Sef on 2009-01-16
Moved to mythbuntu forum.

---

### Post by fenian on 2009-01-16
Before installing the drivers did you stop MythTV Backend?If not you need to do that or you will have errors.
First you need to uninstall the drivers you installed,in a terminal enter...

> cd v4l-dvb
sudo make uninstall

Next shutdown the Mythtv-Backend,in a terminal enter...
> 
sudo /etc/init.d/mythtv-backend stop

Reinstall the drivers following the instructions.

---

### Post by cartisdm on 2009-01-17
Got this:

```
sudo make uninstall
[sudo] password for desktop: 
make -C /home/desktop/v4l-dvb/v4l uninstall
make[1]: Entering directory `/home/desktop/v4l-dvb/v4l'
make[1]: *** No rule to make target `uninstall'.  Stop.
make[1]: Leaving directory `/home/desktop/v4l-dvb/v4l'
make: *** [uninstall] Error 2
desktop@desktop-tv:~/v4l-dvb$ 
```

---

### Post by cartisdm on 2009-01-17
Scratch that last post, I was able to get the correct drivers installed.  I even watched TV once, I didn't get all the channels I should've had but it was a start.  I didn't make any major changes (aside from themes and some minor preferences etc.) but now when ever I go to "Watch TV" the screen goes blank like it is going to start watching TV then all of MythTV crashes and I'm brought back to the desktop.

Any Ideas?

---

