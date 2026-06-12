---
title: "SSH into home PC"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by Shamess707 on 2010-07-29
So I have a PC in my office and at home. I can SSH just fine from my home to office, but I would like to go the other way. I am assuming that I have to forward some ports on my router. In the port forwarding section of my router I am given boxes named "port from" "protocol" "IP address" and "port to" I entered 22 for both port from/to, under protocol I put both tcp and udp and for ip address I put the local ip of my machine. Even with these settings I am unable to access my home machine from my office machine. Are there some more settings that I have to change? Thanks for the help in advance

---

### Post by HermanAB on 2010-07-29
Maybe you have SSH blocked in the UFW or Firestarter or some such?

On the home machine, try to connect to yourself and look at the error messages:

ssh localhost
ssh 192.168.1.2 (or whatever your machine IP address is)

and also via the router IP address.

---

### Post by Shamess707 on 2010-07-29
hmm I get an error saying the connection was refused when i try ssh localhost or my ip

---

### Post by Shamess707 on 2010-07-29
I did not have the ssh server installed. whoops. Thanks for the help

---

