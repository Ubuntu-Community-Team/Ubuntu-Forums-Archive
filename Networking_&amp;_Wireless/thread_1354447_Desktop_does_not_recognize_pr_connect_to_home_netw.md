---
title: "Desktop does not recognize pr connect to home network"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by agargye on 2009-12-13
I just installed 9.1 and am unable to connect to my home network (wired) and therefore the internet.

I configured a connection manually providing a available ip and rebooted. didnt seem to help. When it rebooted however it seems to have recognized the network and created a new network with the correct mac address of my router.

But it still does not let me connect to or ping the router.

How can I troubleshoot the network connection or what "else" do I need to do to complete the connection?

I know for sure the nic was working on windows so that is not the issue.

Thanks fo your help

---

### Post by shairozan on 2009-12-14
Hey there, 

First, can you post the output of the ifconfig command?

```
sudo ifconfig -a
```

We want to make sure that the card is registering correctly. Now when you say you manually configured it, were you configuring it via the network manager or the /etc/network/interfaces file?

---

### Post by Iowan on 2009-12-14
> **agargye said:**
> I configured a connection manually providing a available ip and rebooted. didnt seem to help. When it rebooted however it seems to have recognized the network and created a new network with the correct mac address of my router.

But it still does not let me connect to or ping the router.
As mentioned, **ifconfig -a** will show if the interface has an address. Where did you see the new network with router MAC address?
Did you **ping** by name or IP address?

---

### Post by davidm84 on 2009-12-14
Also make sure if you are setting a static IP you also should set the default gateway. This may be one of the many things wrong. If you haven't set a gateway, ubuntu doesn't know where to go next to get to the Internet (but you should be able to ping the local network anyway).

---

### Post by shairozan on 2009-12-14
Indeed, the gateway is often the one piece people leave out when configuring a static addres. When working with networks, especially home networks, there are only three real parts (logically) that you need for your connection to work correctly

(1) IP Address - Needs to be on the same network as your router
(2) Subnet Mask - Needs to be the same as your router
(3) Default Gateway - Also known as your router. This basically tells the system where to send information when it has no idea about the destination. 

Thus, if you leave out the gateway, and your system doesn't know how to get to google.com, then you get packet timeouts.

---

### Post by agargye on 2009-12-15
I did assign the default gateway ip (my router) ... 
configured via the network manager (network connections)

Pinged by ip --- says network is unreachable ... checked connections too :)

**well ... this is embarrassing! **I was reviewing all my network connectionsso I unplugged and plugged the network cable (for the pc in question) at the router and the network came right up. It must just be a bad connection.

Thanks for all the help!

---

### Post by shairozan on 2009-12-15
Haha not a problem. Normally, we would investigate physical, or layer 1, issues first, but I thought it was the gateway, so I threw that in ;)

Glad everything is up and running though!

---

