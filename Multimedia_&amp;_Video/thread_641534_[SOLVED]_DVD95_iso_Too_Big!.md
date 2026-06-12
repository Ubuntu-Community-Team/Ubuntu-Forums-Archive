---
title: "[SOLVED] DVD95 iso Too Big!"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by Spike-X on 2007-12-15
I've been trying to use this nifty lil' program to copy a commercial DVD (own copy, personal use, legal fair use, blah blah blah), making sure I use the 4.7 Gb option. However, no matter what I do, the .iso ends up too big to fit onto a single-layer DVD. The same problem happens with k9copy.

I've read about many other people having success with this program, so I'm sure it's just something simple I'm overlooking. The question is, what?

---

### Post by Craigus on 2007-12-15
Not the answer you are seeking, I know, but I have no experience with dvd95.

DVDShrink works fine however : [http://www.mrbass.org/linux/ubuntu/dvdshrink/]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")

---

### Post by Spike-X on 2007-12-15
I appreciate the suggestion, but if I wanted to use DVDShrink, I'd just boot into my Windows partition. I really need to learn how to do this using Ubuntu-only tools, as my next computer won't have Windows in any form.

---

### Post by ron999 on 2007-12-15
Hi

With k9copy.
Settings > Configure k9copy > DVD
Set the DVD size.

Mine is set to 4400mb.
(Because 4.7GB DVD-R discs are really 4.7GiB (NOT GB) which is approx 4.3GB).


:cool:[

Edit. I'm wrong about the GiB statement above.
What I should say is that the discs are measured in 1000 to the power of something and the computer thinks in terms of 1024 to power of something.

---

### Post by Spike-X on 2007-12-15
Fixed it!

I'd included the 5-channel audio track when ripping the disc. I removed that, and it got the size down small enough. I guess there's a limit to how much these programs can compress video.

---

