---
title: "hauppage nova-t dvb usb stick on 12.04"
date: 2012-06-02
forum: Multimedia Software
---

### Post by matpol on 2012-06-02
I am trying to get a hauppage nova-t stick working on 12.04. Seems to be the reccommended usb dvb stick but it does not work. It registers but when I do a scan I get tuning failed. Using kaffeine i get no channels when I tune. There are lots of posts about this but they all seem to be a few years old. Just wondering whether someone had some uptodate info about how to set this up.

when I do:

```
dmesg | grep -i dvb
```

I get:

```
[   45.683911] usbcore: registered new interface driver dvb_usb_af9015
[   46.628091] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   46.628398] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   46.629043] DVB: registering new adapter (Hauppauge Nova-T Stick)
[   46.935790] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   47.190910] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   47.220820] usbcore: registered new interface driver dvb_usb_dib0700
```

I have also built v4l stuff and this does not seem to make any difference.

Any help would be much appreciated at the moment I feel like there's a magic switch somewhere I just don't know about.

PS this works on my laptop which uses mint 12.

---

### Post by howefield on 2012-06-02
You might need to update the transmitter information to get the scan to work.

Which transmitter are you using ?

If you want to use kaffeine, open up the following file in a text editor. 

```
/home/hugh/.kde/share/apps/kaffeine/scan.dvb
```

(substituting your username instead of mine of course)and scroll down to your transmitter and check the data.

---

### Post by matpol on 2012-06-02
I am using rowridge - plugging the stick into my laptop using the same aerial into my laptop the stick works - this is using the 3.0 kernel the other machine is using 3.2

---

### Post by howefield on 2012-06-02
You could try putting this into the above file, pasting over the existing Rowbridge data or renaming it) and then try scanning.

[dvb-t/uk-Rowridge]
T 498000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 522000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 474200000 8MHz 2/3 NONE QAM256 32k 1/32 NONE
T 506000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 482200000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 530000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE

---

### Post by matpol on 2012-06-02
genius - I think that's done it!

---

### Post by howefield on 2012-06-02
> **matpol said:**
> genius - I think that's done it!

Glad it worked, I have the same hardware and had the same issue with scanning (different transmitter). Took a while to suss out what the problem was.

---

