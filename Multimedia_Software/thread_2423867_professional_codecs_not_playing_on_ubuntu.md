---
title: "professional codecs not playing on ubuntu"
date: 2019-07-30
forum: Multimedia Software
---

### Post by babag on 2019-07-30
i'm using davinci resolve on ubuntu kxstudio and am having as hard time playing back anything but lower quality files. i can play back mp4 exports fine on vlc and parole but the only player i seem to be able to get to play professional codecs (like dnxhd, dnxhr, grass valley hqx, goprocineform) is ffplay, which is not the most convenient play. seems to work great, though. anyone know of a solution to get these codecs to be accessible more generally in the system?

thanks,
babag

---

### Post by mc4man on 2019-07-30
Don't have any of those codecs lying around but grabbed a dnxhd sample from grass valley site, works fine in mpv.
I'd  suspect any file that plays in ffplay will play in mpv.
In Ubuntu repos or better builds for some Ubuntu releases [here]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")

---

### Post by babag on 2019-07-30
thanks, mc4man. 

you've confirmed what i was told on the blackmagic forum as well as what i've found in my brief experience. tried mpv with all of the various things i output from davinci resolve and they all seem to be handled just fine by mpv. and, btw, how'd you get all of that great info displaying onscreen? or, was it just part of the colorbars file?

thanks again,
babag

---

### Post by mc4man on 2019-07-31
The overlay is a built-in lua script, to get a timed (about 4 sec) display  hit the i key, to toggle on/off hit shift+i
(- additional  timing info shown is using some resample options like --video-sync=display-resample in cli.

---

### Post by babag on 2019-07-31
cool! thanks.

---

