---
title: "Switching cable from VGA to HDMI broke SPDIF"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by TheKorn2 on 2008-03-24
Man, I really hate ALSA right about now.

So a couple of weeks ago I broke my HDMI cable.  Annoying, but whatcha gonna do.  So I fell back to my VGA cable.  In that process, my SPDIF output stopped working.  I screwed around with it for two days, and eventually got SPDIF working again.

Well, now we're on the other end.  The new HDMI cable is here, and installed, and like clockwork all SPDIF output has now ceased working.

The only thing I can guess is that Ubuntu (for who knows WHAT reason) is seeing an HDMI connectino and going "ah-ha, sound goes there!" even though the device doesn't have any audio capabilities whatsoever.  That's my theory, anyway.  I'm saying that because if I run "alsamixer", the chip is reported as being " Generic 1095 SI HDMI".

So, I guess I want to know how can I tell the system to STUFF IT when it thinks it wants to send output via either HDMI port.  (I have two, the onboard intel card and the nvidia 7x00 card that I'm actually using.)  How can I FORCE the system to send all audio through the SPDIF port?

Not really sure what would be appropriate for debugging info, but as a start, here's aplay -l:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I (think) I need to *force* everything through card 0, device 1. 

Oh yeah, after lots of google searching I've already checked all my mixer settings, made sure both IEC958 outputs are checked, headphones are unchecked, made sure nothing is muted, etc.  Also tried adding "options snd-hda-intel model=6stack-dig", 6stack, and other permutations to /etc/modprobe.d/alsa-base .  That will make different things show up in the alsa mixer, but other than that doesn't do much.

Thanks in advance for any and all ideas!

---

### Post by TheKorn2 on 2008-03-25
Morning bump...

(Doesn't [SIZE="7"]anyone[/SIZE] know [SIZE="7"]ANYTHING[/SIZE] about fixing Alsa bugs, and forcing Alsa NOT to shove everything over HDMI erronously!???)

---

