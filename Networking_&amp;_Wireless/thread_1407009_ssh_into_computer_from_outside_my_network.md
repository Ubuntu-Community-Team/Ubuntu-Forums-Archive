---
title: "ssh into computer from outside my network"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by giantsfan7791 on 2010-02-14
Scenario: I have an old Dell desktop connected to my router. The router's a Linksys WRT54G with the Tomato firmware. The box has openssh-server installed and running on port 2222. I'm pretty sure the router's setup right, it has port 2222 being forwarded to 192.168.2.96 (the desktop), I have a Dyndns hostname being forwarded to that same internal IP, and I'm able to ssh into it from my laptop when I'm connected to this network. I also have my hosts.allow file to sshd: all: allow. However, I still can't seem to be able to access my desktop from any computer outside my network. Any ideas/links/tests to run?

---

### Post by bpalone on 2010-02-14
First I hope that you meant to say that your DynDNS was forwarded to your routers IP address, not the internal LAN address.  Then that you have your router forwarding port 2222 to your internal LAN address.

I just did this myself, so I could check on my server when out of town.  My router allows you to forward an odd ball port number to whatever port you want internally.  So, I picked an odd ball port number to use when calling home, with being forwarded to the standard port 22.

Now assuming that you have your router and server set up as described, try this:

ssh -p 2222 -l your_user_name_on_server xxx.xxx.xxx.xxx

your_user_name_on_server is whatever you set it up as, such as admin or fred

xxx.xxx.xxx.xxx is your routers IP address on the web

Hope this helps you out.

---

### Post by giantsfan7791 on 2010-02-14
> **bpalone said:**
> First I hope that you meant to say that your DynDNS was forwarded to your routers IP address, not the internal LAN address

How silly of me, this was the problem all along. Thanks mate.

---

### Post by giantsfan7791 on 2010-02-14
I seem to be having another problem. if I try ssh username@hostname from within my network I can get into the machine fine, but if I enter ssh [email]username@dyndns.url.org[/email] I keep recieving an "Access Denied" error at the password prompt. It can't have a different password set, any idea what it could be?

---

### Post by bpalone on 2010-02-14
Just for giggles, try the long way and see if it lets you in:

```
ssh -p 2222 -l your_user_name_on_server xxx.xxx.xxx.xxx

```
your_user_name_on_server is whatever you set it up as, such as admin or fred

xxx.xxx.xxx.xxx is your routers IP address on the web

If that gets you in, then you know you have it working, it is in how you are trying to get in.  Then try substituting domain name for the IP address and see if that gets you in. 

I just tried on my set up, using domain_name rather than the IP address and it got me into my system.  Note that the -l is a lower case L.

I am still learning this stuff, so I may not be getting you the best answer, but telling you what I would try.  Good luck.

Got me to wondering just how short I could go to get in, so I just did some experimenting.  I found that I could get by with this
 ```
ssh -p port_number user_name@domain_name
```

---

