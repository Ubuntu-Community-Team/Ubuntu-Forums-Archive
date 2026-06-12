---
title: "SSH over internet.... what am I doing wrong?"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by adam.ec on 2010-04-13
I set up SSH on my office network. It has worked fine for the last three weeks. I suddenly discovered that I needed to access via SSH over the net too but I can't get it working.

My Ubuntu machine IP is set to 192.168.0.102 on the internal network (static) My routers internal address is 192.168.0.1 and the external we'll just say is xxx.xxx.xxx.x. The routers address is the same as that when I got to whatsmyip.com and check it there.

No when I used to log on with the internal network I would use:

ssh adam@198.168.0.102

Port forwarding has been set up on the router (default ports) according to the router manufacturers guidelines. How do I connect to this machine using SSH over the internet? It seems to me I need an ssh command that uses both xxx.xxx.xxx.x and 192.168.0.102 but I'm not sure how to put them together. If not, how do I get into this machine? ssh [email]adam@xxx.xxx.xxx[/email].x doesn't work, the connection just times out.

---

### Post by Iowan on 2010-04-13
> **adam.ec said:**
> ssh [email]adam@xxx.xxx.xxx[/email].x doesn't work, the connection just times out.If port forwarding is working correctly - that should work. You can verify your IP again - if you get DHCP address from your ISP, that may have changed. ISP might block port 22 (you might want to use different port anyway).

---

### Post by Maheriano on 2010-04-13
I'm going to assign you a dummy IP that will be used for the remainder of your troubleshooting in this thread: 199.188.7.6. Remember this.

Okay so your internal IP of your machine on your network is 192.168.0.102 and when you go to [www.whatismyip.com](www.whatismyip.com) from that machine you get 199.188.7.6. Awesome. Log into your router and forward port 22 to your local IP of 192.168.0.102.

This way when you access it from outside the network you'll type:
```
ssh username@199.188.7.6
``` This will connect you to port 22 on the router which will forward to port 22 of the correct machine and ask for your password.

I do it all the time.

---

### Post by adam.ec on 2010-04-13
Thanks guys, from what you've suggested it looks like my ISP must be blocking port 22. I will have to change it when I get back to my home-office in the morning. If I change the port and it still doesn't work I'll post back first thing in the morning.

---

