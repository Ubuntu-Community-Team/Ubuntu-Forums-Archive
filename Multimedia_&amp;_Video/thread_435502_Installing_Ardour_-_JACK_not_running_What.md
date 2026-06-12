---
title: "Installing Ardour - JACK not running? What?"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Fireblend on 2007-05-07
So I'm really interested in trying out Ardour. I installed Ardour-GTK from the Universe repositories, but when I run it, I get an error message saying JACK is not running... is JACK not included with Ardour? What packages should I install to get it running? I got jackd, but it didn't help. I just want to try Ardour out!

Thanks in advance!

---

### Post by forsaken_pariah on 2007-05-07
I had the same problem and the only way I found to fix it was installing the qjackctl package and starting the jack daemon from there. There's probably an easier way but I haven't found it.

---

### Post by Fireblend on 2007-05-07
> **forsaken_pariah said:**
> I had the same problem and the only way I found to fix it was installing the qjackctl package and starting the jack daemon from there. There's probably an easier way but I haven't found it.

Thanks! That worked, now it's time to play around with this, looks a little too complicated for me, but what the hell, I'll have fun exploring it :p

---

