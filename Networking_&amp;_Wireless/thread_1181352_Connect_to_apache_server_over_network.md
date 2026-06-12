---
title: "Connect to apache server over network"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by zephyrcat on 2009-06-07
I have a localhost apache server set up on one machine for testing. Is it possible to connect to this from another computer on the same network without making the server available to the internet?

(I need to test something involving PHP session variables.)

Thanks!

(Sorry if this is the wrong section.)

---

### Post by Iowan on 2009-06-07
Your router will be the biggest influence over whether the server is available to the internet.  Without port forwarding, it *should* be difficult to access the server from outside your local network.

---

### Post by zephyrcat on 2009-06-07
Thanks. You indirectly told me the answer. :-)

For anyone else wondering, this is actually really simple. By default the LAMP server is accessible from other machines (as mentioned your router will probably block it off from the rest of the internet), so you just need to get your ip. Type ifconfig in the terminal and look for the right interface (wlan0 or eth0 usually) and type that in to another computer's web browser.

---

### Post by Iowan on 2009-06-07
Oops! :oops:
Guess I was answering the wrong question - I thought the question was about exposing the server to the internet.  Glad you found the answer anyway...

---

### Post by dmizer on 2009-06-07
> **zephyrcat said:**
> Thanks. You indirectly told me the answer. :-)

For anyone else wondering, this is actually really simple. By default the LAMP server is accessible from other machines (as mentioned your router will probably block it off from the rest of the internet), so you just need to get your ip. Type ifconfig in the terminal and look for the right interface (wlan0 or eth0 usually) and type that in to another computer's web browser.

You can go a step further.

On the client computer (not the server), you can give your server a name by editing /etc/hosts. That way, you can browse to [noparse]http://server-name[/noparse] rather than having to enter the IP address.

Here's an example from my own network:
```
127.0.0.1       localhost shinkansen
127.0.1.1
192.168.24.53   www-testing

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

