---
title: "setting up media server"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by goof on 2013-04-17
hi im tying to set up a media server with a ubuntu laptop i have enabled system->preferences->remote desktop on the server and am using applications->internet->remote desktop viewer on my laptop to control it. this all works fine and i quite simple to set up but how safe is it is there a way i can connect as i am but preventing the media server from haveing internet access? as i dont want it to get hacked and have people going throiugh my stuff thanks any advice would be great thanks

allso on the media server when i try to login it requires me to click allow this defeats the point as i want to leave media server in attic is there a way around this? while keeping safe

---

### Post by TheFu on 2013-04-17
The media server software used will determine the answer to most of your questions.  I think there are about 10-20 options. Which are you using?

To prevent internet access from the media server might not be what you really want. How will you patch?  However, you can block all outbound  and inbound connections using any firewall software under Linux. Be careful blocking too much, since you could easily block all remote connections and prevent access that you want from local machines.  Of course, you could use iptables directly too, but most people would be happier with either ufw or firestarter tools as the front-end.

---

