---
title: "suddenly the internet not work"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by erez1012 on 2006-05-29
I work with lan network in my ppc g3 ubuntu 5.1
when the system is up the network interfaces dont find a net
the network connection (eth0) in the desktop is active, their is sent and received.

thanks

when i write : ping -c 5 [www.google.com](www.google.com)
ping -c 5 64.233.183.104

its write ping: unknown host
connect: network is unreachable

i write sudo dhclient eth0 it dont work

when i do it manual i connect just to the other computer in my home

---

### Post by ssam on 2006-05-29
the output of the following commands would be usefull to diagnose the problem

```
ifconfig
route
ping -c 5 www.google.com
ping -c 5 64.233.183.104

```

---

### Post by erez1012 on 2006-05-29
its write ping: unknown host
connect: network is unreachable

---

### Post by erez1012 on 2006-05-29
when i write ifconfig its write:
etho     link encap:ethernet hwaddr00:0a:1f:6c
up broadcast running multicast ...............

---

### Post by ssam on 2006-05-29
looks like you have no IP address. you should get this from a dhcp server when you connect (unless you have it set to manual)

does
```
sudo dhclient eth0
```
make it work?

---

### Post by eidex on 2006-05-29
hi, i've got problems with my network as well, i accidently pulled the plug while doing a
 "**apt-get install ipmasq dnsmasq dhcpd**" for mac on linux. after rebooting i had to do a **sudo dpkg --configure -a**. 

when i boot the iBook with an connected ethernet cable to my router the internet connection runs fine. if i start my script for a wireless airport connection everything seems just fine but i get no internet connection:

```
 
.paul@wolfos-laptop:~$ ifconfig eth1
eth1   Protokoll:Ethernet  Hardware Adresse 00:xx:xx:xx:xx:xx
          inet Adresse:192.168.0.3  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::211:24ff:fe91:54c3/64                Gültigkeitsbereich:Verbindung
```

          ```
paul@wolfos-laptop:~$ iwconfig eth1

          eth1      IEEE 802.11b/g  ESSID:"hoehle"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:xx:xx:xx:xx:xx
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:o
```
          
          ```
paul@wolfos-laptop:~$ route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

```
paul@wolfos-laptop:~$ ping -c 5 www.google.com
ping: unknown host www.google.com
```

```
paul@wolfos-laptop:~$ sudo ping -c 5 64.233.183.104
PING 64.233.183.104 (64.233.183.104) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 64.233.183.104 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4012ms
```


So i am connected to my wireless network with a valid ip but i cant reach any servers, not even the router i am connected to. any ideas?

---

### Post by eidex on 2006-05-30
after removing the packages for mol network support (ipmasq dnsmasq dhcpd) it worked again...

---

### Post by erez1012 on 2006-05-30
i write sudo dhclient eth0 and it dont work

when i do it manual i connect gust to the other computer in my home

---

### Post by SqRt7744 on 2006-06-02
if you can connect to another computer on your local network then it sounds like the problem is not related to your network, but rather the connection between the router and your ISP.  Does ifconfig show that eth0 has an IP?

---

### Post by erez1012 on 2006-06-02
when i write ifconfig its write:
etho link encap:ethernet hwaddr00:0a:1f:6c
up broadcast running multicast ...............

in the network setting when i choose static ip it connected just to other computer
but when i choose dhcp, like all the time it is dont connected at all

---

### Post by Iowan on 2006-06-02
[QUOTE=erez1012]when i write ifconfig its write:
etho link encap:ethernet hwaddr00:0a:1f:6c
up broadcast running multicast ...............

in the network setting when i choose static ip it connected just to other computer
but when i choose dhcp, like all the time it is dont connected at all[/QUOTE]Sounds like router setup... unless you have another local server handling DHCP.  If the static address you chose isn't in the router's subnet, it probably won't route.

---

### Post by erez1012 on 2006-06-02
but the other computer(xp) works on this cable?

---

### Post by erez1012 on 2006-06-02
but the other computer(xp) works on this cable?

---

### Post by Iowan on 2006-06-02
DHCP, static, or both?  What IP address does the XP box get/use?

---

### Post by erez1012 on 2006-06-02
the dhcp dont do notting
the static connect just to the xp computer
ip (xp) 84.299.45.150

---

### Post by Iowan on 2006-06-02
Let's back up a couple of steps...
How is your network configured?
Are both machines connected to a router (via hub)?
If there is a router, is it providing DHCP? 
If no router, what is SUPPOSED to provide DHCP... your ISP?
If your ISP is providing DHCP, it *might* issue address to only specific MAC address (which the XP box may have). 
Somewhere, you'll need a gateway address to provide an exit from your LAN.  (ordinarily, this would be your router).

---

### Post by erez1012 on 2006-06-02
i have an old hub and i dont have adialer. i connect with lan
my mac is always connected in dhcp mode and its work wonderful.
the xp and the mac connected to the old hub.

i run the live cd and the internet connection still dont work
it happen suddenly i dont know whay!!

---

### Post by Iowan on 2006-06-02
I seem to have more questions than answers for you...
The PC (XP) and Mac(intosh - not to be confused with Media Access Control) both connect to ISP via hub?
Mac (when not running Ubuntu) gets IP address via DHCP (from ISP)?
Mac (when not running Ubuntu) and PC both reach internet (at the same time)?
Mac (running Ubuntu) does NOT get IP address via DHCP (from ISP)?
Does Mac (running Ubuntu) get IP address (via DHCP) if PC is disconnected?

---

### Post by kpurcell on 2006-06-02
I'm having the same problem as above.  I am booting from Live CD and I have a networked laptop and desktop using a Linksys WRT54G router.  The laptop is a Dell 9300 with a Broadcom 2200 Wifi card.

I have it set up with static ip address.  When in XP it works fine so I no that my network is working.

Using the same address in ubuntu it won't work.  I can access the router, but not the Internet.

---

### Post by kpurcell on 2006-06-02
Just to let you know how I solved my problem.  I went into the networking tool and selected my wireless adapter (eth1) and opened the properties and entered my IP address.  Then in the Network settings box I went to DNS tab and added my router as a DNS server.  Now its working.

---

