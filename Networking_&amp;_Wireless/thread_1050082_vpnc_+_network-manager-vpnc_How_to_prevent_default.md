---
title: "vpnc + network-manager-vpnc: How to prevent default route being the VPN tunnel?"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by ByteJuggler on 2009-01-25
OK, so I've set up my VPN how I like it, however vpnc + network-manager-vpnc by default sets my default route to being the VPN tunnel rather than my normal internet connection.  As a result, I'm having to enter 

```
sudo route add default gw <internet gateway IP>
```

after the connection is established, to fix normal internet connection while still keeping the VPN functional. 

Does anyone know the proper way to have network-manager-vpnc NOT do this?  I've looked in the network manager dialogs to no avail.

---

### Post by ByteJuggler on 2009-01-26
No one done this then?  :(

---

### Post by joebeasley on 2009-01-26
Edit the connection, IPv4 Settings, routes.  Click ignore automatically obtained routes.  You will have to add the routes for networks you want to use the vpn for. 

This assumes your VPN (IT Department) allows split tunneling.

---

### Post by ByteJuggler on 2009-01-27
> **joebeasley said:**
> Edit the connection, IPv4 Settings, routes.  Click ignore automatically obtained routes.  You will have to add the routes for networks you want to use the vpn for. 

This assumes your VPN (IT Department) allows split tunneling.

OK thanks, I was hoping there's a more elegant way of doing this, but thanks anyway.  (It would seem to me to be a common enough use-case to warrant a feature in the GUI somewhere.)

---

### Post by cmoman on 2009-05-20
kvpnc  seems to allow a configuration for vpnc to allow to "Keep the default route"

I found this thread while trying to find a solution to this problem myself.

This was the output of route -n  after setting up the vpn tunnel where the 192.... address are my network and the 10... addressess are at the other end of the tunnel.  The real world address has been changed for obscurity.

I think this works.  Let me know if it doesn't.

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.20       0.0.0.0         255.255.255.255 UH    0      0        0 tun0
273.117.203.203 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.12       0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by alienbrain on 2009-11-17
Click on the Network Manager icon and choose "VPN Connections" -> "Configure
VPN...". Then choose the connection name and click "Edit". Go to "IPv4
Settings" tab and click the "Routes" button at the lower-right corner.
Check off "Use this connection only for resources on its network".

References: [https://bugzilla.redhat.com/show_bug.cgi?id=492208](https://bugzilla.redhat.com/show_bug.cgi?id=492208)

---

### Post by jetblackstar on 2009-12-03
Yeah, saw that redhat bug thread. But Strangely the same checkbox is not available in the window. Presume it's a version difference between NetworkManager for Redhat and Ubuntu. 

For Ubuntu you just have to ignore the default routes and set it manually. 
Pita for something so simple.

---

### Post by leif81 on 2010-02-19
> **alienbrain said:**
> Click on the Network Manager icon and choose "VPN Connections" -> "Configure
VPN...". Then choose the connection name and click "Edit". Go to "IPv4
Settings" tab and click the "Routes" button at the lower-right corner.
Check off "Use this connection only for resources on its network".

References: [https://bugzilla.redhat.com/show_bug.cgi?id=492208](https://bugzilla.redhat.com/show_bug.cgi?id=492208)

Sweet, this is the answer I was looking for.

---

### Post by kb2001 on 2010-02-26
> Click on the Network Manager icon and choose "VPN Connections" -> "Configure
VPN...". Then choose the connection name and click "Edit". Go to "IPv4
Settings" tab and click the "Routes" button at the lower-right corner.
Check off "Use this connection only for resources on its network".

Thank you alienbrain, this did the trick for me as well.

---

### Post by phonixor on 2010-03-01
wtf does "check-off" mean?
does that mean check the box?
or does it mean uncheck the box?
both dont work for me btw :(

i can either get my Internet to work or connect to the VPN network...

btw what do you use as gateways?

say i want to connect to: 10.111.111.111 and 10.112.112.112 and vpn has 188.111.111.111
what should my settings be???

routes: (ip/netmask/gateway/Metric)
10.whatevernr.whatevernr.whatevernr/255.0.0.0/blank/blank  - to get every ip that starts with a 10...
188.whatevernr.whatevernr.whatevernr/255.0.0.0/blank/blank - to get every ip that starts with a 188... (dont know if this one helps or screws.. but i tried pretty much every combination :P :()
Ignore automaticly obtained routes: unchecked
Use this connection only for resources on its network: checked  (if i have this checked everything goes trough vpn, if i have this unchecked i can browse normally...)

though i can never just tunnel everything that starts with 10 and 193 and normal browse the rest... :(

i really hate this new VPNC manager... it was much more clear... and more importantly it worked before... :(

---

### Post by Purple8 on 2010-03-19
Windows has a nice simple  'use default gateway on remote network' Tick box
in the ipv4 advanced, That you simply untick. This works nicely for connections into my office. but no nice simply way in ubuntu grrr

---

### Post by Michl on 2010-05-04
> **alienbrain said:**
> Click on the Network Manager icon and choose "VPN Connections" -> "Configure
VPN...". Then choose the connection name and click "Edit". Go to "IPv4
Settings" tab and click the "Routes" button at the lower-right corner.
Check off "Use this connection only for resources on its network".

References: [https://bugzilla.redhat.com/show_bug.cgi?id=492208](https://bugzilla.redhat.com/show_bug.cgi?id=492208)

This is not available in the network manager 0.6.6.  There
is no tab for IPv4 settings.

---

### Post by eudoxos on 2010-12-13
The solution in #6 is nice, but I need to connect to VPN that's serving both local network (10.16.16.0/...) but also a block of public IPs.

When I connect to the VPN, it will only route private addresses (the 10.16.16.0/... block) through the VPN gateway. The VPN gateway itself is in the public block, but no other machines from the public block can be accessed directly, only routed through the VPN.

Now I have in route (changing the public ips):

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
123.1.94.19     10.0.0.138      255.255.255.255 UGH   0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.16.16.0      0.0.0.0         255.255.240.0   U     0      0        0 tun0
129.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0

```

where 10.0.0.138 is my local gateway (adsl modem), 123.1.94.19 is the VPN gateway I am connected to, 10.16.16.0/255.255.240.0 is the private block in the VPN.

Obviously accessing e.g. 123.1.2.3 will not pass through the VPN (but the address cannot be accessed directly). What should I add to extra routes in the VPN setup to have e.g. 123.1.0.0/255.255.0.0 routed through the VPN as well?

Thanks!

---

