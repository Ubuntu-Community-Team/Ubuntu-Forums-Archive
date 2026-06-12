---
title: "network card not found after update"
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by HaQDaQ on 2006-01-12
(Using Ubuntu Dapper)
When I came back from Austria two days ago, I did a massive update (apt-get dist-upgrade) with a lot of new stuff, including a new kernel. After the reboot, gdm did not work anymore. I figured this was due to the ati drivers needed a recompile. But my network also doesn't work anymore. I checked the modules with pcimodules, 8139cp and 8139too are loaded, I have a 8139 network card.
But if I try to do 'ifconfig eth0 up' as root, I get the error:
"eth0: ERROR while getting interface flags: No such device"

I searched in the forums for a solution, but couldn't find anything. In windows my network still works fine, so it's a software/driver problem.

---

