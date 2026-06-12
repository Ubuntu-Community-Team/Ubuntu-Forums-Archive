---
title: "Cannot connect to one and only one website"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by geomcd1949 on 2013-03-18
Ubuntu 12.10

Strange problem. Have talked to both the website server company (1and1.com) and my own ISP (AT&T U-verse). Neither has a solution. Neither claims to have heard of the problem.

I can connect to any website except one. Everyone else I've talked to in the world can access the website that I cannot. 1and1.com says my IP address is not blocked. U-verse says there is no block on the website from the modem's internal firewall.

Also (I am the webmaster for this website) cannot connect to the website server (1and1.com) using FileZilla. Others to whom I've given the username/password for the account can access the server.

I can connect to other website servers  (e.g.,; GoDaddy) using FileZilla.

Flushed DNS; rebooted modem; restarted computers - no joy.

The output from running gksu gedit /etc/hosts is: 

127.0.0.1    localhost
127.0.1.1    george-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

My wife has a Windows 7 computer, and I cannot access the website using her machine, either. (The website is not listed as blocked on her computer.)

Any help is greatly appreciated!

~George

---

### Post by coldraven on 2013-03-18
The only, most unlikely, thing that I can think of is that you have fail2ban installed on your server. It has blocked your IP address by logging in with the wrong password too many times.

---

