---
title: "How can I find out what ports are blocked by a  firewall?"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by grs on 2008-12-02
Between my PC and the internet is a firewall which I have no access to. I think there may be more than one firewall.
Is there a tool/application I can use to see what ports are blocked by a firewall?

---

### Post by Kevbert on 2008-12-02
Try running [[COLOR="Red"]ShieldsUp[/COLOR]]("http://www.grc.com/") which is a good well-known online tool for checking ports.

---

### Post by WinterMadness on 2008-12-02
typically speaking port 139 and 23  is usually blocked by your ISP, 25 is common now a days as well

a lot of times, your router blocks ports. log into your router and find out

---

### Post by cariboo on 2008-12-02
If you have the ability to loop around the firewall, you can run a port scan on the external ip address using System-->Administration-->Network Tools-->Port Scan.

Edit: I'm not sure if the bug has been fixed yet, but you may get some false positives up in the higher port ranges.

Jim

---

