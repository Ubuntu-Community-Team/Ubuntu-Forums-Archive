---
title: "Ubuntu Server to Desktop &amp; Network Manager"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by Mr.Macdonald on 2009-09-14
I installed ubuntu desktop via the server install and then installing the ubuntu-desktop package. It works well, just when I looked at network manager, it appeared to not be managing the network. all that appears upon left clicking is "Manual configuration" option.


How do I make network manager the used network managing system?

---

### Post by Iowan on 2009-09-15
Check */etc/network/interfaces*. Interface(s) are probably configured there (since that would have been server setup). Network Manager won't touch those configurations, so you can comment out all but the two "lo" lines. Restart services (or reboot) and see if NM has more options.

---

