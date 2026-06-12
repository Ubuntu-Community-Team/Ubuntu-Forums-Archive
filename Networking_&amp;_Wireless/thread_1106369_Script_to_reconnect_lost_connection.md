---
title: "Script to reconnect lost connection"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by xoroz on 2009-03-25
I wrote a simple script and added to cron every to check my internet connection every 5 minutes, and if the connection dosent work restart Network Manager. 
The script is this:
#!/bin/bash
ping -c 2 -w 3 google.com || /etc/init.d/NetworkManager restart

If I run from root it works fine, but during the cron it NEVER works because it gets an error with getting the KeyRing security.

Anyone has a similar script or have a solution for this ?

---

