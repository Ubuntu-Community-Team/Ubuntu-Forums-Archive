---
title: "Exaile not downloading album art from Amazon"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Oobowo on 2009-08-27
Hi

My Exaile (ver 0.2.14) has started to give me problems when I request to find the covers for my albums. It tells me 'Sorry, no covers were found.' when I use the 'Fetch from Amazon' command.

It used to work perfectly until a week or so ago, I haven't changed Ubuntu versions either, still Jaunty. I've tried uninstalling Exaile completely, deleting ~/.exaile and reinstalling, but still same problem.

I've looked around and saw some people have had the same problems in the past, but it doesn't look like their solutions work for me.

Is it a case of Amazon having changed their API again? (as this has apparently happened in the past)

Please help if you can?

Thanks.

---

### Post by frigginacky on 2009-08-27
Amazon did it.

[https://bugs.launchpad.net/exaile/+bug/415852]("https://bugs.launchpad.net/exaile/+bug/415852")

The latest version of Exaile (0.3.0) will let you enter your own AWS key, or you could use the last.fm cover art downloading feature.

---

