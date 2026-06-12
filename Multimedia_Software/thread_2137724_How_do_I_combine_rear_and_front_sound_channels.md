---
title: "How do I combine rear and front sound channels"
date: 2013-04-21
forum: Multimedia Software
---

### Post by alexm287 on 2013-04-21
I've been working at this for quite some time, trying to configure my speakers properly. It's a little odd as I have two normal stereo speakers (front left and front right) and a subwoofer (which is from a different speaker system).

 What I'd like to do is to have the subwoofer play only as the LFE channel: either without using 4.1, 5.1, 7.1 etc. or by combining the front and rear stereo channels to play only out of the front speakers. On my windows partition my motherboard's software allows me to do this quite simply, but I've fruitlessly searched on and off over the past year for this. Am I the only one with this problem?

---

### Post by CatKiller on 2013-04-22
I vaguely remember something about speaker mapping in the Pulse Audio config file, but I'm not at my computer to check. Don't 5.1 and 7.1 automatically bounce down to 2.1 without any fiddling, though?

---

### Post by alexm287 on 2013-04-23
They play as that, more or less, but the speakers drive less sound each. Pulse thinks it's driving through more speakers so it divides up the sound. Also, the main reason I'm interested in this is that it plays middle-tones and woofer tones in the subwoofer because it thinks its both the center and LFE channel, where it should only be playing the LFE channel.

---

### Post by CatKiller on 2013-04-23
From a quick search, I found [this tutorial]("http://confignewton.com/?p=211") on remapping channels that seems reasonably comprehensive. There are probably other good ones, too.

---

