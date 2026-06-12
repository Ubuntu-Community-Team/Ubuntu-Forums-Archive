---
title: "Internet connection only on one computer"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-09-08
Running 2 computers, both 9.04, one is 32 bit, the other 64 bit. I used to run Firestarter on both computers, but have recently removed Firestarter on one, and installed UFW.

Computer A - 32 bit 9.04 , all updates and UFW
Computer B - 64 bit 9.04 , updates up until over a mth ago, and Firestarter

Computer A is okay, and can connect to the internet, however computer B cannot connect to the net at all. Today, decided to update Computer B and no internet ??

Obviously thought it was firewall related, but syslogs on both computers show no entries for either computer (i.e no 192.168.nnn.nnn entries).

Both computers can ping each other, computer A can ping anything, computer B cannot ping any domain, and it cannot ping any (outside) IP address.

As it has been over a month since doing updates on Computer B, have I mised an important update, to do with networking ??

I even booted to an old kernel, but still no internet connection.

When Computer A had Firestarter, it had the option for ICS, but UFW doesn't have this option, it seems. (Computer B gets out to the internet via eth1, as Computer A shares the connection).

Would appreciate some help on this please.  :(

Oygle

---

### Post by hal10000 on 2009-09-08
I suppose your Computer A serves as a router for your Computer B. That means, A has two network cards, one pointing to your modem and the other one to your Computer B, is that right?

If so, then you will need ICS or a corresponding mechanism, otherwise your Computer B will never get an Internet connection. I don't know anything about confiuring UFW, but i'm sure you can do that with it.

btw., why are you using two firewalls? It's usually sufficient if your router machine is running a firewall.

---

### Post by oygle on 2009-09-10
Unfortunately, I don't have a router. My internet connection is a USB dongle (wireless broadband). However my understanding of iptables (very limited) is that it is 'NAT' anyway.

In regards to ICS, yes, I will need that, and I'm fairly sure that is the problem; computer A _should_ have it, but it doesn't at present, and that is why computer B cannot use the internet.

Thanks,

Oygle

---

### Post by hal10000 on 2009-09-10
Where is your USB-Dongle which provides the internet connection plugged in?

If it's in Computer A, then Computer A actually is a router (a router always mediates between two networks). 
You can see this ifyou run [COLOR="Red"]ifconfig[/COLOR], then you will see, that computer A has two network connections established, probably one with an ip-address that starts with 192.168.X.Y and another one with a different ip-address

I just figured out that ufw is mostly used as a personal firewall, so it might not be the best choice for a router. I think the best would be if you install firestarter or another firewall software that can preserve NAT (and port forwarding) on Computer A and (only if you like) ufw on computer B.

---

### Post by oygle on 2009-09-13
> **hal10000 said:**
> Where is your USB-Dongle which provides the internet connection plugged in?

The USB dongle is in Computer A.

The [COLOR="Red"]ifconfig[/COLOR] command showed:

* lo (loopback)
* ppp0 (the USB connection with the ISP assigned IP address
* eth0 (IP 192.168.X.Y)

Thanks,

Oygle

---

