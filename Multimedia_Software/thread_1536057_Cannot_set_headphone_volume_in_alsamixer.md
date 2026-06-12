---
title: "Cannot set headphone volume in alsamixer"
date: 2010-07-21
forum: Multimedia Software
---

### Post by muttley75 on 2010-07-21
Hi, 

since updating my laptop to 10.04, I can't get any sound out of my headphones. If I plug the jack in, the sound from the loudspeakers turns off, but the headphones stay quiet.

I have run alsamixer and in fact the volume for the headphones is stuck to zero, and it's not possible to increase it.

My hardware config is posted here:
[http://www.alsa-project.org/db/?f=3f70d9a282bd5ac80b591b8df0a0250fa39fabe0](http://www.alsa-project.org/db/?f=3f70d9a282bd5ac80b591b8df0a0250fa39fabe0)

What I find funny, is that amixer reports that I don't have the capability of regulating the headphone volume:

Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]


I have also used the AlsaUpgrade script to get the latest version of alsa, but it still doesn't work.

Anybody got a clue?

---

### Post by Yellow Pasque on 2010-07-22
Try adding this line to /etc/modprobe.d/alsa-base.conf file:
```
options snd-hda-intel model=auto
```

---

### Post by muttley75 on 2010-07-22
> **Temüjin said:**
> Try adding this line to /etc/modprobe.d/alsa-base.conf file:
```
options snd-hda-intel model=auto
```

I have tried, but it still doesn't work.

```

Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

```

There is another funny thing I have noticed: when running alsamixer, I have a "Caller ID" slider. Isn't this a modem setting???

---

### Post by lidex on 2010-07-23
More options to try:
```
options snd-hda-intel model=asus-mode3
options snd-hda-intel model=3stack
options snd-hda-intel model=3stack-660
options snd-hda-intel model=asus-v1s
```
Remember to use only one line at a time and reboot for changes to take effect.

---

### Post by muttley75 on 2010-07-24
I have tried all the options you mentioned, I have also tried model=lenovo, but without success.

What really disappoints me is that the headphones were working fine with version 9.10. I guess I would have to downgrade to an older version of alsa and try again...

---

### Post by skatested on 2010-07-24
I had/have a similar problem. Go to the control panel, then to hardware and sound, then sound. You should see something called manage audio devices. Plug in your headphones and see if they show up. If they don't, then either your divers

---

### Post by muttley75 on 2010-07-24
Ok guys it's solved. To quickly check all the combinations I was only checking with alsamixer.
It turns out that even if alsamixer reports headphones' volume at zero, I can still hear stuff.

Many thanks for the help!

---

### Post by jandugacek on 2010-08-17
I have a similar problem, but I don`t know what is the control panel. It is only in Windows, I think. In preferences and administration, there is no hardware and sound option.

---

### Post by connellc on 2011-04-03
In ALSA Mixer I found that even though I could not fix the headphone levels, I could change the "Front", "Side" and "Center" levels, and these controls were ***also ***set to zero. All I had to do to get my headphones to work again was to raise the other levels to a comfortable level.:P

---

