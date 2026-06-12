---
title: "Lost wireless"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by Hal85 on 2011-11-22
I am using Ubuntu 11.10 from a flash drive. It has worked great for me so far, but today the internet stopped working. It says I am connected to the public wifi I use but it doesn't work. I can connect on my windows computer just fine. Any ideas of how I can fix this?

This same thing actually happened to my windows computer. I ended up finding a solution listed in the microsoft ask website. All I had to do was add a "preffered DNS server" under the IPv4 Properties. I couldn't figure out how to do this in ubuntu.

---

### Post by ajgreeny on 2011-11-22
I have shown two screenshots for my eth0 connection but it will be the same for your wireless.

The first shows where you change to Automatic (DHCP addresses only) and the second shows where you put your preferred DNS server, eg 8.8.8.8 for google public DNS server.  Then restart you network and it should be good to go.

---

### Post by Hal85 on 2011-11-22
Perfect!
Thanks for the help

---

