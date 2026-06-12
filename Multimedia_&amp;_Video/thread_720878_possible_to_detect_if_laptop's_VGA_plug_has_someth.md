---
title: "possible to detect if laptop's VGA plug has something in it?"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by thebigkevdogg on 2008-03-10
Hi all, I have a Lenovo Thinkpad T61 which I plug into a 22 in widescreen monitor when at work (same as laptop screen's native resolution, 1680x1050). In my attempt to easily switch between the internal and external display I made 2 xorg.conf files, 1 for each setup.

If I want to switch to the external monitor, I just run a command with sudo which swaps the conf files and then restart X. My GDM shutdown script automatically puts the internal screen's xorg.conf script back in on shutdown or restart. If I have to manually kill the machine, then I have to just run my script to switch them back. Now that I think about it, maybe I should make it a startup script to avoid that problem.

Now, for my real question: is there any way to detect if the VGA cable is plugged in during startup (BEFORE X STARTS), to then automatically install the necessary configuration file? Will the output of any command be different when it's plugged in (so that I could write a little script to check it)?

Thanks a lot!

Kevin

---

