---
title: "PulseAudio &quot;enabled by default&quot;?"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by johannes123 on 2008-04-06
> from [http://www.ubuntu.com/testing/hardy/beta#head-ef5f51ac1766db2be9f025f57fa9e0d3b8e35871](http://www.ubuntu.com/testing/hardy/beta#head-ef5f51ac1766db2be9f025f57fa9e0d3b8e35871)
PulseAudio is now enabled by default. Some non-GNOME applications still need to be changed to output to pulse/esd by default and the volume control tools are not yet integrated.

Oh no. I have some really bad memories about esd... It did some annoying things like breaking sound and eating up (then) precious CPU time, and it was impossible to remove because of package dependencies (this wasn't ubuntu though, i think it was debian). I remember doing something like ">/usr/bin/esd" in the end as a "workaround"...
I hope it will be easy to disable PulseAudio in 8.04, or better remove it completely? Packages won't be "changed" to be dependent on it at compile-time will they?

I know the feature list sounds quite impressive... But there may be times when you dont want it, when it messes things up...

---

