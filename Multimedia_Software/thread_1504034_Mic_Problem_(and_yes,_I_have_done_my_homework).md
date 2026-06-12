---
title: "Mic Problem (and yes, I have done my homework)"
date: 2010-06-07
forum: Multimedia Software
---

### Post by connor4312 on 2010-06-07
Running Ubuntu 10.04 LTS with 

I have a problem with microphone recording. I plugged in my microphone, opened Audacity (1.3.3 beta) (and I later tried this in Gnome sound recorder) and flipped through the input options. Nothing.

So then, I decided to switch to OSS. I did that just fine (sounds weem to play a lot better now!) but Audicy popped an "Error while opening..." thing. OK then, I tried going around a possible bug by creating a bymbolic link between /dev/pda (or whatever it is) and /dev/pda1 and 0. Thing time, I get strange little static that does not seem to come from the microphone at all, and I can't hear it played back. I decided to downgrade to the stable version of Audacity, where I am now, and still nothing. I get the same thing in Gnome sound recorder. I tried "ossrecord - | ossplay -" and nothing. I don't have jackd and installed audiooss and oss-alsa.

Help please!

---

