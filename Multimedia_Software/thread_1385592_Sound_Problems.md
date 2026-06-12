---
title: "Sound Problems"
date: 2010-01-19
forum: Multimedia Software
---

### Post by Noptron on 2010-01-19
Hello, i'm still a newbie with the ubuntu thingy, the sound of the windows itself is good (the music in booting, the sound when opening folders & playing videos on youtube too) but for pidgin for example or when playing a song. the sound gets pretty bad quality :S i'm using a laptop "Medion MD 41667"
and a sound card "Intel 82801DB-ICH4"

another problem is that when plug in my headphones (the one that came with my nokia 5800) i could hear the sound but there's a weird problem... for example if i'm playing a song i could listen to the music very well but the sound of the singer himself is too low and i couldn't hear a thing...

---

### Post by Noptron on 2010-01-20
any one help me please?? :(

---

### Post by sports.car.guy on 2010-01-20
For starters the headphones from a cellphone are designed totally differently then normal ones. You can not use them like normal ones and expect them to perform the same. They not only have signal going to the earpieces, but also the mic to phone. Normal headphones work one way with signal to the speakers only. Try another set of headphones and I bet the listening experience will change.

Your other issues sounds like you are overdriving the tiny speakers in your laptop. Try turning down your levels when using those applications. Not the master volume, try PCM / Wave. Pidgin you can't, but with the music players run them at a low volume level.

If that clears up the audio then that is exactly the cause. One solution is to create Alsa devices for the offending applications to use that take the over driven sound in and lower it's levels to a usable one. It is similar to how you set the levels of the left and right channels in an Alsa device when creating a center channel from them.

I hope this helps, it is all I could think of for your problem.

---

