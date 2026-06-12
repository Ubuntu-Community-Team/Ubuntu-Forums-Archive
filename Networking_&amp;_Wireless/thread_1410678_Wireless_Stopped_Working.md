---
title: "Wireless Stopped Working"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by fedfan on 2010-02-19
Dear All,

I am new to Linux world. Facing a really strange problem.

Here are the details.

- Running Ubuntu Netbook Remix 9.10 on USB Disk
- Wireless Internet Was Working Fine
- All of a sudden Internet is down - Checked if connection is available if IPs are available. Everything is fine but still cant connect to internet.
- Restarted and tested the network in Windows XP - works fine
- Switched back to Ubuntu Netbook Remix 9.10 - Can find networks, can connect to networks, signal strength is 'very good', ip,dns etc is avilable but still cant connect to the internet.

Have tried few options in various forums without any success.

Your help is very much appreciated.

Thank You.

---

### Post by cariboo on 2010-02-19
Can you ping [www.google.com?](www.google.com?) Go to System-> Administration-->Network Tools, click the Ping tab and enter [www.google.com](www.google.com) in the Network Address text box then click the Ping button. If that doesn't work, enter 74.125.53.106 in the Network Address text box and click Ping again. If you can ping by number, but not by name, you have a DNS problem.

---

### Post by trueno_ray on 2010-02-19
As u said everything is fine if boot to xp, so the router is ok, right?
So, 
1. Can u get ip from router, can you ping your router in ubuntu?
2. Use wire cable connect to the router, can go internet?
3. Any security application block? e.g: selinux, iptable, firewall you installed.....

---

