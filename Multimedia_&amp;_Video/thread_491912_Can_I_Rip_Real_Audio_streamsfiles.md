---
title: "Can I Rip Real Audio streams/files?"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by dkaddict on 2007-07-04
Is it possible to rip Real Audio streams/files in Ubuntu Feisty?

I can rip streams through 'StreamTuner/StreamRipper' no problem. It would be nice to be able to rip all kinds of streams with a Linux application!

Am I suffering from wishful thinking?

Give thanks for any help.

peace

dk

---

### Post by flossgeek on 2007-07-04
Yes you can, and you use Mplayer on the command line to do this:- 

```
$ mplayer -dumpstream "<urlOfSteam>" -dumpfile <YourFileName>
```

Works in most cases but fails on some streams.

---

### Post by dkaddict on 2007-07-04
> **flossgeek said:**
> Yes you can, and you use Mplayer on the command line to do this:- 

```
$ mplayer -dumpstream "<urlOfSteam>" -dumpfile <YourFileName>
```

Works in most cases but fails on some streams.

Ok flossgeek,

Cheers for replying m8, I shall give your method a try soon. I hope it works with Real media streams. 

peace

dk

---

### Post by flossgeek on 2007-07-04
It does work on Real Streams, as I do it myself ;-)....

---

