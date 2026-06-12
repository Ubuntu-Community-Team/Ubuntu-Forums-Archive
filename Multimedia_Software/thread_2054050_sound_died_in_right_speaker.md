---
title: "sound died in right speaker"
date: 2012-09-06
forum: Multimedia Software
---

### Post by greatsirkain on 2012-09-06
I had the same sort of problem a week or so ago but when I did the alsa update thing I lost sound altogether for days, eventually got it working again and the right speaker went quiet so I clicked on the gnome alsa mixer I keep in the launcher and the sound in the right speaker reappeared for a while but then died. I've checked connections, the speaker, the balance, the volume, made sure nothings muted etc with no luck.
It's a realtek ac'97 onboard soundcard

```
lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
``````

sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
``` ```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```maybe if I reset the sound and logout and in? Is there anyway I can prevent the sound from going again, I don't really want to touch anything in case I'm left without any sound lol, ideas?

---

### Post by greatsirkain on 2012-09-06
resetting, relogging in, rebooting didn't work. Saw a few fixes for similar problems such as downloading QAMixer (ubuntu software center has never heard of it?), unplugging cables and plugging them back in...None worked, only thing I can think of is reinstalling alsa which fixed my no sound problem (when it eventually worked properly) but if it's only going to last a few hours before losing the right speaker it's not worth the amount of effort...Takes me ten minutes just to boot up :S

---

### Post by Epodx64 on 2012-09-07
Maybe your speakers are going bad try plugging in a pair of headphones if you have two different audio ports (front & back) maybe the connections are going bad try headphones in both ports and see if that fixes it.

---

### Post by greatsirkain on 2012-09-08
sorted, mechanical fault in my T.V was causing it and when I'd tried headphones before I'd just used the T.V jack, think the pots just need cleaning. Watching some flash videos does sometimes randomly mute the right channel for some reason. All is good :)

---

