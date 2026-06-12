---
title: "Audio works only with half of the headphone jack plugged in"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by finferflu on 2006-08-16
Hi all,

This morning I switched on my laptop and found out that there was no sound. 

It was working perfectly until last night, and today it just stopped. After playing a bit around with it I discovered that I could hear some really weak sound through my headphones, almost unperceptible, and I could hear a bit louder sounds but a bit dirty, only plugging in just half of the headphone jack. 

This sounds really weird, it's the first time I face such a weird situation. I don't know what to think about: is it hardware problem o hardware recognition problem? How to find out?

Here is some information about my sound card:

```
mmanu@ubuntumachine:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Thanks for your time.

---

### Post by finferflu on 2006-08-16
Ah, I've just found out! My room-mate has been playing around with my laptop and had put the "mechanical" mute (Fn+F8 ) on. So I had to re-play around with it, and with a bit of suffering I managed to get it working again. \\:D/

---

