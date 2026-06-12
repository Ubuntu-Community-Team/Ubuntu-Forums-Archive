---
title: "Microphone works but does not record"
date: 2010-01-31
forum: Multimedia Software
---

### Post by alevincio on 2010-01-31
Hi,
I'm running Ubuntu 9.10 on an Asus F3JC laptop with an integrated webcam and microphone.
The webcam is a
```

user@ubuntu:~$ lsusb
... 
Bus 001 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd DC-1125 WebCam
...

```and it works. If i tap on the microphone or if I blow on it, I hear noises but after I record something with gnome-sound-recorder I don't hear any sound! The same with Skype, for example.

On Xp (other hd partition) it works.

The audio device on the laptop is a
```

user@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660 Analog [ALC660 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC660 Digital [ALC660 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```If I open the "sound preferences tool" the device for sound input is "Internal Audio Analog Stereo" and even if I tune the volume of the microphone I don't see any movement in the input level bar. I've also checked alsamixer and the digital volum in the capture interface is set at the maximum.

What should I do to fix it? Any idea? If you need other information ask me and I'll post them.

Thank You in advance.

---

### Post by gradinaruvasile on 2010-01-31
Post an image with the alsamixer's capture view. Lets see whats there.

---

### Post by alevincio on 2010-01-31
Here it is ... the "All" interface.

Let me add that if I rise the volume in "MIC" higher than 83% I hear a strong sound, like an interference.

---

### Post by gradinaruvasile on 2010-01-31
Not All, only the capture. All is confusing.

Also, on the Playback make sure you mute the mic.

---

### Post by alevincio on 2010-01-31
Does it tell you something?

---

### Post by gradinaruvasile on 2010-01-31
> **alevincio said:**
> Does it tell you something?

Not really. And its a bit small. The text is not visible. Regardless i see that its only 1 item there which is strange. It should be 2-3 at least. Did it look the same with the default 1.0.20 ALSA?

---

### Post by alevincio on 2010-01-31
Sorry. This one should works but i think that the forum makes a thumbnail cause it is also smallare in size when i upload it.

Yes, alsamixer 1.0.22 shows only one vertical line called Digital. In the item description the db gain is 30.0 (maximum level). I don't know how it looked before with 1.0.20! I had the same problem before and i used to switch to windows whenever i needed to call with skype.

I attach also the windows showed by "gnome alsa mixer".

Well .. if i record few seconds of myself talking, then i don't hear a perfect silence but soething like a rustle ...

I don't really know what to add.

---

