---
title: "No wired Internet on fresh 8.1 install on Dell X300 Latitude"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by TMarvelous on 2008-12-13
I did a fresh install on a Dell X300 Latitude.

My network info (top right of desktop) shows me a connected.
From my XP PC I can connect to my router and see that my router sees the laptop as connected and I have lights on the network port where my Ethernet cable is plugged in.

But I cannot see the internet.  Nor can I connect to my router at the default address.

I've scanned these forums and can't find help.

---

### Post by albinootje on 2008-12-13
Can you ping your router's ip-address ?
Can you ping ip-addresses on the internet ? 
For example 62.108.1.65
Did you enable a firewall ?

---

### Post by TMarvelous on 2008-12-13
Can you ping your router's ip-address ? NETWORK IS UNREACHABLE
Can you ping ip-addresses on the internet ? UNKNOWN HOST
For example 62.108.1.65
Did you enable a firewall ? YES - ENABLED ON ROUTER

My Windows XP PC is connected to same router with no issues.

---

### Post by TMarvelous on 2008-12-31
The same thing happened to an Ubuntu desktop I built a few days after this issue cropped up with my laptop.  I found this solution and it worked for both machines:

[http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install](http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install)

---

### Post by superprash2003 on 2009-01-01
post output of the following commands from the terminal
1)ifconfig
2)ping 72.14.205.100
3)cat /etc/resolv.conf

---

