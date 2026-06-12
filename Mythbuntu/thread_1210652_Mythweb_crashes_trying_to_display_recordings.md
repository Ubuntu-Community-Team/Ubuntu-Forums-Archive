---
title: "Mythweb crashes trying to display recordings"
date: 2009-07-11
forum: Mythbuntu
---

### Post by stevecartermo on 2009-07-11
Mythweb crashes when I try to view the RECORDED PROGRAMS tab

the error message is

Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 71 bytes) in /usr/share/mythtv/mythweb/includes/mythbackend.php on line 190

It worked before but I guess as I got more recordings it stopped working. I just upgraded to a 1 Terabyte drive.

Any ideas how I could get it working again. The machine is and AMD64 and has 4 gigs of RAM, running MYTHBUNTU 9.04 64 BIT

Thanks

Steve

---

### Post by crez79 on 2009-07-11
This happens when php runs out of memory. It is a known bug check [here]("https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/141528") or [here]("http://ubuntuforums.org/showthread.php?t=992229") for solutions.

---

