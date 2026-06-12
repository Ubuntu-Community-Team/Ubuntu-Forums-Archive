---
title: "Initial Setup of DNS server failed"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by dwanders on 2011-11-14
I am setting up a learning computer in Virtual Box. I have installed Ubuntu 11.10 and selected DNS Server from the Task Select during the initial install. All went well with the initial install. I changed my IP Address to Static (following the Ubuntu Server Guide) and then began setting up a DNS server for my small home network (Again following the Ubuntu server guide). The first thing the guide states to do is add your forwarders, then restart DNS, which I did and I get:

service bind9 restart
* Stopping domain name service... bind9
rndc: connect failed: 127.0.0.1#953: connection refused [OK]
* Starting domain name service... bind9  [fail]

So I kind of thought, well we really have not configured anything, so that does not seem too crazy, and contiuned on with the guide. Everytime I am being asked to restart bind9 I am getting the same message so the configuration is not progressing any further. 

So I tried to locate a log file to tell me why it was failing and cannot seem to find that either. 

Any guidance with this initial set up of a very small private home network would be greatly appreciated.

---

### Post by sum1nil on 2011-11-14
If the connection is refused, I believe there may not be an exception for port 953 in the firewall.

Try 'sudo ufw status' to see if the firewall is enabled.

If it is enabled, then disable it temporarily with 'sudo ufw disable' and run your command again to see if the connection is not refused.

Enable it again with 'sudo ufw enable' after you check.

---

### Post by dwanders on 2011-11-14
Well I think maybe it fails to connect because it was never running to terminate. But I tried you suggestion just the same, sudo ufw status

Status: inactive

This is a brand new install of 11.10, all I have done so far is set my IP address to static and installed DNS. I am following the Ubuntu Server to configure the DNS - but there must be something missing.:confused:

---

### Post by dwanders on 2011-11-14
Well shuck my nubbin folks - simply a matter of RIF apparently I got a ; in the wrong place and since I could not find the log (which I now know is /var/log/syslog - it was very easy to track down my typos. 

Sorry to have bothered!

---

