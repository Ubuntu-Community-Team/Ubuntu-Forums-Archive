---
title: "Network Routing Question"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by igb on 2009-04-07
I want to set up an IP webcam on a computer in a different building. In the house I have a network in the 192.168.0.xxx range. I am using a wireless N router to connect to a computer in an outbuilding, which is also part of the 192.168.0.xxx subnet.

The computer in the outbuilding will have a second Ethernet card in addition to the wireless card, which will be connected to the IP webcam. I want to be able to view pictures from the webcam from the house network. If I make the ethernet card which is connected to the webcam part of the 192.168.0.xxx subnet, will the computer in the outbuilding be able to sort out the routing to the network in the house, via the wireless LAN itself? 

Would I be better off making the wireless interface and the ethernet interface into separate subnets and setting up routing explicitly?

Ian.

---

### Post by superprash2003 on 2009-04-07
is the computer which is connected to the IP webcam running windows or ubuntu?? you just need to bridge the connection..

---

### Post by igb on 2009-04-07
> **superprash2003 said:**
> is the computer which is connected to the IP webcam running windows or ubuntu?? you just need to bridge the connection..

It's running Ubntu. Eventually, I decided to create a new subnet and add a route as I will probably be adding more than one camera and creating a new subnet lets me be more flexible.

For anyone else who wants to do something similar you can just:

```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.80
wlan0
```

This routes addresses for the 192.168.1.x subnet through 192.168.0.80 (the computer with 2 cards). You can make this permanent by using:

```
up route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.80
wlan0
```

in the stanza for your card in /etc/network/interfaces

Ian.

---

