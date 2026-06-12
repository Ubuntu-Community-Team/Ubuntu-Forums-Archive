---
title: "transmitting bits via ethernet"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by vindsstar on 2009-06-26
[SIZE=3]Hi ! [/SIZE][-o<
[SIZE=3]I'm a new user for linux and for the forums.[/SIZE]
[SIZE=3]For networking, linux is the best. Isn't it?
but can i transmit raw bits (without a browser) to any destination addresses using ubuntu?.
Please help me how to do it.
Thanks:popcorn:
[/SIZE]

---

### Post by philcamlin on 2009-06-26
what are you trying to do ?? forgive me for being new to tis i have no idea what your talking baout rather then theres 8 bits in a bute :P:popcorn:

---

### Post by capscrew on 2009-06-27
> can i transmit raw bits (without a browser)...

Not raw bits.  You will need to use some application that will speak to a TCP/UDP socket.  The bit stream is only part of the equation.

For example you can ping another address.  Try this in the terminal

```
ping -c4 [some IP address]
```

Thsi uses the ICMP protocol and asks the target machine to respond.  The -c4 switch tells ping to send 4 packets to the IP address.

---

### Post by vindsstar on 2009-06-27
[SIZE=2]Thank you very much friends. :o
I like to create a LAN and i need to transmit some data(bits or bytes) within the LAN via UBUNTU. I can ping the other computer with the address provided by the server. But how to transmit data to the particular computer with UBUNTU. :confused:

[/SIZE]

---

### Post by DGortze380 on 2009-06-27
> **vindsstar said:**
> [SIZE=2]Thank you very much friends. :o
I like to create a LAN and i need to transmit some data(bits or bytes) within the LAN via UBUNTU. I can ping the other computer with the address provided by the server. But how to transmit data to the particular computer with UBUNTU. :confused:

[/SIZE]

What exactly are you trying to do?

If you actually want to work at the low level you're indicating here, you'll need to choose a programming language, and write yourself a couple of sockets to connect and do the transfer.

---

### Post by mpokrywka on 2009-06-27
For sending/receiving using TCP or UDP best command line tool is **netcat** (or **socat** if you need for example SSL connection)

If you need lower level access (on packet level) you can use **scapy** - but you need solid low level protocol knowledge + python programming skills

---

### Post by vindsstar on 2009-06-30
Thanks guys for directing me through a right way.
I'll refer it more.

---

