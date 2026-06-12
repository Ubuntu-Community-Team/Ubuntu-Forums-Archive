---
title: "Network Bridging Ubuntu to Windows"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by sinclair86 on 2009-02-28
I've followed the jam here:[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) to set up the bridge but when I go to the windows machine it says "network cable unplugged". 

Did a lot of searching and saw that the cards had to be in promisc mode so that my bridge (br0) would handle the packets so I did that sudo ifconfig eth0 0.0.0.0 -promisc. No luck also tried forwarding echo "0" /etc/...... 

Is there something I'm missing or a combination of me doing things that cancel each other out. I put everything back to normal so I could start fresh.

On a second note which is better? ICS or Bridging?

---

### Post by puppywhacker on 2009-03-01
windows has the nasty habbit of using specific error messages for all kinds of different events. So "network cable unplugged" has nothing to do with the actual cable.

From the linux side "mii-tool eth0" can show you the ethernet state of the link. The link should be up and the speed negotiated (or at least set). This means that the orange network light should be steady and the green one should be blinking and the network statistics for Tx sent and Rx received should not be zero and preferably increasing.

For your bridge on your linux you should have a br0 interface that bridges the ethernet. Post your "ifconfig br0" and check if the arp table is building (on both the windows and linux). The arp table is a list of mappings between mac-address and ip-address that the machine has learned. "arp -a"

I think that using an ICS (a microsoft term for NAT, the linux term is masquerading) is a better option if you don't need ethernet broadcast connectivity (virtually never for casual usage). You can set up the linux machine to be the NAT like this

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sysctl -w net.ipv4.conf.all.forwarding=1
iptables-save
```

---

### Post by sinclair86 on 2009-03-01
Yea after I posted that last night I decided to go different approaches I tried NAT'ing with dhcp and dns 

[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

[http://www.debuntu.org/iptables-how-to-share-your-internet-connection-p2](http://www.debuntu.org/iptables-how-to-share-your-internet-connection-p2)

but the problem is every time I do anything the lights on the back of the card do no light up (eth1). I thought that it might just be the card is bad or something but i took the internet connection from eth0 and pugged it into eth1 and it worked. Even following your code did nothing

also what is "ethernet broadcast connectivity"

---

### Post by sinclair86 on 2009-03-01
Ok So I got it working. Now I kinda ran into another problem. Long story short I have an ethernet cord coming off a switch to eth0. eth1 is nat'ed and then I plugged it back into the same switch. Now I have 2 different network broadcast 10.10.0.1 (eth1) and 192.168.1.1 (my real router). Is there any way to pick one up over another without having to go into the rest of my network to change settings? Because now when i renew/release on my windows machines downstairs their default network is 10.10.0.1 instead of 192.168.1.1


Also since acts like a router? how do i forward ports?

---

### Post by puppywhacker on 2009-03-02
so first the quick summary
1. you only need an ip-route between your windows machine and the router
2. this can be achieved by changing the "option routers" in the dhcp server in linux.
3. you have now 2 ethernet networks which map to 2 ip networks (good choice :) ) instead of bridging where you would have 2 eth segments and 1 ip network. 

release/renew in windows triggers a DHCP request. DHCP uses ethernet broadcasts (for instance, wake-on-lan also uses ethernet broadcasts) in contrast to ip-broadcasts for higher level applications like streaming video.

Anyway, as I understand your network setup is like this

```
WINDOWS               LINUX                 ROUTER
10.10.0.X ---- 10.10.0.1 192.168.1.X ---- 192.168.1.1
```

that means that you have two NAT's in your network, which is OK. But not necessary. what you could do is configure the Linux dhcp server to give out ip addresses in the 10.10.0.X range (like it already does) and on the dhcp server set the default gateway to 192.168.1.1. Your linux machine than only has to route the packets between the 10.10.0.X network and the  192.168.1.X network.

The DHCP server config file is located here
/etc/dhcp3/dhcpd.conf
the configuration you need to change is "option routers 192.168.0.1"

You can restart the dhcp server with
/etc/init.d/dhcpd restart

Since you don't need to NAT you only need to allow routing via the linux box.
```
sysctl -w net.ipv4.conf.all.forwarding=1
```
to undo the NAT you can flush the tables
```
iptables -F
```

and make sure that all routes are setup. use the command "route" on linux and "route PRINT" on windows. You should have the following routes to make this work 

Windows:
10.10.0.0/24   -> 10.10.0.1
default        -> 10.10.0.1

Linux
192.168.0.0/24 -> 192.168.0.1
10.10.0.0/24   -> 10.10.0.1
default        -> 192.168.0.1

---

### Post by sinclair86 on 2009-03-02
Thanks a lot for all your help puppywhacker.

One last thing tho I am a little confused on and I have trying to look for it is port forwarding with the nat. It has to be done prerouting and that it? or do I have open the port as well? What I am trying to do now is forward port 80 and 110. I already opened them on the router and pointed it to 192.168.1.12 (eth0) how do i route it from there to 10.10.0.1 (eth0) -> windows (10.10.0.x) also is it going to be the same for allowing and ip or range except its going to be under FORWARD chain now instead of input?

all i have in my iptables is iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

---

### Post by puppywhacker on 2009-03-03
For the port forwarding you need a Destination NAT (next to the source nat you already set up). The -i is the incoming interface. in the other rule it's -o for outgoing.

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 10.10.0.12:80

---

### Post by sinclair86 on 2009-03-03
Ok thanks you've help me out a lot so far this is just the last few things I need to clear up.

The PREROUTING and POSTROUTING is confusing me. Is it just basically INPUT and FORWARD but for nat? ALSO

sudo iptables -t nat -A PREROUTING -s 192.168.22.130/24 -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p udp --dport 80 -j DNAT --to-destination 10.10.0.118:80
sudo iptables -t nat -A PREROUTING -j DROP

I looked in my logs and it drops connection 10.10.0.118 (the nat'ed computer) so I went up and added sudo iptables -t nat -A PREROUTING -s 10.10.0.18 -j ACCEPT but of course it doesnt port forward to 80 cause once a packeted is determined no other rules affect it. So I tried putting -s in the prerouting to dnat and it just dropped the packet again. My question here, as it seems, would I be better off just blocking it on the eth0 face. Actually now that I think about it blocking it there would be a horrible/ugly way to do it. Lol but either way I'm confused. I know a decent amount about iptables (not the nat'ing). So if you dont mind, could you please explain it or point me in the right direction?

---

