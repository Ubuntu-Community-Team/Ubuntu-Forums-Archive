---
title: "Problem configuring Audigy 2 zs"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by SandBird2 on 2007-08-21
I'm quite new to linux, at first i had no trouble with the sound/
Then after playing ac3 dvd the regular PCM had stopped working after few days of searching the forums I was able to configure it to work again using this:
pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}
howewer using this I'm only able to hear only 1 aplication and there some aplications that unable to connect to the alsa driver at all like VirtulBox.
It's been few weeks now and I've still haven't came with a solution so any help will be much apriciated.

---

