---
title: "Baffling hostname issue"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by jmoone on 2011-06-06
**Background:** I have an Asus netbook running a (more or less) fresh install of 10.04, formerly (pre)installed with WinXP, at which time my computer/network name was 'calvin-aegis'. I have formatted, wiped, and reinstalled more than once since then, and (as far as I can remember) I have never so much as typed that previous name on any linux installation. (I may be mistaken about that -- perhaps it was reused once on a previous ubuntu install, but still, the whole drive has been shredded since then).

**Problem:** I happened to run netstat earlier today, and noticed that 'calvin-aegis' shows up now under 'Local Address'!

/etc/hosts, /etc/hostname, and running 'hostname' without args all return the correct hostname, 'john'.

... Wha?

'Local Address' IS supposed to show my hostname, right?
Well, where is netstat getting this hostname, then? Clearly not from anywhere on disk?
Most importantly, how might I change it?


If anyone has any advice, speculation, or corrections, I'd greatly appreciate it. I've only been a regular linux user for ~6 months, so perhaps I'm just fundamentally misunderstanding something, here.

---

### Post by capscrew on 2011-06-06
> **jmoone said:**
> **Background:** I have an Asus netbook running a (more or less) fresh install of 10.04, formerly (pre)installed with WinXP, at which time my computer/network name was 'calvin-aegis'. I have formatted, wiped, and reinstalled more than once since then, and (as far as I can remember) I have never so much as typed that previous name on any linux installation. (I may be mistaken about that -- perhaps it was reused once on a previous ubuntu install, but still, the whole drive has been shredded since then).

**Problem:** I happened to run netstat earlier today, and noticed that 'calvin-aegis' shows up now under 'Local Address'!

/etc/hosts, /etc/hostname, and running 'hostname' without args all return the correct hostname, 'john'.

... Wha?

'Local Address' IS supposed to show my hostname, right?
Well, where is netstat getting this hostname, then? Clearly not from anywhere on disk?
Most importantly, how might I change it?


If anyone has any advice, speculation, or corrections, I'd greatly appreciate it. I've only been a regular linux user for ~6 months, so perhaps I'm just fundamentally misunderstanding something, here.

Speculation:  You have some remote service that you originated with "calvin-aegis".  You are still using that app and it uses the original name.  What is the Foreign Address using the name.  Is it a TCP/UDP connection?  Does it show up with ```
netstat -t
```

---

### Post by conradin on 2011-06-06
I'm with capscrew here, I would geuss your ISP may be assigning your hostname and or network alias. Are you by chance on a college campus?

---

### Post by doas777 on 2011-06-07
or it may be your router caching a hostname lookup. I'd check your router and powercycle it if you don;t find the name anywhere in your config.

---

### Post by jmoone on 2011-06-07
Yes, when running 'netstat -t', ALL active internet connections show 'calvin-aegis' as the hostname for the local address. 

No, I am not on a college campus. I don't know how my ISP could be assigning it... Currently, and ever since the most recent format/reinstall, I have been signed on to a family member's home wireless network. This laptop had been on this network before under the WinXP install, so I considered that the router may have remembered my MAC and was somehow responsible.

I haven't yet tried cycling its power, but logging in to the router's control panel does actually reflect that the correct computer/network name, 'john', is connected.

I was thinking that I might be able to spoof the MAC and check for any change, just in case, but I'm not sure that my wireless adapter allows that, or of how much hassle that test might be.

Edit: is it at all possible/heard of for a wireless adapter to store a hostname? This idea disturbs me.

---

### Post by capscrew on 2011-06-07
> **jmoone said:**
> Yes, when running 'netstat -t', ALL active internet connections show 'calvin-aegis' as the hostname for the local address. 

No, I am not on a college campus. I don't know how my ISP could be assigning it... Currently, and ever since the most recent format/reinstall, I have been signed on to a family member's home wireless network. This laptop had been on this network before under the WinXP install, so I considered that the router may have remembered my MAC and was somehow responsible.


I doubt it has anything to do with the MAC address.  Hostnames are mapped to IP addresses. 
> 

I haven't yet tried cycling its power, but logging in to the router's control panel does actually reflect that the correct computer/network name, 'john', is connected.

I was thinking that I might be able to spoof the MAC and check for any change, just in case, but I'm not sure that my wireless adapter allows that, or of how much hassle that test might be.

Edit: is it at all possible/heard of for a wireless adapter to store a hostname? This idea disturbs me.

Not likely as a network adapter communicates via MAC to IP address, not hostname at all.  

Can you post the output of ```
ping calvin-aegis
```

Somewhere your IP address is mapped to that hostname.  Do you use Network Manager to manage the interfaces?

---

### Post by jmoone on 2011-06-07
> I doubt it has anything to do with the MAC address.  Hostnames are mapped to IP addresses. Well, I can't cycle the router right this moment (like I said, it's not my network, I will have to wait), but we lost power the other night, so it has been cycled and the IP address has changed within the past 48 hours. There hasn't been any link between a machine named 'calvin-aegis' and this network for months.

Yes, according to 'sudo NetworkManager', "NetworkManager is already running".

ping results:
```
john@john:~$ ping calvin-aegis
PING calvin-aegis.gateway.2wire.net (192.168.1.70) 56(84) bytes of data.
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=1 ttl=64 time=0.092 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=2 ttl=64 time=0.057 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=3 ttl=64 time=0.061 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=4 ttl=64 time=0.058 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=5 ttl=64 time=0.059 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=6 ttl=64 time=0.060 ms
^C
--- calvin-aegis.gateway.2wire.net ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 0.057/0.064/0.092/0.014 ms

```

---

### Post by doas777 on 2011-06-07
> **jmoone said:**
> Well, I can't cycle the router right this moment (like I said, it's not my network, I will have to wait), but we lost power the other night, so it has been cycled and the IP address has changed within the past 48 hours. There hasn't been any link between a machine named 'calvin-aegis' and this network for months.

Yes, according to 'sudo NetworkManager', "NetworkManager is already running".

ping results:
```
john@john:~$ ping calvin-aegis
PING calvin-aegis.gateway.2wire.net (192.168.1.70) 56(84) bytes of data.
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=1 ttl=64 time=0.092 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=2 ttl=64 time=0.057 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=3 ttl=64 time=0.061 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=4 ttl=64 time=0.058 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=5 ttl=64 time=0.059 ms
64 bytes from calvin-aegis (192.168.1.70): icmp_seq=6 ttl=64 time=0.060 ms
^C
--- **[COLOR=Red]calvin-aegis.gateway.2wire.net ping statistics[/COLOR]** ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 0.057/0.064/0.092/0.014 ms

```

based on the bolded, it does look like an ISP registration, but your host may just be concatenating the hostname onto the local dns suffix. 
what do you have in /etc/resolv.conf?

---

### Post by jmoone on 2011-06-07
> but your host may just be concatenating the hostname onto the local dns suffix. 
This, I think? 
'gateway.2wire.net' == the local dns/192.168.1.254, and
'calvin-aegis.gateway.2wire.net' == 'calvin-aegis' == 192.168.1.70

/etc/resolv.conf
```
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
```

Also, in case it's relevant: Logging in to the router's control panel lists only the 4 currently connected machines under 'device list', and this machine is properly labelled there. When assigning firewall settings, there's a record of formerly connected devices, but 'calvin-aegis' is NOT one of them.

---

### Post by jmoone on 2011-06-07
Okay, guys. I think I've figured it out; it appears that I was right the first time around -- the router has been remembering the MAC addresses of every single device that has ever connected to it, whether it allows you to view/edit them or not.

Did this simple test:
```
ifconfig wlan0 down
ifconfig wlan0 hw ether 00:22:44:66:88:AA
ifconfig wlan0 up

```

Now the router's control panel lists my device twice -- once for each MAC address.

netstat is now showing all new connections with 'john' as the hostname.

I still don't entirely understand why this happens/is allowed in the first place, and would rather not spoof my MAC just to get a correct hostname, but short of resetting the router to factory settings, I'm not sure what recourse I have....

Thanks for all your help!

---

