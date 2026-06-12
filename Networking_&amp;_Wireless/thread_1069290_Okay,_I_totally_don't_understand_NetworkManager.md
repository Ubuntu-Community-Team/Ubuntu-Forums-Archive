---
title: "Okay, I totally don't understand NetworkManager"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by fedoraboy on 2009-02-13
I'm being stupid.  I'm being dense.

Here's the long story... skip to the end if you just want to see the question.

I set up wireless on my new laptop.  The first iteration, I just did it by hand, then folded everything into /etc/network/interfaces.  Worked like a charm.  (This is WPA1 if that is important to you.)  When I brought up the interfaces, they came up IMMEDIATELY.

Then I realized this config did not work with networkmanager.  In other words, things were not seemless.  Moving from wired to wireless and back required effort.  This is shared with the wife... and needs to be totally seamless.

So I started over... this time doing it with the NM gui.  After futzing with it for a while, it started working.  Then not... then working.  It took me a while to figure it out, but it appears as if with the NM setup the only way wireless works is if I connect wired -- then unplug.  Under no circumstances will it connect, for instance, immediately after a reboot with no tether.

What the hell am I doing wrong.  I'm not entirely sure even where to look to debug this.  My brain is config-file oriented and not gui oriented.

---

