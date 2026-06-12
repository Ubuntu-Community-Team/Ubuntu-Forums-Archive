---
title: "problem with the eth0"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by ultimatebuster on 2009-09-02
A guy gave me this really old desktop (2.6Ghz Pentium, 4x512MB DDR Ram, 128MB ATI card), Want to use it as a testing server for php and stuff, so I install Ubuntu 9.04 32bit server on it. (It was Windows XP before, and i think the guy mentioned something about internet is not working, not too sure)

At install, it tells me DHCP config failed (epically). I skipped it
Now I can't connect to the network. I already edited eth0 to dhcp. No luck (as if I ever have any x.x)

Trying to restart /etc/init.d/networking will output:

> SIOCSIFFLAGS: Service temporarily unavailable.
SIOCSIFFLAGS: Service temporarily unavailable.
Listening on LPF/eth0/00:20:ed:7b:61:31
Sending on LPF/eth0/00:20:ed:7b:61:31
Sending on Socket/fallback
receive_packet failed on eth0: Network is down

But the network is fine. Ethernet is connected and fine (I hope). 

The ethernet controller is Intel 82562EZ 10/100. (Is that bad? jkjk)

Any ideas?

---

### Post by uylug on 2009-09-02
Are you sure your interface is enabled?

```
ifconfig
```

Can you see any eth0 interface?

If not, what is the output of:
```
cat /etc/network/interfaces
```

If there is a eth0 interface, try this:

```
sudo ifconfig eth0 up
```

If this works, see if you can get an ip:

```
sudo dhclient eth0
```

If this does not help, provide additional information by running:

```
sudo lshw -C network 
```

---

### Post by Charly85551 on 2009-09-05
Hi together,
you got already quite a good advice for manipulating the software. My experience is that the software of Ubunut 9.04 is extremely reliable and when it says eth0 not found then you might just considering the investment into a small interface card. It's the cheapest way!:(
cheers

---

### Post by shredder12 on 2009-09-05
> 
```
cat /etc/network/interfaces
```

If there is a eth0 interface, try this:



I am not trying to hijack this thread but out of curiosity.. I am using xubuntu 8.04 and using an ethernet connection to access internet (eth0 interface)
but my /etc/network/interfaces field just shows loopback interface..

Isn't it supposed to show all the network interfaces..

---

### Post by Iowan on 2009-09-05
Before Hardy, */etc/network/interfaces* contained the network configuration information. Beginning with Hardy, Network Manager started keeping it's information somewhere else (I have a hard time remembering where).Though easier in Jaunty, the previous two versions had ways to configure a manual (static) address.

---

