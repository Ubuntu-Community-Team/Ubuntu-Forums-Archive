---
title: "HVR-950/HVR-980 USB Tuner http://mcentral.de/hg/~mrec/v4l-dvb-kernel, dead?"
date: 2008-07-04
forum: Multimedia Software
---

### Post by bigdawgte on 2008-07-04
I am a noob. I am having trouble installing an HVR-950 - actually, an HVR-980, or EyeTV Hybrid (Mac OS X)- a nearly identical piece of hardware to the Hauppage. However, my trouble in installing is because of the method of installation in linux. The method recommended by everyone in Ubuntu (and otherwise) requires to "hg clone" to [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel). I have been trying to do this step for two days now and the site is unavailable. How can it be that with hardware this popular, the entire world has to go to the back porch of this one guy and get what they need out of the back door from a brown paper bag? And, apparently the demise of this site was seen coming. I found this article, which states: "In case you haven’t noticed, both Markus’ v4l-dvb-experimental and my v4l-dvb-makomk are slowly dying." Why?  If this is the only way this hardware can be installed, can't anything be done about it? Yes, I know its free - so what?  I would pay for the driver if I could.  Why isn't there more than one source for it?

---

### Post by xc3RnbFO8P on 2008-07-04
Did you do:
> hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)
in Terminal.
Is there some error messages?

> ~$ hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)
The program 'hg' is currently not installed.  You can install it by typing:
sudo apt-get install mercurial
bash: hg: command not found


---

### Post by bigdawgte on 2008-07-04
I did exactly that.  My post must have spurred some action, because instead of timing out as it had ~20 times in the past, it began to install.  Squeaky wheel?

---

### Post by xc3RnbFO8P on 2008-07-04
I am just sorry to see no response to your question.
I can open the link  [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel),
can you?

---

### Post by bigdawgte on 2008-07-04
My bad, I should have stated, in both cases "hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental" rather than "hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel".  No matter, because both seem to be working now.  Thanks.

---

### Post by xc3RnbFO8P on 2008-07-04
super :)

---

### Post by bigdawgte on 2008-07-04
what should happen after I "sudo modprobe em2880-dvb"?  Because mine does nothing, just returns to command line.

---

### Post by xc3RnbFO8P on 2008-07-04
Show output of **dmesg | grep dvb**

---

### Post by bigdawgte on 2008-07-04
dmesg says this, about that:

44.936204] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 1014654
[   44.936205] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   44.936207] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   44.936209] tveeprom 0-0050: audio processor is None (idx 0)
[   44.936211] tveeprom 0-0050: has radio
[   44.938429] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[   44.938442] attach inform (default): detected I2C address c2
[   44.938446] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[   44.938448] tuner 0x61: Configuration acknowledged
[   44.938450] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[   44.938476] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[   44.938479] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: xc3028 tuner successfully loaded
[   44.944432] attach_inform: tvp5150 detected.
[   45.006834] tvp5150 0-005c: tvp5150am1 detected.
[   45.096711] Loading base firmware: xc3028_init0.i2c.fw
[   46.070264] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[   46.102213] xc3028-tuner.c: firmware 2.7
[   46.102216] ANALOG TV REQUEST
[   46.108328] em28xx #0: V4L2 device registered as /dev/video0
[   46.108331] em28xx #0: Found Hauppauge WinTV HVR 950
[   46.108345] usbcore: registered new interface driver em28xx
[   46.124808] usbcore: registered new interface driver snd-usb-audio
[   46.134994] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   46.134996] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   46.135181] Em28xx: Initialized (Em28xx Audio Extension) extension
[   46.432077] lp0: using parport0 (interrupt-driven).
[   46.468773] em2880-dvb.c: DVB Init
[   46.468780] Loading base firmware: xc3028_8MHz_init0.i2c.fw

Does that look right?

---

### Post by xc3RnbFO8P on 2008-07-04
Yes, 
and now you can install TV software (if you haven't):
Kaffeine (Digital TV)
Me-tv (Digital TV)
Tvtime (analog TV)

---

### Post by xc3RnbFO8P on 2008-07-04
You also want to add this:

> sudo gedit /etc/modules

add this lines:
> em28xx
em2880-dvb

---

### Post by jcoles on 2008-09-13
I don't have an em2880-dvb module. Or, is the em28xx module the same thing? My HVR-950 is a Q model, I think. so, potentially there are modules au0828 and au8522 as well. 

I'm not sure what I am supposed to do about these modules. The device is not detected. But, sometimes the device is added if I modprobe one or more or the modules, unplug and plug in the device. Even if the device is detected, scanning fails on every channel every time.

I checked the HVR-950 on a Windows box, so I know the hardware is OK. Any ideas how I could get this to work?

---

