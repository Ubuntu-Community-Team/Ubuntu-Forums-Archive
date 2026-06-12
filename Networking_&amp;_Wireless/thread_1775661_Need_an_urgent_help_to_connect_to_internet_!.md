---
title: "Need an urgent help to connect to internet !"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by Aagat on 2011-06-05
I just installed Ubuntu in my PC and I tried to connect to internet using broadband connection. I use a ADSL router with WiFi access point to connect with network and dial my username and password using my computer to connect to internet. I could so it easily on windows 7 from Network and Sharing center and Setting up new connection or network and connect to internet using broadband internet. 
How can i do it with ubuntu 11.04 ?
Please help !

---

### Post by Iowan on 2011-06-05
Does machine have an IP address? Info is available via Network Manager icon, or from a terminal (Applications>Accessories>Terminal) via **ifconfig -a**.

---

### Post by ssreddy555 on 2011-06-05
It should detect and connect automatically to wireless. If not, enable wireless in the dropdownlist of the wireless indicator at the top right handside.

However, if yours is a Broadcom wireless adopter, see the following post:

[http://ubuntuforums.org/showthread.php?p=10892215#post10892215](http://ubuntuforums.org/showthread.php?p=10892215#post10892215)

---

### Post by Aagat on 2011-06-06
There is no problem connecting to wireless network, i can access the network. But I can't get access to internet unless i dial using PPPoE and provide my username and password. It is ADSL connection. I use ADSL router in bridge mode. I've attached the screenshot of how it looks in windows.
Thanx

---

### Post by dineshs on 2011-06-06
If > There is no problem connecting to wireless network, try steps 1,2,5 and 6 in [this ]("http://ubuntuforums.org/showthread.php?p=9857165#post9857165")thread

---

### Post by Aagat on 2011-06-07
still doesn't help :(

---

### Post by crispy_420 on 2011-06-07
Do you have a DNS server listed via 'less /etc/resolv.conf'?

Also Windows 7 has a great tool for diagnosing network issues built in, give it a shot. On the pic you have there click the "Open Network and Sharing Center" and it will show where the link to the outside world is broken. Click the red X and let it do it's thing.

---

### Post by dineshs on 2011-06-07
Please do ```
sudo pon wlan
```
```
plog
```
```
ifconfig -a
```
and post results.

---

### Post by Aagat on 2011-06-07
[HTML]agt@agt-beast:~$ sudo pon wlan
[sudo] password for agt: 
Plugin rp-pppoe.so loaded.
agt@agt-beast:~$ plog
Jun  7 23:14:44 agt-beast pppd[1706]: Plugin rp-pppoe.so loaded.
Jun  7 23:14:44 agt-beast pppd[1708]: pppd 2.4.5 started by root, uid 0
agt@agt-beast:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40400 (40.4 KB)  TX bytes:40400 (40.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e3:b8:fb:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

agt@agt-beast:~$ 

[/HTML]

---

### Post by Aagat on 2011-06-09
Seems no one is interested to help me :(

---

### Post by OM NOM NOM on 2011-06-09
Sorry is the ADSL router/modem connected directly to your PC or are you connecting through a wireless router? I don't see that you're getting an IP address and you should, at least from the router if DHCP is turned on.

---

### Post by Talon2 on 2011-06-09
> **Aagat said:**
> There is no problem connecting to wireless network, i can access the network. But I can't get access to internet unless i dial using PPPoE and provide my username and password. It is ADSL connection. I use ADSL router in bridge mode. I've attached the screenshot of how it looks in windows.
Thanx

Not the answer you are looking for likely but what I would recommend you consider is buying a cheap wireless router.  The router can then dial your PPPoE automagically for you.

---

### Post by Aagat on 2011-06-10
> **OM NOM NOM said:**
> Sorry is the ADSL router/modem connected directly to your PC or are you connecting through a wireless router? I don't see that you're getting an IP address and you should, at least from the router if DHCP is turned on.

I am connection to ADSL router via WiFi. I don'e know what thing went wrong that it works fine in Windows but creates problem with Ubuntu !

---

