---
title: "Can't resolve windows host names on the network"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by sepul6 on 2011-09-25
I can't access resolve hostnames on the network, pinging them by name doesn't work either, but ip address works fine.
anyway, I really need to access them by name, could you give me some hints on how can I fix this? I'm also a newbie to linux and networking.

I have already installed samba, and windows computers can access my shares. they can also resolve and ping my linux ("ping sepul-laptop") without a problem.

my network configuration is a router/adsl modem on 192.168.1.1
and wireless computers connect through an access point on 192.168.1.2

here's my /etc/samba/smb.conf :
```

[global]
	workgroup = HOMEGROUP
	netbios name = sepul-laptop
;	server string = samba 3.5.8
	username map = /etc/samba/smbusers
	security = user
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

[Downloads]
	path = /home/....
        ....

```

here's "smbtree -l" command result :
```

HOMEGROUP
	\\SEPUL-LAPTOP   		Samba 3.5.8
		\\SEPUL-LAPTOP\IPC$           	IPC Service (Samba 3.5.8)
		\\SEPUL-LAPTOP\Pictures       	
		\\SEPUL-LAPTOP\Downloads      	
	\\HOST-PC    

```

"ping host-pc" doesn't work, but nmb (NetBIOS?) resolve works fine :
```

 nmblookup host-pc
querying host-pc on 192.168.1.255
192.168.1.4 host-pc<00>

```

and here's my ifconfig :
```

eth0      Link encap:Ethernet  HWaddr 00:15:c5:37:13:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:254307 (254.3 KB)  TX bytes:254307 (254.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:6c:6a:fe  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [blah blah]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3585371 (3.5 MB)  TX bytes:1272298 (1.2 MB)

```

and here's "route -n" result, in case if gateway/router setup is important :
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```
any help would be really appreciated
thanks.

---

### Post by sepul6 on 2011-09-28
up
anyone ?

---

