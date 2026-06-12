---
title: "Resetting eth1 to original eth0"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by BlakeJustBlake on 2009-04-15
I changed the hwaddr of eth0 using:

```
ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
```

Then I restarted my system to reset the hwaddr, but now it's stuck with that hwaddr and shows it as eth1. I've tried things like:

```

#ifconfig eth1 down
#ifconfig eth0 up

```

But it always says:

```
eth0: ERROR while getting interface flags: No such device

```

Can anyone help me return back to my original MAC address for the NIC card and using eth0? I don't know what the MAC address originally was or I would just try changing it back manually.


I was trying to do this because I was setting up Ubuntu Server in my dorm room, but the dorm ISP requires you login to the network on a device before it can access anything. You have to do that graphically though. So I tried spoofing my MAC address on a workstation and logging in, but now it's stuck like this and the server still can't access the internet.

---

### Post by Iowan on 2009-04-15
MAC address should be on card/chip... Check **lshw -C network**. Also, */etc/udev/rules.d/70-persistent-net.rules* might list card/MAC/alias.

---

### Post by BlakeJustBlake on 2009-04-16
I used lshw -C network and it showed me the original mac address for my nic card. I changed it back and now everything is working again. Thanks.

---

