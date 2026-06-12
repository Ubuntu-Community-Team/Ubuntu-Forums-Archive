---
title: "iproute2 loopback source address"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by racitup on 2011-12-17
Hi,
I'm trying to set up a test bed where I can use a single machine to do some network packet captures between 2 different applications without needing a network connection.
I'm actually trying to do some SIP VoIP development, but for illustration purposes will use ping. I want:
ping 127.0.0.1 (will send a packet dest: 127.0.0.1, src: 127.0.0.2)
(the reply will be dest: 127.0.0.2, src: 127.0.0.1)
Except I DON'T want to use the -I option.

I have figured out how to add the addresses to lo:
/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto lo:0
allow-hotplug lo:0
iface lo:0 inet static
  address 127.0.0.2
  netmask 255.0.0.0

```This works.

However, whenever I try to use these addresses as sources in the iproute2 command there appears to be something overriding my routes:
```

sudo ip route replace local 127.0.0.1 dev lo table local scope host src 127.0.0.2 proto static
sudo ip route replace local 127.0.0.2 dev lo table local scope host src 127.0.0.1 proto static

rich@adventure:~$ ip route show table local
broadcast 192.168.0.255 dev eth0  proto kernel  scope link  src 192.168.0.2 
broadcast 192.168.0.255 dev wlan0  proto kernel  scope link  src 192.168.0.6 
broadcast 127.255.255.255 dev lo  proto kernel  scope link  src 127.0.0.1 
broadcast 172.16.250.255 dev vmnet1  proto kernel  scope link  src 172.16.250.1 
broadcast 172.16.226.255 dev vmnet8  proto kernel  scope link  src 172.16.226.1 
broadcast 192.168.0.0 dev eth0  proto kernel  scope link  src 192.168.0.2 
broadcast 192.168.0.0 dev wlan0  proto kernel  scope link  src 192.168.0.6 
broadcast 172.16.250.0 dev vmnet1  proto kernel  scope link  src 172.16.250.1 
local 192.168.0.2 dev eth0  proto kernel  scope host  src 192.168.0.2 
local 172.16.250.1 dev vmnet1  proto kernel  scope host  src 172.16.250.1 
broadcast 172.16.226.0 dev vmnet8  proto kernel  scope link  src 172.16.226.1 
local 127.0.0.2 dev lo  proto static  scope host  src 127.0.0.1 
local 172.16.226.1 dev vmnet8  proto kernel  scope host  src 172.16.226.1 
broadcast 127.0.0.0 dev lo  proto kernel  scope link  src 127.0.0.1 
local 192.168.0.6 dev wlan0  proto kernel  scope host  src 192.168.0.6 
local 127.0.0.1 dev lo  proto static  scope host  src 127.0.0.2 
local 127.0.0.0/8 dev lo  proto kernel  scope host  src 127.0.0.1 

rich@adventure:~$ ip route get 127.0.0.1
local 127.0.0.1 dev lo  src 127.0.0.1 
    cache <local>  mtu 16436 advmss 16396 hoplimit 64
rich@adventure:~$ ip route get 127.0.0.2
local 127.0.0.2 dev lo  src 127.0.0.2 
    cache <local>  mtu 16436 advmss 16396 hoplimit 64

rich@adventure:~$ sudo ip route del 127.0.0.0/8 table local
rich@adventure:~$ ip route show table local
broadcast 192.168.0.255 dev eth0  proto kernel  scope link  src 192.168.0.2 
broadcast 192.168.0.255 dev wlan0  proto kernel  scope link  src 192.168.0.6 
broadcast 127.255.255.255 dev lo  proto kernel  scope link  src 127.0.0.1 
broadcast 172.16.250.255 dev vmnet1  proto kernel  scope link  src 172.16.250.1 
broadcast 172.16.226.255 dev vmnet8  proto kernel  scope link  src 172.16.226.1 
broadcast 192.168.0.0 dev eth0  proto kernel  scope link  src 192.168.0.2 
broadcast 192.168.0.0 dev wlan0  proto kernel  scope link  src 192.168.0.6 
broadcast 172.16.250.0 dev vmnet1  proto kernel  scope link  src 172.16.250.1 
local 192.168.0.2 dev eth0  proto kernel  scope host  src 192.168.0.2 
local 172.16.250.1 dev vmnet1  proto kernel  scope host  src 172.16.250.1 
broadcast 172.16.226.0 dev vmnet8  proto kernel  scope link  src 172.16.226.1 
local 127.0.0.2 dev lo  proto static  scope host  src 127.0.0.1 
local 172.16.226.1 dev vmnet8  proto kernel  scope host  src 172.16.226.1 
broadcast 127.0.0.0 dev lo  proto kernel  scope link  src 127.0.0.1 
local 192.168.0.6 dev wlan0  proto kernel  scope host  src 192.168.0.6 
local 127.0.0.1 dev lo  proto static  scope host  src 127.0.0.2 

rich@adventure:~$ sudo ip route flush table cache
rich@adventure:~$ ip route get 127.0.0.1
local 127.0.0.1 dev lo  src 127.0.0.1 
    cache <local>  mtu 16436 advmss 16396 hoplimit 64
rich@adventure:~$ ip route get 127.0.0.2
local 127.0.0.2 dev lo  src 127.0.0.2 
    cache <local>  mtu 16436 advmss 16396 hoplimit 64

```And doing a packet capture confirms the results of "ip route get"
I read somewhere that the "src" is only a "hint" to the kernel. Is there a way to make it strict!?
Any help would be much appreciated!

TIA,
Richard

---

### Post by racitup on 2011-12-21
Bump, anyone? :(

---

