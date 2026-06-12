---
title: "HP 8440p Compatibility Report - All Good Except Black Screen on Wake"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rebootme on 2010-09-14
In 10.4 everything worked except the buttons to control screen brightness.  They work!

But now when I wake from sleep I get a sad black empty screen.

Note this is an upgrade from 10.4.  To do the initial install of 10.4 I did have to add "nosplash nomodeset" to grub to force basic video (see [http://blog.triumphovermadness.com/2010/05/ubuntu-1004-lts-on-hp-elitebook-8440p.html](http://blog.triumphovermadness.com/2010/05/ubuntu-1004-lts-on-hp-elitebook-8440p.html)).  Otherwise you get a screen full of garbage.  I'll pop in a CD and post the results for 10.10.

---

### Post by rebootme on 2010-09-14
I tested it and it is still broken.

If you boot the 8440p with an nvidia card from the CD all you get is a bunch of crazy lines all over the screen.

It does work when attached to an external monitor.

I'll file a bug report.

---

### Post by krazyd on 2010-09-16
Interesting, I've got the intel integrated graphics 8440p. Good to hear the brightness buttons work now.

In 10.04 I've never been able to get Suspend/Hibernate to resume properly (black screen on resume). I'll have to try 10.10 and report back.

---

### Post by rebootme on 2010-09-18
The display now comes out of sleep properly after the latest round of updates!

---

