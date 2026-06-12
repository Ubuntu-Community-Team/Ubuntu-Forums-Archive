---
title: "New server can't ping on network, can be pinged, can't ping internet"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by bRobertson on 2011-01-09
Hi all.

I'm trying to set up a new server as a useful tool and overall linux learning experience. I've got 10.10 Server installed, since it's an old machine, and am hoping to set it up as a private file and web server.

Getting wireless networking right has been problematic. I managed to bootstrap myself into getting the card drivers installed, but I'm stuck: the server can ping our router, and other machines can ping my server. The server, however, can't get a ping response from the other (Windows) machines on our network. Further, it can't ping hosts on the Internet. Using a known-good machine to get the IP address of an Internet host and typing it in by hand works, but 'ping -Iwlan0 [www.google.com](www.google.com)', for example, yields 'unknown host [www.google.com](www.google.com)'.

To summarize: Windows machines can ping each other, and ping the server. Server can ping router, but not the Windows machines. Server can ping Internet hosts by IP address but not by domain name, so DNS is borked somehow.

How do I go about fixing either of these issues?

Thanks,
Bob

---

### Post by bRobertson on 2011-01-09
Progress and new data.

It turns out that the server I'm setting up is the only machine on our network that responds to ping. All the other Windows machines do not, regardless of whether the request comes from a Windows or Linux box.

Also I fixed the DNS issue; /etc/resolv.conf was pointed at 192.168.0.1, which doesn't exist on our network. However, 'ping [www.google.com](www.google.com)' takes some 100 seconds to service 10 ping requests. Is this normal?

Thanks,
Bob

---

### Post by PatchesTheCaveman on 2011-01-10
Windows Firewall, the firewall built-in to Windows XP and later, is configured by default to block *ping* and other ICMP requests.  

To unblock them, open an administrative Command Prompt.  To do so on Windows Vista and 7, press Start, type *cmd*, and press CTRL+SHIFT+ENTER.  On Windows XP, just go to Start > All Programs > Accessories > Command Prompt.

Then, run this command:
```
netsh firewall set icmpsetting all enable
```

---

