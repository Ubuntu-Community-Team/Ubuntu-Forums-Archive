---
title: "Ubuntu 12.10 static ip cant connect externally"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by achacko90 on 2012-12-25
Hi,

I recently installed Ubuntu 12.10 server. When using DHCP, everything works fine, but when I tried to setup a static ip, I can ping other devices within the network, but cant connect to anything outside. I have googled for a solution, but have not yet been successful.

This is the contents of my /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.254
    network 192.168.1.0
    broadcast 192.168.1.255
    dns-search hsd1.tx.comcast.net
    dns-nameservers 75.75.75.75 75.75.76.76


Any help on this matter would be greatly appreciated.

---

### Post by chadk5utc on 2012-12-25
for static setup make sure network manager is not attempting to control. have you compared the dhcp addressing with your current?
Whats your router address?
> 
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1 Change your gateway address like so this should do it. the gateway is usually the first not the last address

---

### Post by achacko90 on 2012-12-25
I have compared the static setup with the DHCP setup, and they both match except for the IP address, so I'm not entirely sure why it doesn't work.

My gateway address is: 192.168.1.254

I have tried changing it to 192.168.1.1, but that doesn't work since it doesn't point to anything.
I am using the standard Comcast Router/Modem that comes with Xfinity.

---

### Post by chadk5utc on 2012-12-25
ok out of curiosity what address does dhcp assign?

---

### Post by Kirk Schnable on 2012-12-25
It might be helpful if you could supply the output of:

```
sudo route -n
```

---

### Post by achacko90 on 2012-12-25
This is the output:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

---

### Post by achacko90 on 2012-12-25
> **chadk5utc said:**
> ok out of curiosity what address does dhcp assign?

DHCP assigns: 192.168.1.16

---

### Post by Kirk Schnable on 2012-12-25
> **achacko90 said:**
> DHCP assigns: 192.168.1.16

Can you give us the output of these commands from working/DHCP configuration?

```
sudo route -n
```
```
sudo ifconfig
```

---

### Post by achacko90 on 2012-12-25
> **Kirk Schnable said:**
> Can you give us the output of these commands from working/DHCP configuration?

"sudo route -n":

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```


"sudo ifconfig":

```

eth0      Link encap:Ethernet  HWaddr 00:24:21:52:2a:cc  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe52:2acc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4209 errors:0 dropped:3 overruns:0 frame:0
          TX packets:1933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462116 (462.1 KB)  TX bytes:230385 (230.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1618 (1.6 KB)  TX bytes:1618 (1.6 KB)

```

---

### Post by chadk5utc on 2012-12-25
The network/subnet appear correct should work fine. The only thing that stands out to me at this point is DNS
remove the nameservers if they are in the same file as listed in your original post and show the output for
> cat /etc/resolv.conf

---

### Post by achacko90 on 2012-12-25
> **chadk5utc said:**
> The network/subnet appear correct should work fine. The only thing that stands out to me at this point is DNS
remove the nameservers if they are in the same file as listed in your original post and show the output for

Alright, I commented out the dns-search and dns-nameservers, and restarted networking.

"cat /etc/network/interfaces":

```

auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.254
    network 192.168.1.0
    broadcast 192.168.1.255
    #dns-search hsd1.tx.comcast.net
    #dns-nameservers 75.75.75.75 75.75.76.76

```

"cat /etc/resolv.conf":

```

nameserver 75.75.76.76
nameserver 75.75.75.75
search hsd1.tx.comcast.net

```

---

### Post by chadk5utc on 2012-12-25
are you able to ping or traceroute or dig?

---

### Post by achacko90 on 2012-12-25
> **chadk5utc said:**
> are you able to ping or traceroute or dig?

I have tried all three, but none of them work... I have tried googling, and it looks like others have had the same type of issue, but none of their solutions have fixed my problem yet. So I'm not really sure what else to try.

---

### Post by chadk5utc on 2012-12-25
Ok this is kindof last ditch only other thing I can think of. I have a server(OpenSuse) I had to disable IPv6 on Totally in order to get it talking as my ISP doesnt support it. Ive also had same issue with a desktop but cant remember what OS it was but it was Debian based

---

### Post by achacko90 on 2012-12-26
I'm not sure if this is a conflict with IPv6 and my ISP (Comcast), since everything works fine with DHCP.

---

### Post by achacko90 on 2012-12-26
So I just figured it out. 
I was curious to see if I could set a static ip on a windows machine, and I wasn't able to get that working either. So I figured it was an issue with the gateway. I looked through all of the settings on my gateway, and came to find out that you have to hard code entries into a form for each static ip that you want to use. It is by far one of the dumbest things I have run into. I have attached a screenshot of it.

Thank you guys so much for your help.

---

### Post by chadk5utc on 2012-12-26
> **achacko90 said:**
> So I just figured it out. 
I was curious to see if I could set a static ip on a windows machine, and I wasn't able to get that working either. So I figured it was an issue with the gateway. I looked through all of the settings on my gateway, and came to find out that you have to hard code entries into a form for each static ip that you want to use. It is by far one of the dumbest things I have run into. I have attached a screenshot of it.

Thank you guys so much for your help.

Thats a first Ive seen in a router like that glad its resolved in any event.

---

### Post by Kirk Schnable on 2012-12-26
> **chadk5utc said:**
> Thats a first Ive seen in a router like that glad its resolved in any event.

Me too... Wow. I will have to keep that in mind if I ever see something like this in the future.

---

