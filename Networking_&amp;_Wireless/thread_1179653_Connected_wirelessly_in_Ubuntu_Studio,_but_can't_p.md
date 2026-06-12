---
title: "Connected wirelessly in Ubuntu Studio, but can't ping anywhere."
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by Nixie Pixel on 2009-06-05
Hi, I have recently moved to Ubuntu Studio on my work laptop (for the nice multimedia tools) and really like what I have seen so far, except for one problem - I can't get wireless to work.

My router and AP are running WPA, and I'm able to connect, authenticate, and get an IP address on the correct range without an issue. But when I try to ping a computer on the network, including the internet router and the wireless access point, I am told that the destination host is unreachable.

Can anyone help me troubleshoot this problem?

Thanks!

Edit:  I have manually added network-manager-gnome which is what I used to get this far.

---

### Post by qbprog on 2009-06-05
Sounds like an interesting problem. How about the output from the following commands:

```
ifconfig -a
``````
route
``````
sudo iptables -L
```Might help narrow it down some.

---

### Post by Nixie Pixel on 2009-06-06
Hmm, after shutting down the laptop and moving it twice, upon reboot I can now both ping computers on the network and connect to the internet.

So I have no idea why it suddenly began working with any changes, but...now it does.

Thanks for your help!

---

### Post by veruus on 2009-06-06
> **Nixie Pixel said:**
> Hmm, after shutting down the laptop and moving it twice, upon reboot I can now both ping computers on the network and connect to the internet.

So I have no idea why it suddenly began working with any changes, but...now it does.

Thanks for your help!

Magic! :D

---

### Post by Bios Element on 2009-06-06
> **veruus said:**
> Magic! :D

Or more likely, the flying monkeys woke up and decided to get to work. ;)

---

### Post by bigbrovar on 2009-06-06
> **Nixie Pixel said:**
> Hmm, after shutting down the laptop and moving it twice, upon reboot I can now both ping computers on the network and connect to the internet.

So I have no idea why it suddenly began working with any changes, but...now it does.

Thanks for your help!

net time have have a connection and u experience the same problem, Try ```
sudo dhclient 
```

---

