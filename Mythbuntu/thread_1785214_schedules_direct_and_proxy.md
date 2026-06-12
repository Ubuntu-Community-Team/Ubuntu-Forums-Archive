---
title: "schedules direct and proxy"
date: 2011-06-18
forum: Mythbuntu
---

### Post by sciguy125 on 2011-06-18
Is it possible to get mythfilldatabase to go through a proxy to download from Schedules Direct?  I couldn't find any settings for it.

---

### Post by ian dobson on 2011-06-18
Hi,

I think you just need to tell userspace to use a http proxy.

Just try from the terminal:-

export http_proxy=proxyip:port

where proxyip:port is the ip of your proxy and port is the port number.

After rebooting the setting will be gone, so if it works add the command to /etc/rc.local

Regards
Ian Dobson

---

### Post by sciguy125 on 2011-06-19
Any ideas on how to set it ONLY for mythfilldatabase?  There used to be something in the setup, but it seems to be gone now (or I can't find it anymore).

---

