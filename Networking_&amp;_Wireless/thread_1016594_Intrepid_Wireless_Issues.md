---
title: "Intrepid Wireless Issues"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Jimmy9pints on 2008-12-20
I have intrepid installed on 5 laptops (2 of my own and 3 of friends and family) and all of them have wireless and wired networking issues. 

Often it is fixed by going restarting several times or in the case of the dual booters, going into Windows, using the internet for a while, logging back out and going into Ubuntu. 

The laptops are all different ages and brands, so I don't see anything in common really. 

Often, the network manager icon doesn't even appear. 

Right now, my little laptop won't connect to the internet. Restarting doesn't help. 

```
ping google.com
``` gives ```
unknown host
```
```
ping localhost
``` gives 
```
ping: icmp open socket: Operation not permitted
```

```
sudo ifdown eth0 && sudo ifup eth0 
``` gives
```
ifdown: interface eth0 not configured
```
Which is strange because I am absolutely sure that the ethernet interface was labelled eth0 before.

I have tried changing /etc/network/interfaces from
```
auto eth0
iface eth0 inet dhcp
```
to
```
auto lo 
iface lo inet loopback
```

I didn't know what I was doing here, just having a stab in the dark.

So I have 5 laptops that all intermittently don't connect to the internet.

Furthermore, I have a friend who is suffering under a virus loaded Vista. I have suggested he would be much better off using Ubuntu. But given this burdensome problem I am now very reluctant to suggest this to him. 

If anyone can give me some advice or point me in the right direction for the ultimate Intrepid wired/wireless trouble shooting guide, I and my friends using Ubuntu would be very much obliged. 

James.

---

### Post by ieee488 on 2008-12-20
Running Intrepid 8.10 on my desktop.
The wired ethernet to Verizon DSL is rock solid.

Running Hardy 8.04 on my laptop.
Wired ethernet and wireless (open network) and mobile broadband (AT&T Aircard 860) are also rock solid.

Something doesn't sound right for your setups that all 5 have problems.

---

### Post by Jimmy9pints on 2008-12-20
I quite agree! 

Sorry this thread is a duplicate. 

The original is [here.]("http://ubuntuforums.org/showthread.php?t=1016593")

Mods please lock this.

---

