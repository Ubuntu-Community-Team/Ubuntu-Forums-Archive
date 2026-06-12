---
title: "VPN and Internet Connection cannot Co-exist"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by rdp870 on 2012-11-15
Hi,

I have a PPTP VPN setup at my office. I'm trying to connect to it from my house on Ubuntu 12.10 x64. I can successfully connect, however when I do, I can only access remote resources (devices on the VPN). I can't access the internet.

After some searching, I thought  that if I checkded  "Use this connection only for resources on its network"  I would be set...that's not the case. When I checked this box, I was able to access the internet, but no remote resources.

I know the VPN server is set correctly because I can successfully connect in this manner using a Windows computer. I've attached outputs of the route command in the various scenarios.

Any help would be greatly appreciated.

---

### Post by rdp870 on 2012-11-17
I fixed it:

I had to check "Ignore automatically obtained routes" and "Use this connection only for resources on its network" in the VPN routes configuration and I had to manually add the route for the remote network:

sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 74.7.X.X

Where 192.168.1.0 is the remote network and 74.7.X.X is the public IP of the remote network. After that it worked like a charm.

---

### Post by tguitar.su on 2013-01-11
> **rdp870 said:**
> I fixed it:

I had to check "Ignore automatically obtained routes" and "Use this connection only for resources on its network" in the VPN routes configuration and I had to manually add the route for the remote network:

sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 74.7.X.X

Where 192.168.1.0 is the remote network and 74.7.X.X is the public IP of the remote network. After that it worked like a charm.

This works, thanks

---

