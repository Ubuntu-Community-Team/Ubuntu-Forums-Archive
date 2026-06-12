---
title: "Open Local Apache2 server to non-local access"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by Peptid on 2013-08-12
Dear All,

I have a problem which I believe easy rather easy to be solved; however I am very new to these networking stuff.

I installed Apache2 server on my laptop and then installed wordpress in it. Now, I can access the website I am building from my own computer. On the other hand, I want to access the website outside of my local area network; that is I want to access my server from any other computer around the world.

I have tried to play with NAT settings of my router but so far it seems I couldn't succeed. 

Is there anyone who knows how to open access your local server to non-local access?

I am using Kubuntu 12.04, if it will make any difference.

Cheers

---

### Post by newbie-user on 2013-08-13
You need port forwarding on your router to send port 80 to your laptop.

---

### Post by Peptid on 2013-08-13
Thank you. 

I did it right away.

I got my local address from ifconfig command, and forwarded port 80 to this local ip address. For the first time I managed to connect outside of LAN.

But, when I enter the ip address of mine, I am directed to routers admin page, rather than the html page I've created. (I enter routers admin page through 192.168.2.1 and my laptops local ip is 192.168.2.2)

---

### Post by newbie-user on 2013-08-13
Port forwarding goes from the WAN to the LAN. So you'd have to access your public IP, and your router would then port forward to your webserver. If you just enter the private IP of your router (192.168.2.1), you'll be taken to the router's admin page.

---

### Post by Peptid on 2013-08-13
Nope, I enter my public IP to browser which is outside of LAN and I am directed to router's admin page which is 192.168.2.1, although I entered 192.168.2.2 at NAT settings.

---

### Post by newbie-user on 2013-08-13
You'll probably have to disable remote administration on your router, or set remote administration to run on https only. It's safer that way anyway. You don't want to be passing your password over an unencrypted http session.

---

