---
title: "Can I get the latest version of Shotwell in 10.04"
date: 2011-05-09
forum: Multimedia Software
---

### Post by xmrkite on 2011-05-09
Hello, This is more of a general ubuntu question, but for now it's specific to shotwell, the photo management software.

I'm running ubuntu 10.04 on one computer, 10.10 on another two and kubuntu 10.04 on a 4th computer.

I'd like to get the latest version of shotwell installed on each of those computers. That way I can share libraries among the computers and keep my pictures in sync with tags and events.

How would I go about doing that other than upgrading all the computers to 10.10. Is this something ubuntu can do or is this a downside of ubuntu?

-Thanks for any help provided.

---

### Post by Paddy Landau on 2011-05-09
It's on the Shotwell website.

[http://trac.yorba.org/wiki/Shotwell/FAQ#CanIrunShotwell0.9.0onUbuntu10.04LucidLynx](http://trac.yorba.org/wiki/Shotwell/FAQ#CanIrunShotwell0.9.0onUbuntu10.04LucidLynx)

---

### Post by xmrkite on 2011-05-09
Hello and Thank you.
That worked like a charm.

It's too bad that you have to resort to this kind of trickery though. It seems like i could easily get some sort of conflicting versions of other software installed as this required me to update about 20 other programs to newer versions.

It would be great if we could just install the newer version of the one program that is needed.

-Thanks

---

### Post by Paddy Landau on 2011-05-09
> **xmrkite said:**
> It's too bad that you have to resort to this kind of trickery ... this required me to update about 20 other programs to newer versions.
There's no trickery involved. You are simply installing the latest version.

The beauty of the repository system is that it always checks for dependencies, so you can be almost certain that the program will work. Hence the 20 other programs.

Canonical has a cut-off point for each release, after which it does not release upgrades except for security releases. The intention is to leave a stable system. You upgrade beyond the Canonical-provided releases at your own risk. Admittedly, it's a very low risk, but it's there anyway. The worst case scenario is to uninstall and revert to the official release.

BTW, please mark the thread as Solved.

---

