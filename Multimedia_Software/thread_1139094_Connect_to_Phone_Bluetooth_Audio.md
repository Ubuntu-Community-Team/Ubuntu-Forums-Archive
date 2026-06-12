---
title: "Connect to Phone Bluetooth Audio"
date: 2009-04-26
forum: Multimedia Software
---

### Post by mwolfgang on 2009-04-26
I am attempting to to connect to the bluetooth audio on my phone.  I am recording a podcast, and would like to be able to connect to my phone via bluetooth to not only record, but also so the person on the other end of the phone call would hear the output from my pc.  My show will be streamed live and syndicated as a podcast, so I will be takiing phone calls.

I am able to coneect to my phone via bluetooth (ie. for BitPim), but I'm unable to capture the audio.  I'm fairly certain I need to do something with *btsco*, but being a n00b, I'm really struggling with this.  

I created an .asoundrc file with the following:
```
pcm.bluetooth {
   type bluetooth
   device 00:00:00:00:00:00
}
```

I did use my actual address.  (I'm not that much of a n00b.)

I have a feeling that the .asoundrc I created is for a headset, and not the other way around.  I basically want the computer to act as a headset.

Thanks in advance for your help,
Matt

---

### Post by mwolfgang on 2009-04-26
I am able to connect to the headset function of the phone using:

```
 btsco -v 00:00:00:00:00:00
```

It adds a device called **BT Headset (Alsa mixer)** to the volume control, but I'm still not able to capture anything from this device, or hear anything from the computer when on a call with the phone.

---

