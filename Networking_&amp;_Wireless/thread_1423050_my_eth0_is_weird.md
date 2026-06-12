---
title: "my eth0 is weird"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by 71GA on 2010-03-06
Hello i am using wpa_supplicant and am trying to access network. 
If i type command **ifconfig** i get what is shown on picture below:

[img]http://www.shrani.si/f/1I/tX/15cAf6pm/screenshot.png[/img]

In second paragraph i get **eth0:avahi** which shouldnt be there and i think it is messing my connection. 
I must remove this to only get first and third paragraph on this picture. [COLOR="Red"]How do i do this?[/COLOR]

Allso it is weird that in first paragraph (eth0) i have **inet6 **instead **inet**. [COLOR="red"]How do i change this?[/COLOR]

---

### Post by 71GA on 2010-03-06
I tried to use command **sudo /etc/init.d/networking restart** in terminal and after this i checked up my connections with command **sudo ifconfig**. What i got is listed in picture below. I marked suspicious parts. 

It is weird that i get 2 ip adresses for eth0...

[[img]http://www.shrani.si/t/31/Zk/3XkZka5g/1.jpg[/img]](http://www.shrani.si/?31/Zk/3XkZka5g/1.png)

Is maybe this the problem i cant connect to network?

---

### Post by chili555 on 2010-03-06
eth0:avahi addresses of 169.xx occur when the actual DHCP server has not given you a valid IP address and, therefor access to the internet and your system assigns a place-holder address, 169.xx. It simply means that you need to refine your settings and try again.

In your second post, it looks to me like you connected just perfectly and I see nothing wrong. Can you surf the web, etc.?

---

