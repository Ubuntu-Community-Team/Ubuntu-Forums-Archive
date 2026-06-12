---
title: "Sound only works when volume &gt; 50%"
date: 2008-12-26
forum: Multimedia Software
---

### Post by scandido on 2008-12-26
I have a strange problem. My audio works fine when the Master volume (on the Gnome Panel) is set over 50%. It even scales, as its supposed to, until reaching below 50% at which point I get no audio. I can adjust the volume in individual applications lowering the volume further, just not with the system volume control.

Does anyone have any idea why this would be or where the right place to begin troubleshooting is?

Thanks for your help.

---

### Post by laxwrestler on 2009-01-16
I have this same issue.  It can be quite annoying with such a limited sound range.

---

### Post by scandido on 2009-02-04
Well, maybe it is an issue with some common bit of hardware. My computer is a Gateway MX6448. Perhaps you could mention the model of your computer?

---

### Post by laxwrestler on 2009-02-05
gateway m385 - its a tablet laptop.

---

### Post by scandido on 2009-02-07
I tried looking for my sound card to see if we have the same:

scandido@scl:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Same card?

---

### Post by bba1973 on 2009-02-07
Sorry I can't add any help, but I've got the same issue on a Gateway MT6828. The volume increments are too big. Any way to make them smaller?

---

### Post by laxwrestler on 2009-02-07
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

don't really know what any of this output means.  I guess HDA Intel and HDA ATI are different

---

### Post by scandido on 2009-02-15
There is a bug report associated to this problem at

[https://bugs.launchpad.net/ubuntu/+bug/319971](https://bugs.launchpad.net/ubuntu/+bug/319971)

I'd encourage all of you to add your debugging information there so hopefully someone can help us.

---

### Post by tpx60s on 2009-06-27
I don't use Ubuntu but openSUSE 11.1 but have the same problem on my Thinkpad X60s as described in the bug link above (no sound below 70%). I use KDE though not Gnome and have a Intel HDA sound card.

Since the problem seems to exist across the two distros and on Gnome and KDE I'd image it's something in the Kernel as that would be the only common thing. I can't see anything in any of the config files that seems to specify the volume increments.

Just wondering if this bug has been fixed in Ubuntu yet.

---

