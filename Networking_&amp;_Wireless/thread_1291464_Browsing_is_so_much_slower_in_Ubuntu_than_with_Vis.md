---
title: "Browsing is so much slower in Ubuntu than with Vista"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by RedMartin on 2009-10-14
For approximately the last two months my browsing experience has been very slow. Pages take ages to load and stuff like Youtube clips are unwatchable.

I've tried all sorts until the other day when I decided to see what it was like on Vista. Very fast. Switched back to Ubuntu and it was slow.

I'm using Firefox on both. Ubuntu is 8.10 and fully updated. I've looked at the DNS servers and they match. I've switched IPV6 off. I've run numerous speedtests which all report that I should be having a fast browsing experience. The reality if the FF through 8.10 is so slow I'm seriously considering switching back to Vista. 

I've used Ubuntu for about a year and really like it but this is a deal-breaker if I can't fix it. Was there a major update about two, maybe 3 months ago that has caused some kind of problem?

---

### Post by yeats on 2009-10-14
> I've used Ubuntu for about a year and really like it but this is a deal-breaker if I can't fix it. Was there a major update about two, maybe 3 months ago that has caused some kind of problem?

That seems to indicate that it *used* to be faster...?

If you've added add-ons/extensions, it may be one of them (or a conflict between two or more add-ons).  You can easily test this by closing any open firefox sessions, opening a terminal, and typing:

```
firefox -safe-mode
``` 

which will disable any add-ons.  If things move faster, you'll know where to look.

Otherwise, there are *many* "speed up firefox" posts on the web, and if you're brave, you can install FF3.5 using [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page"). (which I've used without issue).

---

### Post by RedMartin on 2009-10-14
You're spot on about how it was faster. I've not added anything to Firefox for months. I'll give the safe-mode a try though.

---

### Post by WinterMadness on 2009-10-14
try epiphany-browser

its basically firefox without all the freezing

---

### Post by RedMartin on 2009-10-15
> **WinterMadness said:**
> try epiphany-browser

its basically firefox without all the freezing

I've tried it and it's also subject to slowness with my current problems. As Swiftfox suffers too I'm guess that the 'dodgy' add-on route may be a dead end.

---

### Post by RedMartin on 2009-10-16
Right. I've tried safe mode, Epiphany, Swiftfox and updating to FF3.5

Still much slower than FF3.5 in Vista! I'm stumped. 

Any more suggestions?

---

