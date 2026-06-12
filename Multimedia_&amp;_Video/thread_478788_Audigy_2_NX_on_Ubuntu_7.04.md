---
title: "Audigy 2 NX on Ubuntu 7.04?"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by th0r0n on 2007-06-19
Has anyone managed to get this card installed?

I keep finding different guides everywhere but I don't really understand what they are telling me to do?

It's an external USB card, if that helps.

Any ideas on how to get this working please guys?

Thanks,

T

---

### Post by gredondo on 2007-06-19
Well, this is my first post as I began with linux seriously one week ago (holidays). I hope this is helpful.

Most probably your sound card, as my USB Audigy 2 NX, is working. The matter is that the default card is the on-board one, so this is what you have to do:

      sudo asoundconf list                            (with this you will see that your card is called simply NX)

And finally:

     sudo asoundconf set-default-card NX


That's all friend!

---

### Post by th0r0n on 2007-08-20
Still never managed to resolve this, has anyone ever got this working?

T

---

