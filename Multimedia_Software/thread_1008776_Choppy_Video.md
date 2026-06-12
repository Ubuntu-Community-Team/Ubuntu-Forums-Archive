---
title: "Choppy Video?"
date: 2008-12-11
forum: Multimedia Software
---

### Post by ToyotaGuy23 on 2008-12-11
Hi All,

Today I learned all about Medibuntu, and added it to the repository.  I did the whole keyring thing, and set all that up.

Now that I can finally SEE my videos, they have a blinky, choppy playback.

How can I diagnose this, and what should I do to try to fix it?

I use 8.10 Intrepid 32 bit

---

### Post by DarkSoul1984 on 2008-12-13
I'm having the same issue, specifically with Mplayer and VLC. I'm working on it for now. If I discover the problem I'll post it here. Otherwise, hopefully somebody else knows what is going on...

---

### Post by echo_maker on 2008-12-13
Exactly the same issue...

Interesting, it is Ubuntu 8.10 specific: I was able to watch video just fine on Ubuntu 8.04 (and on its derivative LinuxMint 5) but not on 8.10 (and its derivative LinuxMint 6 RC1). 

In both cases on DVD playback attempt nothing was going on before the ATI proprietary driver had been installed; and once installed the movie is showing up but unbearably choppy. 

I have Thinkpad T60 2623-D3U with  ATI X1400 128MB Graphics.

I am a novice here. Anybody knows how to submit a bug report?

Thanks

---

### Post by echo_maker on 2008-12-13
Hey - there is an easy fix for that!

Here it is:

System -> Appearance -> Visual Effects (Tab) -> None

DVD started working perfectly fine.

Enjoy!

---

### Post by jbrown96 on 2008-12-13
ATI cards have a nasty problem with Vsync. Until the drivers are fixed, there's nothing to keep the video from tearing. You might try changing the video mode to OpenGL in VLC, not sure if there are similar options for other players

---

### Post by fmb on 2008-12-14
Using radeonhd driver instead of fglrx may also solve the problem. The driver is an open source alternative for Radeon HD cards (I'm using it for 3650), and is under development in matter of 3D, AFAIK. But 2D are solid.

---

### Post by jbrown96 on 2008-12-14
> **fmb said:**
> Using radeonhd driver instead of fglrx may also solve the problem. The driver is an open source alternative for Radeon HD cards (I'm using it for 3650), and is under development in matter of 3D, AFAIK. But 2D are solid.

How's video playback? What kind of video are you playing (codec and resolution? What's the processor usage? What kind of processor?
I'm getting really sick of ATI's driver and would love to switch to something else if there is less tearing.

---

