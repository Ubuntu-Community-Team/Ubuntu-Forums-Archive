---
title: "Cant get IP by hostname"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by tdyer on 2009-03-03
If I run 'hostname -i' I will get 127.0.1.1

I have some programs which requires that it knows its correct local IP.

So that it can do RPC to another computer and have the callbacks return.

As well it multicasts its presence announcing it's IP.

I am assuming that because hostname -i returns 127.0.1.1 the program is announcing its IP as 127.0.1.1 which leads to problems.

Is there a way to make ubuntu resolve the IP instead of loopback?

I dont need a real IP, nat'ed is fine.

---

### Post by capscrew on 2009-03-03
> **tdyer said:**
> If I run 'hostname -i' I will get 127.0.1.1

I have some programs which requires that it knows its correct local IP.

So that it can do RPC to another computer and have the callbacks return.

As well it multicasts its presence announcing it's IP.

I am assuming that because hostname -i returns 127.0.1.1 the program is announcing its IP as 127.0.1.1 which leads to problems.

Is there a way to make ubuntu resolve the IP instead of loopback?

I dont need a real IP, nat'ed is fine.


I get the correct response.
```

bruce@malibu:~>hostname -i
192.168.1.12
bruce@malibu:~>

```

The basic command gets.
```
bruce@malibu:~>hostname
malibu
bruce@malibu:~>

```

Maybe your /etc/hosts file isn't correct.
Mine is as follows.
```

bruce@malibu:~>cat /etc/hosts
127.0.0.1 localhost
192.168.1.12 malibu
192.168.1.200 printer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bruce@malibu:~>

```

---

### Post by Iowan on 2009-03-03
> **tdyer said:**
> If I run 'hostname -i' I will get 127.0.1.1For what it's worth, my (pretty much stock) /etc/hosts file:```
127.0.0.1 localhost
127.0.1.1 DELLbox.Mynet DELLbox

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
(END) 

```And yes, **hostname -i** also returns 127.0.1.1.

But... one of my servers is configured:```
127.0.0.1       localhost.Mynet   localhost
192.168.1.2   server1.Mynet    server1
```And, **hostname -i**  returns 192.168.1.2

---

### Post by tdyer on 2009-03-04
My machine has a staticly assigned IP address, but most others are assigned dynamically by DHCP,

Is there any way to make it automatic? I just don't think I can expect people to manually edit their /etc/hosts file every morning.

/etc/hosts
```
127.0.0.1 localhost
127.0.1.1 scu0237
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$hostname
scu0237
$hostname -i
127.0.1.1

any ideas?

---

### Post by capscrew on 2009-03-04
> **tdyer said:**
> My machine has a staticly assigned IP address, but most others are assigned dynamically by DHCP,

Is there any way to make it automatic? I just don't think I can expect people to manually edit their /etc/hosts file every morning.


Yes you can.  See [**here**]("http://ubuntuforums.org/showthread.php?t=367974") for instructions. 
> 

/etc/hosts
```
127.0.0.1 localhost
127.0.1.1 scu0237
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$hostname
scu0237
$hostname -i
127.0.1.1

any ideas?

All we are doing is providing a mapping between the hostname and an IP address.  Everything in the 127.x.x.x range refers to the loopback address.  This is the NIC (ethernet card) itself.

We need to know your "statically assigned IP address"  You can find that by using the command:
```
ifconfig -a
```

My data looks like this:
```
bruce@malibu:~>ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:76:CD:DD:E0  
          inet addr:[COLOR="Red"]192.168.1.12 [/COLOR] Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fecd:DDe0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2571400 (2.4 MB)  TX bytes:258847 (252.7 KB)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:[COLOR="Blue"]127.0.0.1[/COLOR]  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

In the above example the eth0 address is the interface you need.

The **lo** address is your loopback address.  Not the one you need.

Edit your hosts file and replace the 127.0.1.1 with the the eth0 address.

---

