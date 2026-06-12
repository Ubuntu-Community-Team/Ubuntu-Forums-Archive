---
title: "internet dead, skype works after force quit"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by zhanglini on 2012-06-27
Hi,
Yesterday I managed to remote desktop to my work computer. But when I finished, I did not close Chromium and vinagre etc properly --- I just turned the computer off.
Then when I turned it back on, I no longer have internet (tried both Firefox and Chromium), I still have Skype, I could not ping IP address (such as 72.14.205.100) so I guess it is not a dns problem.
I can go online using my live-usb Ubuntu (as doing right now), so it is not a hardware problem either.
Is there some kind of settings that got screwed up?
I use 12.04 Ubuntu, 32bit.
Thanks in advance

---

### Post by nipunshakya on 2012-06-27
try to list out what were the last things u did in your computer and check the settings for those... make a reverse move to what u did the last time on your machine..maybe u can find some clue...

Goodluck

---

### Post by zhanglini on 2012-06-27
The only thing I did was opening this VPN url to my workplace in Chromium (it has to stay open to Remote Desktop), and then open this Juniper Java thing and then Vinagre.  Did not really set anything, not even in Vinagre, because I had all the settings during my previous failed attempts (had to set workplace Windows b4 my last attemp which was a success).  Then I force closed them by turning off the PC.  Then my nightmare started.... not much I can reverse...

---

### Post by nipunshakya on 2012-06-27
Haven't got that kinda issue before with myself... maybe someone with an answer might just come up.... have a google around about your problem too... 

Goodluck

---

### Post by gradinaruvasile on 2012-06-28
> **zhanglini said:**
> The only thing I did was opening this VPN url to my workplace in Chromium (it has to stay open to Remote Desktop), and then open this Juniper Java thing and then Vinagre.  Did not really set anything, not even in Vinagre, because I had all the settings during my previous failed attempts (had to set workplace Windows b4 my last attemp which was a success).  Then I force closed them by turning off the PC.  Then my nightmare started.... not much I can reverse...

So you use a VPN?

You have to check the default route (gateway), maybe the VPN replaced it, it happens if it isnt configured correctly OR, i heard that some vpns work only this way so youre screwed in this case.

Open a terminal and type:

```

ifconfig
ip rou

```

the first command is to find your network adapters IP address, the second is to display the network routes. This second command has an entry that should begin with "default".
That entry should point to one of your local adapters - the one that provides network connection, by cable (eth0 typically) or by wireless (this may vary, wlan0 or eth1 are commonly used).

For example, my computer has a network connection via ethernet, on device eth0 with an ip address of 192.168.100.100 and uses 192.168.100.254 (my routers address) as gateway:

ifconfig gives (removed the rest of the entries that are not relevant):

```

eth0      Link encap:Ethernet  HWaddr 00:24:8c:d5:de:a9  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1669592 errors:638 dropped:0 overruns:638 frame:0
          TX packets:910273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1125421874 (1.0 GiB)  TX bytes:1485250934 (1.3 GiB)
          Interrupt:41 

```

ip rou gives (removed the unrelevant entries, this is the first line):

```

default via 192.168.100.254 dev eth0

```

Issue these commands and paste their output here.

---

### Post by zhanglini on 2012-06-28
Thanks
ifconfig (I actually use wireless)
```
eth0      Link encap:Ethernet  HWaddr e0:69:95:10:37:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:localloop  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr e0:91:53:34:d4:14  
	  inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e291:53ff:fe34:d414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	  RX packets:20 errors:0 dropped:42 overruns:0 frame:0
          TX packets:288 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5950 (5.9 KB)  TX bytes:102415 (102.4 KB)
```

ip rou
```
default via 192.168.0.1 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.100  metric 2 
```

---

### Post by gradinaruvasile on 2012-06-28
Hm. You dont have anything vpn-related there.
But you do have something thats not helping: 

169.254.0.0/16 dev wlan0  scope link  metric 1000 

Delete it:

```

sudo ip rou del 169.254.0.0/16 dev wlan0  scope link  metric 1000 

```

Then try pinging the gateway (192.168.0.1), then 8.8.8.8 (thats google's DNS, always up, best internet connectivity check) and then [www.google.com](www.google.com).
For the last test make sure you do have some nameserver (i recommend 8.8.8.8) in your /etc/resolv.conf file.

You should disable the avahi service, it isnt good for anything in practice - thats the one providing those annoying link-local connection ips that sometimes mess up stuff.

---

### Post by zhanglini on 2012-06-28
Thank you gradinaruvasile!
After I remove the entry in "ip rou" and add 8.8.8.8 as nameserver, I got my internet back!  even after I rebooted I still have it.  Hopefully it will stick!
Thanks again!

---

### Post by zhanglini on 2012-06-29
To whoever might find this helpful:
when you run VPN, it changes nameserver into its nameserver temporarily, and when you close VPN down, it will be changed back in /etc/resolv.conf.  So when you close VPN improperly (like force quit), /etc/resolv.conf still has the temp value, thus you lose your internet ---- that is my understanding.
The ONLY thing you need to do is to run:
```
sudo /sbin/dhclient 
```
Which will reset your resolv.conf (among other things I guess.
There is no need to delete that line in "ip rou" and add nameserver 8.8.8.8.
Thanks

---

### Post by gradinaruvasile on 2012-07-09
> **zhanglini said:**
> To whoever might find this helpful:
when you run VPN, it changes nameserver into its nameserver temporarily, and when you close VPN down, it will be changed back in /etc/resolv.conf.  So when you close VPN improperly (like force quit), /etc/resolv.conf still has the temp value, thus you lose your internet ---- that is my understanding.
The ONLY thing you need to do is to run:
```
sudo /sbin/dhclient 
```
Which will reset your resolv.conf (among other things I guess.
There is no need to delete that line in "ip rou" and add nameserver 8.8.8.8.
Thanks


In this case the vpn connection dies, the network interface is deleted and the routes associted with it go away too. But the dns servers remain.

What kind of vpn is this? Did you configure it via network-manager?
Because network manager has the option to keep your net connection as it was and to not change resolv.conf.

BTW the solution you give doesnt work for those who use static addresses.

---

### Post by zhanglini on 2012-07-09
I did not use network manager, I used Mad Scientist's script and it worked!
[http://mad-scientist.us/juniper.html]("http://mad-scientist.us/juniper.html")

---

