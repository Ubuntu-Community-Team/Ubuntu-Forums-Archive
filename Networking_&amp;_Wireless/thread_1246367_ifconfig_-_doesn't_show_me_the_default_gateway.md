---
title: "ifconfig - doesn't show me the default gateway?"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-08-21
Being with Ubuntu as long as I have you'd think I'd know the answer, but unfortunately... I don't.

I need to find out my default gateway, which I know what it is due to my Windows 7 VM being able to barf it out at me when I hit ipconfig on it, but I want to figure this out in Ubuntu/Linux/whatever.

How can I do this? Preferably in terminal.

---

### Post by Iowan on 2009-08-21
Check via **route -n** - default gateway should be on the last line.

---

### Post by edwardtilbury on 2009-08-22
ahh perfect thanks

---

