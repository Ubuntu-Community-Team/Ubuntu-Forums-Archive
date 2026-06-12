---
title: "&quot;You Must Have Root Privileges&quot; to start Firestarter."
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by AlphaMack on 2006-04-26
I had Firestarter turned off, but upon logging in I received a strange message that I needed root privileges to turn on Firestarter, even though I did not launch the program.  How do I resolve this issue with permissions?  Perhaps this could be the culprit of [my](http://www.ubuntuforums.org/showthread.php?t=165731) [ situation?](http://www.ubuntuforums.org/showthread.php?t=165584)

---

### Post by lucia_engel on 2006-04-26
Check Preferences > Sessions
See if there's an entry in the startup tab like "sudo firestarter" or "gksudo firestarter". You can delete the entry if you don't want firestarter to startup when you log in.

If there's no entry, then maybe there's a CLI way you can check, but I'm not sure.

---

