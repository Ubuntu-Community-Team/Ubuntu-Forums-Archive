---
title: "No sound, compaq presario laptop, intel sound card"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by joshyf on 2006-08-25
hi, i followed the "comprehensive sound guide" but didn't help. i've got no sound whatsoever. i'm using a presario b3800, and the ubuntu 6.06 lts.

below is the result of aplay -l :
```

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

using alsamixer gets me nowhere.

please please help as i would really love to play music and hear things on my laptop! ](*,) 

thanks in advance, josh.

---

### Post by wjp.reg on 2006-08-25
Perhaps this link will help..

[http://www.ubuntuforums.org/showpost.php?p=1101974&postcount=10]("http://www.ubuntuforums.org/showpost.php?p=1101974&postcount=10")

---

### Post by joshyf on 2006-08-25
nope, didn't work, thanks for trying anyways! :)

---

### Post by joshyf on 2006-08-25
okay, really weird, but i sorted it out :S

turns out that muting 'headphone jack sense' got the sound working. how weird is that!?

---

### Post by wjp.reg on 2006-08-25
you said it..

---

### Post by KrakensDen on 2006-08-25
Unfortunately, that's pretty standard. I have a desktop from 2003 (I think, maybe 2004) with an intel soundcard, it needs the same fix. Honestly, it's one of those polish things that the Ubuntu people should look at doing by default :).

---

### Post by LegolasV on 2006-09-01
Hi,
I'm using the same laptop Presario B3800 and encounter the same problem as yours. I disabled Headphone Jack Sense but it doesn't work. Can you help me by providing the detail on how you fix the problem? Thanks!

---

### Post by joshyf on 2006-09-01
hi,

i'm not too experienced at providing support but I'll try my best! can you show me what aplay -l outputs? if, as above like mine, you get the sound card recognised, then use alsamixer and i'll give you what my settings are -

Master - 100%
Master Mono - 100%
Headphone - 100%
Headphone Jack Sense - Muted
PCM - About 50%
Line - Muted
Line Jack Sense - Muted
CD - Muted
Microphone - Muted
Mic Boost - Muted
Phone - Muted
IEC958 - Muted
Aux - Muted
External - Muted
Stereo Mic - Muted

i also installed gnome-alsa-mixer before I got it working, but i don't know if that helped.

try the above, let me know if it works or not. good luck! :)

---

### Post by LegolasV on 2006-09-01
Thank you very much, after setting all as your, the sound works now. Quite surprise :)

---

### Post by LegolasV on 2006-09-01
Frankly speaking, the sound quality is not as good as in Windows

---

### Post by Pindulet on 2008-03-11
Hi
I bellieve I have the same problem.. it looks like I have the same card and my aplay -l looks like this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: [COLOR="Red"]1[/COLOR]/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The only difference is red 1 where Joshyf has a 0.

anyway... in alsamixer there is no option called headphone jack sense or line jack sense!? I only have headphone and a line option...Is it because my alsamixer isn't up to date?? or...
maybe I should mention that I installed gutsy and I live everything about it besides that there is no sound

please help... I too would really like to listen to music and hear sounds on my laptop..

regards 
Kristian

---

