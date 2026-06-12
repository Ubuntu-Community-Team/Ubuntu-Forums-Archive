---
title: "Fix: broken networking with broadcom BCM43228 and 13.04 (fully up to date)"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by chinamusic on 2013-07-03
After wrestling with this for a while...

On my brand spanking new Dell Latitude 6430, I couldn't get a fresh Ubuntu 13.04 install + all updates to recognize the wireless network adapter.  I finally determined that it was using the BCM43228 chipset by using lspci.  I plugged into an ethernet port and then did:

apt-get install bcmwl-kernel-source

and shazaam!! the wifi sprang to life.

Thought this might help out some other unfortunate soul.

Best,

---

