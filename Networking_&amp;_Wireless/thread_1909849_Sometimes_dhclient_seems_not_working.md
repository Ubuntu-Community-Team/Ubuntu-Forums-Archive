---
title: "Sometimes dhclient seems not working"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by splater on 2012-01-16
Hi,

running ubuntu 11.10 with
Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)

when powering on the unit sometimes the network manager is not able to get an IP from my LAN. The only solution I have found is to connect the ethernet cable to an other port of the router. (so almost on every start I have to change the position of the ethernet cable ...)

when trying to get the IP I got from ifconfig eth0 ( I replace some data with xx)

```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:1e  
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62556 (62.5 KB)  TX bytes:20005 (20.0 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 
```

Can someone help me with this to see what is the problem? What test can I do when it's happening?

Thx in advance !

---

### Post by varunendra on 2012-01-16
> **splater said:**
> The only solution I have found is to connect the ethernet cable to an other port of the router. (so almost on every start I have to change the position of the ethernet cable ...)
Then replacing the cable, or at least its header plugs (if you can) would be the first thing to suggest.

If you think the cable and other physical contacts are fine, you may try:
```
sudo ifconfig eth0 down
```

then after a few seconds:
```
sudo ifconfig eth0 up
```

If this doesn't seem to help, I'll strongly suggest replacing the cable first.

---

### Post by splater on 2012-01-17
Thanks for your message. I tried this morning and after 3 times of down and up it worked! About the cable I have already change it but the same happens ...
Any more idea? where to check?

thanks
Regards

---

### Post by varunendra on 2012-01-17
Let's go through a standard check-routine then. Please post outputs of:
```

lsb_release -a
uname -rm
ifconfig -a
sudo lshw -C network
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ping x.x.x.x -c 6
(replace x's with IP of your router)
dmesg | grep eth
```

And please post the actual IPs if it's okay for you. It being an IP on LAN's part, doesn't risk any threat from outside world and helps us understand your LAN a bit better. It's not necessary though, as long as you are able to verify its consistency yourself.

---

### Post by splater on 2012-01-17
Thanks again for your help !!!
About 
Hope this helps my internal IP is 192.168.0.39

lsb_release -a
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

uname -rm
```
3.0.0-14-generic x86_64
```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:1a:a0:96:41:1e  
          inet addr:192.168.0.39  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxxx::xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80917896 (80.9 MB)  TX bytes:25895440 (25.8 MB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21049 (21.0 KB)  TX bytes:21049 (21.0 KB)
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:96:41:1e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=1.1-2 ip=192.168.0.39 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
```

lsmod
```
Module                  Size  Used by
ipheth                 13563  0 
des_generic            21415  0 
md4                    12595  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  1 
parport_pc             36962  0 
ppdev                  17113  0 
vboxdrv               282739  4 vboxpci,vboxnetadp,vboxnetflt
nls_utf8               12557  15 
cifs                  273872  16 
binfmt_misc            17540  1 
ftdi_sio               40675  1 
usbserial              47107  3 ftdi_sio
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
dcdbas                 14490  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
radeon               1016226  4 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
soundcore              12680  1 snd
drm                   236290  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
floppy                 70365  0 
e1000e                160582  0
```


cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

cat /etc/resolv.conf
```
# Generated by NetworkManager
domain lan
search lan
nameserver 80.58.61.250
nameserver 80.58.61.254
```

 route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

ping 192.168.0.1 -c 6
```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.55 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=0.910 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=0.942 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=64 time=0.943 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=64 time=0.914 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=64 time=0.901 ms

--- 192.168.0.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5000ms
rtt min/avg/max/mdev = 0.901/1.027/1.553/0.236 ms
```


dmesg | grep eth
```

[    1.550072] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) xx:xx:xx:xx:xx:xx
[    1.550075] e1000e 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    1.550096] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 7, PBA No: FFFFFF-0FF
[   16.876764] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.684764] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   18.684768] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   18.685189] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.024046] eth0: no IPv6 routers present
[   87.056653] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   88.624758] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   88.624765] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   88.625283] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  103.540696] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  104.940766] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  104.940771] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  104.941179] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  115.348032] eth0: no IPv6 routers present
[ 5112.743301] device eth0 entered promiscuous mode
[ 8971.851555] ipheth 2-4:4.2: Apple iPhone USB Ethernet device attached
[ 8971.851572] usbcore: registered new interface driver ipheth
[ 8971.902043] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by varunendra on 2012-01-17
Hi splater, and you are welcome!

I don't see anything abnormal in the above outputs (the link ready / not ready messages in dmesg output seem to be results of you "ifconfig eth0 up/down" commands), although I am not familiar with the network adapter or the driver you are using. So maybe looking a bit deeper into them may reveal if there is some known issue related to them. I'll do that as soon as I get sufficient time to dig it.

Meanwhile, when it fails to get address, try dmesg once more (looking for *e1000e* errors this time) to see if something appears suspicious. Post the result if not sure. This time, make it:
```
dmesg | grep -iE 'eth | e1000e'
```


Additionally, please try disabling IPv6 on your port using any of these guides (although I don't know how it can be related, but I come across new things every day!):
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)


Also, can you make sure the fault is not on the router's side? That is, are there other computers in the network which work fine with DHCP? (or the same system with a different OS/kernel)

---

### Post by spacecheck on 2012-01-17
> Also, can you make sure the fault is not on the router's side? Some routers have a "take a snooze when nothin's goin' on" mode. Sometimes they just snooze too deeply. Check router settings to see if that mode is in operation. IF so, turn it off and see if the problem remains.
Also, look to see if there is a large enough allotment of IP addresses available in the router for all of the devices attached to the subnet, to prevent an alternative device from stealing an IP.

Happy hunting!

---

### Post by jonobr on 2012-01-17
Best way to check if a router has "taken a snooze" is to run the following when its not acquiring

open a terminal window

```
sudo tcpdump -i any proto bootps
```

When the packet is issued you should see something like this

```
0.0.0.0.bootpc-->255.255.255.255
```



This shows a packet went from the machine to the whole network (255.255.255.255 means everyone)

If you see a response then the router is alive and responding.
if you see the same thing over and over again looking for an IP , the router is indeed taking a lyin for some reason.

If you have a hard time reading the results you could post here.

Cheers

jonobr

---

### Post by splater on 2012-01-18
thanks but I get 

tcpdump: unknown ip proto 'bootps'

Regards
Laurent

---

### Post by jonobr on 2012-01-18
yikes


how about this
```

sudo tcpdump -i any  port 67 or port 68
```

---

### Post by splater on 2012-01-19
first thanks for your help.

I tried some stuff this morning because the same thing happens so 

dmesg | grep -iE 'eth | e1000e'
```

[    1.387918] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    1.387921] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.387957] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.387966] e1000e 0000:00:19.0: setting latency timer to 64
[    1.394572] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    1.554089] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) xx:xx:xx:xx:xx:xx
[    1.554093] e1000e 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    1.554113] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 7, PBA No: FFFFFF-0FF
[   17.680197] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   17.736112] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   19.152768] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   19.152773] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
```

then I activate tcpdump and nothing appears. Then with ifconfig up and down it gets the IP adress and I get with tcpdump the following
```

09:27:58.756227 IP 192.168.0.1.bootps > xxxxxx.bootpc: BOOTP/DHCP, Reply, length 283
09:27:58.760868 IP 192.168.0.1.bootps > xxxxxx.bootpc: BOOTP/DHCP, Reply, length 283

```


It is strange, it seems the switch (dlink DES-1016D) is affecting here because it seems that if I add an other small switch in between it works well ...

any idea?
Thanks

---

### Post by jonobr on 2012-01-19
Hey there,

looking at your logs, I wondering if you have auto negotiation problems with the switch?

Ethernet interfaces are usually set to auto where they figure out each others capabilities.
they figure if they are 10, 100 or gig speeds and whether they are full or half duplex,
sometimes, this doesn't work and usually setting one side to a set rate as opposed to negotiating it helps
[here is a good article about it]("http://www.linuxscrew.com/2008/11/20/faq-how-to-change-duplex-andor-auto-negotiation-nic-settings-in-linux/") you will need something like ethtool to set your Nic configuration

---

### Post by splater on 2012-01-24
Thanks Jonobr, it could be !! with ethtool I got when the problem occurs this morning:

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000001 (1)
			       drv
	Link detected: yes

when putting down and up eth0 and solving the problem:
I have seen only one difference with ethtool
MDI-X: off

Any clue?
Tomorrow I will try the following
[http://kerneltrap.org/mailarchive/linux-netdev/2010/11/17/6289820](http://kerneltrap.org/mailarchive/linux-netdev/2010/11/17/6289820)

Thanks for your help

---

### Post by splater on 2012-02-20
well no luck ... the only think that works is to do


sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo ethtool -r eth0

and still it's not always I have to try sometimes 2 or 3 times ...

Any ideas to try?

Thanks

---

### Post by roelforg on 2012-02-20
> **splater said:**
> Thanks again for your help !!!
About 
Hope this helps my internal IP is 192.168.0.39
....
cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

I'm gonna address the elephant in the room here.
Add this to your /etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp

```
Skip the 1e line if you don't want ubuntu autoloading your nic (i can't see why not, but hey)
Reboot and try again.

---

### Post by splater on 2012-03-11
well I tried all thoses things but no results ...
I wil ltry to change the switch and see ..

---

