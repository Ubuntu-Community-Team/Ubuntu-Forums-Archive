---
title: "Must I now give up XMMS?"
date: 2008-04-29
forum: Multimedia Software
---

### Post by Beretta_NZ on 2008-04-29
I just installed the Hardy Heron. It's nice, I like.

But now I'm trying to install XMMS, my favourite MP3 player for Linux. But - wha? It doesn't exist, so it seems. It's not in my list of available programs.

I went to packages.ubuntu.com, but all I can find are plugins *for* xmms. Not xmms itself. I installed the package called "xmms core package," but to no avail. No new program appeared in my programs list.

So I tried the obvious: sudo apt-get install xmms2

Success - or so it seemed. The command line looked like it was installing the program. But when it was all done, still no new program in my programs list!

So what gives, is xmms no more?

---

### Post by kostkon on 2008-04-29
Yes, *XMMS* is obsolete and its removal from the repos was long overdue. A very good replacement is *Audacious*.

---

### Post by lbarnes on 2008-04-29
i installed audacious through synaptic
and ran it in terminal and it says
Segmentation fault
what does that mean?

---

### Post by Beretta_NZ on 2008-04-29
Does Audacious have an EQ?

---

### Post by Fenrisulf on 2008-04-29
You don't have to give up XMMS. I use it in Hardy. This may help you: [http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html]("http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html")
And don't install XMMS2, it has no GUI yet, it's a terminal based program.

---

### Post by Continuum on 2008-05-05
> **Fenrisulf said:**
> And don't install XMMS2, it has no GUI yet, it's a terminal based program.

XMMS2d itself will never have a GUI (it is intended to run as a daemon). But, fear not as there are already [many clients]("http://wiki.xmms2.xmms.se/index.php/XMMS2_Clients") written for XMMS2 if you want to use it.

---

### Post by MetalMusicAddict on 2008-05-05
> **Beretta_NZ said:**
> Does Audacious have an EQ?

It does but was broken just before Hardy's release. I'm working on getting this updated with a fix soon.

---

### Post by Lalapalooza on 2008-05-06
In the synaptic package under amarok, xmms-kde 3.2.2 is listed.  Is this the same xmms you guys are talking about or something different?  (Yes, I'm really new with this stuff).

---

