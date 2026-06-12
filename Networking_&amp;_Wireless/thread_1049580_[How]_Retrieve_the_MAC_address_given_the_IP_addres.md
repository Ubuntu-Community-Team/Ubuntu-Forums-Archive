---
title: "[How] Retrieve the MAC address given the IP address"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by NeoIndigo on 2009-01-24
Hi there, 

How to get the MAC address of a host if we know its IP address ?

Any commands that we can use to do it ? 

Thanks,

---

### Post by Loosewheel on 2009-01-24
I can access the info with 'http://192.168.1.1' in the address bar of Firefox.
That is the Westell dslrouter,( modem, dhcp, nat device).
It is listed under, 'Trouble shooting>LAN stats'

---

### Post by capscrew on 2009-01-24
> **NeoIndigo said:**
> Hi there, 

How to get the MAC address of a host if we know its IP address ?

Any commands that we can use to do it ? 

Thanks,

I assume the host is part of your local LAN.  With that host connected; you can use the command ```
arp -a
```

You will see all hosts in the arp cache listed by IP and MAC

---

### Post by NeoIndigo on 2009-01-24
Thanks a lot for your help !!.. 

However, is there a way for us to know the MAC address if the host is not part of our LAN ? 

Thanks again !!

---

### Post by capscrew on 2009-01-25
> **NeoIndigo said:**
> Thanks a lot for your help !!.. 

However, is there a way for us to know the MAC address if the host is not part of our LAN ? 

Thanks again !!

I usually don't question why users do what they do, but in this instance I have to ask; why would you need to know the MAC address of a device that is not on your local LAN?  

To network a device TCP/IP (Layers 3 and 4) does not need to know the specifics the underlying Layer 2 protocol to function. 

The the MAC (Ethernet) address is removed once the packet (data) leaves the LAN.  Layer 2 protocols can be Frame Relay or ATM and others as well as Ethernet.

If really do need a MAC address for a device NOT on your LAN you will have to get it from the device itself or an ARP request while the device is connected to that local LAN.

---

### Post by jonobr on 2009-01-25
The best way for me would be using something like snmpwalk, a program that uses snmp to gather information.

If SNMP is enabled on the remote device (a lot do by default) and if you know the community strings, (its usually private and public for read and read + write

the default query would be
snmpwalk <IPaddr_device_or_name> <community_string> IpnetToMediaPhysAddress

eg snmpwalk 20.20.20.20 public IpnetToMediaPhysAddress

---

### Post by NeoIndigo on 2009-01-25
> **capscrew said:**
> I usually don't question why users do what they do, but in this instance I have to ask; why would you need to know the MAC address of a device that is not on your local LAN?  

To network a device TCP/IP (Layers 3 and 4) does not need to know the specifics the underlying Layer 2 protocol to function. 

The the MAC (Ethernet) address is removed once the packet (data) leaves the LAN.  Layer 2 protocols can be Frame Relay or ATM and others as well as Ethernet.

If really do need a MAC address for a device NOT on your LAN you will have to get it from the device itself or an ARP request while the device is connected to that local LAN.

Oh.. actually i am just curious to know is there a way to know the MAC address that is not part of the LAN. But now, I think I am clear why you ask. 

I actually have a task to do related to the MAC addresses of hosts connected to our computer. Your explanation help me to make sure I am on the right track !!   

Thanks ! 

 

So,

---

### Post by NeoIndigo on 2009-01-25
> **jonobr said:**
> The best way for me would be using something like snmpwalk, a program that uses snmp to gather information.

If SNMP is enabled on the remote device (a lot do by default) and if you know the community strings, (its usually private and public for read and read + write

the default query would be
snmpwalk <IPaddr_device_or_name> <community_string> IpnetToMediaPhysAddress

eg snmpwalk 20.20.20.20 public IpnetToMediaPhysAddress

Thanks for the information !!

---

