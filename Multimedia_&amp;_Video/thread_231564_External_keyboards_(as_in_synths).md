---
title: "External keyboards (as in synths)"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by morganpatrick on 2006-08-07
Hello,

I am running Dapper. I have a KORG Triton and I would like to know how to get Ubuntu to control it. I looked at Ubuntu Studio and saw a lot pertaining to software synths, But I don't really need a software synth. I just want to stor my midi sequences on my computer and play them back through my synthesizer. I have an m-audio midisport 4x4 and the driver is installed; however, When I go to a sequencer, like seq24, I can't get any sound. When I use the onboard keyboard I don't hear anything out of my synth either. How do  I connect my synth to Ubuntu?

Thanks.

---

### Post by Pocadotty on 2008-01-20
I'm not sure about a Triton, though this interests me as a band mate of mine has one, and at some point I would like to hook things up.

Firstly are you using JACK, if your not, you should be.

Secondly, instead of using seq24, try out rosegarden, it is a fairly comprehensive studio program and works great with JACK.

Thirdly, with the jack server running, make sure there is a midi connection between rosegarden(or whatever else you choose to use).  If you don't know how to do this, try using the program Patchage, which is a graphical way to manage JACK connections. Your midisport should show up on there and therefore give you a way to connect it to the programs you want to use.

Try that and let me know how it works, or fails to work.

---

