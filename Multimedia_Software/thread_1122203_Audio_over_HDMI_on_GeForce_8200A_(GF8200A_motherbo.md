---
title: "Audio over HDMI on GeForce 8200A (GF8200A motherboard)"
date: 2009-04-10
forum: Multimedia Software
---

### Post by klingera on 2009-04-10
Hi, could someone please help me figure out how to get audio to go over HDMI with a gf8200a motherboard.
I am running Ubuntu 8.10

Thanks in advance!
Alex

---

### Post by ssricardo on 2009-04-12
Hi,

I just got the same problem here. I was working under ubuntu 8.10 but decided to go back to my origins and install debian, after a long while.

I have the same motherboard, by the way. In ubuntu the sound was working.
I don't know if it was high definition, but was working anyhow.

In debian it was "working" but crappier then hell. Wasn't possible to listen to it. So, I decided go for a search.

I compiled a new kernel, this time, with rt patch. But I must have done something wrong. Now the sound isn't working at all.
The alsamixer returns 

alsamixer: function snd_ctl_open failed for default: No such device or address

In a nutshell, I got the same problem as you: how to get sound working in a gf8200a motherboard.

---

