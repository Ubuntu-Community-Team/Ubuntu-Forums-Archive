---
title: "Banshee 1.x process keeps running after quit"
date: 2008-10-03
forum: Multimedia Software
---

### Post by samwisgg on 2008-10-03
To all banshee users,

I have the following problem since I began using banshee 1.x (first 1.0, then 1.2.1 and now the 1.3.1).

When I quit banshee (menu : media => quit), the application closes but the banshee process keeps on running (do a 'ps -ef | grep banshee' from command line).

I first noticed this when I quit banshee and it didn't restart after. Since the process was not killed, banshee wouldn't restart.

I already filed a bug at bugzilla and one of their developpers took a look at it but could not resolve the problem.

Now I noticed that F-spot also has a problem when you quit the application : it hangs.

So my (current) conclusion is that there might be something with mono (Banshee and F-spot both are mono apps) under Ubuntu (I'm running Hardy).

Anybody has the same experience with Banshee and/or know of this mono issue in Ubuntu Hardy ?

Even some solutions ... ? :D

If I notice more people have the same issue I'll open a bug in Launchpad.

---

### Post by blogsarticle on 2008-10-03
that's good.

---

### Post by samwisgg on 2008-10-03
> **blogsarticle said:**
> that's good.

Meaning ?:-?

---

