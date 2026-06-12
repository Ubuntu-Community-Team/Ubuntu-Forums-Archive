---
title: "Need to change eth0 back to be primary nic"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by iMPR3SSiON on 2011-03-16
Hi,

I've been fighting with this nearly for three hours, but nothing seems to be working. I have one Gigabit Realtek chip integrated on my Mainboard (which I use for internet connection), and one aditional 100Mbit in PCI slot. So, I basically want to use this 100Mbit for testing purposes, but when I connect something to this 100Mbit NIC adapter, it becomes default and I can not access internet. So, I want to set my eth0 (gigabit integrated adapter) as default adapter. Can somebody explain me, how to do it? Thanks.

P.S. I've tried to edit /etc/network/interfaces and iftab, but nothing worked.

---

### Post by iMPR3SSiON on 2011-03-17
bump

---

### Post by BkkBonanza on 2011-03-17
You can set the interface IP address value with the **ifconfig** command. The /etc/network/interface file will set them too but only when networking is restarted or system rebooted.

eg.
sudo ifconfig eth0 192.168.0.1 
sudo ifconfig eth1 192.168.2.1

Also ensure the routing is correct by checking output of **route -n** command. Post here if unclear. It should be showing the default gateway going to your internet facing interface. eg. mine,
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```
The destination 0.0.0.0 means "anything else", which is where stuff goes when it's not for the 192.168.2.0/24 network above (ie.the internet). See it says to send this to 192.168.2.1 on interface eth0. Normally this route info is set correctly by ifconfig but it can be wrong sometimes and then you need to alter it. It can also be configured in the interfaces file using the "gateway" setting.

If this doesn't seem to help then post output of ifconfig and interfaces file here.

Another factor is if you have NetworkManager running. It has an awful habit of taking over and trying to automate the interfaces, over writing the interfaces file. If you want manual control you'd be better to remove NetworkManager and set the interfaces file yourself, or as I do, install Wicd instead, which doesn't take over like it's King o'the Network.

---

### Post by iMPR3SSiON on 2011-03-17
Oh, thanks a lot for the reply!

But ... Now my Ubuntu 10.10 seems not to be able to find my secondary 100Mbit/s NIC :( Can't figure out why. How can I reset everything? So, first of all, uninstall network manager, then edit interfaces file (can I use dhcp parameter too? and ... what means inet as a parameter?) and I am done? And to set my gigabit device to be "default", I have to put in "gateway 0.0.0.0" only? Thank you a lot! :)

P.S. Earlier the day I have edited something and now my NetworkManager says instead of "auto eth0" "ifupdown (eth0)" ... what is wrong with that?

---

### Post by BkkBonanza on 2011-03-17
Yes, for a custom config like this you may be better removing network-manager.

sudo apt-get remove network-manager

Edit the interfaces file to have two sections one for each network card. You don't want 0.0.0.0 as the gateway, you want the actual IP address of your router connected to the internet.

Here's an example but you will need your own values, 
(this is my router interfaces file)
```

# The loopback network interface
auto lo
iface lo inet loopback

# The WAN network interface
auto eth0
iface eth0 inet dhcp
    gateway 192.168.1.241
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255

# The LAN network interface
auto eth1
iface eth1 inet static
    address 192.168.2.1
    network 192.168.2.0
    netmask 255.255.255.0
    broadcast 192.168.2.255


```

Use **iface ethX inet dhcp** when you want it to get it's IP from the DHCP server, and use **iface ethX inet static** when you manually set it's IP value. For your internet facing network you likely want dhcp but for your test interface you may not if there is no DHCP server on that network segment. You only want a gateway statement if there is a router on that segment that can get out to another network. ie. single network = no gateway, multi-network (like internet) = need gateway. Your router is your gateway.

**inet** is just the address family, for normal stuff that's what you want. See **man interfaces** for more details. You can do so much more here as well but this is the basics that should get you started. 

After editing interfaces you must restart with,

sudo /etc/init.d/networking restart

---

### Post by iMPR3SSiON on 2011-03-17
Thank you a lot again, I really appreciate your effort!

My Ubuntu still doesn't see the test NIC adapter! How can I force it to "rescan" for new adapters or what not? I have configured interfaces file pretty much as you posted before, because I have basically the same network arrangement.

```

lshw -C network

```

shows only Gigabit adapter. Why? I don't get it ...

---

### Post by BkkBonanza on 2011-03-17
You should see it when you type the **sudo ifconfig -a** command. If it's there then it's just matter of bringing it up, **sudo ifconfig eth1 up** (assuming eth1, chg to suit).

If it's not listed and it was working before then it sounds like a loose card issue. Shutdown. Re-seat the card to be sure it isn't loose. Boot up. Hopefully it will show up. In general, with cards like this that did work, they should still work unless there is now driver or hardware issues, which would be a bit unusual. There isn't a re-scan type function. During boot the card should be detected and a driver loaded.

---

### Post by iMPR3SSiON on 2011-03-17
Well, I just can not thank you enough! It works! I've changed this test 100Mbit/s NIC for another one I have (also 100Mb), Ubuntu sees it and config is just working as it should be! Amazing! But I have one simple question: I have done about 3 Cisco CCNA Courses (I am not total newbie to networking at all) and I can see metric 100 from my routing tables on my default route (0.0.0.0). Why this number is so high? :) 169.254.0.0 is some Samba crap. It doesn't matter.

```

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

---

### Post by BkkBonanza on 2011-03-17
I never really paid any attention to that but checking **man route** indicates that recent kernels no longer use the metric value. So I guess they just get set to some default arbitrary value.

---

