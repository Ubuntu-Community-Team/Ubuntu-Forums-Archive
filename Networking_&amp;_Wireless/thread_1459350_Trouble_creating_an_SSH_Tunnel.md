---
title: "Trouble creating an SSH Tunnel"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by x1a4 on 2010-04-21
Hi,

I need to browse the net more securely and bypass throttling by an infrastructure-dictator by creating a SSH Tunnel directly to my internet service provider and use it as proxy.  

I tried both a dynamic and local tunnel, was a able to connect to the server and log-in just fine, but when I tried to surf I get a 'Connection refused' error.  

Here's what I tried: 
```

ssh -D 8022 user@tunnel.host -N
ssh -L 8022:tunnel.host:8080 user@tunnel.host -N

```
(not at the same time of course)

Then I set 127.0.0.1:8022 as proxy in browser settings.  As long as the tunnel is open the browser displays a blank page with no error when I try to open a remote web page, while the terminal gives me a 'Connection refused' error. 

I'm using OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007 on Xubuntu Hardy.

In case anybody is wondering this is perfectly legitimate.  The tunnel.host I connect to is a server set-up by my ISP specifically for this purpose.  

Either of the examples above should work as others who have the same ISP reported that it works.  Therefore, I suspect this is an issue with my own security settings which are slightly on the paranoid side but I can't figure out what.  Stopping ufw and explicitly opening port 8022 didn't help.

---

### Post by x1a4 on 2010-04-24
Bump and some more info.  

I'm using OpenDNS services and thought that perhaps they might be the culprit as a proxy is part of the service.  So I removed the OpenDNS servers and reverted to my ISP's but this didn't help either.  

How can I diagnose the problem and find out what the deal is?  Please help.  Thank you.

---

