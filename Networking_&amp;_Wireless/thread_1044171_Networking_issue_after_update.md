---
title: "Networking issue after update"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Remuria on 2009-01-19
I just used the update manager to install some updates for ubuntu, and after restarting networking is messed up. It claims to be connected to the wired connection, and my router confirms, but I am unable to connect to any computer on the network, or the internet.

This is with Ubuntu 8.10

---

### Post by mikewhatever on 2009-01-19
What's the output of <ifconfig> and <iwconfig>. Can you ping the router?

---

### Post by Remuria on 2009-01-19
I figured out the problem after reinstalling, when it happened again. One of the applications I had installed ipmasq.

I realized this when I was getting operation not permitted on pings.

All it took to fix it was sudo apt-get remove ipmasq

---

### Post by mikewhatever on 2009-01-19
Cool, thanks for updating.

---

