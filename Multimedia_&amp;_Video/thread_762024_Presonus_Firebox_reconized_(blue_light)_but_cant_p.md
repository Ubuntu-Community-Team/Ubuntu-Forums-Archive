---
title: "Presonus Firebox reconized (blue light) but cant play"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by mnobre on 2008-04-21
Presonus Firebox is detected when starting Jack Control, but can't hear any output.
Additional info: Ubuntu 7.10
Jack audio connect kit (GUI): 0.2.22
Jack setup info:
> Server Path: jackd
> Realtime unchecked (Jack client cannot start with this option checked)
> Interface: hd:0
> Audio: duplex
> Frames per period: 32
> Sample rate: 44100
> Periods/buffer: 3
> Port max: 256
> Timeout: 500 msec
> Input and output latency: 0
> Latency: 2.18 msec

gscanbus shows: S400Presonus: Port 0: connected to child node

I am using Rhythmbox 0.11.2 to play an audio file, but no sound are produced. Additionally, no readable client is shown by the "connect" window.

Thinks I've tried already:
- compile a Linux -rt kernel
- linked my user to "disk" group

Any clues on how to proceed?
Thanks,
MN

---

