---
title: "Laptop won't connect to LAN wirelessly"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by jfed on 2011-07-26
First off the bat this is a verizon router

I am trying to play Minecraft in a LAN server with a friend, the only problem is that I only have one available Ethernet cable, so for the other computer I was going to connect to my router wirelessly. The LAN router I am using for this right now used to be my family's regular router for use of connecting to the internet, and what not. Now I am just using it to play LAN games, it used to have encryption on it and whatnot, and I couldn't remember my old password for it, so I gave it a factory reset. I then went to the admin page for the router, 192.168.1.47 (in the URL bar) and i turned everything but wireless off, there is no security, no firewall, no encryption, now WEP, nothing. The issue is that whenever I try to connect to it via wireless on my friend's laptop, it tries to connect for some time, then tells me the connection failed, and it was unable to get IP address. Is there anything I can do to fix this? Any help is appreciated, thanks in advance.

---

### Post by wildmanne39 on 2011-07-26
Hi, run these commands in a terminal please
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by newbie-user on 2011-07-27
Check to see that the DHCP server is enabled on the router.  Also check that you aren't using any MAC filtering.

---

