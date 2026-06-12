---
title: "ip address change problem!"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by paprikaUpavlaci83 on 2012-02-08
Does anyone know how to permanently change the ip address?
I want to change my ip address in /etc/network/interfaces file, but there is only:

auto lo
iface lo inet loopback

there's no eth0 lines that i have to edit. Please help

---

### Post by jonobr on 2012-02-08
Hello


You need to ensure that the nm applet is not controlling your nic

You can stop it using 
```
sudo /etc/init.d/NetworkManager stop 
```

If you want you can remove altogether by doing

```
sudo apt-get remove network-manager-gnome
```
If you want to remove it, then only do that once your new configuration is good
You would have to add an entry for your nic in /etc/network/interfaces

Eg if its eth0



```
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

You would obviously need to change as required for your configuration/;

You may also add a dns enrty into /etc/resolv.conf based on your dns settings

---

### Post by capscrew on 2012-02-08
> **jonobr said:**
> ...
Eg if its eth0

```
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

You would obviously need to change as required for your configuration/;

You may also add a dns enrty into /etc/resolv.conf based on your dns settings

If you want this configuration to bring up the interface at boot you should add this also```
auto eth0

```
I usually add it just above the code that @jonobr provided.  It doesn't have anything do do with dhcp.  :-)

---

### Post by jonobr on 2012-02-08
Yikes


Fair catch capscrew, its been a long day:-)

---

### Post by paprikaUpavlaci83 on 2012-02-09
Ok, i removed network manager and i couldn't get the Internet back on so i
reinstalled it back and now i don't have the /etc/network/interfaces file any more

this is my connection information:

IPv4
IP Address: 172.16.1.78
Broadcast Address: 172.16.255.255
Subnet Mask: 255.255.0.0
Default Route: 172.16.0.1
Primary DNS: 172.16.0.1

should the interfaces file look like this and only this:
auto eth0

iface eth0 inet static
 address 172.16.1.xxx (new ip)
 netmask 255.255.0.0
 network 192.168.1.0 (dont know what is this, should it look like 172.16.0.0?)
 broadcast 172.16.255.255
 gateway 172.16.0.1

---

### Post by jonobr on 2012-02-09
Hello


The network address should be a 172,
however, do you won the default router?
Are you on a 172 network?
Did someone give you that static IP address?
If you assign that to your self, and its in the DHCP pool, it will cause trouble.
If you assign the nic a 172 and its in a 192 network, then your not going to work their either,

Would you not jsut leave everything DHCP and make life easy on your self?

---

### Post by capscrew on 2012-02-09
> **paprikaUpavlaci83 said:**
> Ok, i removed network manager and i couldn't get the Internet back on so i
reinstalled it back and now i don't have the /etc/network/interfaces file any more

this is my connection information:

IPv4
IP Address: 172.16.1.78
Broadcast Address: 172.16.255.255
Subnet Mask: 255.255.0.0
Default Route: 172.16.0.1
Primary DNS: 172.16.0.1

should the interfaces file look like this and only this:
auto eth0

iface eth0 inet static
 address 172.16.1.xxx (new ip) [COLOR="Red"]**Use whatever address you want in the range you pick.  It won't directly face the internet**[/COLOR]
 netmask 255.255.0.0 [COLOR="Red"]or use 255.255.255.0 (a /24 net)[/COLOR]
 network 192.168.1.0 (dont know what is this, should it look like 172.16.0.0?) [COLOR="Red"]not needed[/COLOR]  
 broadcast 172.16.255.255 [COLOR="Red"]if using a /24 net it SB 172.16.0.255[/COLOR]
 gateway 172.16.0.1[COLOR="Red"]Is this the router LAN side interface?[/COLOR]

The entire 172.16.0.0 /12 address space is for private addresses only.  This runs between 172.16.0.1 to 172.31.255.255.  it is functionally the same as using a 192.168.0.0 /12 address space.  With that said, see my comments in read above.

Edit: as @jonobr said, you need to define the IP range of your network and all addresses SB in that range.  This is done with the netmask, as it defines the start and end of the range.

---

### Post by paprikaUpavlaci83 on 2012-02-09
> The network address should be a 172,
however, do you won the default router?
i dont have access to the router

> Are you on a 172 network?
i think i am, all ip addresses on all computers start with 172
> 
Did someone give you that static IP address?
im not sure, no one made any configurations since i installed ubuntu

> If you assign that to your self, and its in the DHCP pool, it will cause trouble.
i dont know what DHCP pool is

> Would you not jsut leave everything DHCP and make life easy on your self?
no, i like to know how things work even if its a pain in the *** work :)
but if you think im wasting my time i wont waste yours

---

### Post by capscrew on 2012-02-09
> **paprikaUpavlaci83 said:**
> i dont have access to the router


i think i am, all ip addresses on all computers start with 172

im not sure, no one made any configurations since i installed ubuntu


i dont know what DHCP pool is


no, i like to know how things work even if its a pain in the *** work :)
but if you think im wasting my time i wont waste yours

You need to ask the sys admin of the router what the ip range is of the network you are on.  In addition you need to ask the scope of his/her dhcp pool is.  Then you can set your static configuration.

---

### Post by paprikaUpavlaci83 on 2012-02-09
> **capscrew said:**
> You need to ask the sys admin of the router what the ip range is of the network you are on.  In addition you need to ask the scope of his/her dhcp pool is.  Then you can set your static configuration.

so it is possible to change the ip even if i dont have access to the router? all i need is the range and dhcp pool info?

---

### Post by capscrew on 2012-02-09
> **paprikaUpavlaci83 said:**
> so it is possible to change the ip even if i dont have access to the router? all i need is the range and dhcp pool info?

Let me answer the question in another way.  The IP address is only to differentiate you machine from others at the IP address level of a network.  This means you must use a number that is in that network range.  It can be assigned via dhcp or statically (via a conf file). There is no advantage to the end user how the address is procured.  At the LAN level you communicate by MAC addresses anyway.  This is via ARP and that is not configurable,  except to change the MAC address.  But to what end?

I've seen your other threads.  I would work with the sys admin to learn how the system works.  You are a threat to the network right now.  Sys Admins don't like folks messing with their networks.

---

### Post by jonobr on 2012-02-09
Hello

DHCP wont know you gave yourself a static and will probably eventually hand out your IP address to some else.
Then you will have an IP address conflict and a very annoyed sysadmin breathing down your neck....

---

### Post by paprikaUpavlaci83 on 2012-02-09
ok, thanks for the info guys, ill figure things out on my own from here.

---

