---
title: "msi wind u100 alc883 audio configuration"
date: 2009-03-20
forum: Multimedia Software
---

### Post by carlosIII on 2009-03-20
hello
i'd like somebody to help.

i installed ubuntu in my msi u100 432.
But it seems that it does not properly recognize the soundcard or something.
i mean, the audio works for playing mp3s or firefox, but i like to work with hydrogen (drum machine) and jack and jack mixer to connect everything with ardour, nevertheless whenever i do that the sound gets messed up. (also when trying to use audacious and play a video at the same time)

i try that "options snd-hda-intel model= " thing 
but it doesnt work

this is mi lspci -v result

 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0110
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ffe00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

please, what can i do

---

### Post by maxadocious on 2010-06-21
I wanted to say that I had similar problems with Karmic. I had to wipe the harddrive because of partition issues though and after re-installing it seems to work for me. I know this isn't a good fix, but you're not alone w/ msi wind audio frustration.

As a side note, do you know any good Jack tutorials? There's so much out there it's hard to get started.

thx & gl

---

