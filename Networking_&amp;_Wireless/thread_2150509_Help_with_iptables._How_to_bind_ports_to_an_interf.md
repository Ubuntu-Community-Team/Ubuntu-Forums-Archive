---
title: "Help with iptables. How to bind ports to an interface ?"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by SASDOE2 on 2013-06-01
Hi all!

I have a website available at a no-ip url, pointing to my real IP. I would like to be able to run deluge behing my VPN, and keep the apache server available at it's public ip. However whenever I start openvpn it seems to modify my routes and makes eth0 (the non-vpned interface, as opposed to tun0, virtual interface created by openvpn) useless.```
 ping -I eth0 google.com
``` shows this: 
```
[ maxime @ neo ~]
$ ping -c 3 -I eth0 google.com
PING google.com (173.194.34.4) from 10.200.2.13 eth0: 56(84) bytes of data.
^C
--- google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms
```

And here is ifconfig, what we see is that eth0 uses tun0's inet address, whatever that means.

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:85:2d:be  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe85:2dbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7158971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7583556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3051860180 (3.0 GB)  TX bytes:5464645559 (5.4 GB)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:504337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:504337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94060305 (94.0 MB)  TX bytes:94060305 (94.0 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.200.2.13  P-t-P:10.200.2.13  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13239 (13.2 KB)  TX bytes:15945 (15.9 KB)
```

So when I have openvpn running I can't connect at all to my no-ip address. 

After two months of using a raspberry pi as a deluge/openvpn box as a workaround to my problem, I realized how slow downloading was on the RPI (I was putting that on account that my VPN was slow, but was wrong, the machine just isn't capable of torrenting any faster that 500KB/s up or down), and thus decided to change my setup since I am not satisfied with the download speeds.

I has since then wisened up a bit regarding linux, and know I can tell my computer to send all ports but one to interface eth0 and all port xxx to interface tun0. 

Could somebody give me a hint as to how i could achieve that ?

Cheers!!

---

### Post by prodigy_ on 2013-06-01
> **SASDOE2 said:**
> However whenever I start openvpn it seems to modify my routes and makes eth0 (the non-vpned interface, as opposed to tun0, virtual interface created by openvpn) useless.
You can avoid that by commenting out the following line in OpenVPN config (on the server):
```
push "redirect-gateway"
```
The rest of your post doesn't make a lot of sense to me, sorry. You seem to have 2 (or more?) machines. One of them is RPi and for some reason (why?) you use a VPN tunnel to connect from RPi to some other machine. It seems you want to set up [NAT](http://www.revsys.com/writings/quicktips/nat.html) and [port forwarding](http://www.cyberciti.biz/faq/linux-port-redirection-with-iptables/) with iptables which is rather easy to do but it may or may not help depending on your overall network configuration and your *actual* demands.

---

### Post by SASDOE2 on 2013-06-01
Thanks for the prompt reply!

Ok i'll try to make it clearer. I have a main server running owncloud and other webservices that is accessible via no-ip, on my public IP. Because of my ISP I need to pass my torrenting via a VPN. To avoid setting up seemingly (at the time) too complicated iptables, I bought a RPi and had it do my torrenting behind a VPN and save the files on the main server (via sshfs on LAN, not through the VPN), because whenever I started openvpn on my main server I could no longer access the webservices with the no ip address. Now I would like to get rid of the RPi (or at least use it for something else), and setup port forwarding so as to have the webservices available by no-ip, and deluge behind a VPN, all on the same main server. 

> 
You can avoid that by commenting out the following line in OpenVPN config (on the server):
push "redirect-gateway"

Seems like a start but I still don't wan't the two mixing up.

---

### Post by SASDOE2 on 2013-06-01
After checking out your websites I still can't seem to figure out exactly what I want. I don't quite understand why I would want to setup NAT (also the NAT link speaks of eth0 and eth1, being external and internal interfaces, I only have one that does both, I think). The iptables speak of port forwarding (say 80 to 8309), when what I want is forwading a specific port (say 9880) to tun0 (openvpn's virtual interface) and all the others to eth0. I would have to do the push redirect-gateway as well I think.

---

### Post by prodigy_ on 2013-06-01
Do you use RPi only for torrenting? If yes, you need to connect to OVPN directly from RPi and setup port forwarding on your router. This way VPN won't affect any other device. If OVPN also overrides default gateway on the server, you can fix it with ```
ip route
``` command. Something like:
```

ip route del default
ip route add default via <physical interface IP>
ip route add <tunnel subnet/prefix> via <tunnel interface IP>

```
See **man ip** for more details ans examples.

---

### Post by SASDOE2 on 2013-06-01
That's exactly the setup I have now, with all the torrenting and VPN on the RPi, but not being a powerful device the speed is terrible, so I would like to have the torrenting and VPN on the main server, but without it interfering with no ip and the webservices.

---

### Post by prodigy_ on 2013-06-01
I see. You want to use the tunnel only for torrent traffic while having the default gateway on eth0 network. This is possible to achieve with iptables but may be harder than you think. Here's a good place to start:
[http://superuser.com/questions/354855/setup-routing-and-iptables-for-new-vpn-connection-to-redirect-only-ports-80](http://superuser.com/questions/354855/setup-routing-and-iptables-for-new-vpn-connection-to-redirect-only-ports-80)

There are much simpler solutions though. For example you could run a VM (possibly with something lightweight like LXC or OpenVZ) on your server.

P.S. You also should think about switching to another ISP because in a nutshell it's not a technical issue but a net neutrality issue. A good ISP treats all traffic equally.

---

### Post by SASDOE2 on 2013-06-01
Thanks for the idea, I'm kicking myself for not having though of this before! 

Would I realy see a noticeable difference load wise between a lightweight VM and Virtualbox ? I'm allready used to VB and know how to install it on a headless server. There's also more community support, which I have to admit, I sort of depend on!

Thanks for the help!

---

### Post by prodigy_ on 2013-06-01
Never benchmarked VMs so can't really say. Unless your machine is already resource-starved either way should be OK. But you'll probably need to allow direct disk access from the VM.

---

