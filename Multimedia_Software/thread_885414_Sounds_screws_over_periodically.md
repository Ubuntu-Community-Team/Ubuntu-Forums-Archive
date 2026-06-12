---
title: "Sounds screws over periodically"
date: 2008-08-10
forum: Multimedia Software
---

### Post by miickEe on 2008-08-10
Hey

I'm running gutsy, and have a creative sound blaster live sound card. It's set up the way it is in the Comprehensive Sound sticky.

It works fine, and sometimes when new software is installed, or updates are installed, the sound decides to become horribly distorted. In the past I've had success in playing with alsamixer to fix it, muting channels that contribute to the distortion, or purging alsamixer and audio stuff, and reinstalling. This time it's not doing a thing to help.

What can I do? It's not the amp, or the speakers, cause the same configuration a) worked perfectly before and b) works perfectly with the same configuration on my xp partition.

Anyways, hope to get some helpful answers

Mike

---

### Post by miickEe on 2008-08-11
Would love some helpful suggestions ASAP.

---

### Post by miickEe on 2008-08-26
Bump, Bump.

I'm an audiophile and I NEED to have sound playing as it should. So, because of this minor glitch, I am using xp again and it is so painful to switch between partitions all the time, and it's not good for my data to be switching all over the place.

Anyone help me?

---

### Post by miickEe on 2008-08-27
Ok, I can get sound working better with my onboard sound card (via82xx), it's not distorted because I turned down the volume levels in alsamixer and made sure there were no large dB gains.

Now, my emu10k1 card is not there anymore.. like, when I type the command

```
aplay -l
```
It only lists my via82xx sound card.. When it used to list them both.
And yes, my other sound card IS plugged in and is pretty new so it would not be broken. It was working yesterday.

I've typed
```
sudo modprobe snd-emu10k1x
```
And it still doesn't install..

I've used ```
sudo apt-cache search emu10k1
``` and it comes up with all these driver packages, and I installed them. It still doesn't show up with my soundcard. What's the go?

---

### Post by miickEe on 2008-09-10
Bump bump.

I'm absolutely sick of crap sound in ubuntu. I am even more sick of the lack of support from the community, who are so happy to point out how wonderfully configured their machines are and that anyone who can't achieve the same is a total noob, that they can't stop and help. Thing is, if we got a little help we'd stop asking questions.

Now, I've put up with it for ages. I've looked up almost every thread from this forum and others, tried what others said was the proverbial silver bullet with no avail. I have a dual boot system just so I can listen to music. Everything sounds fine in xp (no surprises there).

Just help.

---

