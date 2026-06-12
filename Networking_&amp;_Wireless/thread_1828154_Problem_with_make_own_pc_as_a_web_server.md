---
title: "Problem with make own pc as a web server"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by NingZhang on 2011-08-18
Hi all, 

I am trying to make my pc as a small web server. 
so i followed the steps below

1) Configure the router - Active Port Forwarding
                                                                                [FONT=Liberation Serif]Private IP[/FONT]             [FONT=Liberation Serif]Protocol Type[/FONT]             [FONT=Liberation Serif]Public Start Port[/FONT]             [FONT=Liberation Serif]Public End Port[/FONT]             [FONT=Liberation Serif]Connection[/FONT]                               [FONT=Liberation Serif]192.168.1.3[/FONT]             [FONT=Liberation Serif]ALL[/FONT]             [FONT=Liberation Serif]78[/FONT]             [FONT=Liberation Serif]78[/FONT]             [FONT=Liberation Serif]PVC0[/FONT]                
2) Find the public ip address from 

[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

3) edit  apache port configuration
3.1)
sudo gedit /etc/apache2/ports.conf

NameVirtualHost *:78
Listen 78
3.2)
sudo gedit /etc/apache2/sites-available/default

<VirtualHost *:78>
    ServerAdmin webmaster@localhost

4) restart the apache
sudo /etc/init.d/apache2 restart

[B]everything works for the local ip address. 
However, when i am trying to use public ip. it goes to the router's configuration page. [/B]

I have spent the past two days to work on this. If anyone can help me, i would really appreciated.
thanks again!!

regards,
Ning

---

### Post by restorator on 2011-08-18
When you are inside your local network that's what you will see due to the way routing works. You can test from the outside by using a proxy. Try a proxy at [http://proxy.org](http://proxy.org) and see if it loads from there.

---

### Post by NingZhang on 2011-08-19
thank you so much. Because i am very new for the network. Do you mind explain a bit further how to configure the proxy in order for the public ip talk to my private ip?

many thanks in advance!

Ning

---

### Post by restorator on 2011-08-19
You do not need to do anything. If it works correctly via the proxy, the outside world can see you just fine and all is well. You cannot see your outside IP address from inside your local home network because you are on the other side of the router. Just access it from the inside via its internal IP or [http://localhost](http://localhost) if it is on the same machine.

---

### Post by NingZhang on 2011-08-20
i have tried the proxy on . it said 

couldn't connect to host

is that mean i need to talk to my service provider?
So that means i can not set my desktop as a webserver use a simple router at home with my current contract? 

could you kindly help me confirm this? many thanks!

regards,
Ning

---

