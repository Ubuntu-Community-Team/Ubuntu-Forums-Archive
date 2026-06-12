---
title: "WinTV-HVR-950Q - Hauppauge"
date: 2014-05-23
forum: Multimedia Software
---

### Post by lisanels47 on 2014-05-23
Running Uubntu 14.04, I found it was very simple to get this device working.  Ubuntu has the /lib/firmware/dvb-fe-xc5000-1.6.114.fw is included with 14.04, but the second file is not.

Download the extra firmware file from:  [http://kernellabs.com/firmware/xc5000/](http://kernellabs.com/firmware/xc5000/)

cp dvb-fe-xc5000c-4.1.30.7.fw /lib/firmware

/lib/firmware/dvb-fe-xc5000-1.6.114.fw
/lib/firmware/dvb-fe-xc5000c-4.1.30.7.fw

w_scan -ft -c US -X > ~/channels.conf

The only quirk I notice is that after scanning channels in me-tv, I need to reboot in order to use the device again.
Unpluging it does not work, the device seems to stay "in use" by something.

---

### Post by lisanels47 on 2014-05-26
Still works great, but the usb device will be unusable after scanning channels, or using another program that uses the device.
I have to reboot the computer to get it working again.
Looks like it needs some work on the USB removal script somewhere.  Even re-plugging it in won't work.  The lights on the unit remain off after unplugging it and putting it back in.

---

### Post by dianemeeks2 on 2014-07-18
I can't really offer a solution. I'm just seconding the issue in hopes that someone will jump in here. I'm using tvtime, but if I attempt to open the device in VLC, tvtime will see it as in use even with VLC closed.

Just out of curiosity, did you have any trouble getting sound? I'm still unable to get sound, only video.

---

### Post by lisanels47 on 2014-07-18
I had no issue with the sound, it worked perfect.  I'm using Me-TV.  The channel scanner was tricky to find, it's under Channels/ADD/Scan.

---

### Post by uudruid74 on 2014-08-18
I use tvtime and sometimes I get sound and sometimes I don't.  I haven't figured out what makes the difference.   I have not installed the second firmware file, but right NOW, my sound is working.  I don't do any aplay tricks, which is weird because it would seem as though tvtime expects an analog link from the tvcard to the sound card, so it tries to control a mixer.   That mixer does NOT work since I don't have one.  Something has to read the audio from the USB tv tuner and send it to pulseaudio (or rather alsa, and a plugin picks it up).  I can then send it to any of my sound output devices, or all of them at once.

> **lisanels47 said:**
> 
/lib/firmware/dvb-fe-xc5000c-4.1.30.7.fw


Does your kernel actually load this file?  I think they may be for different devices.   Check your dmesg, and what is the USB device IDs of your HVR-950Q.  lsusb will show it.  Mine is ..

Bus 001 Device 021: ID 2040:7217 Hauppauge 

2040:7217 is how the kernel recognizes it.

It loads the xc5000 firmware.  Is the xc5000c a different model?

---

