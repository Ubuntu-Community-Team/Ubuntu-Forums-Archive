---
title: "how to produce sound in vkeybd"
date: 2008-12-25
forum: Multimedia Software
---

### Post by halida on 2008-12-25
alsa donnot have midi support, so if you want to use vkeybd,
you need install TiMidity++ first.
after install , you must add a simulation port.

timidity -iA -B2,8 -Os1l -s 44100

it will print port information like:


Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3

then you can connect vkeybd to it.

vkeybd --device alsa --addr 129:0


---
finnally, I can play piano in ubuntu NOW!
good for me!!!!!!:guitar:

---
if you know the easy way , please tell me, I cannot google one.

---

