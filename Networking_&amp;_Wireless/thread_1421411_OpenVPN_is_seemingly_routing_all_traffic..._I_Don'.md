---
title: "OpenVPN is seemingly routing all traffic... I Don't want it to"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Taijitu on 2010-03-04
Hello everyone.

I wish I knew of a better place to post this issue, as it might not be related to Ubuntu, but here goes anyway:

I am using dd-wrt on my Linksys WRT54G router, and have set it up to be an OpenVPN server. This works perfectly for the purpose of connecting to my home network from outside, but it appears that my computer (Ubuntu 10.04) is routing all of its traffic through the vpn connection, including web browsing etc.

This is not what I want, since the VPN is only for connecting securely to my newly homemade NAS, not for using my home router as an encrypting proxy.

This is the content of the openvpn config file:
```
push "route 192.168.2.0 255.255.255.0" 
server 10.67.89.0 255.255.255.0 

dev tun0 
proto tcp 
keepalive 10 120 
dh /tmp/openvpn/dh.pem 
ca /tmp/openvpn/ca.crt 
cert /tmp/openvpn/cert.pem 
key /tmp/openvpn/key.pem
```

It does not contain the line that specifies to route all traffic (push "redirect-gateway"), so I'm thinking that it might be my computer doing it on its own and not the server pushing it to do it.

I've done a traceroute from an outside IP (mobile broadband) when connected to the vpn, and the first hop is to the openvpn server followed by the excact same hops as if I did the traceroute from within my home network.

This is the output of "route -n" when connected to the vpn using my mobile broadband (HTC Hero network share via usb, hence "usb0"). Hope this says at least something about my problem... The IPs on 10.67.89.0 is the openvpn subnet adresses.
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.67.89.1      10.67.89.5      255.255.255.255 UGH   0      0        0 tun0
10.67.89.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
My.home.ip      192.168.100.254 255.255.255.255 UGH   0      0        0 usb0
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 usb0
192.168.2.0     10.67.89.5      255.255.255.0   UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
0.0.0.0         10.67.89.5      0.0.0.0         UG    0      0        0 tun0

```

If anyone can help me on this, I'd be extremely glad :-). Also if you have an idea for a more appropriate forum for asking.
Thank you
Christoffer

---

### Post by coutts99 on 2010-03-04
```
0.0.0.0         10.67.89.5      0.0.0.0         UG    0      0        0 tun0
```

Surely that is pushing everything through your VPN?

---

### Post by Taijitu on 2010-03-04
> **coutts99 said:**
> ```
0.0.0.0         10.67.89.5      0.0.0.0         UG    0      0        0 tun0
```

Surely that is pushing everything through your VPN?
Thank you for your answer.

I wouldn't know, but that seems to make sense, yes. I'm not an expert in reading routing tables yet, since this is the most advanced linux networking stuff I've tried yet. Do you have any idea how I could go about changing it?

---

### Post by coutts99 on 2010-03-04
> **Taijitu said:**
> Thank you for your answer.

I wouldn't know, but that seems to make sense, yes. I'm not an expert in reading routing tables yet, since this is the most advanced linux networking stuff I've tried yet. Do you have any idea how I could go about changing it?


That line (0.0.0.0) is you default route.

What is your routing table before you connect the VPN?

Something is setting that route, double check your OpenVPN config.

---

### Post by Taijitu on 2010-03-04
Without the vpn, but still on the mobile broadband, it is like this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 usb0
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 usb0

```
I suppose the phone is playing the role of router with adress 192.168.100.254 here.

But the openvpn config on my computer is done via the networkmanagaer applet in gnome, and the only config file I've found in ~/.gconf provides no more info than the config window of the applet and says nothing regarding routes...

Thanks a lot for your help and patience, btw :-)

---

### Post by coutts99 on 2010-03-04
> **Taijitu said:**
> Without the vpn, but still on the mobile broadband, it is like this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 usb0
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 usb0

```
I suppose the phone is playing the role of router with adress 192.168.100.254 here.

**But the openvpn config on my computer is done via the networkmanagaer applet in gnome**, and the only config file I've found in ~/.gconf provides no more info than the config window of the applet and says nothing regarding routes...

Thanks a lot for your help and patience, btw :-)

I suspect this is setting the default route, I've always just done a text config file myself. What options are in the networkmanager applet for the VPN?

---

### Post by coutts99 on 2010-03-04
Try this link -:

[http://www.debuntu.org/how-to-network-manager-openvpn-overwrites-default-route](http://www.debuntu.org/how-to-network-manager-openvpn-overwrites-default-route)

---

### Post by Taijitu on 2010-03-04
Wow, that was simpler than i thought!
Thank you very very much :D.

---

