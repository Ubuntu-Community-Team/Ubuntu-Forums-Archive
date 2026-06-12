---
title: "DVD won't play. No errors, just nothing happens."
date: 2012-02-05
forum: Multimedia Software
---

### Post by scottbomb on 2012-02-05
Title pretty much sums it up. Running Xubuntu 11.10. I tried using SM Player and VLC. With both programs, the DVD drive spins up and then after a few seconds, it spins down. Nothing happens. No errors, no clues, nothing.

I know it's not a hardware problem because the same computer dual-boots with Windows 7 and plays DVDs just fine.

Any ideas?

---

### Post by inobe on 2012-02-05
has this worked before, if yes, what guide or steps did you use to get it working?

i have to know what you did in order to help you correct the issue.

---

### Post by scottbomb on 2012-02-10
I've never tried to play a DVD on this install. For what it's worth, it works fine with data DVDs. I can play .avi videos from a data-formatted DVD as well. But put a commercial DVD in, and it acts like it doesn't know what to do.

---

### Post by scottbomb on 2012-05-06
Fixed!

sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

---

