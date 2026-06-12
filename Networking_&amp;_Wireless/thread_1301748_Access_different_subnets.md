---
title: "Access different subnets"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by reasilvabr on 2009-10-26
Hi ubuntu users,

It's my first post here on Ubuntu. I'm trying to get rid of windows once and for all and this must be the third or fourth try. Now, my problem is:

I am on a huge network on the company I work. I have an IP (via DHCP) like 10.2.4.194.
I need to connect to a VMWare which IP is 192.168.34.53.

I've used nmap and it finds the IP. If with windows, i can find and ping the IP, and the vmware works, but i can't ping it on Ubuntu and can't connect to vmware.

Can you help me?!

Please let me know if you need some more information (i'm sure you will, but i don't know where to start)!

Thanks in advance,

Renato.

---[EDIT]---

i took Route PRINT output from a windows machine that's working fine:

===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       10.2.1.200       10.2.5.143     20
         10.2.0.0    255.255.248.0       10.2.5.143       10.2.5.143     20
         10.2.2.0    255.255.254.0       10.2.1.200       10.2.5.143      1
       10.2.5.143  255.255.255.255        127.0.0.1        127.0.0.1     20
         10.2.6.0    255.255.254.0       10.2.1.200       10.2.5.143      1
   10.255.255.255  255.255.255.255       10.2.5.143       10.2.5.143     20
        127.0.0.0        255.0.0.0        127.0.0.1        127.0.0.1      1
        224.0.0.0        240.0.0.0       10.2.5.143       10.2.5.143     20
  255.255.255.255  255.255.255.255       10.2.5.143                2      1
  255.255.255.255  255.255.255.255       10.2.5.143       10.2.5.143      1
Default Gateway:        10.2.1.200
===========================================================================
Persistent Routes:
  NoneAnd here goes "route" output from my Ubuntu:
Destino                Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
10.2.0.0                      *               255.255.248.0         U          1      0        0 eth0
link-local                     *               255.255.0.0             U       1000   0        0 eth0
default                  10.2.1.200      0.0.0.0                    UG        0      0        0 eth0

---

### Post by reasilvabr on 2009-10-27
OK, seems like it wasn't helpful (the info I sent) so here it goes again, now I hope it's at least organized:

this is what is shown on another machine with windows route PRINT command:

```

Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       10.2.1.200       10.2.5.143     20
         10.2.0.0    255.255.248.0       10.2.5.143       10.2.5.143     20
         10.2.2.0    255.255.254.0       10.2.1.200       10.2.5.143      1
       10.2.5.143  255.255.255.255        127.0.0.1        127.0.0.1     20
         10.2.6.0    255.255.254.0       10.2.1.200       10.2.5.143      1
   10.255.255.255  255.255.255.255       10.2.5.143       10.2.5.143     20
        127.0.0.0        255.0.0.0        127.0.0.1        127.0.0.1      1
        224.0.0.0        240.0.0.0       10.2.5.143       10.2.5.143     20
  255.255.255.255  255.255.255.255       10.2.5.143                2      1
  255.255.255.255  255.255.255.255       10.2.5.143       10.2.5.143      1
Default Gateway:        10.2.1.200

```And here goes my ubuntu machine route output:

```

Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
10.2.0.0        *               255.255.248.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.2.1.200      0.0.0.0         UG    0      0        0 eth0

```And the ifconfig command:

```

eth0      Link encap:Ethernet  Endereço de HW 00:16:36:69:eb:fa  
          inet end.: 10.2.4.2  Bcast:10.2.7.255  Masc:255.255.248.0
          endereço inet6: fe80::216:36ff:fe69:ebfa/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:25933 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:5901 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:8205075 (8.2 MB) TX bytes:1053571 (1.0 MB)
          IRQ:20 Endereço de E/S:0xe000 

eth1      Link encap:Ethernet  Endereço de HW 00:14:a5:b4:c1:49  
          endereço inet6: fe80::214:a5ff:feb4:c149/64 Escopo:Link
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:19 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:64 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:64 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:4920 (4.9 KB) TX bytes:4920 (4.9 KB)

```Hope this could help you help me ;) I'm on a little urgency here.

Ah, another thing, when I try to ping this 192 ip, it doesn't show anything... just when I stop the program (ctrl+c) it shows:

```

$ ping 192.168.34.53
PING 192.168.34.53 (192.168.34.53) 56(84) bytes of data.
^C
--- 192.168.34.53 ping statistics ---
20 packets transmitted, 0 received, 100% packet loss, time 19153ms


```Thanx

---

### Post by t0mppa on 2009-10-27
Ok, are all those subnetworks VPN's or are you simply trusted to use all of them by plugging in anywhere at work?

Basically you're only missing some routes here, all the data is really given to you. Re-editing the windows routing table makes it look like this, so it's easier to follow what's going on:```
Network		Netmask		Gateway		Interface	Metric
[COLOR="Red"]0.0.0.0		0.0.0.0		10.2.1.200	10.2.5.143	20[/COLOR]
[COLOR="Lime"]10.2.2.0	255.255.254.0	10.2.1.200	10.2.5.143	1
10.2.6.0	255.255.254.0	10.2.1.200	10.2.5.143	1[/COLOR]

[COLOR="Red"]10.2.0.0	255.255.248.0	10.2.5.143	10.2.5.143	20[/COLOR]
[COLOR="Blue"]10.255.255.255	255.255.255.255	10.2.5.143	10.2.5.143	20[/COLOR]
224.0.0.0	240.0.0.0	10.2.5.143	10.2.5.143	20
[COLOR="Blue"]255.255.255.255	255.255.255.255	10.2.5.143	10.2.5.143	1[/COLOR]

[COLOR="Yellow"]10.2.5.143	255.255.255.255	127.0.0.1	127.0.0.1	20[/COLOR]
[COLOR="Red"]127.0.0.0	255.0.0.0	127.0.0.1	127.0.0.1	1[/COLOR]

[COLOR="DarkOrchid"]255.255.255.255	255.255.255.255	10.2.5.143	2		1[/COLOR]
```

Then you have your Linux routing table:```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.2.0.0        *               255.255.248.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.2.1.200      0.0.0.0         UG    0      0        0 eth0
```

link-local means the localhost, which is 127.0.0.1 and default just means all the rest, which is represented by 0.0.0.0 in the numerical format. Then the Linux uses interfaces by their logical names, not their IP addresses. And lastly, the *'s when it comes to gateways mean that no external gateway is used, i.e., local networks.

So, you have 3 routes that match on both (the red ones) and then the rest need to be added to gain access to the same subnets. Because your Ubuntu system is trying to route everything else through 10.2.1.200 and that's not working, except for the green ones (which have different metric, i.e., priority, on Windows). The blue ones seem a little redundant, since they only nominate some broadcasting addresses, so you can try leaving them alone at first and of the violet one I have no idea, since it's using an odd interface, but otherwise exactly the same route as one of the blue ones.

You can add the routes through command line with **route add -net <destionation> netmask <netmask> dev <interface>** (no need to specify the gateway with these, since they're local networks) or then through whatever GUI you're using to get connected, by editing the connection details.

As for the 192.168.34.53, there's no route for it on your Windows machine either, so I have no idea what the details for the subnet where it is are.

EDIT: The IP of your Windows machine is 10.2.5.143, so note that that will differ in your Ubuntu configuration. Missed the yellow one at first, it's simply another way of stating the localhost and thus looks redundant as far as connecting to other computers goes, it really only saves traffic from the network when you're connecting to your own computer from your own computer (for instance running a server locally and testing web development with it) through your own IP, so if you do that a lot in your line of work, you can add it as well. Just make sure the IP it points to is your own IP.

---

### Post by reasilvabr on 2009-10-27
Thanks for you answer [t0mppa]("http://ubuntuforums.org/member.php?u=787201")!

But, unfortunatly it didn't solve the problem. I just copied the route PRINT output from another windows machine that seems to have some 192.168 addresses routed on it. Maybe with that you can tell me which routes to add.

```

Active Routes: 
Network Destination        Netmask          Gateway       Interface  Metric 
          0.0.0.0          0.0.0.0       10.2.1.200       10.2.5.118     20 
         10.2.0.0    255.255.248.0       10.2.5.118       10.2.5.118     20 
         10.2.2.0    255.255.254.0       10.2.1.200       10.2.5.118      1 
       10.2.5.118  255.255.255.255        127.0.0.1        127.0.0.1     20 
         10.2.6.0    255.255.254.0       10.2.1.200       10.2.5.118      1 
   10.255.255.255  255.255.255.255       10.2.5.118       10.2.5.118     20 
        127.0.0.0        255.0.0.0        127.0.0.1        127.0.0.1      1 
    192.168.127.0    255.255.255.0    192.168.127.1    192.168.127.1     20 
    192.168.127.1  255.255.255.255        127.0.0.1        127.0.0.1     20 
  192.168.127.255  255.255.255.255    192.168.127.1    192.168.127.1     20 
    192.168.236.0    255.255.255.0    192.168.236.1    192.168.236.1     20 
    192.168.236.1  255.255.255.255        127.0.0.1        127.0.0.1     20 
  192.168.236.255  255.255.255.255    192.168.236.1    192.168.236.1     20 
        224.0.0.0        240.0.0.0       10.2.5.118       10.2.5.118     20 
        224.0.0.0        240.0.0.0    192.168.127.1    192.168.127.1     20 
        224.0.0.0        240.0.0.0    192.168.236.1    192.168.236.1     20 
  255.255.255.255  255.255.255.255       10.2.5.118       10.2.5.118      1 
  255.255.255.255  255.255.255.255    192.168.127.1           200007      1 
  255.255.255.255  255.255.255.255    192.168.127.1            e0006      1 
  255.255.255.255  255.255.255.255    192.168.127.1    192.168.127.1      1 
  255.255.255.255  255.255.255.255    192.168.236.1    192.168.236.1      1 
Default Gateway:        10.2.1.200 
=========================================================================== 
Persistent Routes: 
  None

```

Anyway I really apreciate your explanation on the last post. Thanks a lot.

[ ]

---

### Post by t0mppa on 2009-10-27
By looking at the interface section, you can see that there are 3 different addresses (localhost doesn't count). What this means in practice is that the machine either has 3 interfaces, each of which are connected to different networks or then the other two are VPN's. If it's the former, you can set up [virtual interfaces]("http://handsonhowto.com/virt.html") as long as all the network are physically interconnected and if it's the latter, you'll be needing a bit more details.

If you're unsure of the network architecture, any chance you can ask for details/help from the network administrator?

---

