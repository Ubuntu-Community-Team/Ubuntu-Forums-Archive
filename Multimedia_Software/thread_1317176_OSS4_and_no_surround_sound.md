---
title: "OSS4 and no surround sound"
date: 2009-11-06
forum: Multimedia Software
---

### Post by luki91 on 2009-11-06
Hello everybody:)
I'm fresh user of Ubuntu so I'm still learning:)
i'm using Ubuntu KK and i have problem with sound since i started to use it. I have 5.1 speakers on Realtek alc660 sound card and i can get sound from only two speakers(one channel), the rest play so quiet that it's impossible to hear them on normal sound level, now i'm using oss4 drivers, i also tried alsa and pulseaudio but it was a failure... When typing osstest into a terminal all speakers play correctly but when listening to music or watching a film i can hear only two, i changed all settings which i found but there's no effect. Also one day an icon of mixer on gnome panel just disapeared, such as a Sound icon from System>Preferences but fortunately oss still works. 
Can anybody help me? I asked on other forums but there's no answer yet...

Thanks in advance and sorry for my poor English:)

---

### Post by oxiroxt on 2009-11-07
Right, I've got exactly the same problem. I'm trying to setup a 4.0 profile. osstest makes all the outputs sound, however I only get sound out of the front speakers when playing music, movies, etc. I suspect this is because it defaults to sending 2ch streams to the front speakers only. Ideally, I'd expect it to pass a stereo stream both onto the front speakers output and rear speakers output by default, AND a 4ch stream the way it's supposed to be done. [S]I think the latter case is working (but I didn't really get to try it)...
[/S]
I tried changing the dropdown box in ossxmix from Stereo to Multich, but I didn't notice any difference... How am I supposed to tell oss4 to play stereo streams onto all 4 speakers WHILE preserving the obvious functionality of playing 4ch streams, each channel in its corresponding speaker? I mean, if for instance I'm playing a 4ch stream I wouln't like having just the 2 first channels replicated to all 4 speakers... Hope this makes some sense

Thanks

---

### Post by Philippo.co on 2009-11-18
Hi ppl
I'm on karmic_amd64

I have same problem here, my sound card(AudigyLS) works really nice with OSS drivers but I couldn't know how to configure rear speakers.

When I ran the osstest, front speakers worked good but rear speakers doesn't, only right one works.

Regards!

---

