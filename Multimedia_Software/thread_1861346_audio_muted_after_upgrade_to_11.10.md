---
title: "audio muted after upgrade to 11.10"
date: 2011-10-15
forum: Multimedia Software
---

### Post by someitalian123 on 2011-10-15
My audio is muted every time I start ubuntu after upgrading and it's annoying me. How do I fix it?

---

### Post by Ianman on 2011-10-19
I have the exact same thing...huh?

---

### Post by feeela on 2011-10-19
Same thing here. It doesn't matter how loud one turns the volume – it's always mute after startup.

---

### Post by collisionystm on 2011-10-19
Open terminal

Type

alsamixer

Any where you see a blue MM at the bottom of the bar you need to hit M on your keyboard to unmute it. Use arrow keys to move around and I think f6 to look at other audio devices ( I'm on my phone) lol

---

### Post by Kadai on 2011-10-19
For me, it worked to install and run 'pavucontrol' (from console), there i was able to notice that (K)Ubuntu has (misteriously) muted everything.

Also, I have the problem that whenever I stop to use one of the headphones jacks (unplug them), the sound volume of my speakers is not restored to is regular value... so you may need to keep at hand alsamixer too, whenever you use the jacks.

And yes, that last bug is pretty annoyning.

---

