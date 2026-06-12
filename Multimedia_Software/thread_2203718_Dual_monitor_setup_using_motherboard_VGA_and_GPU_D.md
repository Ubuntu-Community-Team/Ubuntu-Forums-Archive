---
title: "Dual monitor setup using motherboard VGA and GPU DVI"
date: 2014-02-04
forum: Multimedia Software
---

### Post by vancinas on 2014-02-04
Hi, I'm trying to set up a dual-monitor system. I have a DVI capable monitor hooked up to my graphics card (Nvidia GTS 450), and I'd like to connect a VGA monitor as well. The graphics card doesn't have a VGA output though, so I have to connect it to the VGA port on my motherboard. This works in Windows just fine (after tweeking the BIOS and updating the VGA drivers). On Ubuntu though, only the DVI monitor works. The VGA monitor does not show up in the display settings.

The odd thing though is that, when starting the computer, the Ubuntu startup screen is displayed on the VGA monitor, but switches to the DVI monitor as soon as the login screen comes up. Same story when shutting down: the Ubuntu shutdown screen appears on the VGA monitor. The VGA monitor also does not show the "no signal" message while the computer is running; it's just blank, so it's obviously receiving some sort of signal.

So my question is, does anybody know how get a picture on both the DVI monitor and the VGA monitor at the same time? I know that I could order a DVI-to-VGA adapter and just use my GPU's second DVI-out, but I'd rather not do that if I don't have to. Any ideas? Thanks!

---

### Post by motorcity909 on 2014-02-07
Does the Nvidia X Server settings application detect both monitors?

Dave

[ATTACH=CONFIG]250169[/ATTACH]

---

