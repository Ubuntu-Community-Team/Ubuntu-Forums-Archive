---
title: "can I use ubuntu as a network switch?"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by jmansfield04 on 2009-05-21
I have a ubuntu 9.04 system that I would like to use as a network switch. I have eth0 that is receiving a DHCP address from my Vonage router. I also have eth1 and eth2 in the ubuntu box, I would like to connect a PC to each and have them use the same DHCP server the ubuntu box is using. Is this even possible without making the ubuntu machine a router? I already have a DHCP server on my network (Vonage Modem).

---

### Post by Iowan on 2009-05-21
Not exactly the intended application, but [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page might help create a switch.

---

### Post by helgman on 2009-05-22
You might be able if you play around with the instructions [here]("https://help.ubuntu.com/community/NetworkConnectionBridge"). You'll have to adjust it a bit ...

Let us know if you run into trouble.

Regards,
Helgman

---

### Post by helgman on 2009-05-23
Here is what I did ...

*1.0 Setup*

I've got one Ubuntu Server 9.04 with for NICs.

eth0 is "management"
eth1-3 will be used as the bridge/switch

*1.1 Not a router*

```
server#cat /proc/sys/net/ipv4/ip_forward
0
```

*1.2 Management setup*

I set one interface as management so that I have one "out-of-band" connection to the computer while setting it up (I have to access it through the network). 

```
ifconfig eth0 172.16.0.1
```

*2.0 Setting up the bridge*

First of, let's remove any previous IP addresses (and stop any DHCP client that might be lurking in the background).

```
ifconfig ethX 0.0.0.0
```

(These instruction, and the tools needed, can more or less be found in the link I posted above.)

Now let's setup the actual bridge:

```
brtctl addbr br0
brtctl addif br0 eth1
brtctl addif br0 eth2
brtctl addif br0 eth3
ifconfig br0 up
```

And now the bridge should be up and running.

*3.0 Testing the setup*

By now it's time to connect one of the computers that should use the Ubuntu machine as a switch and see if it's working. When that is confirmed - activate the dhcp client

```
dhclient br0
```

- - -

That should be it ...

... modify to your own needs and let me know how it works out!

Regards,
Helgman

---

