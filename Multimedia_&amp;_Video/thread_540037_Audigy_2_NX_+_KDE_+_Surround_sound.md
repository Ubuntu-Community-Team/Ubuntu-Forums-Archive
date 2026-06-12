---
title: "Audigy 2 NX + KDE + Surround sound"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by 5loth on 2007-09-01
Hi all,

I've been using kubuntu for one week now, so i'm very new.

basically everything is working ok apart from 5.1 sound with the Creative
Audigy 2 NX USB.

I've read endless fixes on the net but unable to get it sorted,
i followed this thread:
[http://ubuntuforums.org/showthread.php?t=285065&highlight=audigy](http://ubuntuforums.org/showthread.php?t=285065&highlight=audigy)

but still can't get it to work.

basically, my laptop has onboard sound and it can't be disabled in the bios,
when i run alsamixer it is showing the Intel Onboard sound (HDA Intel) as the card being used.

can someone put an end to my misery and tell me how I go about setting Alsa's default sound as my audigy.

aplay -l gives the following output:

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
   Subdevices: 1/1
   Subdevice: #0, subdevice #0
card 1: NX [SB Audigy 2 NX], device 0: USB Audio [USB Audio]
   Subdevices: 1/1
   Subdevice: #0, #0



any help greatly appreciated.

---

### Post by wraezor on 2007-09-05
This should help:

```
# asoundconf

# asoundconf list

# asoundconf set-default-card Audigy
```

(Replace Audigy with whatever it calls your card of choice)

---

