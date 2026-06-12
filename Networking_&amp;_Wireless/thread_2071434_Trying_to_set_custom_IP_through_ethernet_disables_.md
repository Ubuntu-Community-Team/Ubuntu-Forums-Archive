---
title: "Trying to set custom IP through ethernet disables internet"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by hakermania on 2012-10-15
Soooo, I just moved to a block with students from all around Greece, and they share the internet to the rooms via Ethernet. Every room's ip address depends on its room number, so, the student team who is responsible for this installed the ethernet cable to my room and asked me to configure the IP so as to match my room's.

For example, if I am at the room No 6 and my local ip is
150.140.216.**74**, I should make it be 150.140.216.**6**

So, I open the system settings, head to Nework then Wired->Options->IPv4 Settings, I choose Method:Manual, I add exactly the same settings as the present with the only difference which I pointed out previously and.... I lose my internet connection till I restart... :(

Any thoughts ?

---

### Post by sandyd on 2012-10-15
Can you ping the gateway if you add the ip address?

btw, that seems like a weird config to me - why are they not using dhcp?

---

### Post by ahallubuntu on 2012-10-15
150.140.216.74 sounds like the gateway, so you'd need to set that too.  Get the exact subnet mask for this config as well from the local admin for your network.  You need to set all of those things.

---

### Post by Cheesemill on 2012-10-15
Can you post the output of:
```
ifconfig -a
```
With both the working and broken configuration please.

---

### Post by PowerBarry43 on 2012-10-16
You could try running
```

sudo gedit /etc/network/interfaces
```

from the terminal and edit the addresses in that file

Barry

---

### Post by hakermania on 2012-10-16
When I have internet connection but with the wrong IP:
```

alex@MaD-pc:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:9c:09:49  
          inet addr:150.140.216.74  Bcast:150.140.216.255  Mask:255.255.255.0
          inet6 addr: fec0::b:21e:ecff:fe9c:949/64 Scope:Site
          inet6 addr: 2002:968c:d820:b:21e:ecff:fe9c:949/64 Scope:Global
          inet6 addr: 2002:8000:1:b:21e:ecff:fe9c:949/64 Scope:Global
          inet6 addr: fe80::21e:ecff:fe9c:949/64 Scope:Link
          inet6 addr: fec0::b:98c8:2076:a776:fbd/64 Scope:Site
          inet6 addr: 2002:968c:d820:b:98c8:2076:a776:fbd/64 Scope:Global
          inet6 addr: 2002:8000:1:b:98c8:2076:a776:fbd/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27568491 (27.5 MB)  TX bytes:3498916 (3.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:413153 (413.1 KB)  TX bytes:413153 (413.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:3c:06:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

When I don't have internet connection but I've tried to set the right IP:
```

alex@MaD-pc:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:9c:09:49  
          inet addr:150.140.216.6  Bcast:150.140.216.255  Mask:255.255.255.0
          inet6 addr: fec0::b:21e:ecff:fe9c:949/64 Scope:Site
          inet6 addr: 2002:968c:d820:b:21e:ecff:fe9c:949/64 Scope:Global
          inet6 addr: 2002:8000:1:b:21e:ecff:fe9c:949/64 Scope:Global
          inet6 addr: fe80::21e:ecff:fe9c:949/64 Scope:Link
          inet6 addr: fec0::b:98c8:2076:a776:fbd/64 Scope:Site
          inet6 addr: 2002:968c:d820:b:98c8:2076:a776:fbd/64 Scope:Global
          inet6 addr: 2002:8000:1:b:98c8:2076:a776:fbd/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30950282 (30.9 MB)  TX bytes:4039399 (4.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:578554 (578.5 KB)  TX bytes:578554 (578.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:3c:06:cc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Thanks in advance for trying to help me!

---

### Post by Pieman15 on 2012-10-16
Do you get any errors or messages when you set the IP address to the .6? I'm wondering if someone else is already using the .6 address that you are suppose to use. Is it a big deal to continue using the .74 address?

This is the reason that DHCP exists. Not sure why your network admin doesn't want to do things the easy way.

---

### Post by hakermania on 2012-10-16
I don't get any error messages. There isn't any real problem to continue using the .74 address, unless I'm cutting off the internet connection on the corresponding room number.

---

### Post by The Cog on 2012-10-16
That all looks OK to me. 

Can you ping 150.140.216.6 when your address is 150.140.216.74? If so, then someone else already has that address.

Can you post he output of these commands before and after configuring the .6 address:
```
route -n
ping -c 3 8.8.8.8
ping -c 3 google-public-dns-a.google.com
cat /etc/resolv.conf

``` I am wondering if the default gateway or dns server is getting wiped as you change address.

---

### Post by hakermania on 2012-11-07
Sorry for being so late to reply in this thread.

I finally solved the problem via setting the DNS whose IP wasn't configured previously.

Thanks all :)

---

