---
title: "Ekiga through SSH tunnel?"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by abandonedthe_mulletator on 2009-01-31
I am trying to use ekiga and it is blocked by the firewall.
At home I have a Ubuntu server which I can connect to with SSH.
Is it possible to use a SSH tunnel for ekiga?

I have never used an SSH tunnel before but I believe that is what I need to get around the firewall.
I read that I could use the gnome network proxy in system>preferences>network proxy but i had no luck.

I ran ```
ssh -N -f -D 8080 me@server.net
```

and put 127.0.0.1 and port 8080 in the gnome proxy window.

Am I out to lunch here or what?

---

### Post by dmizer on 2009-02-02
Well, I'm just starting to look into this as well. Let me know if you find something. I haven't yet.

---

### Post by dmizer on 2009-02-02
Found the answer faster than I though.

Not good news though. SSH can only forward TCP. Ekiga needs UDP, so you'll have to configure openvpn.

---

### Post by kevdog on 2009-02-02
Never really thought about ssh only handling tcp.  Interesting.  What about maybe using tsocks?  This would allow ekiga to use a socks proxy?  I'm not sure if this even makes sense.

---

### Post by dmizer on 2009-02-02
Yeah, that's why you can't get DNS over an SSH tunnel (DNS is also UDP). I should have known when I first started researching this, but the TCP/UDP thing slipped my mind somehow.

tsocks is also TCP. Point in fact, the SSH proxy tunnel switch (-D port) is also a tsocks proxy.

The only thing I can think of that would make this work is VPN.

---

### Post by abandonedthe_mulletator on 2009-02-04
Can you use VPN without X?
My server runs on command line only.
There has got to be a way to do a UDP proxy.

That's a bummer about SSH.  I had high hopes.

---

### Post by pdtpatrick on 2009-02-04
you should be able to setup vpn using commandline. Have you tried openvpn?? btw .. how are u using commandline only and running ekiga?

---

### Post by dmizer on 2009-02-04
> **the_mulletator said:**
> Can you use VPN without X?
My server runs on command line only.
There has got to be a way to do a UDP proxy.

That's a bummer about SSH.  I had high hopes.
Yes, this would be no problem. Though OpenVPN configuration is something of an enigma. Here's some documentation to get you started: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

> **pdtpatrick said:**
> you should be able to setup vpn using commandline. Have you tried openvpn?? btw .. how are u using commandline only and running ekiga?
It is easy to make calls from computer to computer as long as you are on the same subnet. The problem is calling across NAT. If you can tunnel Ekiga's sip through VPN (or as was hoped earlier ... ssh) so that Ekiga is on the same subnet as the remote computer, then it's easy (and secure) to make the call; just type sip:192.168.1.x and off you go.

---

### Post by ktrnka on 2009-02-11
> **dmizer said:**
> Yeah, that's why you can't get DNS over an SSH tunnel (DNS is also UDP). I should have known when I first started researching this, but the TCP/UDP thing slipped my mind somehow.

tsocks is also TCP. Point in fact, the SSH proxy tunnel switch (-D port) is also a tsocks proxy.

The only thing I can think of that would make this work is VPN.

It is possible to tunnel udp through ssh. The tutorial is specifically about tunneling DNS traffic but with some modification you might be able to, although I have not tried it myself. SSH is great! It can do pretty much anything! :)

Link:

[http://zarb.org/~gc/html/udp-in-ssh-tunneling.html]("http://zarb.org/~gc/html/udp-in-ssh-tunneling.html")

---

### Post by dmizer on 2009-02-11
I dug that up when I was looking for a solution myself. Even if you do manage to accomplish that method to reliably forward UDP, DNS is one thing but VoIP traffic would be afflicted by too much fifo latency.

---

### Post by ktrnka on 2009-02-12
>  I dug that up when I was looking for a solution myself. Even if you do manage to accomplish that method to reliably forward UDP, DNS is one thing but VoIP traffic would be afflicted by too much fifo latency.

haha yea, very true, though I'm still curious about how bad it would be. I just might try it anyway and see how it sounds.

---

### Post by daudag on 2009-02-19
How does it run?

Please leave a note with your expirience. I am mostly blocked by firewalls in hotels.

Greetings
Hans

---

