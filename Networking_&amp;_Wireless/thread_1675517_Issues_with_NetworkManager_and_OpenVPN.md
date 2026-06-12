---
title: "Issues with NetworkManager and OpenVPN"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by aggiemarine07 on 2011-01-25
Good Morning all,

I am having some issues getting OpenVPN to work on my ubuntu 10.10 system. 

I installed the network-manager-openvpn and network-manager-openvpn-gnome packages. I can set it up using the .ovpn file and I can enter my username and password correctly. It will even successfully connect to the VPN but the problem is every time I try to go somewhere on the internet (even google.com) it times out.

I have read the community documentation and tried suggestions from other forums that I have read about but to no avail.

If you need me to post any outputs then just let me know and I will gladly post them. I am at wits end trying to figure this out and now I am asking the community if they have any suggestions. Thanks in advance!

---

### Post by dmizer on 2011-01-26
Can you post speedtest results from the VPN server side of things?

I have the same problem, but I believe it's simply a physical limitation of my network connection. Here's my VPN server's speedtest results:

[[IMG]http://www.speedtest.net/result/1128633492.png[/IMG]](http://www.speedtest.net)
The bigger the "Upload" number, the better your VPN connection will be when you connect remotely.

---

### Post by ripat on 2011-01-27
That's because gnome network manager changes the default gateway. If you do a
```
$ ip route ls
```
I bet that the default gateway is routed through the tun0 interface.

To change this, gnome-networkmanager -> VPN connections -> Configure VPN -> Edit -> IPV4 parameters -> Routes and tick the second option, something like "Use this connection only for...."

---

### Post by aggiemarine07 on 2011-01-27
@ripat - Right, I believe that is what I want it to do. I am stationed here in Japan and I am using a VPN service so that I can still watch netflix and hulu.

Using the setup works flawlessly on Win Xp, why not for ubuntu?

I think the issue might be that I cant tick the box making it use a certain port.


@dmizer - Also I cant post SpeedTest results because I cant go anywhere on the internet, not even google.com (it times out).

Any other suggestions.

---

### Post by dmizer on 2011-01-27
ripat has it. I just did this tonight while I was out and it worked much better than previously.

(left) click on the NMapplet in the taskbar -> go to "VPN connections" and "Configure VPN" -> select your VPN connection and click "edit" -> select the "IPv4 settings" tab -> click on the "routes" button -> put a checkmark in "Use this connection only for resources on its network".

---

### Post by aggiemarine07 on 2011-01-27
@dmizer - Yes I know it works but it does not make my IP address any different. Whenever I browse the web I still have a Japan IP address and not the address in the states. Do you know what else it could be?

Im going to test this out on 10.04 and see if it works there. 

I appreciate the help and responses; thanks.

---

### Post by aggiemarine07 on 2011-01-30
I can confirm that OpenVpn with Network Manager works completely in Ubuntu 10.04.

I followed the same process of configuring the VPN in 10.04 as in 10.10 and it works flawlessly.

The problem seems to be somewhere in 10.10 any ideas where I could change this? Thanks.

---

### Post by taojian on 2011-03-27
I'm having the same issue, in 10.10. The custom port option will not stick, I've turned on LZO data compression (seemed to solve other people's problems), but no dice.

Same as aggiemarine: If I check "Use this connection only for resources on its network" my connections don't go through the VPN. If I uncheck it, they timeout.

If this isn't solveable, does anyone have recommendations for using the openvpn command line, and maybe scripts to manually re-route?

Thanks!

---

### Post by aggiemarine07 on 2011-04-09
well lets hope they fixed it in 11.04 because it doesnt look like 10.10 is going get it fixed. :-/

---

### Post by taojian on 2011-04-11
Actually we got this working -- in our case it didn't have to do with NetworkManager at all. We hadn't set up IP forwarding and IP tables correctly on the server, and once that was done all worked as it should. I won't pretend to really know what that means, but from [this link]("http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu"), the key commands were:

```
echo 1 > /proc/sys/net/ipv4/ip_forward

sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

Give that a shot -- who knows, maybe you're having the same issue. At any rate, in NetworkManager I think it will uncheck the custom port box for you if you're using the default port (1194), so I don't think that was an issue. And of course all traffic should be routed through the proxy.

---

