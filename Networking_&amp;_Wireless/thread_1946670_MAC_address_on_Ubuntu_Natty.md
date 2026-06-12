---
title: "MAC address on Ubuntu Natty"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by eawz9999 on 2012-03-25
The server must have a specific LAN address to be able to work with programs on my other computers on the LAN. 
My router assigns these addresses on the LAN setup based on MAC (hardware) addresses of the machines. This works fine until I have to reboot Ubuntu, then the server assigns a different MAC address and it connects to a random address. I have to edit my router to record the servers new MAC address.
Setting a manual connection does not help. For instance connect to 192.168.0.100 is wrong because the router’s MAC address is different for that address as set in the previous connection.
I tried editing (_without success_)  /etc/network/interfaces:
auto lo
iface lo inet loopback
_adding_:
auto etho
iface eth0 inet dhcp
	hwsddress ether 01:02:03:04:05:06 (an example)
Is there any way to force Ubuntu to a specific MAC address on reboot? 
Any help would be greatly appreciated.
Thank you, Enrique

---

### Post by haqking on 2012-03-25
> **eawz9999 said:**
> The server must have a specific LAN address to be able to work with programs on my other computers on the LAN. 
My router assigns these addresses on the LAN setup based on MAC (hardware) addresses of the machines. This works fine until I have to reboot Ubuntu, then the server assigns a different MAC address and it connects to a random address. I have to edit my router to record the servers new MAC address.
Setting a manual connection does not help. For instance connect to 192.168.0.100 is wrong because the router’s MAC address is different for that address as set in the previous connection.
I tried editing (_without success_)  /etc/network/interfaces:
auto lo
iface lo inet loopback
_adding_:
auto etho
iface eth0 inet dhcp
	hwsddress ether 01:02:03:04:05:06 (an example)
Is there any way to force Ubuntu to a specific MAC address on reboot? 
Any help would be greatly appreciated.
Thank you, Enrique

you have totally lost me.

why dont you use the actual mac addresses of the devices which never changes.

why are you changing them

---

### Post by eawz9999 on 2012-03-25
Now I am lost. My Ubuntu actual MAC address **_always_** changes on reboot. My windows XP and windows 7 do not.

---

### Post by bkratz on 2012-03-25
> **eawz9999 said:**
> Now I am lost. My Ubuntu actual MAC address **_always_** changes on reboot. My windows XP and windows 7 do not.


I think you are confusing the MAC address with the IP address. The MAC never changes   and looks something like XX:XX:XX:XX:XX:XX

---

### Post by eawz9999 on 2012-03-25
Perhaps I am doing something wrong.
This is my ifconfig NOW
eth0      Link encap:Ethernet  HWaddr _**1c:6f:65:52:91:cc**_
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255 
This is my ifconfig after REBOOT
eth0      Link encap:Ethernet  HWaddr _**aa:00:04:00:0a:04**_
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
Isn't this the MAC address?

---

### Post by haqking on 2012-03-25
> **eawz9999 said:**
> Perhaps I am doing something wrong.
This is my ifconfig NOW
eth0      Link encap:Ethernet  HWaddr _**1c:6f:65:52:91:cc**_
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255 
This is my ifconfig after REBOOT
eth0      Link encap:Ethernet  HWaddr _**aa:00:04:00:0a:04**_
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
Isn't this the MAC address?

ahh ok yeah i have seen that mac address before.

see here [http://www.fantaghost.com/2010/06/eth0-mac-address-fixed-on-aa0004000a04/](http://www.fantaghost.com/2010/06/eth0-mac-address-fixed-on-aa0004000a04/) it usually happens after an install of a network tool/scanner etc or something similiar

---

### Post by bkratz on 2012-03-25
> **eawz9999 said:**
> Perhaps I am doing something wrong.
This is my ifconfig NOW
eth0      Link encap:Ethernet  HWaddr _**1c:6f:65:52:91:cc**_
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255 
This is my ifconfig after REBOOT
eth0      Link encap:Ethernet  HWaddr _**aa:00:04:00:0a:04**_
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
Isn't this the MAC address?


I see it but I don't understand!  The MAC address is part of the hardware.  Anyway, I sit in a motel right now and have to spoof my mac for probably the same reason and this works for me.  

sudo ifconfig eth0 down hw ether XX:XX:XX:XX:XX:XX
sudo ifconfig eth0 up 


put what you want at the xx's

---

### Post by eawz9999 on 2012-03-25
**THANK YOU VERY MUCH HAQKING!!!**
I don't know how those DECnet got into my server, probably due to experimenting with programing. They were not listed as installed. I reinstalled those libraries and tools and then I totally remove them.
Now my server's MAC address is always the same!
Working great!
Enrique

---

### Post by bkratz on 2012-03-25
thanks from me too, I learned something!

---

### Post by haqking on 2012-03-25
no worries you are welcome.

Remember to mark the thread as solved using thread tools menu.

Cheers

---

