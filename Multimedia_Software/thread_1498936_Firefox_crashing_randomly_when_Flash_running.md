---
title: "Firefox crashing randomly when Flash running"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Superluke on 2010-06-01
I've (finally) got the 64-bit Flash driver installed and working, but now I get an illegal instruction when I run a flash operation (video, game...) at a random point while it runs.  I see this in the terminal:

```
(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead
Illegal instruction

```
and it just quits. :|

---

### Post by lovinglinux on 2010-06-01
> **Superluke said:**
> I've (finally) got the 64-bit Flash driver installed and working, but now I get an illegal instruction when I run a flash operation (video, game...) at a random point while it runs.  I see this in the terminal:

```
(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2108): Gdk-WARNING **: XID collision, trouble ahead
Illegal instruction

```
and it just quits. :|

Check if you have libmoon installed and remove it.

I presume you still have FLASH-AID installed. If the above doesn't help, then run FLASH-AID again and install the 32bit version of flash. Restart Firefox and check if the problem persists and if you can pause and interact with an YouTube video. I usually recommend the 64bit version of flash, but if the 32bit doesn't crash and doesn't exhibit the interaction issue, then is better to stick with it.

---

