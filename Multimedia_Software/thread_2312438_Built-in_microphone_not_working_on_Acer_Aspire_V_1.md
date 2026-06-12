---
title: "Built-in microphone not working on Acer Aspire V 15"
date: 2016-02-04
forum: Multimedia Software
---

### Post by inh38 on 2016-02-04
Newbie here, so please excuse anything trivial I may have missed.
  I have a Acer Aspire V15 Nitro Black Edition VN7-592G. I have installed Ubuntu 14.04 on it, and it is working mostly fine.

  One thing I didn't get to work is the built-in microphone. I tried  all the solutions involving changes in alsa-base.conf, to no avail. 

I  also tried installing pavucontrol, but all I could see was 'Monitor of Built-in Analog Stereo' and 'Built-in Audio Analog Stereo'. Neither had any activity


  Right now, in my sounds setting, I have:
  
[LIST]
[*]with my headphones (no mic) on: headphones/analog input (no speakers option) 
[*]with my headphones off: speakers/analog input 
[/LIST]
  Both headphones and speakers work fine, but the analog input shows no signs of activity.
  Anyone has any idea how I can get this to work?
  This is what sudo aplay -l returns:
```
**** List of PLAYBACK Hardware Devices **** 

card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by inh38 on 2016-02-09
I tried running alsamixer, as recommanded by [this post]("http://askubuntu.com/questions/726579/built-in-microphone-not-working-on-acer-aspire/730679#730679"),  but alsamixer tells me that "This sound device does not have any capture controls".

---

### Post by mörgæs on 2016-02-09
Hi, welcome to the fora.

For such new hardware I would not recommend stale software like 14.04 but 15.10 or 16.04 (development).
How does it work using one of these in a live boot?

---

### Post by inh38 on 2016-02-09
No luck with 15.10 and 16.04.

In both cases, when I open the sound settings, input only has analog input.

---

### Post by mörgæs on 2016-02-09
Still I believe it was worth a try. 

Hopefully other posters can use the information for troubleshooting.

---

### Post by inh38 on 2016-02-09
Yes, it was worth a try indeed, now I can rule this out. Thanks :-)

---

