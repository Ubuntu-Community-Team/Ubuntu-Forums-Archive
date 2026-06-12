---
title: "Motherboard Change now eth0 (and static IP) is gone"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by MonctonJohn on 2011-09-14
I had to change my motherboard due to Bad capacitors: long story short the hardware is different. I had a static IP setup in /etc/network/interfaces, but now the new NIC is eth1 instead of eth0 and it gets a DHCP IP. KnetworkManager is useless and shows neither interface. I would like to know whats the best way to manage the interfaces and how to get eth1 using the static IP without reboot.

I changed all the eth0 to eth1 in the interfaces file BTW.

---

### Post by haqking on 2011-09-14
> **MonctonJohn said:**
> I had to change my motherboard due to Bad capacitors: long story short the hardware is different. I had a static IP setup in /etc/network/interfaces, but now the new NIC is eth1 instead of eth0 and it gets a DHCP IP. KnetworkManager is useless and shows neither interface. I would like to know whats the best way to manage the interfaces and how to get eth1 using the static IP without reboot.

I changed all the eth0 to eth1 in the interfaces file BTW.


the IP was bound to a MAC address thats why.

see here for information on how to do it [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

and here [http://www.jonathanmoeller.com/screed/?p=2305](http://www.jonathanmoeller.com/screed/?p=2305)

or do it using your Network Manager Applet

---

### Post by drs305 on 2011-09-14
Multiple threads. This one closed.

Other  one is at:
[http://ubuntuforums.org/showthread.php?p=11252380#post11252380]("http://ubuntuforums.org/showthread.php?p=11252380#post11252380")

---

### Post by haqking on 2011-09-14
OK so it seems there was confusion with the thread closures there for a while ;-)

so i hope you are seeing this one now.

Anyways i am confused ? you renamed all the references to eth0 to eth1 ? why did you do that again ?

the local interface alias is stored in :

/etc/udev/rules.d/70-persistent-net.rules

all you needed to do was assign a static to your new ethx interface whatever that was, ethx ?

perhaps i am not understanding you ?

you can assign a static from cli with ifconfig but that is temporary, for persistance then modify your etc/network/interfaces

but i think you have done that but by renaming the interfaces ? is this correct ?

im still confused ;-)

---

### Post by MonctonJohn on 2011-09-15
No problem now.

Here is what happened and what I did.

Old config: eth0: static IP

Installed new motherboard (onboard NIC, just like the old one (eth0))

The system saw a new card and assigned it eth1 and eth0 no longer existed. I had a DHCP address with eth1, but I wanted this machine set back to static as it's my file/media server, so I edited /etc/network/interfaces and changed all the eth0 entries to eth1 since eth1 is now the only NIC.

This did not work as expected so I played around for a while and even tried DHCP again. No luck.

I googled and found a thread saying to modify /etc/udev/rules.d/70-persistent-net.rules. I did this and removed the entry for eth0 (original Mobo NIC) and then changed the new entry from eth1 to eth0 so that I only had the one NIC entry. Then I edited /etc/network/interfaces again to my static IP.

Reboot and I was in business.

---

### Post by haqking on 2011-09-15
> **MonctonJohn said:**
> No problem now.

Here is what happened and what I did.

Old config: eth0: static IP

Installed new motherboard (onboard NIC, just like the old one (eth0))

The system saw a new card and assigned it eth1 and eth0 no longer existed. I had a DHCP address with eth1, but I wanted this machine set back to static as it's my file/media server, so I edited /etc/network/interfaces and changed all the eth0 entries to eth1 since eth1 is now the only NIC.

This did not work as expected so I played around for a while and even tried DHCP again. No luck.

I googled and found a thread saying to modify** /etc/udev/rules.d/70-persistent-net.rules**. I did this and removed the entry for eth0 (original Mobo NIC) and then changed the new entry from eth1 to eth0 so that I only had the one NIC entry. Then I edited /etc/network/interfaces again to my static IP.

Reboot and I was in business.


ahh yeah thought so as i posted above.

glad you got it sorted.

remember to mark your thread as solved using thread tools.

cheers

regards

haqking

---

