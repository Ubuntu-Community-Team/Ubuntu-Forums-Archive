---
title: "Ubuntu server not recieving packets and repository not updating"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by sodejm on 2011-09-15
Hi all, 
First time post i hope this is in theright area if not let me know.  I am working with ubuntu server 11.04
And when i ping google i get 100% packet loss i have tried dhcp and static ips and A few other things i found going through forums but i have come to an end in ideas for troubleshooting any help from more experienced users would be awesome

Thanks in advance and if i posted this in the wrong area or something else is wrong with the post let me know for future reference

---

### Post by 2F4U on 2011-09-15
What is providing your server internet access, for example, is your server connected to a router, which provides internet access?

---

### Post by HugoSerrano on 2011-09-15
Hello!

First, welcome :-)

Now some question to help us!

What's your network IP?
What's the IP of your server?
What's the IP of your router?

First thing you should be able to do it's ping your gateway, not google! 

Best Regards!

---

### Post by sodejm on 2011-09-15
I probably should have mentioned that i am a student and this server is kind of a test for a possible student systems admin job.

what i know if that

my server ip for dhcp was 141.238.52.17
and static should be 141.238.30.26

im not sure how to get any other information right now outside of that because my access before getting the job is rather limited so i'll ask one of the sys admins what the router ip is 

from what i know the dhcp comes from a campus dhcp server and the static goes to a switch 

i hope that is enough to get started

---

### Post by HugoSerrano on 2011-09-16
If you can get IP via dhcp, you can see you're gateway.

do:
> # dhclient

show the output of:

> ifconfig

> route -n

Regards!

---

### Post by sodejm on 2011-09-24
Sorry i never got back things got a little hectic but i believe i figured it out i needed that Mac address to be registered with our network

Thanks to those who replied and tried to help

---

