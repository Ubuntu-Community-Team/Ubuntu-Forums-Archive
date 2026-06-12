---
title: "VPN connection between two LANs"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2010-02-18
Hi everyone!

Have you ever created a VPN connection between two LANs which are geographically far away? For example LAN1 is 192.168.1.0 and LAN2 is 10.0.0.0. If I am in LAN1 I would like to be able to ping 10.0.0.1 and get packets back.

I am trying to do it with OpenVPN. I can connect two computers from both LANs using their virtual IP but I can't do that with their private IP. I think the solution must be in creating a bridge or using the "push" command of OpenVPN, unfortunately I haven't found clear information within the internet. Can you help me please?

Thanks in advance

---

### Post by gombadi on 2010-02-18
> 
For example LAN1 is 192.168.1.0 and LAN2 is 10.0.0.0. If I am in LAN1 I would like to be able to ping 10.0.0.1 and get packets back.


You need to set up routing between the two LAN's so that machines on LAN1 know that to get to LAN2(10.0.0.0 network) they need to send packets to the VPN gateway machine.

If your gateway and VPN machine are on the same box then it is settings in OpenVPN to get it to tell the kernel to send packets for the 10.0.0.0 network via your tunnel.

If your gateway and VPN server are different machines then you need to set a static route on your gateway to tell it to send packets for the 10.0.0.0 network via the ip address of your VPN server. something like -
```

route add -net 10.10.37.0 netmask 255.255.255.0 gw 192.168.0.22

```

This tells the kernel that for packets going to the 10.10.37.0/24 network it needs to send the packet to 192.168.0.22 which is our OpenVPN gateway.

You will also have to setup routes on LAN2 so the machines there send packets for your 192.168.1.0 network via the OpenVPN gateway at that end.

---

### Post by DGortze380 on 2010-02-18
> **mosquetero said:**
> Hi everyone!

Have you ever created a VPN connection between two LANs which are geographically far away? For example LAN1 is 192.168.1.0 and LAN2 is 10.0.0.0. If I am in LAN1 I would like to be able to ping 10.0.0.1 and get packets back.

I am trying to do it with OpenVPN. I can connect two computers from both LANs using their virtual IP but I can't do that with their private IP. I think the solution must be in creating a bridge or using the "push" command of OpenVPN, unfortunately I haven't found clear information within the internet. Can you help me please?

Thanks in advance

What you want is a Point-to-Point Bridged VPN.

[http://openvpn.net/index.php/open-source/documentation/howto.html#quick](http://openvpn.net/index.php/open-source/documentation/howto.html#quick)

It can be accomplished with a Routed VPN, I've done it, a number of times. But it involves a lot more configuration.

---

