---
title: "Network routing problem w/Ubuntu, not WinXP"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Kung Fu Hamster on 2009-03-04
I've noticed something a bit strange about my Internet connection: whenever I try visiting one specific site (including ping and traceroute), Ubuntu can't find it at all. When I try accessing the site in Windows XP. however, everything works perfectly fine. Ping returns a "Destination Port Unreachable" error, and traceroute only returns my network interface's IP address.

Does anyone have any suggestions?

---

### Post by Crafty Kisses on 2009-03-04
Can you actually access the site? I'm not sure but it could be an IPv6 site, have you checked that?

---

### Post by Kung Fu Hamster on 2009-03-04
It's a dating site called [www.luckylovers.net](www.luckylovers.net) (ip address 67.220.200.125)

---

### Post by Crafty Kisses on 2009-03-04
Do you have anything blocking certificates?

---

### Post by Kung Fu Hamster on 2009-03-04
Nothing at all. I even tried booting from an Ubuntu LiveCD, and get the same problem.

---

### Post by Crafty Kisses on 2009-03-04
Well try this, enter the following command:
```
cat /proc/sys/net/ipv4/tcp_ecn
```
If that returns "1" try replacing it with "0" so enter the following in Terminal:
```
echo 0 > /proc/sys/net/ipv4/tcp_ecn
```
Then see if you can access the website after doing that.

---

### Post by Kung Fu Hamster on 2009-03-04
cat /proc/sys/net/ipv4/tcp_ecn returns a 0 by default for me. Still no access.

---

### Post by Crafty Kisses on 2009-03-04
Here's a couple of things you can try, Call your ISP and see if they have port 80 blocked, and in some cases port 80 can be blocked on their servers. In some cases if that's blocked you're going to have some troubles with sites. It also could be a DNS issue, I'd say it could be your ISP doing work so try again tomorrow, unless you've had this issue for longer than a day.

---

### Post by Kung Fu Hamster on 2009-03-04
I thought that might be the case too. However, if I reboot into Windows I can access everything perfectly fine, as can every other computer on the network. It's just in Ubuntu that I have this issue.

---

### Post by Crafty Kisses on 2009-03-04
Yeah the website works perfectly for me anyway. Do you have any firewall settings on your router? If so try to disable them and see if you can access the website. It appears the website is hosted by GoDaddy, so try and see if you can even go on GoDaddy's website.

---

