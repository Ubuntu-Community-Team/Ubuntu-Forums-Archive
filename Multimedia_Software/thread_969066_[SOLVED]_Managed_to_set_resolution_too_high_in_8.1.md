---
title: "[SOLVED] Managed to set resolution too high in 8.10, screen now blank due to out-of-r"
date: 2008-11-03
forum: Multimedia Software
---

### Post by ottokruse on 2008-11-03
Hi Everyone,

Well, I managed to set my screen resolution too high in 8.10. Now the signal is out-of-range to my monitor and I get a black screen. How can I change this back without GUI access? Probably some gnome setting I should be able to change (or delete) through a command line?

If only the resolution tool featured something like 'Keep this resolution click OK or it will be reverted in 15 secs' .... Sometimes I like monkey proof :)

Thanks!

Otto

---

### Post by ottokruse on 2008-11-03
All Right I got it solved...


There is a text file monitors.xml in directory ~/.config that contains your screen resolution. I just hacked it back to 1024x768 and that did it.

Otto

---

