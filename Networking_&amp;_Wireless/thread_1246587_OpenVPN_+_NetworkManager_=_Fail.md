---
title: "OpenVPN + NetworkManager = Fail?"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-08-21
Hi,

I've set up a OpenVPN server.  I created the client files by hand and then I imported them into NetworkManager.  I cannot even begin to think or describe what it is doing when it connects or attempting to connect.   Has anyone had any success with making that work.

I have tested that OpenVPN works with a windows client installed in vmware on my computer.

I have tested that OpenVPN works when I start it as a client from the command line.

However when I try to connect with NetworkManager it somehow .. well I don't know exactly what it does, all I know is that it is not working as expected or as the two above examples.

Are there any gui's for linux that actually works, like the one for windows?

Thanks.

---

### Post by s3MA00RRNY on 2009-08-22
NetworkManager does work. I'm using it to connect to a Cisco VPN (vpnc). Try uninstalling resolvconf and removing /etc/resolv.conf. That should fix it.

---

### Post by sefs on 2009-08-22
> **pcdude2143 said:**
> NetworkManager does work. I'm using it to connect to a Cisco VPN (vpnc). Try uninstalling resolvconf and removing /etc/resolv.conf. That should fix it.

OpenVPN.  That's what I am having the problem with, not Cisco VPN which I believe is an IPSec based vpn and will most likely work fine with NetworkManager.

OpenVPN and NetworkManager is a different kettle of fish to that.

---

### Post by Xanthomryr on 2009-08-22
I am using the network-manager with OpenVPN to connect to the office where I work, no problem.

Buuut, the network-manager is a bit bitchy.

You  don't get any errormessage?
How do you know then that it is not working.
If there is any problem, the network-manager will tell it to you, I know this because mine is telling me what is wrong in a bubble/popup under the icon. 

You have openvpn installed on the machine from which you want connect to the OpenVPN-server?

You have openvpn started (/etc/init.d/openvpn start)?

---

### Post by sefs on 2009-08-22
> **Xanthomryr said:**
> I am using the network-manager with OpenVPN to connect to the office where I work, no problem.

Buuut, the network-manager is a bit bitchy.

You  don't get any errormessage?
How do you know then that it is not working.
If there is any problem, the network-manager will tell it to you, I know this because mine is telling me what is wrong in a bubble/popup under the icon. 

You have openvpn installed on the machine from which you want connect to the OpenVPN-server?

You have openvpn started (/etc/init.d/openvpn start)?


It connects but no information is flowing or is not flowing properly.

When i do a "route" test I can see that the route table looks screwed up and way different to if start openvpn from the command line

I am thinking it does not work very well (does not fully support openvpn) with imported conf files and bugs out on them.

---

### Post by Xanthomryr on 2009-08-23
I would say you are conneccted if you do not get any feedback from the networkmanager.
By the way, when you are connected there is a littel lock showing in the networkmanager icon.

It works perfect for me with an imported openvpn config file.
All I had to do was to activate the IP4 > Advanced > Routes "Use this connection only for resources on its network" option, because when I was connected via VPN all traffic was send into the VPN Tunnel and so i could not surf in the internet anymore.
After I activated that option I could surf the internet over my router and reached all machines at work through the openvpn tunnel.

The only problem is that I need sometimes to start openvpn by hand as the network-manager doesen't start it automaticly.

---

### Post by sefs on 2009-08-23
> **Xanthomryr said:**
> I would say you are conneccted if you do not get any feedback from the networkmanager.
By the way, when you are connected there is a littel lock showing in the networkmanager icon.

It works perfect for me with an imported openvpn config file.
All I had to do was to activate the IP4 > Advanced > Routes "Use this connection only for resources on its network" option, because when I was connected via VPN all traffic was send into the VPN Tunnel and so i could not surf in the internet anymore.
After I activated that option I could surf the internet over my router and reached all machines at work through the openvpn tunnel.

The only problem is that I need sometimes to start openvpn by hand as the network-manager doesen't start it automaticly.


That's exactly it.  I have two client profiles
One that ships all traffic thru the vpn and one that does not.

Both profiles work beatutifully in windows, and or if i start them from the command line in ubuntu via "sudo openvpn --client --config client1.conf"

Not so with the NM.  NM says its connected and I see the lock.  But like I said, it screws up the routing table with either profile.

Routes with NetworkManager started OpenVPN
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
72.51.93.165    192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
172.16.16.0     *               255.255.255.0   U     0      0        0 vmnet1
192.168.127.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.254.0   *               255.255.255.0   U     0      0        0 tap0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         *               0.0.0.0         U     0      0        0 tap0

```


Routes with Command line started OpenVPN
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
172.16.16.0     *               255.255.255.0   U     0      0        0 vmnet1
192.168.127.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.254.0   *               255.255.255.0   U     0      0        0 tap0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```




NM for some reason decides to add some extra routing that I have no idea about
```

72.51.93.165    192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0

```
What is this really saying?


```

link-local      *               255.255.0.0     U     1000   0        0 wlan0

```
What is this really saying?



```

default         *               0.0.0.0         U     0      0        0 tap0

```
What is this really saying?

---

