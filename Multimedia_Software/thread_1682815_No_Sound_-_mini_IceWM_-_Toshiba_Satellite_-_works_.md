---
title: "No Sound - mini IceWM - Toshiba Satellite - works in Knoppix"
date: 2011-02-06
forum: Multimedia Software
---

### Post by pnguine on 2011-02-06
Hi.

I've been trying to get this sorted for days. I'm trying to use this older Toshiba Satellite 1800 as a kind of Internet Radio kiosk. Sound was working in Xubuntu but everything was too slow so I switched to fresh minimal install from the mini cd and used the guide from psychocats to install IceWM. No I have _no_ sound. (It works perfectly off of Knoppix 6.0.1 live cd.)

```
aplay -l
```

is good

```
lspci -v
```

is good

alsamixer looks right

moc acts like it's playing OK, but there is _nothing_ coming out of the speakers.

There are no errors anywhere.

```
lsmod
```

shows the correct module loaded (snd-ali5451)

Anybody have any idea what I could try next (other than installing Knoppix to the hard drive :p )

TIA

---

### Post by pnguine on 2011-02-06
OK - right now it's working.

What I did:

- installed Xfce4
- installed xfce4-mixer
- ran xfce4-mixer
- only choice for playback: Internal Audio Analog Stereo (Pulse Audio Mixer)
- no controls showing
- enabled "Master" (only option)
- showed muted
- unmuted
- sound worked

Will now keep fingers crossed :rolleyes:

---

