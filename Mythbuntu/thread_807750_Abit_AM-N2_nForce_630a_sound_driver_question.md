---
title: "Abit AM-N2 nForce 630a sound driver question"
date: 2008-05-26
forum: Mythbuntu
---

### Post by +++ IGOR +++ on 2008-05-26
Hello, I have an Abit AM-M2 motherboard with nForce 630a chipset.
I was wondering if there exists a driver that works for this card. I was hoping to output audio either over the digital sound output or at the "line out" stereo jack plug.

I have a Gainward GeForce 8600GT graphics adapter (with HDMI) and I was hoping to output audio together with video over that cable but this is impossible as my reciever (amp) will not accept audio over HDMI in any format other than HDCP.

So my plan was to use either the digital sound output on the motherboard or the "line out" stereo jack plug.

Can anyone help me with this issue?

---

### Post by db260179 on 2008-05-26
Hello,

I have a Asrock NF7G Live board - similiar to your board.

To get digital sound out, set this setting in /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=6stack-dig

Hope this helps?

> **+++ IGOR +++ said:**
> Hello, I have an Abit AM-M2 motherboard with nForce 630a chipset.
I was wondering if there exists a driver that works for this card. I was hoping to output audio either over the digital sound output or at the "line out" stereo jack plug.

I have a Gainward GeForce 8600GT graphics adapter (with HDMI) and I was hoping to output audio together with video over that cable but this is impossible as my reciever (amp) will not accept audio over HDMI in any format other than HDCP.

So my plan was to use either the digital sound output on the motherboard or the "line out" stereo jack plug.

Can anyone help me with this issue?

---

### Post by +++ IGOR +++ on 2008-05-28
Thanks, Ill try it tomorrow. :)

---

### Post by Dewey_Oxberger on 2008-05-28
Hey,does that get you audio over hdmi?

---

### Post by +++ IGOR +++ on 2008-05-29
No, just (maybe) audio over an spdif output

---

