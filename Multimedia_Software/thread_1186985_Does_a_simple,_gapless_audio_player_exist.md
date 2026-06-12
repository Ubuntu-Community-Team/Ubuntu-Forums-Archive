---
title: "Does a simple, gapless audio player exist?"
date: 2009-06-14
forum: Multimedia Software
---

### Post by BetterSense on 2009-06-14
I don't care if it's gui or command line. Command line would be fine. It just needs to play .flac gaplessly. Mplayer does not. 

Some people have a hard time with the concept of gapless....gapless means no gaps. None. At all. To the extent that I can listen to classical music without hearing ANY transition between tracks.

I used to use Amarok but I don't like Amarok 2 at all due to the UI. I'm trying to find something to replace it and not finding much.

---

### Post by cherva on 2009-06-14
well remove Amarok 2 and reinstall the old Amarok. ;)

---

### Post by BetterSense on 2009-06-14
Seriously, how can I do that?

---

### Post by cherva on 2009-06-14
[http://landofthefreeish.com/linux/how-to-amarok-in-ubuntu-jaunty/]("http://landofthefreeish.com/linux/how-to-amarok-in-ubuntu-jaunty/") Here is the tutorial how to add a PPA that has Amarok 1.4 for Ubuntu 9.04

---

### Post by hugmenot on 2009-07-27
Guys, if you want solid, real gapless give Quod Libet a try. You&#8217;ll have to [apply a patch]("http://code.google.com/p/quodlibet/issues/detail?id=49") from the bug tracker, because people haven&#8217;t gotten around to enough testing. But it works as it should.

[Lookit here]("http://www.alice-dsl.net/~towolf/img/ql-gapless.ogv")

---

### Post by TokyoYank on 2009-08-13
How did OP resolve the problem?

...

I searched "gapless" in Synaptic and found three contenders for GNOME:[LIST]
[*]gmpc  --  *had problems, couldn't connect to underlying player*
[*]Aqualung  --  *did play gapless, but super SUPER sluggish.  Delayed reaction controls*
[*]**Potamus  --  *works best for me***
[/LIST]Potamus is *very* plain jane, no frills (for example no cover art display), but that's fine for me.  Initial testing plays mp3 gapless fine

---

