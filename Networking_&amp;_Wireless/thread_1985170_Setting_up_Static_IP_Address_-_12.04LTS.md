---
title: "Setting up Static IP Address - 12.04LTS"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by AustenG on 2012-05-22
Hey All, 

I've attempted to set up a static ip address for my home computer (Ubuntu 12.04LTS), and have followed a few online instructions to no avail. I've managed to reverse what I did, but I'd still like to know the in's and out's of setting up ip addresses.

First of all, what is a static ip address and why does it offer better performance? Is it at all bad for security? Basically, I've heard that I *should* set up a static ip address and I'm not entirely sure why.

My first crack at this was to run the terminal command:
```
ifconfig
```
This shows me a whole bunch of stuff that I don't really know how to interpret. Here's the output:

```

eth0      Link encap:Ethernet  HWaddr c8:60:00:e3:6b:d0  
          inet addr:192.168.1.108  Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fee3:6bd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1669345 (1.6 MB)  TX bytes:301602 (301.6 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74443 (74.4 KB)  TX bytes:74443 (74.4 KB)

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:4b:87:6d  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe4b:876d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:410867 (410.8 KB)  TX bytes:33267 (33.2 KB)

```

What I attempted next was to change the "managed=false" to "managed=true" in the file: /etc/NetworkManager/NetworkManager.conf

Then I went into the file: /etc/network/interfaces

Which originally looked like this:
```

auto lo
iface lo inet loopback

```

And changed it to this:
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

I then edited my connections, and entered in these addresses, and made sure that under IPv4 the method was 'Manual'.

Can anyone see where I messed up?

Thank you for your help!!

---

### Post by chili555 on 2012-05-23
I know of no compelling reason that an ordinary home computer needs a static IP. That said, I have two computers in my home on which I've set up static IPs. My wife's computer runs Ubuntu 12.04. As you might guess, I'm the in-house support. I think it's fun to log on to her computer with ssh and do administrative tasks.

I have a printer attached to a computer and all the other computers in the house use it. It's much easier to set up with a static IP rather than samba, bind, etc. Beyond that, and perhaps a home server, I don't believe there is any speed or stability reason to use static IP addresses.

You've made a few mistakes. First, you have IP addresses for both wired and wireless. If you have the option for wired, use it in preference to wireless. It's faster and more secure. Flip the wireless switch or key combination to OFF.

Second, as you know, there is a provision in Network Manager to set up static IP addresses. There is no need and possibly some complication to mix NM and /etc/network/interfaces. I suggest the NM method but not both. Of course, you could remove NM altogether and use manual methods entirely.

Next, you've picked an IP address that appears to be within the range used in the DHCP server in the router. You want one outside the range so there is no collision. For example, I've set my router to allow ten addresses by DHCP from 192.168.1.3 to x.12. All my static IPs are in the rage of 192.168.1.100 and up.

Also, you haven't specified DNS nameservers. When a computer is given an IP address by DHCP, the router supplies DNS nameserver addresses. If you set static IPs, you are assumed to be in charge of such details.

If you want to try again, I'd suggest:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.178
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```

---

### Post by AustenG on 2012-05-23
Thanks for the response! 

> **chili555 said:**
> 
You've made a few mistakes. First, you have IP addresses for both wired and wireless. If you have the option for wired, use it in preference to wireless. It's faster and more secure. Flip the wireless switch or key combination to OFF.

What do you mean by flip the wireless switch or key combination? I'd like to default to wired connection whenever possible, but I'd like the option to access wireless as well (I have a few machines/devices which could been hooked up and I'd like the freedom to pick and choose).

> **chili555 said:**
> 
Second, as you know, there is a provision in Network Manager to set up static IP addresses. There is no need and possibly some complication to mix NM and /etc/network/interfaces. I suggest the NM method but not both. Of course, you could remove NM altogether and use manual methods entirely.


Is NM accessed by the file in /etc/NetworkManager/NetworkManager.conf ? Also, why do you suggest the NM solution over the other method? 

> **chili555 said:**
> 
Also, you haven't specified DNS nameservers. When a computer is given an IP address by DHCP, the router supplies DNS nameserver addresses. If you set static IPs, you are assumed to be in charge of such details.


So all of this is to ensure that my router knows which IP address to give to which devices, is this correct? For things like screen sharing and ssh, how do I ensure that computers outside my home network will know where to find my network? I've heard things about NO-IP, but when I took a look at it it mentioned something about having to update my address every 30 days... 


> **chili555 said:**
> 
If you want to try again, I'd suggest:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.178
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```


^^  This totally works now! I still don't quite understand the rules of how IP addresses are distributed to hardware on a network, but I'm marking this solved. Just to be perfectly clear about what I did: I literally copied this into my /etc/network/interfaces file. Was it just a coincidence that this worked? I understand in principle what netmask is saying. It allows me to set the number of possible IP addresses my router is allowed to give out, right? But, gateway and dns-nameservers are still a bit of a mystery to me. It seems odd that this exact same setup works for me, too. Also, what happened to broadcast?

Sorry about all of the questions - I'm *completely* new to this whole network thing - when you run Windows and Mac these things are totally invisible most of the time (not that you can't go in and change things if you want to). It's funny how reliant we are on software, and how pissed off people get when it doesn't work in an intuitive, hassle-free way. I really like figuring this stuff out, even if it's a bit frustrating/overwhelming at times (but this is all off topic).

---

### Post by chili555 on 2012-05-24
> What do you mean by flip the wireless switch or key combination? I'd like to default to wired connection whenever possible, but I'd like the option to access wireless as wellPardon me if I was incorrect, but your readings suggest this is a laptop. Laptops usually have a switch or key combination to enable or disable wireless. It is desirable not only for power saving but also a requirement in some countries to comply with flying rules; the wireless radio must be able to be affirmatively switched off. 

Network Manager is supposed to do the job for us; that is, use wired if it's available and wireless if wired isn't available. Like many things computer, it is just a bit imperfect as you saw:> eth0      Link encap:Ethernet  HWaddr c8:60:00:e3:6b:d0  
          inet addr:[COLOR="Red"]192.168.1.108[/COLOR]  Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fee3:6bd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
<snip>

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:4b:87:6d  
          inet addr:[COLOR="Red"]192.168.1.107[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe4b:876d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1My point is that if you can help things along by switching the wireless off by the switch, NM will work correctly.> Is NM accessed by the file in /etc/NetworkManager/NetworkManager.conf ? Also, why do you suggest the NM solution over the other method? The settings are accessed by clicking the NM icon at the top. Where you see your networks and connections, at the bottom, you'll see *Edit Connections*. That's where you can add a static IP address, DNS nameservers, etc. Please see attached. I suggest the NM method simply because it's easier to access and understand in our increasingly point-and-click world. Since you have it working as is now, I'd leave it as is.> So all of this is to ensure that my router knows which IP address to give to which devices, is this correct? Correct.> For things like screen sharing and ssh, how do I ensure that computers outside my home network will know where to find my network? I'm sorry, that's outside my area of knowledge; they only let me play with the simple stuff here. When you get ready to do those things, I suggest a new specific thread.> I still don't quite understand the rules of how IP addresses are distributed to hardware on a network, but I'm marking this solved. Just to be perfectly clear about what I did: I literally copied this into my /etc/network/interfaces file. Was it just a coincidence that this worked? I understand in principle what netmask is saying. It allows me to set the number of possible IP addresses my router is allowed to give out, right? But, gateway and dns-nameservers are still a bit of a mystery to me. It seems odd that this exact same setup works for me, too. Also, what happened to broadcast?Well, my years of experience and 13,000 posts suggest it *wasn't* a coincidence. You posted your malformed interfaces file above and I could see certain details about it which I used to build a file that works.

Your router, using the address of 192.168.1.1, is an ordinary consumer-grade router. They do a fine job. By definition, these devices have available 252 addresses. They are usually set to allow 50 addresses by DHCP; that means, roughly, the router will take care of all the details for us. That's perfect for the ordinary user. The router and the computer will figure out all the details in the background. 

However, that leaves another 202 addresses to be used by those of us who are willing and knowledgeable enough to supply our own details.

The most often missed detail by those who venture into static IPs is DNS nameservers. The internet doesn't know who or what [www.google.com](www.google.com) is. It works by numbers, not names. So, how can we translate [www.google.com](www.google.com) into 173.194.73.147? There are sites that do nothing but that; look up a name, translate it to a number and pass it on. Without that translation, your internet traffic goes nowhere.

One option is your router, we know it has the information, it's providing DNS nameservers for all the other devices on your network. However, Google themselves host a very fast reliable nameserver: 8.8.8.8. So I suggested you use it as a primary DNS and the router as a fallback:> dns-nameservers 8.8.8.8 192.168.1.1As for broadcast, in a private, home network, it works perfectly fine without it. I'm a minimalist; the fewer details I *must* fill in, the fewer that can go wrong!

---

### Post by AustenG on 2012-05-24
Thanks a lot for the information!

---

### Post by AndyA121 on 2012-07-30
:confused:I am new to the basics of Ubuntu  I want to know if I am configured properly because every time I try to go to my Yahoo account I always get a "connection was reset" message.  

 Here is what my configuration looks like:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:21:1b:66  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe21:1b66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244055704 (244.0 MB)  TX bytes:8499422 (8.4 MB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

I don't understand what this means.

---

### Post by rbjscv on 2012-10-07
The above instructions did not work for me.  I followed them exactly but could not get my machine to recognize that I had set up a static IP.

I'm running 12.04 on a six year old e-machine.

---

### Post by alwindoss on 2012-10-23
When I do what you suggest I am unable to connect to the internet.
I used the network manager to do this. I went to the Wireless Connections Tab and I chose Manual in the IPV4 settings and I supplied the parameters as you mentioned. Also I made sure I have an IP which is not in the range of my Router.

I tried doing this on my laptop before trying it on my ubuntu 12.04 LTS servers

---

### Post by fatima101 on 2012-11-28
I have used services of proxy rental to change IP as static one. These are premium USA DSL ISP IP addresses. I'm sure you will be pleased to get their help.

---

### Post by tizothony on 2012-12-09
how to lookup google ip address in ubuntu Plz

---

### Post by chili555 on 2012-12-09
> **tizothony said:**
> how to lookup google ip address in ubuntu PlzIf I understand you correctly, then try this:```
ping -c3 www.google.com
```My computer says:> chili@LAPTOP410:~$ ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) ([COLOR="Red"]173.194.75.103[/COLOR]) 56(84) bytes of data.
64 bytes from ve-in-f103.1e100.net (173.194.75.103): icmp_req=1 ttl=41 time=37.3 ms
<snip>Is that the information you needed?

---

### Post by ijumpship on 2012-12-11
Sorry to write in a solved post but just for persons who have ubuntu versions before 12.04,the problem could be the change in how network manager is now configured

Previously we would put the dns nameserver in /etc/resolve.conf

now its placed in the /etc/network/interface as

dns-nameservers...............

---

### Post by Shogoot on 2013-01-06
Thanks to those contributing to this thread. I was able to solve my problem by reading trough. :)

---

### Post by BProv on 2013-02-15
Thanks for this thread, It help me a lot and solved my problem.

---

### Post by jalirious on 2013-02-22
I wasn't able to easily set a static ip address, so I came up with this.

All I want to do is ssh into my home laptop on occasion. This works when I know the ip, but it is dynamic & changes from time to time.

So that I always know the current ip to ssh into, I did this

gedit send_ip.sh &
copy in "cat <(date) <(curl icanhazip.com)> /home/me/Dropbox/current_ip.txt" without the quotes
save, close.
chmod +x send_ip.sh

crontab -e

*/5 * * * * /bin/bash cat <(date) <(curl icanhazip.com)> /path_to_it/send_ip.sh

[(all one line), close & save]

Now the current_ip.txt is updated by cron every 5 minutes, so I know where to ssh to.

---

### Post by cutesar on 2013-10-09
> **tizothony said:**
> how to lookup google ip address in ubuntu Plz

ping the ip or domain name

For example :  ping [www.google.com]("http://www.google.com")  to find ip address of google.

you can also use [http://www.ip-details.com/domain-host-search/](http://www.ip-details.com/domain-host-search/)   to find website ip address .

---

### Post by Craig_Thomas on 2013-10-09
> **chili555 said:**
> 
I'd suggest:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.178
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```


Thanks this really helped and with the obvious slight change of addresses to suit my range 192.168.10.xxx I got my Ubuntu Server 10.04LTS working.

Craig....

---

### Post by kosmokramer314 on 2014-02-21
> **chili555 said:**
> I know of no compelling reason that an ordinary home computer needs a static IP. That said, I have two computers in my home on which I've set up static IPs. My wife's computer runs Ubuntu 12.04. As you might guess, I'm the in-house support. I think it's fun to log on to her computer with ssh and do administrative tasks.

I have a printer attached to a computer and all the other computers in the house use it. It's much easier to set up with a static IP rather than samba, bind, etc. Beyond that, and perhaps a home server, I don't believe there is any speed or stability reason to use static IP addresses.

You've made a few mistakes. First, you have IP addresses for both wired and wireless. If you have the option for wired, use it in preference to wireless. It's faster and more secure. Flip the wireless switch or key combination to OFF.

Second, as you know, there is a provision in Network Manager to set up static IP addresses. There is no need and possibly some complication to mix NM and /etc/network/interfaces. I suggest the NM method but not both. Of course, you could remove NM altogether and use manual methods entirely.

Next, you've picked an IP address that appears to be within the range used in the DHCP server in the router. You want one outside the range so there is no collision. For example, I've set my router to allow ten addresses by DHCP from 192.168.1.3 to x.12. All my static IPs are in the rage of 192.168.1.100 and up.

Also, you haven't specified DNS nameservers. When a computer is given an IP address by DHCP, the router supplies DNS nameserver addresses. If you set static IPs, you are assumed to be in charge of such details.

If you want to try again, I'd suggest:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.178
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```

thank you kindly for this post.  ubuntu server 12.04.4

---

