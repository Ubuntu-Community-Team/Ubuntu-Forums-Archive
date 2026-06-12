---
title: "samba share stopped working?"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by knottshawk on 2009-12-16
I had a samba share setup to share my 8.10 machine to two Windows machines. Seemingly randomly today it suddenly stopped working. Now when I try to connect from a Windows box it says "An error occurred while reconnecting U: to \\192.168.0.12\share Microsoft Windows Network: The network path was not found."

How do I fix this?

EDIT: As I stated below, it was a conflict that occurred due to removal of firestarter. I solved it by reinstalling firestarter and just setting policies appropriately.

---

### Post by knottshawk on 2009-12-16
Ok... I've narrowed it down... if I 
```
sudo ufw disable
```
then it works again... I previously had firestarter installed, but removed it awhile back. Do I need to reinstall and configure firestarter to allow my samba connections?

---

### Post by Iowan on 2009-12-16
UFW should also work - there's a GUI for it (gufw), if you'd prefer (should be in repos).
UFW continues to evolve - [Here]("http://swik.net/Ubuntu/Planet+Ubuntu/Bodhi.Zazen:+Firewall+Ubuntu+Desktops/dbixv") is one article, [here]("http://ubuntuforums.org/showthread.php?t=823741") is another.

---

