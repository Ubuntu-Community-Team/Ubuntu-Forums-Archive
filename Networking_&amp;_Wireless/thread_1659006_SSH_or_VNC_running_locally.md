---
title: "SSH or VNC running locally"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by sammiev on 2011-01-03
Hi Folks. :)

I'm only using SSH or VNC locally on the wireless and tested my firewall while using SSH or VNC. Firewall reports all ports are Stealth locked using GRC. So my question is then, do I need a VPN ( or something ) to run networking locally? If so, what do you recommend? 
Thanks :)

---

### Post by roton on 2011-01-04
If you're running the services then those ports will be open. The reason grc is telling you all ports are stealth is probably because you're going through a router to the net, so it's scanning the router ports.
If you want those ports available over the internet you'll have to forward them on your router. This is not required unless you want to access your pc from outside your own network.

---

### Post by sammiev on 2011-01-04
Thank you sir! I will only be accessing my network locally and not over the net. ):P

---

