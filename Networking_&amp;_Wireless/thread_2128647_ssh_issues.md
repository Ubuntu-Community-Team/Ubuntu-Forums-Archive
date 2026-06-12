---
title: "ssh issues"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by tabarnak on 2013-03-23
I can ssh into most places from the home computer, but not to one important location. However, I am able to ssh into that important location from any other machine. This is incredibly frustrating since I have to connect to another computer just to ssh into the location, which means lots of lag. ssh -vvv doesn't show anything of note, just a time out. It would be great if anyone can help me resolve this issue.

This problem occurs across each of the OS installs on my home computer, so perhaps my MAC address has something to do with this?

---

### Post by LeDieu on 2013-03-24
MAC address is very unlikely. Sounds more like a firewall is blocking your connection.
Check first if your connection is actually reaching your "important" system. You can test this via
```
sudo tracert -T -p 22 <ip-important-system>
```
The last ip in the list should be your "important" system.

---

### Post by papibe on 2013-03-24
Hi tabarnak.

The situation you describe, and without any more details, sounds like there's restricted access based on IP range. Which it is not too uncommon for an "important" place.

Could you give us more details?

Regards.

---

