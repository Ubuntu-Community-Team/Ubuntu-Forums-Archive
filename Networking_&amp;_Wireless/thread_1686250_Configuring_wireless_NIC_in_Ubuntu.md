---
title: "Configuring wireless NIC in Ubuntu"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by techkid on 2011-02-12
Hi all,

I am looking to reinstall Ubuntu on my desktop computer, in a dual-boot configuration. The system I am installing to should prove no hassle, but my biggest concern is my wireless card.

It's a D-Link DWA-510 wireless card. Checking the D-Link website, they do not seem to have Linux-specific drivers available for that model, so I am wondering if there are compatible drivers available in Ubuntu?

Thank you in advance.

---

### Post by FiggyG on 2011-02-12
It appears to use the Ralink RT61 chipset. The drivers for that are hit and miss as I've heard of wireless adapters working well on 9.10 then breaking in 10.04 (needing to be manually installed). Try it out and let us know if it works or not. Then we'll go from there. :)

---

### Post by gerowen on 2011-02-12
If it doesn't work by default, be sure to plug in an ethernet cable and check under System -> Administration -> Additional Drivers to see if there's any proprietary drivers Ubuntu has in the repos.

---

### Post by techkid on 2011-02-12
Thanks for the assist. On my next day off, I'll run the install and give it a shot. Here's hoping :)

---

### Post by techkid on 2011-02-14
Success! I have installed and am currently running Ubuntu 10.10. The best part was that it had no trouble detecting and running my wireless card.

Thank you to all for your assistance. Time to explore now...

---

