---
title: "Strange Firewire problem - 4250hd"
date: 2008-09-22
forum: Mythbuntu
---

### Post by c3rb3rus on 2008-09-22
I'm having a strange problem with my firewire cable box.  It is reproducible as follows:

- watch live tv times out, cannot get a signal
- run mythprime -v, all attempts fail
- unplug the stb, wait a minute, plug it in again
- after the stb reboots, run mythprime again - the first p2p attempts fail.  The subsequent broadcast attempts are successful and from then on, all p2p attempts are successful.
- i go to watch tv in mythfrontend - the video plays for about a second then freezes (i hear repetitive noises from my hd during this time - almost like its stuck in a loop)
- after this, mythprime fails again completely.

I should note that this setup has been functional before.  Firewire literally stopped working one day a month or 2 ago and I have not had a chance to troubleshoot until now.  I'm also able to prime and test on a channel that should be in the clear.  I assume that 5c encryption is not the problem because of that second or so of video that I see before things go to hell.

Specs:
STB: SA 4250HD
Kernel: 2.6.24-19-generic
Myth: .21
Mythprime: .55b

Thanks for the help!

---

### Post by volkswagner on 2008-09-23
When you unplug/plug in have you tried the other port?

Some boxes are sensitive on live swap of the cable.  It is best if you shutdown the pc, shutdown the cable box, uplug power cable to cable box, change port, than fire up the cable box (waiting for full boot), than power on the pc.

You may need to exchange you box with your provider.

---

### Post by c3rb3rus on 2008-09-23
thanks for the reply.  It turns out I solved this.

The problem was that the channel that myth was starting on was 5c encrypted.  It seems that the cable co just turned it on, since i know the channel was working before.  In any case, i switched the channel that myth starts on and managed to get everything straightened out.

---

