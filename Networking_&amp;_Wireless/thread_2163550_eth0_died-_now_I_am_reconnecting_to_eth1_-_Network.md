---
title: "eth0 died- now I am reconnecting to eth1 - NetworkManger does not connect"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by spindler on 2013-07-18
I had a issue with my hardware.  eth0 is a wired ethernet connection on my motherboard.  I needed to add an additional network connection called eth1.

I am unable to automatically connect to the internet.  The machine always wants to point to eth0.  So I had to make some changes to my system.

1. I changed rc.local to automatically disable eth0 at start up. 
2. Then I changed the NetworkManager.conf so it automatically connects to the internet.... However this is associating with ifupdown(eth1)

Every time I restart the server I must log in and manually change the device to "Wired Connection 1", which is eth1 in order to get internet connectivity.

Here is my rc.local file.

```

sudo ifconfig eth0 down

exit 0

```

Here is my NetworkManager.conf file

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq
no-auto-default=00:21:5A:E0:60:95,   ;  this is eth0  - I changed it to eth1...which did not help.
[ifupdown]
managed=true

```


Automatically NetworkManager is connecting to eth0.     I tried changing the  "no-auto-default = eth1  but what this did was created "Wired Connection 2"  in the System-connection directory. NetworkManager still defaults to eth0.

Where is the reference to the default network card?
How can I get Ubuntu 12.04 to point to eth1?

Thanks,

spindler

---

### Post by steeldriver on 2013-07-18
It may be possible to disable the eth0 device in BIOS - if not, you have a couple of other options

[LIST=1]
[*]list the device (by its MAC) in an unmanaged-devices section of the NetworkManager.conf file 
[*]remove / blacklist the driver (obviously only feasible if eth1 does not use the same driver) 
[/LIST]
 Both methods are described here --> [http://ubuntuforums.org/showthread.php?t=2056652&highlight=unmanaged-devices](http://ubuntuforums.org/showthread.php?t=2056652&highlight=unmanaged-devices)

---

### Post by spindler on 2013-07-19
Thank you for your help.  I was able to disable eth0.   However I cannot 100% connect to the internet.

I am using NetworkManager to manage my connection.   Here is the file  .

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq
no-auto-default=90:E2:BA:44:E7:71,      ; My eth1 network card

[ifupdown]
managed=true

[keyfile]
unmanged-devices=mac:00:21:5A:E0:60:95     ; my defective eth0.


```

When I reboot and attempt to connect I see that the device connected is "ifupdown(eth1)"

Test #1

When I use this connection I am able to probe the following ports using nmap from a MAC computer:

 5060
8080

command is:
```

sudo nmap -sU -p 5060 xxx.xxx.xxx.xxx

```

HOWEVER,  I cannot go to [www.google.ca](www.google.ca) nor can I see my localhost:8080 from the server.

Test #2:

When I change the connection to "Wired Connection" (which uses the same device (eth1)) by clicking on the Network button  on the top right hand corner of the desktop GUI. 

I am now able to see [www.google.ca](www.google.ca) from the server.

HOWEVER, Ports 5060, 8080 are now closed.

Not really sure what is going on or why the two different "types" of connections to the same device produce different results.

Any idea how I can configure eth1 so it has the ports open and can communicate in a bi-direction manner?

Thanks,

---

### Post by steeldriver on 2013-07-19
We the fact that you have 'managed=true' in the ifupdown section suggests you've defined something in /etc/network/interfaces - is that the case? If so please post the contents of that file

Usually it's better to leave only the loopback definition (lo) in /etc/network/interfaces if you want Network-Manager to control your connections

---

### Post by spindler on 2013-07-19
I have set up a static ip address for this machine.  I also included the nameserver information.

Here is my file

```

#The loopback network interface
auto lo
iface lo inet loopback

#The Primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.186
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.186
gateway 192.168.1.1

nsc21.so.cg.shaw.net xx.xx.135.133
nsc22.so.cg.shaw.net xx.xx.135.135
nsc23.so.cg.shaw.net xx.xx.135.143
nsc24.so.cg.shaw.net xx.xx.135.145


```

In an ideal world I would rather not use Network Manager. I would rather alter a .conf file or something so it is clear what the settings are. I would rather not guess at what the device is doing.

---

