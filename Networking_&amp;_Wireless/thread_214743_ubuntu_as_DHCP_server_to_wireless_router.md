---
title: "ubuntu as DHCP server to wireless router"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by Phatie Mcgee on 2006-07-13
it was suggested that I post this here.. since its more advanced than "Absolute beginner" talk

Orignal thread [here]("http://www.ubuntuforums.org/showthread.php?t=214678")
---------------------------------------------------------------------------
ok I have firestarter installed and kinda setup..

My network is now:
eth0 --cable modem
eth1 --AT&T wireless router
eth2 --PC <-- not working on this yet

under Network settings > eth1 > Properties
Config: Statis IP
IP addy: 192.168.1.105
Subnet: 255.255.255.0
Gateway: blank

In firestarter > prefrences > network settings
(Default gateway=eth0)
Internet device: eth0
Local device: eth1
Enable ICS [X]
Enable DHCP [X]
DHCP Server details:
Create new [X]
Lowest IP: 192.168.1.100
Highest IP: 192.168.1.254
Name Server: <dynamic>

but when I hit accept on that screen I get:
Failed to start the firewall
an unknown error occurred.
Please check your network device settings and make sure your internet connection is active.

While I'm thinking to myself..."ofcourse my internet is active.. im on here right now"...

So im problably thinking wrongly


But on the good news..I can get the AT&T wireless router to accept the static IP.. but I cant connect to any website from any of the wireless laptops we have.. so im guessing a DNS problem? how to resolve?

Thanks so much for the help so far, I'm bound and determined to get this working!

here is my ifconfig:
phat@phaty:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:E8:89:7C:E1
          inet addr:67.185.131.118  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::200:e8ff:fe89:7ce1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3624541 (3.4 MiB)  TX bytes:312224 (304.9 KiB)
          Interrupt:177 Base address:0x2f00

eth1      Link encap:Ethernet  HWaddr 00:0F:3D:7D:25:36
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fe7d:2536/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:185 Base address:0xe800

eth2      Link encap:Ethernet  HWaddr 00:A0:C9:77:FD:17
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39316 (38.3 KiB)  TX bytes:39316 (38.3 KiB)


--------------------------------------------
if someone can tell me what info I need to post here, I'll post it :)

---

### Post by IoCaster on 2006-07-13
You could try setting up the wireless router config as - disable dhcp server, give static ip + config as wireless acces point (wap).

Any comps connecting to wireless router (wap) use the router static ip as gateway. They should be able to work as dhcp clients, but you could always assign them static ips as well.

HTH

---

### Post by haaglin on 2006-07-13
be sure you have downloaded the dhcp3-server, and run 

#sudo dpkg-reconfigure dhcp3-server

and input the card you use to share with. One other thing, after this, you may still get the error, but it should work.

---

### Post by haaglin on 2006-07-13
Here you can take a look at my setup. I have 2 wlan cards, 1 that recieves ip from dhcp (ath0), and one i use to share wlan with (ath1):

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo ath0 ath1
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


iface ath0 inet dhcp
wireless-mode managed
wireless-essid Infosmart

#iface eth0 inet static
#address 192.168.2.1
#netmask 255.255.255.0

iface ath1 inet static
address 192.168.2.1
netmask 255.255.255.0
wireless-mode master
wireless-essid WLAN
wireless-channel 6
iwpriv ath1 mode 3

``` 

and my dhcp config file:

/etc/dhcp3/dhcpd.conf

```
# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 192.168.2.0 netmask 255.255.255.0 {
	option routers 192.168.2.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers 193.75.75.193;
	option ip-forwarding off;
	range dynamic-bootp 192.168.2.100 192.168.2.105;
	default-lease-time 21600;
	max-lease-time 43200;
}

```

---

