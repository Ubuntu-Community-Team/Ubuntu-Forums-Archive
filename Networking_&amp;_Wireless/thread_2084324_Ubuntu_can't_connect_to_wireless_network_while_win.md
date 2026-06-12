---
title: "Ubuntu can't connect to wireless network while windows can?"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by daithy on 2012-11-15
OSes Ubuntu 10.10 & Win7

I have 2 wireless networks in my surroundings that I have access to, they are wpa encrypted, I have the keys for both. Both are the same ISP however different Access points and connections. Let's call them A&B

Connection A:
Both OSes connect no hassle.


Connection B:
Does not connect in Ubuntu?! (again something not working ](*,))
I tried the lousy native network manager and also WICD, at least wicd shows you kinda real time update of what's up, I ran wireshark at the same time as well. So I can see that my client is assigned an IP address 192.168.0.11, but will not access the internet, in wireshark you can see the the router and my laptop agreed one anothers IP addresses via ARP protocol and then you see the the router contacts some external IP address, but that's beyond my knowledge.
So I didn't give up, went to to preferences to set up my connnection B on static because I know the ISP's DNS servers.
put in
my ip - 192.168.0.11
default gateway - 192.168.0.1
subnet mask 255.255.255.0

dns server1  83.200.220.80 
dns server2  8.8.8.8

and not a hope,still nothing, so I thought at least my LAN would be up since I was assigned a local IP, tried to access the router via web browser by typing the default gateways ip address, and nothing


I am typing this message in win7 and the network I cannot access from Ubuntu
my internal IP is 192.169.0.11 all exactly the same as in Ubuntu so conflict of IP's with other devices can be excluded.

---

### Post by sdowney717 on 2012-11-15
> I have 2 wireless networks in my surroundings that I have access to, they are wpa encrypted, I have the keys for both. Both are the same ISP however different Access points and connections. Let's call them A&B

Are these routers in any way interconnected or are they distinctly separate connections to the internet?

---

### Post by daithy on 2012-11-15
> **sdowney717 said:**
> Are these routers in any way interconnected or are they distinctly separate connections to the internet?
Thanks for your reply, they are distinctly different routers and connections.

---

### Post by sdowney717 on 2012-11-15
I dont suppose you could temporarily disable the wpa encryption and see if you can connect?

So your Ubuntu machine sees the target router but can not negotiate the connection.

And your positive you have the key right.

There is a variety of WPA connection types
Here is mantioned a system log. If you can find a log which lists out the failure mechanism, maybe you can solve it.
[http://askubuntu.com/questions/131436/wifi-connectivity-problems-when-using-wpa-wpa2-encryption](http://askubuntu.com/questions/131436/wifi-connectivity-problems-when-using-wpa-wpa2-encryption)

from that site seems a driver issue. Also is it AES or TKIP?
> It seems that Ubuntu has some incompability issues with WPA/TKIP. Can you change to WPA2/AES? Does it work for you? &#8211; user57108 May 5 at 12:05
It was an issue with the realtek driver. Thanks for all the answers &#8211; Jeanno May 12 at 19:41

---

### Post by daithy on 2012-11-15
> **sdowney717 said:**
> I dont suppose you could temporarily disable the wpa encryption and see if you can connect?

So your Ubuntu machine sees the target router but can not negotiate the connection.

And your positive you have the key right.

There is a variety of WPA connection types
Here is mantioned a system log. If you can find a log which lists out the failure mechanism, maybe you can solve it.
[http://askubuntu.com/questions/131436/wifi-connectivity-problems-when-using-wpa-wpa2-encryption](http://askubuntu.com/questions/131436/wifi-connectivity-problems-when-using-wpa-wpa2-encryption)

from that site seems a driver issue. Also is it AES or TKIP?


I am 1000% sure the key is correct, when you watch wicd closely it actually passes the point of authentication. I suppose I could try to turn off the encryption temporary to see what it does.

---

