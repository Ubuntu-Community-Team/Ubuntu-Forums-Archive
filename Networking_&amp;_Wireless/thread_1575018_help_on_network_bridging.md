---
title: "help on network bridging"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by CyberAxe on 2010-09-15
Using Ubuntu Server 10.04 yesterday i tried setting up a bridge between a router in bridge mode and the nic deisgnated eth1 which seemed to work put them on their own subnet 255.255.255.0 with the ip's 192.168.0.255 and 254 (i originally had 255.255.0.0 the same as the rest of the network but i dont think that connected to the internet and i read on another topic they have to be on their own respective subnets)

I want to use eth1 as a gateway and for qos and such, the connection seemed to connect after running pppoe but the devices connected through eth0 couldnt connect when that ip address was set as the gateway.

here's my /etc/network/interfaces

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
      address 192.168.0.1
      netmask 255.255.0.0
      broadcast 192.168.255.255
      gateway 192.168.0.255
#      gateway 192.168.0.254

auto eth0:0
iface eth0:0 inet static
      address 192.168.1.2
      netmask 255.255.0.0

auto eth1
iface eth1 inet static
      address 192.168.0.255
#      netmask 255.255.0.0
      netmask 255.255.255.0
      broadcast 192.168.0.255
      gateway 192.168.0.255

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider
```

i was just wondering if the following line would be successfull just by adding it in solving the problem (as i dont want to take the network down again while people are using it just to test it)

```

auto br0
iface br0 inet static
      address 192.168.0.253
      netmask 255.255.0.0
      bridge-ports eth0 eth1
```

i also just found the following on the ubuntu documentation but dont know if they will be required

```

  pre-up ifconfig eth0 down
  pre-up ifconfig eth1 down
  pre-up brctl addbr br0
  pre-up brctl addif br0 eth0
  pre-up brctl addif br0 eth1
  pre-up ifconfig eth0 0.0.0.0
  pre-up ifconfig eth1 0.0.0.0
  post-down ifconfig eth0 down
  post-down ifconfig eth1 down
  post-down ifconfig br0 down
  post-down brctl delif br0 eth0
  post-down brctl delif br0 eth1
  post-down brctl delbr br0
```

I'm uncertain to weather this will work or not as all the configuration examples ive seen dont have both interfaces ips that are being bridged

also will this make the router interface accessable after its bridged via its ip address? (I imagine it will but on router/modem setups ive had before its not always been the case though obviously i wasnt accessing them on this level at the time)

Thanks

---

### Post by CyberAxe on 2010-09-15
I managed to try this configuration but it didn't work so i'm assuming theres either soemthing wrong with the bridging between eth1 and wth0 or i'm gonna have to find out more about NAT so the server can NAT eth0 to eth1

---

### Post by Iowan on 2010-09-15
I've been reading [this]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge") article on bridging, but haven't tried it yet...

---

### Post by dmizer on 2010-09-16
Unless you are doing this for learning experience, you'll be better off installing a gateway OS. For Ubuntu, there's [zentyal]("http://www.zentyal.org/") (used to be called ebox). I use [ClearOS]("http://www.clearfoundation.com/") on my own network.

Ebox can be installed from the commandline of your current server, and offers lots of tools for managing your gateway via a nice web interface.

---

### Post by CyberAxe on 2010-09-16
Thanks for the replies, that link on bridging looks promising.

It is partially a learning experience as i would like to know how to do it manually for lower spec servers and such, though i am contemplating installing ebox on this server in the future.

I'll post my progress on Monday when i'm back at work, thanks.

---

### Post by dmizer on 2010-09-16
> **CyberAxe said:**
> Thanks for the replies, that link on bridging looks promising.

It is partially a learning experience as i would like to know how to do it manually for lower spec servers and such, though i am contemplating installing ebox on this server in the future.

I'll post my progress on Monday when i'm back at work, thanks.

The problem with doing this manually with an Internet facing gateway server is that you will really have to know how to tweak IPtables correctly and accurately. I know of very few people who are proficient with IPtables.

While it can be a challenge and is a good idea for expanding your knowledge, it's best not to experiment with learning IPtables on a live, in-service machine. One small mistake or oversight could leave your entire LAN hanging out in the open.

---

### Post by CyberAxe on 2010-09-29
Finally managed to test the bridging it didnt work, while the connections seem to bridge the server didnt relay anything connected to eth0 not even the local dns, plus is tried configuring ufw for nat as shown on the documentation but that did not seem to work either, ugh this is prooving to be rather difficult.

---

