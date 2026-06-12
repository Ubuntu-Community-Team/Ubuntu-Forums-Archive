---
title: "connection timed out when trying to ssh"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by cosine352 on 2009-05-20
Hi friends,
in my home I have a desktop and set it up as a server. The desktop or the server is connected through a router. In my home network everything works fine. But when I am at work I can not connect it and get a 'connection timed out' error. If I connect the desktop directly to the internet (without the router), I connect it without any problem. 
Now I need to use the router as I have two computers to share the internet. 

So is there any method to overcome this problem? 

Thanks for your help.

---

### Post by cosine352 on 2009-05-20
I searched a little and found that I need to do 'port forwarding' for my router to overcome this problem. I still do not know how to do that. If I found something I will post it here or if somebody  know how to do it please let me know.

---

### Post by Iowan on 2009-05-20
The router manual *should* be able to help set up port-forwarding, but there's another issue.  Unless you have a static IP address from your ISP, you will need a service like no-ip.com or Dyndns.com

---

### Post by Sub101 on 2009-05-20
My Belkin router has port forwarding under the "Virtual Servers" section. Id take a look in the corresponding area on your router.

---

### Post by cosine352 on 2009-05-22
Thanks for the reply guys. 
I have done the steps suggested by Iowan and Sub101 and now I can connect my desktop at home from anywhere. 

Thanks a lot.

---

### Post by cosine352 on 2009-05-22
Now I can do the ssh but still the web server is taking too much time to load (finally error loading because of the time out). I have done the port forwarding for web server in my router. Is there anything else to do?

---

### Post by cosine352 on 2009-05-25
I have solved it. It turns out that my ISP (Cox) blocks the port 80. So I needed to change the port for apache2 and it is working now.

---

