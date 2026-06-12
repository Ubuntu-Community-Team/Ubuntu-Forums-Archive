---
title: "no sound after reboot, /dev/dsp not created"
date: 2008-12-14
forum: Multimedia Software
---

### Post by linuxgrrl on 2008-12-14
hi,
After about 70 days of uptime on my livingroom pc, I rebooted and now my sound is messed up. I have no sound from Banshee, MythTv, etc., but from XMMS if I select "hw 1,0" for the Alsa plugin output device, I get sound from XMMS.

Also, the file /dev/dsp does not exist.  I think it used to be there (I think that is what MythTv used, for instance).  Running 'alsamixer -c 1" does show my soundcard, so that means Alsa is loading, right?  

My other details are: 

```
mary@mythbox:~$ cat /proc/asound/modules
 0 cx88_alsa
 1 snd_via82xx
```


```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
mary@mythbox:~$ lspci | grep audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

I also have a pcHDTV 5500 card installed that uses the cx88xx driver, however I fail to see why that would prevent /dev/dsp from being created at all.

I should mention I am running Gutsy 64.
thanks
Mary

---

