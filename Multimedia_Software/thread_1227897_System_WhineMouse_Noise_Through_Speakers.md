---
title: "System Whine/Mouse Noise Through Speakers"
date: 2009-07-31
forum: Multimedia Software
---

### Post by Bezmotivnik on 2009-07-31
[v9.04]

C-Media CMI 8738 [Ubuntu-identified]

Good board, but when I hook up speakers to the MB's audio line out, they have a constant high-pitched whine and various system racket coming through the speakers -- mouse growl when rolled, drives racket, etc.

Music and sound comes out, but this racket makes listening unpleasant.

Any thoughts on this?  Drivers, board defects, what?

As always, thanks for any help.

00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 80e2
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 10
	I/O ports at a400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI

---

### Post by xc3RnbFO8P on 2009-07-31
Maybe the Jack?
Did you try headphones?

---

### Post by Bezmotivnik on 2009-07-31
> **Ringi said:**
> Maybe the Jack?
No, that wouldn't explain the symptoms, but I checked anyway.  It seems fine.
> Did you try headphones?
Yeah, identical noise problem from that output jack.

---

### Post by xc3RnbFO8P on 2009-07-31
It could be wrong type of Jack:
[http://en.wikipedia.org/wiki/TRS_connector]("http://en.wikipedia.org/wiki/TRS_connector")

---

### Post by Bezmotivnik on 2009-07-31
> **Ringi said:**
> It could be wrong type of Jack:

No, it's fine.  

The stereo output works and I get sound -- I just get all this other system noise, too. :(

I went into alsamixer and boosted the gain, which helped the S/N ratio, but the noise is still unchanged -- just less in the overall signal.

---

### Post by eldragon on 2009-07-31
theres nothing you can do about it...its intereference, probably due to bad design of the hardware....(mainboard, or sound subsystem).

maybe...and its a BIG maybe, replacing the PSU would help.

---

### Post by madnessjack on 2009-07-31
I've had this a fair bit, it could be to do with a noisy motherboard or psu.

I fixed it by unplugging nearby electrical appliances. If you're connected through an extension cable this could also be noisy. I think the noise was still there but it wasn't nearly as bad as it was, and I was able to record with a very acceptable s/n ratio.

---

### Post by Bezmotivnik on 2009-07-31
> **madnessjack said:**
> I've had this a fair bit, it could be to do with a noisy motherboard or psu.

How could a PSU possibly cause mouse and hard drive noise?

Bad board design, yeah, though this is pretty extreme for a high-end (if old) ASUS momboard.

> I fixed it by unplugging nearby electrical appliances. If you're connected through an extension cable this could also be noisy. I think the noise was still there but it wasn't nearly as bad as it was, and I was able to record with a very acceptable s/n ratio.
Again, I don't see how this could produce mouse and drive noise.

External noise sources aren't the problem here; it's a clean AC line that's running through several filters in my (non-Linux) recording studio.

---

### Post by madnessjack on 2009-07-31
Because sound gets converted from electricity, so any interference will affect it

---

### Post by igorzwx on 2009-07-31
"00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)"

Is it yours?
 23 oss_cmpci	pci13f6,111	CMedia CM8738/CM8768
[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)

It might be interesting to try another sound system and
see if it produces noise too.

Another Ubuntu 9.04 in dual boot,
and install OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Bezmotivnik on 2009-07-31
> **madnessjack said:**
> Because sound gets converted from electricity, so any interference will affect it
Hmm.

Well, I'll swap out the PS and see if it makes any difference.

Actually, I think it's that chip in a MB application; I have the same chip in a different board in an XP box in a different part of the house with the best  PS I own and it has the same problem (with substantially less intensity).

I have a Linux box running on that same outlet sharing a KVMA switch with an SiS audio chip and a shoddier PS that's dead quiet.

---

### Post by igorzwx on 2009-07-31
Noise might be produces by PulseAudio

Quote:
"I don't think it is a 'bug' in pulse, it is the fact that 
pulse is a sound server and runs at a specific frame rate.  It has to 
move all sound streams to that frame rate in order to play through the 
sound device.  It uses on the fly rate conversion, and this introduces 
artifacts into the sound."

---

### Post by Zeppe on 2012-12-08
I've been having it too for ages, it's not interferecnes, it's a bug. The noise happens only when the speakers are plugged in, and it's heard only through laptop speakers, no the headphones themselves (it's also the only noise that can be heard). When the headphones aren't plugged. it disappears.

---

