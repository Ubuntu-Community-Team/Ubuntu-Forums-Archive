---
title: "I can't use ststic ip with wireless internet connection"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by ibrahim.k on 2009-12-27
When I change the connection settings from DHCP to manual ip configuration i lose the ability to browse internet but instead i can see the current network.


DHCP= internet connection
Manual= local connection

Can I have both at the same time using the same wireless ?

---

### Post by coffeecat on 2009-12-27
When I change my wireless network manager settings from DHCP to manual (in Karmic) I can still browse the internet just fine. So, the question is, what did you do when you set up a manual IP address? Did you use network manager? Most importantly, did you assign DNS server addresses?

You say:

> **ibrahim.k said:**
> DHCP= internet connection
Manual= local connection

Can I have both at the same time using the same wireless ?

I'm not quite sure what you mean by this. Your local network address will be in the range 192.168.x.y or 10.0.x.y depending on the make of router, whether or not you have set up the address manually, or whether you are using DHCP.

Your external IP address (the outward-facing address on your router) will be assigned by your ISP. There's nothing you can do about that.

What version of Ubuntu are you using? I presume you are using a wireless modem-router. Correct? Do you have any other computers on your local network? Do you assign manual addresses with them or do you use DHCP?

---

### Post by puppywhacker on 2009-12-27
yes with an interface alias (eth0:1), but you will have to let go of the network manager gui and configure your network in /etc/network/interfaces

```
auto lo eth0 eth0:1
iface eth0 inet dhcp

iface eth0:1 inet static
        address 192.168.10.1
        netmask 255.255.255.0

```

and restart networking
```
sudo service network restart
```

---

### Post by ibrahim.k on 2009-12-27
I tried it on ubuntu 9.10 and it didn't work 


> **puppywhacker said:**
> yes with an interface alias (eth0:1), but you will have to let go of the network manager gui and configure your network in /etc/network/interfaces

```
auto lo eth0 eth0:1
iface eth1 inet dhcp

iface eth0:1 inet static
        address 192.168.1.1
        netmask 255.255.255.0

```

---

### Post by ibrahim.k on 2009-12-27
i am using ubuntu 9.10 when i changed it into the manual ip adress using the network manager it was like this
 _192.168.10.1_
255.255.255.0
192.168.10.1
I didn't use DNS settings the field is empty
i am using my laptop wireless
yes i have other computers on the local network I don't use dhcp mode with them
thnx [coffeecat]("http://ubuntuforums.org/member.php?u=129087")

> **coffeecat said:**
> When I change my wireless network manager settings from DHCP to manual (in Karmic) I can still browse the internet just fine. So, the question is, what did you do when you set up a manual IP address? Did you use network manager? Most importantly, did you assign DNS server addresses?

You say:



I'm not quite sure what you mean by this. Your local network address will be in the range 192.168.x.y or 10.0.x.y depending on the make of router, whether or not you have set up the address manually, or whether you are using DHCP.

Your external IP address (the outward-facing address on your router) will be assigned by your ISP. There's nothing you can do about that.

What version of Ubuntu are you using? I presume you are using a wireless modem-router. Correct? Do you have any other computers on your local network? Do you assign manual addresses with them or do you use DHCP?

---

### Post by gradinaruvasile on 2009-12-27
> **ibrahim.k said:**
> When I change the connection settings from DHCP to manual ip configuration i lose the ability to browse internet but instead i can see the current network.


DHCP= internet connection
Manual= local connection

Can I have both at the same time using the same wireless ?

You can have 1 ip assigned to 1 device... Why do you need both?
I use manual IP on wireless and works, no problem.

Try this:
Set to dhcp, connect to it, right-click on the network manager icon, select connection information.
Copy all data from there.

Then set up your manual connection, make sure you give an IP from the same class, use the same netmask, and the most important, use the same gateway/dns servers as from the dhcp connection. That way it will work.

---

### Post by coffeecat on 2009-12-27
> **ibrahim.k said:**
> _192.168.10.1_
255.255.255.0
192.168.10.1
I didn't use DNS settings the field is empty
i am using my laptop wireless


That's your problem - empty DNS settings. When using some (most? all?) routers you need to specify DNS server addresses in network manager if you are setting up your local IP address manually. That's why you can't browse the internet - no DNS resolution.

Use the DNS addresses supplied by your ISP or use OpenDNS.

---

### Post by cabaro on 2009-12-27
> **coffeecat said:**
> That's your problem - empty DNS settings. When using some (most? all?) routers you need to specify DNS server addresses in network manager if you are setting up your local IP address manually. That's why you can't browse the internet - no DNS resolution.

Use the DNS addresses supplied by your ISP or use OpenDNS.

Also Your router ip might work for dns.

---

### Post by focwiz on 2009-12-27
[QUOTE=ibrahim.k;8565526]i am using ubuntu 9.10 when i changed it into the manual ip adress using the network manager it was like this
 _192.168.10.1_
255.255.255.0
192.168.10.1
I didn't use DNS settings the field is empty
i am using my laptop wireless
yes i have other computers on the local network I don't use dhcp mode with them
thnx 

See the attached file for manual settings with explanations...

---

### Post by ibrahim.k on 2009-12-28
I have used this settings with my wireless but still not working
192.168.10.1 (available)
255.255.255.0
192.168.0.1 (gateway wireless router)
[FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]isp dns ([/SIZE][/FONT][FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]82.137.200.86, [/SIZE][/FONT][FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]82.137.200.83)
and didn't work anymore suggestions ?
also i tried to use the gateway ip instead of the dns didn' work !
[/SIZE][/FONT]

---

### Post by iponeverything on 2009-12-28
> **ibrahim.k said:**
> I have used this settings with my wireless but still not working
192.168.10.1 (available)
255.255.255.0
192.168.0.1 (gateway wireless router)
[FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]isp dns ([/SIZE][/FONT][FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]82.137.200.86, [/SIZE][/FONT][FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]82.137.200.83)
and didn't work anymore suggestions ?
also i tried to use the gateway ip instead of the dns didn' work !
[/SIZE][/FONT]

Change your netmask to 255.255.0.0 or pick an IP address on the 192.168.0 network.

---

### Post by ibrahim.k on 2009-12-28
Still not working please see the attached photos to know what my settings exactly are

---

### Post by efflandt on 2009-12-28
Why is your **Wired Connection 1** [COLOR=Red]active[/COLOR]?  Its different IP and default gateway of 0.0.0.0 probably interferes with the default gw for your wireless, because that gw to 0.0.0.0 comes before 192.168.0.1 in the routing table. What is the output of **route -n**?

If you need that Wired Connection 1 using a different IP range for something else local only, its gateway should be blank (not 0.0.0.0).  Or if you do not need it [COLOR=Red]uncheck[/COLOR] **Connect Automatically** for it.

---

### Post by ibrahim.k on 2009-12-29
I need both wireless and wired to be connected at the same time.
I cant keep the gateway for wired blank also
when I type route -n
ibrahim@ibrahim-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.10.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
ibrahim@ibrahim-laptop:~$ ^C
ibrahim@ibrahim-laptop:~$ 




> **efflandt said:**
> Why is your **Wired Connection 1** [COLOR=Red]active[/COLOR]?  Its different IP and default gateway of 0.0.0.0 probably interferes with the default gw for your wireless, because that gw to 0.0.0.0 comes before 192.168.0.1 in the routing table. What is the output of **route -n**?

If you need that Wired Connection 1 using a different IP range for something else local only, its gateway should be blank (not 0.0.0.0).  Or if you do not need it [COLOR=Red]uncheck[/COLOR] **Connect Automatically** for it.

---

