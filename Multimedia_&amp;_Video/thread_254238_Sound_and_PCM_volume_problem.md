---
title: "Sound and PCM volume problem"
date: 2006-09-09
forum: Multimedia &amp; Video
---

### Post by shat on 2006-09-09
Hey all,

I have a weird problem happening on my laptop.  Basically, when I load up my profile, I lose control of my volume via the volume applet or multimedia keys (which were set up correctly before).  For example, when I start up my computer, I get the login drumroll, but after I load my profile I don't get startup sounds.  Also, say I'm listening to music via Banshee.  I can control the volume inside the program itself, but not outside via the PCM volume applet.  

Here is what I think caused the problem:  I plugged in a pair of USB headphones the other day in the lab, to see if they worked.  Ever since that, I've been having this problem.  

Here is another weird thing that happens when I start gedit from the terminal:

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
```

I guess it's looking for the headset sound card, how do I make it stop doing this?

---

### Post by shat on 2006-09-10
bumpy

---

### Post by shat on 2006-09-10
This might help..
```

lucas@lucas-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So, I try..
```
lucas@lucas-laptop:~$ alsamixer
```

and I get..
```

alsamixer: function snd_ctl_open failed for default: No such device
```

but running
```
lucas@lucas-laptop:~$ alsamixer -c 0
```

works..

---

### Post by yargevad on 2007-01-05
I was having this exact same problem and fixed it by commenting out all the lines containing "Headset" in ~/.asoundrc.asoundconf

Edit: and then doing /etc/init.d/alsa-utils restart

---

