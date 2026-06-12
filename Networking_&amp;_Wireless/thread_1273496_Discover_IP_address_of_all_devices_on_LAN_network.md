---
title: "Discover IP address of all devices on LAN network"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by rfkrocktk on 2009-09-23
I need to discover the IP address of every device connected to my LAN router. Is there a way I can do this in the shell easily?

---

### Post by eldragon on 2009-09-23
> **rfkrocktk said:**
> I need to discover the IP address of every device connected to my LAN router. Is there a way I can do this in the shell easily?

one solution would be to try and ping all hosts in the network and then check the arp table for complete entries

---

### Post by rfkrocktk on 2009-09-23
> one solution would be to try and ping all hosts in the network and then check the arp table for complete entries
So how might I do that? I have tried pinging the router itself, but it doesn't send back any useful info or send the pings on to all of the computers on the network. 
```
ping 192.168.1.1
```

---

### Post by cariboo on 2009-09-23
I use this:

```
sudo nmap -PR -sP 192.168.1.0/24
```

To scan all the systems on the network.

---

### Post by rfkrocktk on 2009-09-23
Running 
```
sudo nmap -PR -sP 192.168.1.1/24
```
Yields:
```
Starting Nmap 4.76 ( http://nmap.org ) at 2009-09-23 14:22 PDT
Nmap done: 256 IP addresses (0 hosts up) scanned in 0.10 seconds
```

I'd actually like to see the IP addresses and make sure they're actually live. Nmap looks like a powerful tool, I'll try to read the man pages. Any other suggestions?

---

### Post by p1t0u on 2009-09-24
> **rfkrocktk said:**
> So how might I do that? I have tried pinging the router itself, but it doesn't send back any useful info or send the pings on to all of the computers on the network. 
```
ping 192.168.1.1
```

```
for i in `seq 1 255`; do ping -c 1 192.168.1.$i; done
```will show you 1 ping per address.

```
sudo arp -a
```will confirm who answered without having to scroll through the 255 pings

---

### Post by superprash2003 on 2009-09-24
post output of **ifconfig** from your terminal to know more about your ip and gateway etc..

---

### Post by wojox on 2009-09-24
Log onto the router.

---

### Post by gcopenhaver on 2009-09-24
Try nmap again, but without the '-PR'.  I just tried it with '-PR' and it gave me the same output as it did for you.  Then I did it without '-PR' and it actually tried pinging other machines and gave me a list.

[HTML]nmap -sP 192.168.0.*  # change 192.168.0.* to whatever you need[/HTML]

---

