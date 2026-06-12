---
title: "Flash problems"
date: 2008-05-13
forum: Multimedia Software
---

### Post by ludicrous on 2008-05-13
I had flash working fine, but it stopped working consistently a couple days ago for no apparent reason.  For example, youtube videos will start to play fine for maybe half a second, then stop.

Sometimes they will play all the way through with no problems.
Sometimes if it didn't start but I drag the slider to somewhere in the middle it will play all the way through.
Sometimes it will crash Firefox suddenly without any warning.

I tried reinstalling libflashplugin-nonfree, no change.
Any ideas?

Thanks.

---

### Post by hermes0710 on 2008-05-14
What i have found as solution so far is disable from firefox the security options Tell me if... From that point on, i face no problem at all.

---

### Post by iaswni on 2008-05-14
Hey

I had the same problem with flash player and i can say it is really annoying. 
There seems to be some bug with flash player and pulseaudio that causes it to crash. 
There are a couple of things you could do, what i did was just delete libflashsupport and fixed my problem.

[I]sudo apt-get remove libflashsupport
[/I]
If that doesnt work for you or you dont have any sound when streaming, just go *[here]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox")* for alternatives.

good luck buddy! cheers

---

### Post by CJNyfalt on 2008-05-15
> **hermes0710 said:**
> What i have found as solution so far is disable from firefox the security options Tell me if... From that point on, i face no problem at all.

I had the same problem, and that fixed it. Thanks!

---

### Post by hermes0710 on 2008-05-15
Glad I helped :)

---

