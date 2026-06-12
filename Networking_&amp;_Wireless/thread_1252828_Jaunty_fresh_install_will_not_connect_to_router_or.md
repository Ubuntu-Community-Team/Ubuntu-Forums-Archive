---
title: "Jaunty fresh install will not connect to router or internet"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by weretiger on 2009-08-29
I have a via rhine II VT6102 built-in wired ethernet card. I can't ping anything or connect to the internet.

when I do this 
```

ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```it returns
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:5c:c9:8b  
          inet6 addr: fe80::250:8dff:fe5c:c98b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:563648 (563.6 KB)  TX bytes:258009 (258.0 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24386 (24.3 KB)  TX bytes:24386 (24.3 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ping -c 3 208.67.219.101
connect: Network is unreachable
ping -c 3 www.opendns.com
ping: unknown host www.opendns.com

```Please Help Me!

---

### Post by dbalascak on 2009-08-29
Your system has not acquired any IP address information for the local network.  Your physical connection/cable looks good.  The interface eth0 has TX and RX packet counts.
There are two ways to get IP address configuration. DHCP or static configuration.  The default is to use DHCP, which is an automatic. If there is no DHCP server/service you will need to manually configure the interface.

Is the systems network connections enabled?  Right click the Network Manager icon.
Edit Connections. Does the interface eth0 show up?
Select the interface and Edit.
Is Connect Automatically checked?
IPV4 Settings TAB.  Is Method DHCP?
If the local network dos not have DHCP, this is where you would have to configure the interface. So Method would be changed to Manual. You would enter the IP info on this screen.

---

### Post by weretiger on 2009-08-29
I have tried all of that, it still doesn't work.

I put in a new internet card and it works now!

---

### Post by dbalascak on 2009-08-29
So you see the interface and it all looks good. 
Is this a home network?   Is there a DHCP server on it? Did you make any config changesfrom the above list?  Did you configure */etc/network/interfaces*?

---

