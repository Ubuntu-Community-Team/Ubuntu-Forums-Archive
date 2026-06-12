---
title: "strange screen wont show through remote control"
date: 2009-03-22
forum: Multimedia Software
---

### Post by talkingtree on 2009-03-22
ok, so i tried remote controlling my computer1 with computer2

computer1 works fine and computer2 can do remote controlling when computer1 got a monitor attached to it. now when i restarted computer1 without a monitor and tried using computer2 to remote controlling, computer2 says that monitor cannot be displayed?

so the question is how do i overcome this?

also, in theory, if i got a video card, and got computer1's RCA connected to the tv's RCA, tv should display right? somehow it shows nothing:(

---

### Post by tr333 on 2009-04-15
Try looking in one of the Xorg log files in /var/log (Xorg.log, Xorg.0.log, etc.).  The video driver might be shutting down the GUI part of the system (X window system) when fails to detect any monitor connected to the graphics card.  If this is the case, then the only solution would be to have a monitor of some sort attached to the computer (even if the monitor is never used).

There might be a way to prevent this from happening, but I don't know of any.

---

