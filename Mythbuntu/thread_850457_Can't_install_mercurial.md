---
title: "Can't install mercurial"
date: 2008-07-05
forum: Mythbuntu
---

### Post by MikeB23930 on 2008-07-05
I am trying to compile the em28xx driver for the 2.6.24-19-generic kernel by following the instructions in post 53 of the thread at

[http://ubuntuforums.org/showthread.php?t=740473&page=6](http://ubuntuforums.org/showthread.php?t=740473&page=6)

When I attempt to download mercurial I get a dependency problem, more precisely

mercurial:
 Depends: mercurial-common (=1.0.1-2~hardy1) but it is not installable

Can some one please tell me how to resolve this?

In case it matters, I'm running an AMDX2 64 cpu.

Thanks

Mike

---

### Post by laga on 2008-07-06
Odd. mercurial does not depend on mercurial-support here. Are you running hardy? Maybe you need to run 'sudo apt-get update'.

---

### Post by laga on 2008-07-06
Ah, it looks like this is caused by the version of mercurial in hardy-backports. cjwatson processed it a few minutes ago and it should show up in a few hours or so.

---

