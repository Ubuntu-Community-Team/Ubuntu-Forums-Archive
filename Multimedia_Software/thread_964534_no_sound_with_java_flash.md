---
title: "no sound with java flash"
date: 2008-10-31
forum: Multimedia Software
---

### Post by PeterRedford on 2008-10-31
I get sound with listen or watching movies anything but anything online I dont get any sound anyone have any ideas why, I have tried re installing flash but I have not done that for a few months I just booted up my old computer because I wanted to set it up on my tv.

---

### Post by Bender2k14 on 2008-10-31
Post some example links to content that does not work for you.

---

### Post by PeterRedford on 2008-10-31
youtube no sound.

---

### Post by Bender2k14 on 2008-10-31
That happened to me in 8.04 when I already was playing sound with another program, Rythmbox I believe.  Is that your problem?  Try closing all programs that are playing sound, including Firefox.  Then reopen Firefox and see if youtube sound works then.

---

### Post by PeterRedford on 2008-10-31
weird that worked.
did you figure out how to fix it so you didnt have to close whatever first?

---

### Post by Bender2k14 on 2008-10-31
Yea, I did...but it causes Firefox to "randomly" crash when loading pages with flash, maybe 10% (or less) of the time.  Let me find what I did...

---

### Post by Bender2k14 on 2008-10-31
Here is the [bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/252434") on that issue.

I see that my solution was to install flashplugin-nonfree.  In that case, you might as well install ubuntu-restricted-extras (which includes the flash plugin).

---

