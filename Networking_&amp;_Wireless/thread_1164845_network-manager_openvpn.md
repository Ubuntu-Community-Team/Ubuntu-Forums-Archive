---
title: "network-manager openvpn"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by weboholic on 2009-05-20
The network-manager plasmoid behaves rather buggy. 
openvpn is installed. So I'm able to configure a new openvpn connection via the GUI of the plasmoid. But here is what bothers me:
1) See [screenshot]("http://picasaweb.google.de/lh/photo/8nVRz-plvcEbPFU01t-S0w?feat=directlink")
2) Now change the connection type to anything else
3) Change it back to X.509 certificates, see [screenshot]("http://picasaweb.google.de/lh/photo/pC5w80DaDH8o7womouORBg?feat=directlink")

Despite those obstacles I'm able to enter my data, see [screenshot]("http://picasaweb.google.de/lh/photo/T-M0xBmHYpPB08-EPT0vfA?feat=directlink")

However click on the entry in the connection window of plasmoid, does nothing. I can see it tries something, because it freezes for a second, but nothing happens

Trying to edit the connection, upon opening the edit window:
1) Everything is gone, see [screenshot]("http://picasaweb.google.de/lh/photo/Va9qac_wpuA61iFomqPnhw?feat=directlink")
2) Now change the connection type to anything else
3) Change it back to X.509 certificates, see [screenshot]("http://picasaweb.google.de/lh/photo/T9PkkEv83CUBRHErLmBgJQ?feat=directlink")


I've tried using kvpnc and gadmin-openvpn-client but neither of them manages to connect. The only client that was able to successfully connect (creating the TUN device) was the console :) but none of the internal servers was reachable.

I'm pretty sure it has nothing to do with hardware and/or ISP because before Kubuntu Jaunty I was running Ubuntu Intrepid and openvpn was running fine.

Can anybody help me getting opnevpn running?

---

### Post by Peter09 on 2009-05-20
Once connected you need to do a route command to see if the remote lan is being exported. You should see the IP addresses of the remote servers.

---

### Post by weboholic on 2009-05-20
Can you be please more precise? 

On Intrepid no such thing was necessary

---

### Post by Peter09 on 2009-05-20
At the remote end you need to establish a route from the VPN tunnel to the remote LAN and at the local end you need to establish a route from the local lan to the VPN tunnel. Only then can you see the servers at the remote end. 

Remember that the VPN tunnel has a different IP schema to the Local LAN and the remote LAN, say

192.168.***.*** -> 10.0.0.***->10.2.2.***

Any application will need to understand where to go to get to a device who's ip address is 10.2.2.???

---

### Post by weboholic on 2009-05-20
Very strange. I can see that openvpn adds the routes when starting it from the console but it's not working. Probably because both LANs (local and remote) are on 192.168.1.* (at least part of the remote LAN).

Update: Just let a ping pending for several minutes -> after 2 minutes probably I'm able to ping remote IPs, but remote DNS isn't working, probably timeout. Odd. Firefox also timeouts. Must phone the admin. But the issue with the connection manager plasmoid remains. Will report it as a bug. Thank you Peter09.

---

