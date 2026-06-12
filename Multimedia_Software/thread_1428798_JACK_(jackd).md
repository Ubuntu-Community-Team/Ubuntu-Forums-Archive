---
title: "JACK (jackd) ?"
date: 2010-03-13
forum: Multimedia Software
---

### Post by Beowulf.1000 on 2010-03-13
Do I need to install a special kernel to run jackd (JACK)? I am currently am using Karmic Koala (Ubuntu 9.10 x86 64bit) on an AMD 64 quad core with 8GB RAM. Just starting on a quest to get a system working capable of doing sound recording, midi recording and playback, music composition. JACK seems to be where it is at, but I recall reading somewhere that a special "real time" kernel is needed for doing this? If so, what kernel should I download and how would I install it?

I would be very grateful for any help on this, as this is a huge goal of mine. I recently got into music composition-- purchased Sibelius 6 (notation composition and playback) and Cubase 5 (sequencer), but I would prefer to do most of my daily work in linux including playing with music composition and sequencing. Thus my goal of getting JACK up and running and working with music composition linux applications. (found a really nice article on JACK this morning
  [http://www.linuxjournal.com/node/1004080](http://www.linuxjournal.com/node/1004080)

Thank you all in advance for any help on this!
 Beowulf

---

### Post by markbuntu on 2010-03-13
It really depends on what you are doing. If there is any live component to your work then the rt kernel is a must as it will reduce latency and buffer underuns and give your audio apps cpu priority. 

It is easy enough to install the rt kernel but you may also need to reinstall the nvidia or ati proprietary gpu driver if you are using one

sudo apt-get install linux-rt

This will install the rt kernel and make a new line in the grub menu so you can select it or the generic kernel from grub.

---

