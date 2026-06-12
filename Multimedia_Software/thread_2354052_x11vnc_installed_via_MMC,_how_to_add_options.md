---
title: "x11vnc installed via MMC, how to add options?"
date: 2017-02-27
forum: Multimedia Software
---

### Post by jzig on 2017-02-27
I have the latest Mythbuntu iso (16.04) installed.  I have activated x11vnc server via the Mythbuntu Management Console.  I want to add the -repeat option to x11vnc so that the keyboard auto-repeat will work from the client (tightvnc viewer).

The problem is, that I don't know how the MMC is starting x11vnc.  It's not listed in "startup and sessions" and I can't find it anywhere else.  How do I go about finding how x11vnc is being started in Mythbuntu so I can add the -repeat option?
Thanks in advance.
Zig

---

### Post by jzig on 2017-02-27
Never mind.  I finally found it.  It's started from 
/usr/share/mythbuntu/session.sh
and I can add the -repeat parameter in that script and it works.
(although I don't know what calls that script?)

---

