---
title: "Hi! How do i configure my hub and ethernet card"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by dhruv_1884 on 2006-04-20
Hi,
I am new to Linux. Only a day old. 
I am using the Live CD version of unbuntu Linux 5.10.
I have a Compaq Evo 320 Desktop
My ethrernet card is Intel 10/100 and i have a hub, through which i connect.

Can i connect to the net.
With Windows, i use the "Obtain IP automatically" option and connect to the service provider throgh the WAN port PPPoE.
Everything was automatically configured by windows.

i am not sure if i have given enough info to trouble shoot this issue,so please to mail me if you feel that you reqiure more info to help me.


Looking forward to using the net from unbuntu.


Regards 
Dc
[email]chopra.dhruv@gmail.com[/email]

PS my windows partitions are both NTFS and i have a FAT flash disk of 256MB

---

### Post by Cavaco on 2006-04-20
Hi , if you can open a terminal window and run

> ifconfig

By Default DHCP should be enabled , I guess depending on how you installed the distro. Can you post the output of the above command ?

---

### Post by Cavaco on 2006-04-20
[QUOTE=Cavaco]Hi , if you can open a terminal window and run

> ifconfig

By Default DHCP should be enabled , I guess depending on how you installed the distro. Can you post the output of the above command ?[/QUOTE]


Also you can post the contents of your /etc/networks/interfaces file ... this defines how an IP address is allocated etc ...

---

### Post by xrmuser on 2006-04-21
Yes you have to run these commands to check your Ubuntu IP settings:
1. ifconfig 
2. route -n

---

### Post by dhruv_1884 on 2006-04-23
Hi,
I'd been out of town for business.
I'll surely do what u've asked me to do and get back to you.
Thanks for offering to help
Regards
Dc

---

### Post by dhruv_1884 on 2006-04-23
[QUOTE=Cavaco]Also you can post the contents of your /etc/networks/interfaces file ... this defines how an IP address is allocated etc ...[/QUOTE]

HI,
i RAN THOSE COMMANDS AND THIS IS WHAT I GOT


ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:8E:62:17
          inet6 addr: fe80::210:dcff:fe8e:6217/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:754230 (736.5 KiB)  TX bytes:3834 (3.7 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:287577 (280.8 KiB)  TX bytes:287577 (280.8 KiB)


ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ubuntu@ubuntu:~$ route -e
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
ubuntu@ubuntu:~$

---

### Post by kamal101 on 2006-04-23
me too i have the same problem
eth0 exists, but is not running or is not active.

when i type ifconfig , it doesnt list eth0, it lists only lo
then when i tried ifconfig eth0 up, then ifconfig lists eth0 and lo.

then when i list eth0 configuration : 
inetaddr is empty, there no ip adress assigned. 

here's my /etc/network/interface file : 

auth lo
iface lo inet loopback

auth eth0
iface eth0 inet dhcp


I'm sure my network card is loaded because its module via-rhine is loaded.
And i checked the physical connexion, the card blinks. and the router says it is in communication with the pc.

:confused:

---

### Post by kamal101 on 2006-04-23
me too i have the same problem
eth0 exists, but is not running or is not active.

when i type ifconfig , it doesnt list eth0, it lists only lo
then when i tried ifconfig eth0 up, then ifconfig lists eth0 and lo.

then when i list eth0 configuration : 
inetaddr is empty, there no ip adress assigned. 

here's my /etc/network/interface file : 

auth lo
iface lo inet loopback

auth eth0
iface eth0 inet dhcp


I'm sure my network card is loaded because its module via-rhine is loaded.
And i checked the physical connexion, the card blinks. and the router says it is in communication with the pc.

:confused:

---

### Post by kamal101 on 2006-04-23
me too i have the same problem
eth0 exists, but is not running or is not active.

when i type ifconfig , it doesnt list eth0, it lists only lo
then when i tried ifconfig eth0 up, then ifconfig lists eth0 and lo.

then when i list eth0 configuration : 
inetaddr is empty, there no ip adress assigned. 

here's my /etc/network/interface file : 

auth lo
iface lo inet loopback

auth eth0
iface eth0 inet dhcp


I'm sure my network card is loaded because its module via-rhine is loaded.
And i checked the physical connexion, the card blinks. and the router says it is in communication with the pc.

:confused:

---

### Post by kamal101 on 2006-04-23
sorry for the 3 posts..
i thought the post didn't work

---

### Post by mips on 2006-04-23
Seems your dhcp is not working. Can you try with a static IP and see if that works. Then we could always try and fix the dhcp.

---

### Post by kamal101 on 2006-04-23
when i set eth0 with static, ip addr: 192.168.1.106
and i do ifconfig eth0, eth0 has been assigned this ip address.
But can't connect to the host.
I mean when i ping 192.168.1.1 or 192.168.1.105, they doesn't respond...
192.168.1.105 machine is an xp machine.
both linux and xp machines are connected to a router.
The router is conected to the modem.
THe router is configured to manager dhcp.
Also it seems that eth0 is not running : 

UP BROADCAST MULTICAST MTU:1500 Metric:1
it is suppoed to be : with "RUNNING" : 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

---

### Post by mips on 2006-04-24
try booting with apci or apic =off

---

### Post by kamal101 on 2006-04-24
it doesn't make sense...
i tried that, it's the same problem
i gonna reinstall all ubuntu

---

### Post by daniel83 on 2006-04-26
I am having the same problem as these guys, but I have no lights on the phyisical connection eaither.

mips ... should that "apci" go on the kernel line of our GRUB menu.lst file?? I will try it, but just wanted to make sure that is what you meant.

Thanks.

---

