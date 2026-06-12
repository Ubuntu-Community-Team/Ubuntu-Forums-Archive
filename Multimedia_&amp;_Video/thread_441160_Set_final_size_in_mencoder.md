---
title: "Set final size in mencoder"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by Nonno Bassotto on 2007-05-12
How do I ask mencoder to produce a file not bigger then a fixed size (for instance 700MB)? I do not care very much about all the options for quality, as long as they are reasonable and the output file has a given size.

---

### Post by protorox on 2008-04-19
You simply set the bitrate option to a negative number equaling the file size in Kylobytes.

Example:

To encode a file for an 800mb output size using Xvid::

```

mencoder inputfile.mpg -ovc xvid -xvidencopts bitrate=-800000  -o output.avi

```

---

