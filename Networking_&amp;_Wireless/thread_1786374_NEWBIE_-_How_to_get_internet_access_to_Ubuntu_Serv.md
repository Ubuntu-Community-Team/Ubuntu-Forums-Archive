---
title: "NEWBIE - How to get internet access to Ubuntu Server"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by powerwatt on 2011-06-19
I have a server that was set up by a friend so I have a location to save all my documents for work in a RAID array.

It is on a static IP address, I can ping the hub and other computers on the network absolutely fine.

I can't connect to the internet, the router in question is a Netgear CG3101D. Logging into the router I can see that the server is a trusted device and in all the parameters are the same as other computer running Ubuntu Studio.

Does anyone have any tips of how I can find out how to find what is wrong?

It is Ubuntu 10.04.2 LTS (Lucid).

I am a newbie so things may well need explaining too me in a patronising grandma kind of way.

---

### Post by powerwatt on 2011-06-19
Solved form another forum

---

### Post by chili555 on 2011-06-19
> It is on a static IP address, I can ping the hub and other computers on the network absolutely fine.In order to connect to the internet, as opposed to the local network, every computer needs a way to resolve names to numbers. For example, if I ping Google, a DNS nameserver translates, or resolves 'Google' into a number; in my case 74.125.91.105:> $ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com(74.125.91.105](www.l.google.com(74.125.91.105)) 56(84) bytes of data.
64 bytes from qy-in-f105.1e100.net (74.125.91.105): icmp_req=1 ttl=47 time=36.5 ms
64 bytes from qy-in-f105.1e100.net (74.125.91.105): icmp_req=2 ttl=47 time=37.1 ms
64 bytes from qy-in-f105.1e100.net (74.125.91.105): icmp_req=3 ttl=47 time=52.8 msThe nameservers are declared in a file called /etc/resolv.conf. Run this command to check yours:```
cat /etc/resolv.conf
```Is it empty or does it contain nothing but comments? You can populate it with these commands:```
sudo su
echo "nameserver blahblah" >> /etc/resolv.conf
exit
```But what can we put in there? You could check other computers on the network for their namesever details or use the router to do the work. The router will have some in its configuration and you could use them directly:```
sudo su
echo "nameserver 209.205.x.y" >> /etc/resolv.conf
echo "nameserver 209.205.x.z" >> /etc/resolv.conf
exit
```Or, you could just use the router:```
sudo su
echo "nameserver 192.168.x.y" >> /etc/resolv.conf
exit
```Of course, substitute your details above.

The fix should be immediate, so try:```
ping -c3 www.google.com
```If it resolves to numbers and you get ping returns, you're all set.

---

### Post by powerwatt on 2011-06-19
Thank you, that is exactly what I got from another forum. Quite a simple problem from all accounts. But I was just lost.

Thanks

---

