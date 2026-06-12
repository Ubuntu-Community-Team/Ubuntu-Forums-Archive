---
title: "Strange ALSA behavior for 5.1 sound"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by ansi on 2007-01-21
Hello!

After configuring my Ubuntu "Dapper" for 5.1 sound support, I've got a strange ALSA behavior of most of multimedia programs, such as mplayer, vlc, mpd etc.

What I have done:
 - Created the following ~/.asoundrc

```

defaults.pcm.card 0

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

- I have connected speakers: left && right -- to the green input of sound card, rear speakers to the orange input, and central (heavy-bass) to the black-marked input.

As result I gave: workable 4 (of 5) speakers + subwoofer. And now, Totem play .mp3's well, but:
 mplayer not responding with text: alsa-init: using device *
 vlc can't access to the /dev/dsp
 mpd informs me about problems to connect to the audio device
 Nautilus doesn't play mp3 files when mouse over file icon (It worked for me heretofore)

What I have to do to solve this problems? I've never worked with 5.1 system.

Thanks,
            ansi.

P.S. Sorry for my terrible English.

---

### Post by nixendra on 2007-01-21
don't know if it's related to your 5.1 problem but i remember installing the "oss-compat" package to get /dev/dsp and get sound working under vlc, hope this can help one of your problems

---

### Post by ansi on 2007-01-21
> **nixendra said:**
> don't know if it's related to your 5.1 problem but i remember installing the "oss-compat" package to get /dev/dsp and get sound working under vlc, hope this can help one of your problems

Thank you, but "oss-compat" is nosuch package in Dapper I think. APT do silent about this package and google too.

I've tried to use alsa-oss package, but it is no matter: problems are still the same.

---

### Post by nixendra on 2007-01-21
oops sorry, I'm running Edgy but though that "oss-compat" was available in dapper, don't know the "equivalent" package under dapper or if there is another way to achieve the same result, sorry

---

### Post by ansi on 2007-01-21
So, I've found a fractional solution for this problem, but it looks (when playing something) little unstable. Ok. This version of ~/.asoundrc works for me now:
```
pcm.snd_card {
type hw
card 0
}

pcm.!default{
type plug
slave.pcm "surround"
}


pcm.surround{
type route
slave.pcm dsp0
slave.channels 6
ttable.0.0 1 #L -> FL
ttable.1.1 1 #R -> FR
ttable.0.3 1 #L -> RR
ttable.1.2 1 #R -> Rl
#ttable.0.4 0.2 #L*0.2 -> Center
#ttable.1.4 0.2 #R*0.2 -> Center
#ttable.0.5 0.5 #L*0.5 -> LFE
#ttable.1.5 0.5 #R*0.5 -> LFE
}


pcm.mix {
type dmix
ipc_key 1234
slave.pcm snd_card
slave {
#pcm "hw:0,0"
channels 6
period_time 0
period_size 1024
#buffer_time 0
buffer_size 4092
rate 48000
}
}

pcm.dsp0{
type plug
slave.pcm mix
}

ctl.mixer0 {
type hw
card 0
}
```

I found it somewhere at [http://linuxquestions.org](http://linuxquestions.org).

Disadvantages:
[list]
 [*] Nautilus still doesn't play mp3 files from desktop
 [*] Center speaker sounds silent (or, it may be just a feature)
 [*] Mplayer (isn't a latest version) may made a crash when switching workplaces with speed in Gnome by mouse.
[/list]

---

