---
title: "Programing Bind with Ports for Multiple sites"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by kf7ldr on 2013-01-07
I am attempting to setup a Windows Web-Server with multiple sites running off it.  I am completely new to linux. I am using Ubuntu Server 12.04 with Bind 9 for DNS. My site kf7ldr.com is setup up with GoDaddy as well as 2 other sites 111.com and 222.com. Ubunu Server is setup as my nameserver ns1.kf7ldr.com.

Documentation I found states that I need to do the following on the Windows Server to have multiple sites:
Webserver - IIS - Server - Sites -

kf7ldr - bindings - type: http, host name: kf7ldr.com, port 80, ipaddress: 123.456.789.012

111 - bindings - type: http, host name: 111.com, port 81, ipaddress: 123.456.789.012

222 - bindings - type: http, host name: 222.com, port 82, ipaddress: 123.456.789.012

------
I am trying to get ubuntu server to recognize the ports. Right now I just have kf7ldr.com programmed. I will get the aliases for the other sites programmed in once i can get kf7ldr.com to function.

---
I do have a static IP from my ISP and I programmed my firewall to transfer any DNS requests to my ubuntu server.


Thanks ahead of time for any assistance in this.

---

### Post by chadk5utc on 2013-01-07
KF7LDR see if this helps a bit.
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

73

---

### Post by kf7ldr on 2013-01-07
Thanks Chad for the insite.  I will give this a shot and see where it gets me.

---

