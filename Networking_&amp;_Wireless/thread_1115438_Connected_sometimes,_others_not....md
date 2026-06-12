---
title: "Connected sometimes, others not..."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by fritzy27 on 2009-04-03
I'M A NOVICE, BE GENTLE!
I've installed Ubuntu on a brand new system and it connected to my wired internet no problem. Occasionally it does not when I start up the system. For now we have simply ignored the problem and done a Restart which usually works with one iteration. I'd like to fix this, or at least understand how to deal with it without a Restart. Please help!

Is there a command I can type/click that will tell it to "try connecting again"?

A little searching on this forum told me that the command ifconfig might tell someone something, but I am not sure what...

Here is the output when all is well (i.e. connected):
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
fritzy@fritzy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:73:d1:8a  
          inet addr:71.232.74.17  Bcast:71.232.75.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:193389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23032 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:25405216 (25.4 MB)  TX bytes:2837556 (2.8 MB)
          Interrupt:221 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

And here it is when it does not connect:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
fritzy@fritzy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:73:d1:8a  
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:21705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1321275 (1.3 MB)  TX bytes:2522 (2.5 KB)
          Interrupt:221 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:968 (968.0 B)  TX bytes:968 (968.0 B)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Thanks!

---

### Post by oobe-feisty on 2009-04-03
```
sudo /etc/init.d/networking
```

will restart your network services are you using Network-Managers its a tad buggy

tell us more about how you connect to the internet or networks i.e cable modem. etc. adsl etc. looks like your pc gets assinged a wan ip address so it looks like it could be connected using some kind of ppp

---

### Post by fritzy27 on 2009-04-03
I am not really using anything...I just start up the system and click Firefox. 

It is through a cable modem.

I am not sure about a "wan" ip address...novice...or if I have a "ppp".

I am eager to type some commands and learn, however:p

---

### Post by oobe-feisty on 2009-04-03
> **fritzy27 said:**
> I am not really using anything...

yes you are you just dont know what your using.


we can find out whats going on if you type these commands in a console

ifconfig 

and 

route -n 

cat /etc/resolv.conf

cat /etc/network/interfaces

  pppoe-discovery -I eth0


post back with the out put of each command just copy and paste them. these should all be done while connected 
P.S i havent used pppoe-discovery before so if it doesnt work done worry about it

---

### Post by fritzy27 on 2009-04-04
Correct...using, but don't know what. 

Here is what I get while connected when I type the commands you suggested:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
fritzy@fritzy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:73:d1:8a  
          inet addr:71.232.74.17  Bcast:71.232.75.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:116681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:7867572 (7.8 MB)  TX bytes:186950 (186.9 KB)
          Interrupt:221 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

fritzy@fritzy-desktop:~$ route -n 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
71.232.72.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         71.232.72.1     0.0.0.0         UG    0      0        0 eth0
fritzy@fritzy-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain hsd1.ma.comcast.net.
search hsd1.ma.comcast.net.
nameserver 68.87.71.226
nameserver 68.87.73.242
nameserver 68.87.64.146
fritzy@fritzy-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

fritzy@fritzy-desktop:~$ pppoe-discovery -I eth0
Cannot create raw socket -- pppoe must be run as root.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Thanks for the help!

---

### Post by oobe-feisty on 2009-04-05
ok try this 

uninstall network-manager   

sudo apt-get remove network-manager-kde  network-manager-gnome

then backup and overwrite /etc/network/interfaces

sudo cp /etc/network/interfaces /etc/network/interfaces.old

then open /etc/network/interfaces for editing 

gksu gedit /etc/network/interfaces

then paste in this below 

auto lo
iface lo inet loopback

```
auto eth0
iface eth0 inet static
address 71.232.74.17 
netmask 255.255.252.0
network 71.232.0.0
broadcast 71.232.75.255
gateway 71.232.72.1 

```

now restart your network services 

sudo /etc/init.d/networking restart


test it 

ping google.com

also you might be using dhcp so if above wont work you can try this in the interfaces file

auto eth0
iface eth0 inet dhcp






if it doesnt work 

you can reverse it all by typeing 


sudo cp /etc/network/interfaces.old /etc/network/interfaces

sudo apt-get install network-manager-kde  network-manager-gnome 

and rebooting

---

