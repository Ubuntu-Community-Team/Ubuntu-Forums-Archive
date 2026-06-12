---
title: "Intel HDA issue"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by jdhore on 2008-02-07
(No, this is not the typical Intel HDA not working rant/problem). I have a Foxconn 915A01-P-8KS2 motherboard that has 8-channel Intel HDA Audio using the Realtek ALC880 codec. It works (i can't figure out which jack is the microphone jack, but i guess that's my stupidity), but i constantly have really loud static in any speakers or headphones i attach to it. I'm not sure what the issue is here, but it works beautifully in Windows (and no, i really would prefer not to try Hardy). If it helps, i'm using Gutsy with the -generic kernel.

---

### Post by tgalati4 on 2008-02-07
I assume that 

>aplay -l

looks like:
tgalati4@minty5:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[B]
And that you have the following at the bottom of your /etc/modprobe.d/alsa-base file:[/B]

# to try to get microphone to work: went from 5stack to 6stack
**options snd-hda-intel model=6stack**-digout

There are a lot of switches for Intel HDA:

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

---

### Post by jdhore on 2008-02-07
> **tgalati4 said:**
> I assume that 

>aplay -l

looks like:
tgalati4@minty5:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And that you have the following at the bottom of your /etc/modprobe.d/alsa-base file:

# to try to get microphone to work: went from 5stack to 6stack
options snd-hda-intel model=6stack-digout

There are a lot of switches for Intel HDA:

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

This is the entire output of my alsa-base file: [http://pastebin.ca/895462](http://pastebin.ca/895462)

This is what aplay -l showed: 

```
jd@aurora:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

NOTE: I'm not trying to get the mic to work...I'm trying to get rid of the static...The only thing i use my mic with is Skype and i can Skype on another box.

---

### Post by tgalati4 on 2008-02-07
Well, you need to add the 5stack or 6stack option to your alsa-base file.  I didn't see it so you will have to add it.  Your sound chip doesn't support digital out so you don't need the digout switch.

After adding the switch, reboot and don't be surprised if the headphone/mic jacks are switched from windows.  The chip has assignable inputs and outputs so they may be different between linux and Windows.

---

