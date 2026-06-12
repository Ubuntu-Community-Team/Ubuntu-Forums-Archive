---
title: "Get IP addresses on computers on home LAN?"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2012-12-14
How do I find the IP addresses of all computers that are using my wireless home LAN?

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> How do I find the IP addresses of all computers that are using my wireless home LAN?

Log into the router and look at the DHCP lease list or Attached Devices list.

Or use NMAP to scan your network or one of the many other network scanning tools

---

### Post by sudodus on 2012-12-14
Install and use arp-scan :-)

```
sudo apt-get install arp-scan
```
Get the active network connection on your computer with
```
ifconfig
```
and use that with the I option for arp-scan like this:
```
sudo  arp-scan -l -I eth0
```

*Edit:* it might work also without the I option:
```
sudo  arp-scan -l
```

---

### Post by haqking on 2012-12-14
> **sudodus said:**
> Install and use arp-scan :-)

```
sudo apt-get install arp-scan
```Get the active network connection on your computer with
```
ifconfig
```and use that with the I option for arp-scan like this:
```
sudo  arp-scan -l -I eth0
```*Edit:* it might work also without the I option:
```
sudo  arp-scan -l
```

It might not work if in Wireless isolation mode and will depend on the level of encryption, also eth0 wont work either as the OP is talking about wireless so to the OP it will likely be wlan0 or wlan1 etc

If it your wlan then log into the router, simple

---

### Post by PDA1 on 2012-12-14
I'm trying to use the "Connect to Server" option from "Places (Ubuntu 12.04) so I guess I really need to know the "connection information" IP address of all the computers on my wireless network. The "Connection Information" can be found by clicking on the wireless icon on my taskbar.

While logging into my router will show an IP address for the computer I'm using, the command ifconfig (looking for wlan0) will show a different IP address.

What now?

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> I'm trying to use the "Connect to Server" option from "Places (Ubuntu 12.04) so I guess I really need to know the "connection information" IP address of all the computers on my wireless network. The "Connection Information" can be found by clicking on the wireless icon on my taskbar.

While logging into my router will show an IP address for the computer I'm using, the command ifconfig (looking for wlan0) will show a different IP address.

What now?

Logging into your router if you go to the right place will show you the IP addresses of all the machines connected to it at that time.

So you are saying you have a different IP address to the one that router is telling you it has given you ?

---

### Post by PDA1 on 2012-12-14
Yes, the router is showing a different IP address for my machine than Connection Information (after clicking the wireless icon). The IP address I want to see of all computers  on my LAN are the ones found by clicking on the Connection Information icon on the taskbar.

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> Yes, the router is showing a different IP address for my machine than Connection Information (after clicking the wireless icon). The IP address I want to see of all computers  on my LAN are the ones found by clicking on the Connection Information icon on the taskbar.

Since when does connection information show you all the machines on your LAN ?

and if it does, then you already have it dont you ?

You need to show us a screen dump of what you are referring to for more help, are you sure the router is showing you as having a different address to the actual machine ?

---

### Post by sudodus on 2012-12-14
Sorry for writing eth0 instead of wlan0, and thanks for clarifying, haqking!

If you use arp-scan you will get pairs of
IP address and MAC address, that should match for each network unit. It works for me both with wired and wireless LAN.

The same information should be available from the router, and you should be able to identify network units with addresses (router, computers, printer etc). These addresses should correspond to each other unless you have something in between (hardware or software), that changes the addresses.

---

### Post by PDA1 on 2012-12-14
> **haqking said:**
> Since when does connection information show you all the machines on your LAN ?

and if it does, then you already have it dont you ?

You need to show us a screen dump of what you are referring to for more help, are you sure the router is showing you as having a different address to the actual machine ?

It doesn't. I have to physically go from computer to computer and check the Connection Information.

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> It doesn't. I have to physically go from computer to computer and check the Connection Information.


well if you can show us a screen dump of the router and your ifconfig that would be helpful

---

### Post by PDA1 on 2012-12-14
Figured it out!

What a dummy I am...borderline moron.

The advice you folks were providing was correct.

I couldn't access one of the computers I wanted to connect to because that computer didn't that fancy SSH (whatever-it's-called) program installed so I can access it via the Places---->Connect to Server.

Sorry to trouble you.

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> Figured it out!

What a dummy I am...borderline moron.

The advice you folks were providing was correct.

I couldn't access one of the computers I wanted to connect to because that computer didn't that fancy SSH (whatever-it's-called) program installed so I can access it via the Places---->Connect to Server.

Sorry to trouble you.

happens everyday ;-)

Welcome.

Peace

---

### Post by sudodus on 2012-12-14
You are welcome, I'm glad you solved the problem :-)

---

