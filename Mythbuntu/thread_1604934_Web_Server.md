---
title: "Web Server"
date: 2010-10-24
forum: Mythbuntu
---

### Post by Tteddo on 2010-10-24
Hello! I have decided that I want to use my MythTV box as a web dev server (since it's a quad core that is just sitting there most of the time) but upon checking it out I can't seem to remove the autoforward that Apache does when you access the IP Address of the server, i.e it always forwards to the mythweb site. How can I remove that forward so I can use the IP address for my sites, but still access mythweb like so:
[http://192.168.0.156/mythweb?](http://192.168.0.156/mythweb?)

---

### Post by tgm4883 on 2010-10-24
dpkg-reconfigure mythweb

---

### Post by Tteddo on 2010-10-24
> **tgm4883 said:**
> dpkg-reconfigure mythweb

Well, that was blindingly obvious! Thanks!

---

### Post by Tteddo on 2010-10-24
Can I ask how it was doing that? I didn't see it in the apache config files. All I saw was a link to the Mythweb director in usr/share.

---

