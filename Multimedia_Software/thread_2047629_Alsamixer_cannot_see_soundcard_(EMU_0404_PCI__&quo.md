---
title: "Alsamixer cannot see soundcard (EMU 0404 PCI / &quot;Creative Labs SB0400 Audigy2 Value&quot;)"
date: 2012-08-25
forum: Multimedia Software
---

### Post by Rigby on 2012-08-25
Hello, 

I can't use my EMU soundcard and would really appreciate some help in getting it to work please :)

Lspci can see the soundcard, but alsamixer cannot. Strangely, I tried Fedora and the EMU soundcard 'just works'.

Any ideas?

Here's an excerpt from lspci:

```
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
...
09:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

```

And aplay -l:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Rigby on 2012-08-25
Very simple fix...

1) Terminal:

```
sudo apt-get install alsa-firmware
```2) Restart.

3) Tweak settings/levels using 'alsamixer'.

My soundcard not only works, but sounds as good as when Creative's proprietary Windows Vista/7 driver is used. Hope this helps someone else too.

---

