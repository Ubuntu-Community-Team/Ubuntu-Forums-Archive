---
title: "Speakers / Headphones do not switch each other"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by acojlo on 2006-07-02
Hi, when I plug in my headphones, speakers on the laptop continues to output sound. When I plug them out nothing changes. Plug in headphones again - no change - laptop builtin speakers continue to output sound.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by louis_nichols on 2006-07-02
that is not a software problem. it's hardware. standard jack plugs have 2 internal switches that should disconnect the speakers when earphones are inserted.

so I'm afraid you should ge your laptop checked.

---

### Post by acojlo on 2006-07-03
[QUOTE=louis_nichols]that is not a software problem. it's hardware. standard jack plugs have 2 internal switches that should disconnect the speakers when earphones are inserted.

so I'm afraid you should ge your laptop checked.[/QUOTE]

You have right. Playing now with spining around headphone jack I realised that.
Thanks

---

### Post by kaput on 2006-07-15
Just so people know, though, software *can* affect the jack as well. I have a Dell XPS M140 and was having this issue. However, it occurred after I had updated to the most recent kernel build, 2.6.15-26. Booting in to 2.6.15-25 fixes the issue for me.

---

