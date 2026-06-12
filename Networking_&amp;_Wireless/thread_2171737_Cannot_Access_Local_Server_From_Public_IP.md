---
title: "Cannot Access Local Server From Public IP"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by Spirrwell on 2013-09-01
I know this isn't necessarily related to Ubuntu, but hopefully it will be okay to ask about this here. I recently got a new modem that's all in one with wireless and four Ethernet ports for simplicity. I wanted to host a server via LAMP, and I forwarded port 80 and whatnot, but I cannot access it using my public IP. I know that the port is forwarded properly as I can access it by using some random proxy on the Internet. I know I could access it with my public IP before using my old modem with a router attached to it. I've read about people having this problem, but I've only come across long complicated answers explaining why it is the way it is and not how to fix it exactly.

I'm sure there's a way to set it up in the modem, I just don't know how, but perhaps someone else is more knowledgeable. It's a Netgear 7550. I know I don't really need to be able to connect locally using my public IP, but I would like to be able to anyway so that way I can make sure everything is working. Whenever I host a game server I like to connect to it myself using my public IP to make sure that it's working properly, but with a game server, I'd have to find somebody to try and connect to it first as I wouldn't be able to use a web proxy in order to test it, and plus it just wastes time to check if a port is open using an online service to check it. Any help is greatly appreciated.

---

### Post by Thee on 2013-09-01
Well normally if you have setup port forwarding correctly it should work without problems. Did you consult with [http://portforward.com]("http://portforward.com/") on how to setup port forwarding correctly on your specific model?

---

### Post by scbingham on 2013-09-01
Do you have a static ip from your isp? If not, your public ip address would have changed, especially since you have disconnected & reconnected a new modem. You can see what you public ip is from within the modem.

I'd just ask someone outside of your network to to try, or use your mobile phone. Switch off wifi so it doesn't connect via your router, then it should connect via the phone network.

Hope that helps, it's what I do.

---

### Post by Spirrwell on 2013-09-01
I already said the port is forwarded properly, I could access it through a proxy, which means I could access it if I was on a computer outside of my own network. I just can't access it using my public IP from a local computer. It's some kind of DNS issue. Here, you could access my website as it is now [http://spirrwelltech.twilightparadox.com/](http://spirrwelltech.twilightparadox.com/) (If you want the IP just do a tracert of that address)

---

### Post by Spirrwell on 2013-09-01
Yes I have static IP.

Edit:
Sorry for the double post.

---

### Post by scbingham on 2013-09-01
You didn't double post. :-)
I've never managed to connect to/test my server via my dynamic address from inside my network, hence why I use my phone. The packets never leave my network, which I guess makes sense really.

Edit: It works fine, not many topics ;-)

---

### Post by Thee on 2013-09-01
> **Spirrwell said:**
> I just can't access it using my public IP from a local computer.

What about when you try to visit your site using the local IP address of your server?

---

### Post by steeldriver on 2013-09-01
AFAIK you need a router that supports (and is configured for) [NAT loopback]("https://en.wikipedia.org/wiki/NAT_loopback#NAT_loopback") [wikipedia] - not all do

---

### Post by Spirrwell on 2013-09-01
Ah, that was immensely helpful in pointing me in the right direction steeldriver. However the silly lack of documentation on this stupid modem is seriously making me want to throw it into orbit around the Earth. I believe it's truly a Westell modem 7500. I'm sure there's a way to set it up in the modem, I just can't figure it out. Perhaps if I could get my hands on the original Netgear firmware it would work better, but it's Frontier's. *sigh, if anybody has advice on the matter let me know.

As for you Thee, yes I can, I already said so. But, I want to be able to access any of my servers using my public IP.

---

