---
title: "eth0 connection problems with new install of 12.04"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by professor-g on 2012-06-18
Hi,
Just installed 12.04 64-bit server edition on the following hardware setup (below) and cannot get eth0 to connect to the gateway; using the NIC on the mother-board.

I CAN self-ping the address I set, but cannot ping the gateway. Have ensured gateway is fine (with other machines).

Tried putting the freshly installed harddrive into another one of my machines thats online, same thing (can self-ping, but no pinging out to gateway). 

I have a feeling it is something with the mother-board, else 12.04 itself ... ?!?

/etc/network/interfaces is as follows:

auto eth0
iface eth0 inet static
address xxx.yyy.zzz.138
netmask 255.255.255.0
gateway xxx.yyy.zzz.252

Tried setting eth0 to eth1, ifdown ethX, ifup ethX ... nothing.

Also tried using the university's DHCP ... it hangs (for-ever and then-some).

Finally tried installing Lubuntu 11.10 - same thing.

Are there any known probs with the following hardware ?!? (I give full details for completeness). Please advise. Thx in advance.

G.

--
MBOARD: Asus Sabertooth X79
CPU: Intel I7-3930K
RAM: 4x4G Corsair DD3 @ 1600 MHz
HDD: 2Tb Seagate SATA
--

---

### Post by professor-g on 2012-06-18
To add to my previous posting re. eth0 problems connecting to gateway.


In actuality, I only need to get on the net to install openssh-server so as to be able to ssh into these machines (serving as nodes). After the fresh install, I cannot ssh into them, hence I solved this problem in the past this way - put the node on the net for a bit, update, then install packages I want/need (i.e. openssh-server), then it goes back to being on internal network.

If I set an internal network IP (i.e. 192.168.0.41) the node in question can ssh fine into my server (192.168.0.1), itself on the net through a 2nd NIC (external).

However, I cannot ssh into the node from the server!

Sadly, even though I chose to install ssh-server when opted during server install, it doesnt help anything.

Perhaps this helps shed light on things?
Please advise.
Thanks all.

G.

---

### Post by chili555 on 2012-06-19
> Tried setting eth0 to eth1,This makes no sense to me at all. It only makes sense to use in /etc/network/interfaces, the number that the machine assigns to the physical hardware. What is it?```
ifconfig
```If it's eth0, you have to use eth0 in *interfaces* and none other. Please run:```
sudo lshw -C network
```Please find out the driver associated with eth0, or whatever it is. Here is an example from my machine:>  *-network       
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: xx:de:f1:3e:b2:xx
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=e1000e[/COLOR] driverversion=1.5.1-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pairWe'd like to know what the driver is and if it reports link=yes. Next, see if there are any interesting kernel messages about this:```
dmesg | grep -e eth -e [COLOR="Red"]driver[/COLOR]
```Of course, substitute the actual driver name here.> I give full details for completenessBut you did not. We don't know what kind of ethernet card you have or the driver or if there even *is* a driver. 

One of the wise-guys in the back room bet me there is no working driver yet and therefor no interface to configure.

---

### Post by professor-g on 2012-06-20
> **chili555 said:**
> This makes no sense to me at all. It only makes sense to use in /etc/network/interfaces, the number that the machine assigns to the physical hardware. What is it?

Acknowledged.
I had of course set eth0 --> eth1 within /etc/network/interfaces
Physically assigned address is eth0 *However* I have had the case where the machine assigns eth1 ... stumped as to why?!?

I have run into this problem before, particularly when using on-board NICs. Specifically, that networking would only work if I had set as eth1 within /etc/network/interfaces.

In fact, of these 8 nodes here (identical hardwares as previously described), one of them is displaying this characteristic. Only works with setting to eth1.

All good - as long as it works.


> Please run:```
sudo lshw -C network
```Please find out the driver associated with eth0, or whatever it is. Here is an example from my machine:We'd like to know what the driver is and if it reports link=yes.

Output is near-identical to your-own, with few differences (below).
Importantly, link=yes appeared ... and then after reboot it states link=no. (???) On other nodes (identical setups) it reports link=no
Please elaborate on what this means.

> *-network
description: Ethernet interface
product: 82577LM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 05
serial: c8:60:00:a5:fa:33
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair


> Next, see if there are any interesting kernel messages about this:```
dmesg | grep -e eth -e [COLOR="Red"]driver[/COLOR]
```Of course, substitute the actual driver name here.

Output (of interest) is as follows:

> 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
0000:00:19.0: eth0: Mac: 10, PHY: 11, PBA No: FFFFFF-Off
(ADDRCONF(NETDEV_UP): eth0: link is not ready

link not ready sounds suspect ... driver?

As previously posted, I can set an internal IP for this node (192.168.0.40) and ssh into my server (192.168.0.1), hence can scp the driver from the server.

QUESTION - why is it that I can connect to the server on internal network, ssh from node-->server, scp stuff server-->node, buit CANNOT ssh into the node from the server?!? Error is as follows - where I typically remedy this by apt-get installing openssh-server:

> ssh: connect to host 192.168.0.40 port 22: Connection refused

> But you did not. We don't know what kind of ethernet card you have or the driver or if there even *is* a driver.

Apologies to not be explicit.
As stated, using on-board NIC, specifically on this ASUS Sabertooth X79.
Accordingly, LAN = Intel 82579V Gigabit LAN controller

> One of the wise-guys in the back room bet me there is no working driver yet and therefor no interface to configure.

Acknowledged on this prediction.
Thanks again to you, Mugsy, Bugsy and the rest 'youz-wise-guys'.

G.

---

### Post by chili555 on 2012-06-20
> Next, see if there are any interesting kernel messages about this:```
dmesg | grep -e eth -e driver
```

Of course, substitute the actual driver name here. It appears that you actually used the word 'driver' here, not the name of the driver, e1000e. I asked that you substitute the name of the driver. So what does dmesg report?```
dmesg | grep e1000e
```> link not ready sounds suspect ... driver?Maybe; we'll know more when we see what the message file says.> I have had the case where the machine assigns eth1 ... stumped as to why?!?As have I. I think udev hiccups once in a while and uses eth1 or some other. The quick and easy method is to run ifconfig, see what's been assigned and use it in *interfaces* and be done. The rigorous way is to edit /etc/udev/rules.d/70-persistent-net.rules and force it to eth0 and then use eth0 in *interfaces*. We live in an imperfect world. Electrons happen.> QUESTION - why is it that I can connect to the server on internal network, ssh from node-->server, scp stuff server-->node, buit CANNOT ssh into the node from the server?!? Error is as follows - where I typically remedy this by apt-get installing openssh-server:I don't know much about nodes vs. servers; so I'm not sure I can answer. If it's a problem unique to this machine, it's probably a driver problem.

---

### Post by professor-g on 2012-06-20
> **chili555 said:**
> It appears that you actually used the word 'driver' here, not the name of the driver, e1000e. I asked that you substitute the name of the driver. So what does dmesg report?```
dmesg | grep e1000e
```Maybe; we'll know more when we see what the message file says.

I only copied in the lines 'of interest'.
Here is the full output:

> 
[    1.685750] i2c-core: driver [aat2870] using legacy suspend method
[    1.685752] i2c-core: driver [aat2870] using legacy resume method
[    4.179207] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    4.179208] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    4.179261] e1000e 0000:00:19.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.179301] e1000e 0000:00:19.0: setting latency timer to 64
[    4.180176] e1000e 0000:00:19.0: irq 102 for MSI/MSI-X
[    4.522188] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) c8:60:00:a5:fb:56
[    4.536883] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.551607] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[   12.252985] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.793020] VGA switcheroo: detected Optimus DSM method \ handle
[   15.015594] e1000e 0000:00:19.0: irq 102 for MSI/MSI-X
[   15.071356] e1000e 0000:00:19.0: irq 102 for MSI/MSI-X
[   15.071972] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.570033] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   18.570628] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.115321] eth0: no IPv6 routers present


Likewise, here is the full output of the lshw
NOTE: link=yes

> 
  *-network
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: c8:60:00:a5:fb:56
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-4 ip=138.37.52.138 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:102 memory:fb700000-fb71ffff memory:fb748000-fb748fff ioport:f040(size=32)




> As have I. I think udev hiccups once in a while and uses eth1 or some other. The quick and easy method is to run ifconfig, see what's been assigned and use it in *interfaces* and be done. The rigorous way is to edit /etc/udev/rules.d/70-persistent-net.rules and force it to eth0 and then use eth0 in *interfaces*.

Acknowledged and thanks - helps with my learning of debian/ubuntu.


> We live in an imperfect world. Electrons happen.

Tell me about - going on 16 years of doing quantum theory 6+ days per week ... !!! Was interested to know where, how and why this happens within the machine/OS.


> I don't know much about nodes vs. servers; so I'm not sure I can answer. If it's a problem unique to this machine, it's probably a driver problem.

Apologies for the confusion.
The nodes are essentially the same (in terms of connectivity), just semantics. They are number crunchers for me and dont need to be online to the 'real' world - only the 1 time to apt-get update them.

I just find it strange that these machines (nodes) can ssh out to the other machine (server - set as gateway 192.168.0.1 in /etc/network/interfaces), and for all intents and purposes should be the same as any other gateway.

Thx for the help,
G.

---

### Post by steeldriver on 2012-06-20
I'm confused. Can we take a step back here?

Your #1 problem seems to be that even though you opted to install ssh-server during the install, you can't ssh into the box - correct? And you are assuming that's an interface issue because you can't ping out of the box either? But you can ssh in?

Are you sure the inbound ssh is not failing for other reasons? Have you actually checked if the ssh service is running? Do you have ufw (firewall) running? If so is the ssh port open?

There could be other reasons the gateway machine is not pingable (ICMP blocked) / not giving a connection / dropping WAN packets - I spent days troubleshooting something like that thinking it was a driver issue and it turned out the user forgot he had MAC filtering enabled on the router!

---

### Post by chili555 on 2012-06-20
> *-network
description: Ethernet interface
product: 82579V Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
---
size: 1Gbit/s
capacity: 1Gbit/s
---
 broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-4 ip=138.37.52.138 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
--- Here you have an IP address at 1 Gb/s and link=yes. I doubt it's a driver problem, but rather an *interfaces* problem.

steeldriver seems to have a much better handle on the server vs. node issue, so I suggest he take over from here.

---

### Post by professor-g on 2012-06-20
> **steeldriver said:**
> I'm confused. Can we take a step back here?
Your #1 problem seems to be that even though you opted to install ssh-server during the install, you can't ssh into the box - correct? And you are assuming that's an interface issue because you can't ping out of the box either? But you can ssh in?

-Yes, did opt at install for ssh-server
-CAN ssh out of the box
-CAN ping out of the box 
-Cannot ssh into the box


> Are you sure the inbound ssh is not failing for other reasons? Have you actually checked if the ssh service is running? Do you have ufw (firewall) running? If so is the ssh port open?

-Have not checked if ssh service is running ... how to do this?
-No firewall running


> There could be other reasons the gateway machine is not pingable (ICMP blocked) / not giving a connection / dropping WAN packets - I spent days troubleshooting something like that thinking it was a driver issue and it turned out the user forgot he had MAC filtering enabled on the router!


-CAN ping gateway from this machine (so it IS pingable)
-CANNOT ping gateway from the problem-box
-MAC filtering is most probably on this (university) router
-However, I have in the past put other machines onto the net quickly to get openssh-server installed or to 'apt-get update'
-Perhaps in the interim time they have made it more strict filtering

-Despite this, DHCP is not MAC filtering and when I tried setting to DHCP (even during install) it also fails to asign an address (in fact it just hangs for-ever and then-some).

Thx for the continued help,
G.

---

### Post by professor-g on 2012-06-20
After reading I have tried the following:

```
sudo service ssh status

OR

sudo service ssh start
```

It outputs the following for both commands:

> ssh: unrecognized service

???

Apologies for my ignorance on this one.
G.

---

### Post by steeldriver on 2012-06-20
I don't really know anything about the server distribution, I'm just winging it -  but we could start by seeing what bits of ssh actually got installed:

```
dpkg -l | grep ssh
```and just to be certain about firewall status, 

```
sudo service ufw status
```and if ufw shows status running,

```
sudo ufw status
```for a brief summary of the active rules; also I don't think you provided your ifconfig output yet?

```
ifconfig
```

---

### Post by professor-g on 2012-06-20
> **steeldriver said:**
> I don't really know anything about the server distribution, I'm just winging it -  but we could start by seeing what bits of ssh actually got installed:


```
dpkg -l | grep ssh
```
outputs:
> ii  openssh-client                   1:5.9p1-5ubuntu1           secure shell (SSH) client, for secure access to remote machine


```
sudo service ufw status
```
outputs:
> ufw start/running


```
sudo ufw status
```
outputs:
> Status: inactive


```
ifconfig
```
outputs:
> eth0      Link encap:Ethernet  HWaddr c8:60:00:a5:fa:e5  
          inet addr:192.168.0.43  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fea5:fae5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8799 (8.7 KB)  TX bytes:14757 (14.7 KB)
          Interrupt:18 Memory:fb700000-fb720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9448 (9.4 KB)  TX bytes:9448 (9.4 KB)

---

### Post by steeldriver on 2012-06-20
My apologies if we've come full circle here - I just wanted to make sure we were barking up the right tree. 

So now we need to know why you can connect out to 192.168.0.1 but no further? I assume the 192.168.0.43 address was set manually / statically in /etc/network/interfaces ?

Here are a couple of commands that will tell you if your machine can find any external routes

```
netstat -r

tracepath 8.8.8.8
```I still think it would be a good idea to ask your network admin to add the MAC to their whitelist - I'm pretty sure that at my workplace my personal laptop didn't even get an IP until they did that.

BTW if it *is* a driver issue then chili555 absolutely is the go-to person.

---

### Post by professor-g on 2012-06-21
Before I start into this - big thanks to chili555 and steeldriver. You guys have been a big help and very patient with this issue.
My replies are below this first 'shpeel'.

I am now convinced it is NOT a driver issue and nothing other than ssh not being properly started/running/implemented
I still think it would be a good idea to ask your network admin to add the MAC to their whitelist - I'm pretty sure that at my workplace my personal laptop didn't even get an IP until they did 
When I do ```
sudo service ssh status
``` it tells me ssh is unrecognised.

Also, ssh doesnt appear in /etc/init.d/

I am starting a new thread on this issue - to make it clearer for any future users needing help on this specific issue.

Hence, I am stumped what to do.
I have tried re-installing and choosing (yet again) openssh-server to be installed during isntallation.
Doesnt help.

> **steeldriver said:**
> My apologies if we've come full circle here - I just wanted to make sure we were barking up the right tree.

So now we need to know why you can connect out to 192.168.0.1 but no further? I assume the 192.168.0.43 address was set manually / statically in /etc/network/interfaces ?

Yes - set manually in /etc/network/interfaces/

> Here are a couple of commands that will tell you if your machine can find any external routes

```
netstat -r
tracepath 8.8.8.8
```

This produces the following output:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0


> I still think it would be a good idea to ask your network admin to add the MAC to their whitelist - I'm pretty sure that at my workplace my personal laptop didn't even get an IP until they did that.

Made a request to admin yesterday afternoon, still waiting for response.

> BTW if it *is* a driver issue then chili555 absolutely is the go-to person.

I cant see how it can be a driver issue if the machine is able to ping out, ssh out and be seen (via pinging) from other machines.
 the foll
It seems to be a permissions issue - i.e. allowing ssh out, but not anyone to ssh in ... ?!?

Getting a bit desperate for a solution.
Please advise. Thx,

G.

---

### Post by steeldriver on 2012-06-21
> **professor-g said:**
> It seems to be a permissions issue - i.e. allowing ssh out, but not anyone to ssh in ... ?!?

I don't think it's a question of permissions - it's simply that there's no ssh **server** running on the machine - they are 2 separate things. You are seeing exactly the same 'error' I see if I try to ssh into a box that's not running sshd, i.e.

```
$ ssh 192.168.1.7
ssh: connect to host 192.168.1.7 port 22: Connection refused

```That's true even if you are ssh'ing **out** of the same machine (i.e. 192.168.1.7 in this case).

Once you have public internet access you can install the openssh-server package and it should all work.

---

