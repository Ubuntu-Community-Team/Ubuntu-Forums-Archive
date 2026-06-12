---
title: "changing apache port"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by darylp on 2010-05-28
I'm trying to change the port that apache listens to 8080. I changed it within /etc/apache2/ports.conf. When I enter myip:8080 within a web browser, it forwards to correctly. The problem I'm having, is when I enter my ip without an alternate port, it goes to my router's login prompt. Port 80 is not being forwarded. Is there anything in the configuration to block port 80 completely?

---

### Post by vandorjw on 2010-05-28
Did you forward port 8080?

I am not 100% certain, but since port 80 is the default, you don't have to enter it after an IP. However if you change from port 80, you do have to enter it.

A router is not a human, it cannot guess what you want. (why should it pick port 8080 from your computer? why not port 22? or 25?)

But then, I hardly know anything about this stuff. I suggests that if you do not like entering port 8080 behind your ip, what you can do is just have an ip mask from dyndsn.org for example. and whenever you type whatever address you signed up for, it automatically replaces it with your ip-addy and port 8080.

Hope that helps.

---

### Post by Iowan on 2010-05-28
> **darylp said:**
>  The problem I'm having, is when I enter my ip without an alternate port, it goes to my router's login prompt. I can't find it at the moment, but my modem/router has an option to disable access on external port (remote management?).

---

### Post by mituw16 on 2010-05-29
Hello, 
I assume you are trying this from inside your house network? 

If I type my static WAN IP into a web-browser while inside my house network, it brings up my router's firmware page, while if i do the same thing outside of my house network it just brings up the can't connect thing, because the only ports that my apache server listens on 443. 

Basically, try to connect via your IP outside of your house network, and if port 80 isnt forwarded and apache isnt listening on port 80, then it should bring up the can't connect page for your browser. 

The only reason that you would still be accessing your router's firmware from outside your network via your WAN IP would be if your router had remote management enabled, which I would highly recommend turning off.

---

