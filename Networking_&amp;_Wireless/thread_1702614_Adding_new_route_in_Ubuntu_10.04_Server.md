---
title: "Adding new route in Ubuntu 10.04 Server"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by gpdas on 2011-03-08
Hi all
I have assigned IP 172.25.1.194 netmask 255.255.255.0 gw 172.25.1.224 in my server.
Now I want to add 10.210.0.0 netmask 255.255.0.0 gw 172.25.1.1 as new route. Both of them are required. How to do this in command line?
Thanks in advance.

---

### Post by koszta on 2011-03-08
for testing purposes (wont stay there after boot) you can use
```
ip route add 10.210.0.0/16 via 172.25.1.1 dev eth0
```
=> assuming eth0 has 172.25.1.1

=> can check it by route -n

- adding it permanently (will work after boot):
you can create init script with the command above...

---

### Post by gpdas on 2011-03-08
Thank you for giving attention. But my problem is not solved. After typing this command, it showed me the routes in response to the 'route' command. Still I could not ping to 10.210.69.46. Then I restarted service by the command #/etc/init.d/networking restart.
Then the routes vanished. In Redhat I have done this and a file 'route-eth0' has kept this information. Please tell me how to do it in Ubuntu Server.

---

### Post by gpdas on 2011-03-09
I added the following line in /etc/network/interfaces and my problem is solved.
up route add -net 10.210.0.0 netmask 255.255.0.0 gw 172.25.1.1 dev eth0

---

