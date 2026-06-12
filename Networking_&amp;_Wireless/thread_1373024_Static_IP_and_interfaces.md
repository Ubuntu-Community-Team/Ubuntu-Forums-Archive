---
title: "Static IP and interfaces"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2010-01-05
I wish to set up a static ip address. Having found some instructions I looked in /etc/network/interfaces. Instead of referring to eth0 it says:

auto lo
iface lo inet loopback

I expected to see the eth0 set up. I am using Karmic. Should I just delete the current contents and add the new wording:

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.3
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

I am following the advice here:

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

Robin

---

### Post by slakkie on 2010-01-05
It looks correct :) 

You may want to have a look here: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

---

### Post by Robbyx on 2010-01-05
Following the advice in the referred article, sadly did not work.

> **slakkie said:**
> It looks correct :) 

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

These were my terminal commands:

> rob@rob-desktop:~$ ls /sys/class/net
eth0  lo  vboxnet0
rob@rob-desktop:~$ sudo gedit /etc/network/interfaces
rob@rob-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
                                                                         [ OK ]
rob@rob-desktop:~$ 


This is the content of the interfaces for a static ip:

> ## auto lo
# iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.33
gateway 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255

When it is running this version I can not browse to any address. So it seems the connection is not being made. Can you please add some further guidance?

Robin

---

### Post by slakkie on 2010-01-05
That is your firewall:

firestarter - gtk program for managing and observing your firewall

The first time I see that line when restarting the network via /etc/init.d/networking.

You might want to remove it, or disable it.

---

### Post by Robbyx on 2010-01-05
I think it is sensible to keep the firewall. Do you know how to allow the static address through it?

---

### Post by Iowan on 2010-01-05
It is possible to have Network Manager set up a static address. 

**ifconfig -a** will show if the interface has the static address. By "...can not browse to any address", you mean IP address - like the router? I, too, might recommend trying to get networking going first (IE, disable the firewall). That'll make it a bit easier to determine if there are firewall issues. Not suggesting you abandon the firewall.

---

### Post by Robbyx on 2010-01-11
I am not clear if I have a static IP address. This is what ifconfig shows:

> rob@rob-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:0a:01:3e  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe0a:13e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:317249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:430588617 (430.5 MB)  TX bytes:18654855 (18.6 MB)
          Interrupt:28 Base address:0xc000 


I tried ekiga without the firewall being loaded and I still can not access the test numbers. Is it worth the effort to get ekiga to work? I have skype working. Is Ekiga better?

---

### Post by chili555 on 2010-01-11
I don't think it is at all wise to comment out or remove these lines:```
auto lo
iface lo inet loopback
```

---

### Post by Iowan on 2010-01-11
+1 Somehow I missed that focusing on the eth0 definition.

---

### Post by lisati on 2010-01-11
My own preference is to let my routers hand out IP addresses. Both of them can be set to assign fixed IP addresses to specific machines. That way, in the unlikely event of me hooking up to someone else's network, I defer to their rules and setup, and I'm less likely to run into an IP address conflict.

---

