---
title: "volume log scale"
date: 2009-09-29
forum: Multimedia Software
---

### Post by caitifty on 2009-09-29
Hi

I have sound working just fine on my dell laptop (with ubuntu 9.04).  However when adjusting the volume, pretty much all the 'adjustment' happens at the top end of the scale - if I decrease the volume to about the 3/4 mark using the volume control applet (or any other software-based volume control tool) the audible volume goes to zero.  ie for all practical purposes the bottom 3/4 of the volume scale all = 0 and all real volume adjustment takes place in the top 1/4.  Additionally, because all the 'real' volume change occurs in only a tiny range of the controller, it is hard to make fine-grained volume adjustments - a tiny move becomes a huge jump in sound or a jump from 'too loud' to silence.

Does anyone know if it is possible to change the way the volume control maps to 'real' volume so the full range of the software volume control is used?

I hope this post is clear - I know there's probably more precise terminology for what I'm trying to describe.  

Many thanks in advance

Pete

---

### Post by caitifty on 2009-10-10
Bump.  Anyone?

---

### Post by DrCube on 2009-10-14
Same problem here, thought I'd bump too. Dell inspiron with ubuntu 9.04. Only the highest 3 or 4 'clicks' on the volume control produce any sound at all, and it seems to double the volume for every click. 'Log scale' sounds like the right way to put it.

---

### Post by sesheron on 2009-10-15
I'm here with you too.  I'm running an Asus board with an AMD X2 and a gtx 260 video card.  Nforce on the on motherboard I believe as well.

aplay -l shows the following
> card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v audio related output
> 00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


---

### Post by DrCube on 2009-10-15
Just wanted to say "exponential" is the word we want, not 'logarithmic'; that would imply all the volume control was at the bottom and very little change happened at the top. My math brain won't let me get away with that little mistake.

---

### Post by sesheron on 2009-10-16
alright weird story...so i tried going into 
System>Preference>Sound
and changing everything so that OSS was chosen.
logged out and back in.  heard sound.  still all at the top of the slider.
Went back to ALSA settings, and logged out and in again.
Now the volume slider appears to be smoother...sound all the way from bottom to top.

Go figure.

---

