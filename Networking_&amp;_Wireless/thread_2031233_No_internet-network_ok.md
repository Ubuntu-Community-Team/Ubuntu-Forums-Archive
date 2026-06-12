---
title: "No internet-network ok"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by Protaganist on 2012-07-21
I have been using Ubuntu 12.04 server for a couple of weeks and all has been fine but now the internet access has died. I can ssh into the box, ping from the box to anything else on the network but cannot ping to the net even using an ip address instead of a name.
 Clearly the network interface is fine it's just a internet issue, i guess it's not a dns issue as i can't even ping the ip address of google.com?
A bit of searching led to some older posts talking about problem in network manager but i don't seem to have network manager installed. How are networks managed in 12.04 server?

/etc/resolv.conf gives

```
domain dlink.com
search dlink.com
nameserver 192.168.1.1
```

I don't really know what other information to post so hopefully someone can point me in the right direction. Please remember this is the server version so cli only.
 Many thanks, Hiro.

---

### Post by Cheesehead on 2012-07-21
Did the change correspond to any package actions? (update or install)

Does this machine have direct access to the internet, or just your LAN? (internet through an upstream router)

Please paste the output of the [FONT="Courier New"]ifconfig[/FONT] command, and your /etc/network/interfaces file.

---

### Post by Protaganist on 2012-07-22
Since installation i have installed and configures Samba and vsftpd but that's about it, i haven't run a full update at all. 
Access is through a router and all other boxes on the net still have internet access. 
I am still wondering about NetworkManager, i've been trying to search and see if it is the default tool in the server package for administering networks but i can't be sure. Do you know if it should be installed? I can't see how i could have uninstalled it though so possibly not?


Ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:3a:4d:c5  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe3a:4dc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74836 (74.8 KB)  TX bytes:102261 (102.2 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)
```


Interfaces

#```
 The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Thanks for the help, Hiro.

---

### Post by praseodym on 2012-07-22
Hi,

what hardware is in use?

```
lspci -nnk | grep -iA2 net
lsmod
route -n
ping -c 4 192.168.1.1
ping -c 4 www.ubuntuusers.de #german forum
ping -c 4 213.95.41.11       #IP of the german forum
```
IMHO the NM is not installed per default in the server installation. But you can also use it without GUI. You may want to (Google)-translate this Wiki-page:

[http://wiki.ubuntuusers.de/NetworkManager/NetworkManager_ohne_GUI](http://wiki.ubuntuusers.de/NetworkManager/NetworkManager_ohne_GUI)

---

### Post by Cheesehead on 2012-07-22
Those look good. Thanks.

Next, take a look at your /etc/resolv.conf. It should contain the address of at least one nameserver (mine, for example, shows my router).

Check the settings on your router. Able to reach the LAN but not the WAN is most commonly a mistaken router setting. Did any other machine ever use that 192.168.1.6 IP address before?

Network Manager: You don't need it. It's not magic, it merely automates a few manual tasks for you, like remembering and logging into wi-fi networks. It uses ifup and ifdown and dhclient just like /etc/network/interfaces.

---

### Post by Protaganist on 2012-07-22
I posted the resolv.conf in my first post and it does list the router as a name server also my other Linux box has exactly the same in it's resolv.conf file and it all works fine.
 I don't suspect the router as one day the computer had internet access and the next day i booted it up there was none and the router hadn't been altered or even rebooted in that time. Do you think there might be something there that could have changed?
Although i use dynamic ip addressing this computer has been 192.168.1.6 since installation. I thought they took the lowest available address at every boot but clearly this hasn't done that.
 Thanks for the info on network manager, for some reason i thought that was essential but clearly not so the problem is elsewhere. 
 I can ping from the Ubuntu box to any other computer on the network and vice versa but the other boxes can also ping external websites but the Ubuntu box cannot either using site name or ip address.
 Presumably this means the ethernet card/drivers/cabling etc are all fine and it is something in the software?

Route -n


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

 Any ideas what else i could try?

---

### Post by steeldriver on 2012-07-22
pmji - I don't really know anything about routing but is it normal for the gateway to have such a high metric (100)? do the other (working) machines show the same metric? 

have you been playing with vpns on this machine?

---

### Post by Protaganist on 2012-07-22
I don't know what the metric is for but my Linux Mint box has 1000 as the metric!


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```
 Had to google what vpns was so i'm fairly sure i haven't been playing with it.

Edit: Just noticed the differences between the two, any clues in that?

---

### Post by steeldriver on 2012-07-22
maybe... as I said, I don't really know

I think you can ignore the 169.254.xxx.xxx with metric 1000 - it's a reserved address block that's sometimes used as a kind of fallback when DHCP fails I think (at least on Windows)

More interesting (possibly) is why the actual gateway (the route marked U**G**) has metric 100 on the box that's giving you trouble but 0 on the mint box... it may mean nothing but it may mean the route is deprecated for some reason (high number = low priority)

Have you tried re-adding the default route explicitly, either

```
sudo route add default gw 192.168.1.1 eth0
```or adding a gateway entry in your /etc/network/interfaces file and restarting (sudo service networking restart)

I really am guessing here though

---

### Post by Protaganist on 2012-07-22
Tried adding default route manually but no joy so i was re-reading all the posts here to see if i had missed anything and the line "and the router hadn't been altered or even rebooted in that time" caught my eye. I had tried rebooting the computer when the problem arose but never thought about rebooting the router as the internet worked on all the other machines.
 However in desperate times i'll try anything so i turned the router off and on again and presto everything is back to normal! I've had this router for a couple of years and never experienced anything like that before.
 I'll keep an eye on it and see what happens but does anyone have any ideas what may have happened?
 Many thanks for all your help, Hiro.

---

### Post by steeldriver on 2012-07-22
ok that's good

just out of curiosity do the route metrics look any different now?

---

### Post by Cheesehead on 2012-07-22
Hooray!

About 'metric' in the routing table. From man route:
> Metric The 'distance' to the target (usually counted in  hops).  [B]It  is
              not  used  by  recent kernels[/B], but may be needed by routing dae&#8208;
              mons.

---

