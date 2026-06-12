---
title: "How to run transmission-daemon on a secondary interface"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by sona1111 on 2012-06-25
(i think i put this in the wrong category, sorry for repost)

I have a web/file/halo/etc server going with a main fast  connection, and i also have a slower connection that i want to make use  of. (two separate modems) So basically i want every single thing on the  server to use one interface EXCEPT transmission-daemon, which i want to  use the other. i also want remote connections to go through the main  interface, only the traffic itself goes through the secondary. (both  already have static ips)

Transmission looks like it has this all good to go in its settings.json  file, where you can set a bind ip for both the remote and regular  connections. However, changing it to the ip of the other connection does  nothing, it just uses the main connection. (even after restarting the  daemon, yes)

I have heard you need to mess with iptables or something to get this to  work, but i could not find a tutorial applying to transmission. can  anyone tell me how to do this?

thanks for reading.

---

### Post by sona1111 on 2012-06-26
bump

---

### Post by sona1111 on 2012-06-26
also how do i delete posts? like the useless "bump" ones?

---

### Post by sona1111 on 2012-06-28
bump

---

### Post by papibe on 2012-06-28
Hi sona1111.

I've never done this, but there is a way to 'bind' transmission-daemon to a particular IP address. Since you have to connections, I imagine you'll have 2 public IPs.

From transmission's man page:
```
-i --bind-address-ipv4
             Listen for IPv4 BitTorrent connections on a specific address.
             Only one IPv4 listening address is allowed. Default: 0.0.0.0 (All
             addresses)

```

Also, take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1472045&highlight=transmission+vpn") as an example. It is not exactly your case, but it does use of the binding functionality (in this case to a VPN).

I hope that points you in the right direction.
Regards.

---

### Post by sona1111 on 2012-06-30
i have tried that bind address setting many times in a frustratingly large number of test configurations. it either does not transfer at all or just transfers on the other connection.

---

### Post by sona1111 on 2012-07-04
bump

---

### Post by sona1111 on 2012-07-07
If anyone else ende up reading this thread, i finally got it today. 

follow the first half of this guide (everything before load balancing): [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

MY problem was that in the "ip network" ($P1_NET in the guide) i put 192.168.3.0 when it should have been 192.168.3.0/24. Dont forget the CIDR. 

thank you for anyone else who tried to help.

---

### Post by SirKingChase on 2013-02-25
I patched transmission-daemon with [https://trac.transmissionbt.com/ticket/2313](https://trac.transmissionbt.com/ticket/2313)

Now all I have to do is screw around with the routing tables to get Wlan0 to receive back requests.  

I cant figure out how to do this.  Its so hard and confusing.  

If you have two interfaces linux routes all traffic from the second one through the first one but default.

I want all requests that are on Wlan0, to stay with Wlan0
I want all Eth0 requests to stay with Eth0.

I do not want the data from Wlan0 to get routed through Eth0

This guy details it exactly how I want it.... I followed his guide and it doesnt work

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

Found this guide that is easier to read and basically does the same thing..... doesnt work

[http://www.rjsystems.nl/en/2100-adv-routing.php](http://www.rjsystems.nl/en/2100-adv-routing.php)

Just for giggles ( I needed a break after working on the above ALL DAY ) I tried my hand at bonding

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

....Crashed and burned there as well

---

