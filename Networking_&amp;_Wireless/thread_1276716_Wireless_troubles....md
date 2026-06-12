---
title: "Wireless troubles..."
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by andpal222 on 2009-09-27
Hi, Im new to ubuntu and i love it so far but i have also been having some minor troubles.

First off, when i log in it connects instantly to my wireless network but atrandom times, (I may be web-surfing, or downloading something) it will disconnect. On the top panel it reads that it is still connected, but it really isnt becuase i cant view any websites in Firefox. What i have to do then is to go into the Wirless menu and re-connect to my wirless network. From here, it wont connect, it will not detect it. Then, i have to unplug the AC for the wireless router and plug it back in, and then try re-connecting in ubuntu again, at which point it will now work.

Does anyone have any solutions? Any help is greatly appreciated!

---

### Post by Machnikowski on 2009-09-27
Does it drop the connection for other routers or just yours?

If it's the latter, try doing a factory reset on the router.

---

### Post by andpal222 on 2009-10-12
> **Machnikowski said:**
> Does it drop the connection for other routers or just yours?

If it's the latter, try doing a factory reset on the router.
Well the wireless works perfectly with my Windows Xp partition, but its still acting up in Ubuntu, so im thinking it might not be a router issue

---

### Post by jward3010 on 2009-10-12
Firstly what is your wireless device, to find out go to a terminal and type:
```
sudo lshw -C network
```

When it happens again, open a terminal and type:
```
ping -c 3 208.67.222.222
```

and
```
ping -c 3 www.nyt.com
```

Post what you get. I doubt it somehow, but we'll eliminate bit by bit.

---

### Post by andpal222 on 2009-10-14
> **jward3010 said:**
> Firstly what is your wireless device, to find out go to a terminal and type:
```
sudo lshw -C network
```

When it happens again, open a terminal and type:
```
ping -c 3 208.67.222.222
```

and
```
ping -c 3 www.nyt.com
```

Post what you get. I doubt it somehow, but we'll eliminate bit by bit.
Wireless Device info: 
description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.

Second + Third Steps 

: ping -c 3 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=47 time=21.7 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=47 time=21.1 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=47 time=23.8 ms

--- 208.67.222.222 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 21.100/22.245/23.844/1.177 ms

 ping -c 3 [www.nyt.com](www.nyt.com)
PING [www.nyt.com](www.nyt.com) (199.239.137.217) 56(84) bytes of data.

--- [www.nyt.com](www.nyt.com) ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2013ms

---

### Post by jward3010 on 2009-10-15
Just as I suspected! Your DNS serves aren't doing their job. Technically your connected to the internet but you can't resolve hostnames. Post the output of:
```
nm-tool
```

---

### Post by andpal222 on 2009-10-17
> **jward3010 said:**
> Just as I suspected! Your DNS serves aren't doing their job. Technically your connected to the internet but you can't resolve hostnames. Post the output of:
```
nm-tool
```
Ok i did that, should i post results of the command or is the Internet technically fixed now? Thanks for the help so far!

---

### Post by pckindia on 2009-10-17
hi.. i have a WLAN modem. when i try to establish net connection in ubuntu, its not working. it says connection 100% active. But firefox shows proxy server error when i try to connect. Pls help.

---

### Post by jward3010 on 2009-10-18
Oh, I should have been clearer - yeah, post the output of nm-tool.

---

### Post by andpal222 on 2009-10-18
> **jward3010 said:**
> Oh, I should have been clearer - yeah, post the output of nm-tool.
Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
Capabilities:
    Supported:       yes
    Speed:           54 Mb/s
Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
Is that enough info because there were some addresses that i will only post if needed, i dont want to put too much personal info out there.

---

### Post by jward3010 on 2009-10-18
It was the addresses I was most interested in actually.

Unless you are connected through PPPoE (and basically have an exposed public IP address) you needn't worry about providing IP info as it's all private network based and can't be accessed by anyone here. The IP address of my machine is 10.0.0.118 and everyone can know that but no-one knows what my Public is, even if they did, my firewall would prevent access.

---

### Post by andpal222 on 2009-10-18
> **jward3010 said:**
> It was the addresses I was most interested in actually.

Unless you are connected through PPPoE (and basically have an exposed public IP address) you needn't worry about providing IP info as it's all private network based and can't be accessed by anyone here. The IP address of my machine is 10.0.0.118 and everyone can know that but no-one knows what my Public is, even if they did, my firewall would prevent access.
in that case here it is: IPv4 Settings:
  
  Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

again, if any of this should best stay private then please tell me so i can remove it ASAP.

hope it helps!

---

### Post by jward3010 on 2009-10-18
This stuff is so safe I could give it to the triads and they would laugh at me. Then beat the **** out of me for wasting their time, couldn't blame 'em. What you've given me is private addresses which sounds "private" but they are the range of addresses that are in use everywhere in the world, internal to a LAN, never externally and basically exposed, and are inaccessible from the internet (except for specific conditions and port forwarding and other crap, but if you don't know about those things then you've NOTHING to worry about.)

I would have actually appreciated the exact output of "ifconfig -a" as it shows exactly whats set on your machine and shows any discrepancy. Is the above the exact same as "ifconfig"? Have you tried setting DHCP in wicd to see what automatic address it picks up?

---

### Post by andpal222 on 2009-10-20
.

---

### Post by jward3010 on 2009-10-21
I'd say either within your router's configuration page or on your machine set your DNS servers as Primary: 208.67.222.222 and Secondary: 208.67.220.220. 

If you want to know how to do this, tell us.

EDIT: I should be clear, those server above are servers belonging to OpenDNS ([www.opendns.com](www.opendns.com)). A large, well known DNS server provider who have very good uptime.

---

### Post by andpal222 on 2009-10-24
> **jward3010 said:**
> I'd say either within your router's configuration page or on your machine set your DNS servers as Primary: 208.67.222.222 and Secondary: 208.67.220.220. 

If you want to know how to do this, tell us.

EDIT: I should be clear, those server above are servers belonging to OpenDNS ([www.opendns.com](www.opendns.com)). A large, well known DNS server provider who have very good uptime.
i would actually like help on how to do this, thank you

---

### Post by jward3010 on 2009-10-26
Well we'll keep it easy by starting with network manager, I have the same network manager as you but not necessarily the same router config page and they can be simple or complicated.

1. Right click on network manager and click Edit Connections > Go to Wireless tab.
2. Pick the "Auto XXXXXXX" access point that you are currently connected to and hit edit.
3. Go to "IPv4 Settings" page and in the Method drop down box choose "Automatic (DHCP) addresses only". The DNS box will be useable now.
4. In "DNS servers" entry, type (without apostrophes or quotes) ```
208.67.222.222, 208.67.220.220
```
5. Click apply.

You'll now use these two DNS servers for DNS lookups as opposed to whatever your router was using.

---

### Post by andpal222 on 2009-10-26
> **jward3010 said:**
> Well we'll keep it easy by starting with network manager, I have the same network manager as you but not necessarily the same router config page and they can be simple or complicated.

1. Right click on network manager and click Edit Connections > Go to Wireless tab.
2. Pick the "Auto XXXXXXX" access point that you are currently connected to and hit edit.
3. Go to "IPv4 Settings" page and in the Method drop down box choose "Automatic (DHCP) addresses only". The DNS box will be useable now.
4. In "DNS servers" entry, type (without apostrophes or quotes) ```
208.67.222.222, 208.67.220.220
```
5. Click apply.

You'll now use these two DNS servers for DNS lookups as opposed to whatever your router was using.
Before i do this, will this effect the Windows XP partitoon on my computer? I have a perfect network in XP so i don't want to screw it up.

---

### Post by jward3010 on 2009-10-27
It wont cause the slightest problem with your Windows partition. It has absolutely nothing to do with it so don't worry there. How does XP work with internet out of interest?

---

### Post by andpal222 on 2009-10-27
> **andpal222 said:**
> Before i do this, will this effect the Windows XP partitoon on my computer? I have a perfect network in XP so i don't want to screw it up.
ok thanks! I have yet to see if i encounter the problems i wa shaving again but if i do i will notify you.

XP with interent... you can imagine.... Internet Explorer is the default browser ( this is the bad part) , it connects automatically and hasn't been too much of an issue. Im not too sure, i haven't run into problems that much with it and ubuntu is better in almost everything but this one little glitch i had.

---

### Post by jward3010 on 2009-10-27
If it is the DNS issue I think it is, then XP should be affected to the same degree (whenever it crops up that is). But see how you get on for a while. At the end of the day it depends how much you use each OS each time and whether you notice it happening in one more than the other (while also realising that if you use that particular one 90% more than the other you may notice crop up a lot more, in fact 90% more. Using both equally for a while is obviously best idea).

---

### Post by andpal222 on 2009-10-28
it dosen't happen in Xp, but after switching the DNS in ubuntu i encountered the same exact problem again shortly after switching it

---

### Post by jward3010 on 2009-10-29
Aww Gawd Damn IT!

This is a strange one, could be driver related. Doesn't seem to be related to either DNS or your router although it very much looks like a DNS issue unless you ran the commands (the earliest ones in this post) at co-incidentally the wrong time i.e. when the connection happenend to come back. How often is it at the moment and are you doing something specific when it does happen?

---

### Post by andpal222 on 2009-11-02
> **jward3010 said:**
> Aww Gawd Damn IT!

This is a strange one, could be driver related. Doesn't seem to be related to either DNS or your router although it very much looks like a DNS issue unless you ran the commands (the earliest ones in this post) at co-incidentally the wrong time i.e. when the connection happenend to come back. How often is it at the moment and are you doing something specific when it does happen?
Its usually not that often, i'd say once every other day if im lucky. It tends to happen more pften when i am down;loading something but it sometimes just happens around general web use

---

### Post by jward3010 on 2009-11-02
And does it end up killing the progressing download or does it continue and web surfing suffers or what? 

Do you use torrent?

---

### Post by andpal222 on 2009-11-03
It justs pauses the download and i can't go to any websites. For example, when it is stuck an i go to a website the status will be "looking for..."

no i dont us torrent

---

