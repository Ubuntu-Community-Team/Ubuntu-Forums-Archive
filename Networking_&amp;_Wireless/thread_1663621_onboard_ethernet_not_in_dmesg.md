---
title: "onboard ethernet not in dmesg"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by tbridges42 on 2011-01-09
I've looked good and hard, and I'm pretty sure I've concluded my onboard ethernet is dead, but I'm open to ideas.

I've got a box a relative gave me. It says it's an eMachines d3107. It's gone through quite a line of previous owners, so I don't know if it's all stock or not.

The onboard ethernet, which google tells me should most likely be a VIA Rhine II, is not recognized by Ubuntu 10.04. Not just not recognized, but does not appear in netstat, lspci, or dmesg.

I can't check the BIOS right now because I'm currently headless. I can hook a monitor back up to it, but not tonight.

---

### Post by sj1410 on 2011-01-10
before considering it dead just check if its not disabled in BIOS.

i have seen VIA Rhine II driver problems in ubuntu and some got it worked using irqfixup boot options. you could try that.

---

