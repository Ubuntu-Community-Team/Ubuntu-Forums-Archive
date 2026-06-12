---
title: "Change network device name."
date: 2006-05-17
forum: Networking &amp; Wireless
---

### Post by denisesballs on 2006-05-17
How can I change the name of my network device eth1 to wlan0?

---

### Post by woedend on 2006-05-18
try editing /etc/iftab and changing it there(and naturally subsequently in /etc/network/interfaces).
It seems like it should work but it seems like I tried this a while back to no avail.  Please do follow up though.

---

### Post by denisesballs on 2006-05-18
Yeah it seems like that would work, but my current network device isn't even in there. It only has my old one.

---

### Post by denisesballs on 2006-05-27
Found the answer here - [http://ubuntuforums.org/showthread.php?t=139123](http://ubuntuforums.org/showthread.php?t=139123)

---

### Post by woedend on 2006-05-27
just curious as to if I'm skipping over something but - how is this different from what I had recommended?

---

