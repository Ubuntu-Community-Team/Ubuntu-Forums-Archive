---
title: "Setting up a gateway to connect two cellphones on dynamic IP"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2012-02-21
I need to connect two GSM GPRS devices together.

cellphone_one will connect to mylaptop-dns.com on port 23(telnet)
cellphone_two will connect to mylaptop-dns.com on port 24

how can I make the computer mylaptop-dns.com forward all incoming data from cellphone_one to cellphone_two , and incoming data from cellphone_two to cellphone_one ?

- so - any data incoming with TCP connection to port23 - should be sent put to whatever connects to port 24.

This should be too easy in Linux, except I don't know how to do it .  :)

---

