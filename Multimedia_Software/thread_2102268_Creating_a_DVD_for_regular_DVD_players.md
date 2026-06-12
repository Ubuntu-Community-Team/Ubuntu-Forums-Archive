---
title: "Creating a DVD for regular DVD players"
date: 2013-01-06
forum: Multimedia Software
---

### Post by lykwydchykyn on 2013-01-06
I made a short video for my brother and want to send it to him on a DVD for playback on a regular DVD player.

I created it in DeVeDe and burned it to disc.  It plays back in VLC on my laptop, but won't play in either of my DVD players.  I'm concerned it won't play for him.

I made sure that it was set to NTSC (live in the US).  The disc in question is an 8x RW DVD+R.  Does that make a difference?  I know "back in the day" CD players wouldn't play back an RW disc, but I wasn't sure if that's the case with DVDs.

Anyone have an idea why my disc might be failing?

---

### Post by lykwydchykyn on 2013-01-07
LOL :)

Every time I post a question to this forum I end up answering my own question.

So, for posterity, apparently you need to **FINALIZE** a DVD+R for it to work in a regular DVD player, even if it's burned from an ISO.

The command to do this was:
```

growisofs -M /dev/dvdrw=/dev/zero

```

("Finalize" is apparently fancy speak for "write zeros to the remaining portion of the disc").

---

