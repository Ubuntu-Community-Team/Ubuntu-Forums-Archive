---
title: "Audigy 2 ZS - Microphone"
date: 2009-09-20
forum: Multimedia Software
---

### Post by Fhang on 2009-09-20
Hello,
Ubuntu seems to have a problem with my soundcard (Audigy 2 ZS).
I'm trying to get my microphone to work for now over 2 weeks. I've read though several HOW TO'S and nothing helped. The only results i got from these before mentioned HOW TO's were no sound or no flash sound. :(
Sound in general works ! But the microphone doesn't no matter what settings i use.
I'm using the same Micro + Soundcard on Windows and it works perfectly fine.
My sound is set to ALSA : [http://www.imgwelt.de/show.php?code=39281T66719](http://www.imgwelt.de/show.php?code=39281T66719)
Gnome ALSA Mixer Screenshot : [http://www.imgwelt.de/show.php?code=VR04D8OL8CG](http://www.imgwelt.de/show.php?code=VR04D8OL8CG)
A few guides on how to fix sound problems with an Audigy 2 ZS soundcard told me to check the box "audigy analog/digital output jack". When i do that my sound is entierly gone. Also notice for some reason it says "sigmatel stac9721,23" :confused: on the gnome alsa mixer.
My onboard soundcard is disabled in bios otherwise it wouldn't work in windows even.

Any ideas on how to fix this issue ?

best regards,
Fhang

---

### Post by khelben1979 on 2009-09-20
You need to install [pulse audio]("http://en.wikipedia.org/wiki/Pulse_audio").

---

### Post by Fhang on 2009-09-20
i already have pulse audio : [http://www.imgwelt.de/show.php?code=7UVHYNJ19M2](http://www.imgwelt.de/show.php?code=7UVHYNJ19M2)[]("http://www.imgwelt.de/show.php?code=5J60C0F56HH")

---

### Post by khelben1979 on 2009-09-20
> **Fhang said:**
> i already have pulse audio : [http://www.imgwelt.de/show.php?code=7UVHYNJ19M2](http://www.imgwelt.de/show.php?code=7UVHYNJ19M2)[]("http://www.imgwelt.de/show.php?code=5J60C0F56HH")

I see. Attaching an usb headset is an easier way of getting this to work. Other than that, something is clearly wrong with your configuration, because it should work.

I would recommend that you check the mic volume meter to see if you need to raise it up a bit, see screenshot.

---

### Post by Fhang on 2009-09-20
i have my mic on 100%. when i set it to audigy 2 zs mic capture in the sound preferences menu it works for 30 seconds maybe then it kind of crashes. in SL for example my voice reconnects every 30 seconds because of this. it leaves me a 20 sec in which i can talk. then it takes 10 sec to realize it's crashed and then it reconnects. and for everything else it just works a few seconds and then it's over until i restart the application. for example skype or teamspeak.

---

### Post by khelben1979 on 2009-09-20
It sounds like you should think about doing a complete reinstall of Ubuntu. Is it a new or old install?

---

### Post by Fhang on 2009-09-20
i installed it 2 sep.

---

### Post by khelben1979 on 2009-09-20
> **Fhang said:**
> i installed it 2 sep.

And was it working better at that time or is it the same now?

---

### Post by Fhang on 2009-09-20
it was like that from day one

---

### Post by khelben1979 on 2009-09-21
> **Fhang said:**
> it was like that from day one

Then let's hope someone else will enter this thread, I'm out of ideas. I still do think that there's something with pulseaudio which causes the problem.

---

