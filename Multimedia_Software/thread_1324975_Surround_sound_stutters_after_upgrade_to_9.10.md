---
title: "Surround sound stutters after upgrade to 9.10"
date: 2009-11-13
forum: Multimedia Software
---

### Post by Origin415 on 2009-11-13
Surround sound was working perfectly in 9.04, but when I upgraded to 9.10 it stutters horrendously. 

It seems the sound is bouncing back and forth between the speakers, for instance speaker-test -c6 rotates between different choices of two speakers to alternate between at maybe twice per second.

Setting it to stereo and 4.0 do not stutter but in both cases sound is only from the front two speakers. 4.1, 5.0, and 5.1 all stutter.

What could be the cause of this?

Thanks.

---

### Post by Soldeace on 2010-02-27
I'm interestingly experiencing the same issue with Ubuntu 9.10, but not sure if it worked properly in 9.04. My chip is a Realtek ALC850 (nforce4), which comes with the A8N-SLI SE motherboard.

I've just found setting up PulseAudio for 7.1 (although I've got only 5.1 actual speakers) works pretty decently with no stutters at all. It's the only trick that worked so far, although it's a solution much far from desirable. I really hope they fix things up next release.

Cheers!

---

