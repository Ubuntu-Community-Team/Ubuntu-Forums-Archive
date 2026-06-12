---
title: "Rosegarden: MIDI works but not percussion"
date: 2011-04-11
forum: Multimedia Software
---

### Post by again617 on 2011-04-11
Hello, I will be very grateful if someone is able to help me with my problem. I have Rosegarden working for most MIDI instruments but not for percussion. Percussion tracks either sound like a piano or they are completely silent.

This is my setup. I use qjackctl to start jack and looking at the messages the command used is:
```
/usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
```

I then start timidity with:
```
timidity --realtime-priority=60 -iA -B2,8 -Oj -s 22050
```
        
When I start Rosegarden, all connections get made automatically and audio tracks, synth tracks and *most* MIDI tracks work. Are any of my settings weird or something?

Thank-you,

---

