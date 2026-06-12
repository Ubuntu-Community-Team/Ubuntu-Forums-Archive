---
title: "Network connection in college LAN"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by Charankumar on 2010-01-30
Hi,
I am a newbie to UBUNTU. I have ubuntu 9.10 installed in my laptop along with windows xp(dual boot). I would like to connect my laptop to internet in college, When I boot ubuntu and plu-in the network cable, it says eth0 active connected. But when I open firefox and enter a website it cant load the page. In windows it works fine, the settings our college LAN use are given below:
 
Address Type: Manually configured
IP Adress: 172.16.39.15
Subnet Mask:255.255.0.0
Default Gateway:
DNS servers: 172.16.1.0,172.16.2.0
WINS Server:
 
I tried to establish a new connetion with new profile with the above details changed but I was not able to establish a connection.
Help me.
Thanks in advance...

---

### Post by Iowan on 2010-01-30
They didn't provide a gateway address? 
Can you ping the DNS servers?

---

### Post by Charankumar on 2010-02-01
I figured out few things. Default gateway is given as 0.0.0.0 and I did not try to ping server. Few things are my college is using proxy server and then it provides static ip through out the college. Initially my laptop connects directly to ip, without any proxy and shows auto eth0 connected. What should I do to connect it? If you need anything else I am ready to rely.
 
Can you fix it?

---

### Post by Charankumar on 2010-02-06
I have fixed it........

---

### Post by Abhijit Navale on 2010-02-06
Please post the solution so many others like me wll be benefited from your experience.
And also mark this thread as solved.

---

### Post by Charankumar on 2010-02-06
Solution goto system--> preferences --->network proxy configure the static proxy ip and activate it in all applications. In connection when you plug in it will work else you have to create a new connection which connects with proxy server. you can fetch the ip from your admin are you can view it in windows if you are connected previously.

---

