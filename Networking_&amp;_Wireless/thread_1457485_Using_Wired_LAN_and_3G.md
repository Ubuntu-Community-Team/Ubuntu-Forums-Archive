---
title: "Using Wired LAN and 3G"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by sayeed_vir on 2010-04-18
The issue I am having is that I have a Wired Network to share files between multiple computers, and I use a 3G Mobile USB Stick to access the Internet. 

What occurs is as follows:

If I log in with the Wired Connection attached I can not access the internet, but if I unplug my LAN and use only the wireless USB Stick everything works properly. 

Is there a way to configure the OS to Use my USB stick as the primary internet connection while still having access to the other computers on my LAN through the wired connection. 

My wired connection is currently run from a router that is a DHCP server.

I am currently running Ubuntu 9.10

Thanks in advance.

---

### Post by spiky001 on 2010-04-18
yes you can do this, do all the other pc,c share internet as well,

---

### Post by sayeed_vir on 2010-04-18
No. Just my PC. 

LAN IP: 10.0.8.111
SUBNET: 255.255.254.0
Gateway: 10.0.8.1

3G IP: Dynamic

I need to keep these settings as they are. I also don't want to share my internet connection.

And thanx very much 4 the quick reply. Hope u reply soon this time as well.

---

### Post by spiky001 on 2010-04-19
In  the network manager if you right click it then go to edit select wired connection then edit, then select the ipv4 change it from dhcp to shared to other computors, just for imformation if you try to use wireless with all pc's it will be very slow as it,s not made to do it wired works ok tho

---

### Post by sayeed_vir on 2010-04-19
> **spiky001 said:**
> In  the network manager if you right click it then go to edit select wired connection then edit, then select the ipv4 change it from dhcp to shared to other computors, just for imformation if you try to use wireless with all pc's it will be very slow as it,s not made to do it wired works ok tho

1 more thing.
How would I access shared files on a windows machine from my Ubuntu machine.

I mean is there any thing like browsing PC with ip address... like we do in windows...
e.g. \\10.0.8.1

or any particular application similar to network scanner.

---

### Post by spiky001 on 2010-04-19
I can go to places network places then it finds the windows network like windows dose

---

### Post by sayeed_vir on 2010-04-19
well it shows the various workgroups but not all the pcs. moreover when i try to access any particular pc, it shows error.

how can i browse a pc by its ip address. suppose i want to access shared files in a pc whose ip address is 10.0.8.23

---

### Post by spiky001 on 2010-04-19
are they all windows, turn off firewall on 1,s you cant connect see if that helps, make sure they have file sharing on

---

### Post by Iowan on 2010-04-19
> **sayeed_vir said:**
> Is there a way to configure the OS to Use my USB stick as the primary internet connection while still having access to the other computers on my LAN through the wired connection.  The old NM would only activate one interface at a time - the new one???
IF NM will handle both, you may have a gateway problem. Check **route -n** with both active - if the default gateway (UG) is set for eth0...

---

