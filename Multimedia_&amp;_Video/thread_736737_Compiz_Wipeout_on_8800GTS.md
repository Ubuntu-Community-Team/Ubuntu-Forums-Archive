---
title: "Compiz Wipeout on 8800GTS"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by kooseefoo on 2008-03-26
I just recently purchased a brand new nvidia 8800GTS graphics card for my computer. I got it all installed, and used envy to make sure I was running the latest drivers.

Here's what's interesting - with my old nvidia 6800 card, everything worked fine. With this one, everything seems to work fine too, except compiz crashes on startup. I end up in the old plain jane desktop for (k)ubuntu. If I run compiz --replace& in a terminal, compiz comes back up just fine.

With nvidia-settings, I can confirm that my kubuntu recognizes the card and has the latest drivers. I've also tried running some pretty graphics-intense games and they work beautifully.

Any ideas?

---

### Post by kooseefoo on 2008-03-27
I hate this type of solution, but I woke up with morning and it was working fine.

Hm.


If anybody finds this via search, the only thing I can think of that might have done it is this:

Somehow, I wondered if envy had messed up compiz so it wasn't even trying to start. So, I did a reinstall of kde-compiz and some related packages (for gnome, they're called gnome-compiz or something). Problem solved.

---

