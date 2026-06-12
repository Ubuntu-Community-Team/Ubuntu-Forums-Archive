---
title: "Disable VPN for some connections?"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by garfieldpbj on 2011-10-28
Hi

I connect via VPN via openconnect to my work, which works fine, however I do have the problem that my work have disabled access to external IMAP servers, e.g. imap.gmail.com, which I want to use in Thunderbird.

Can anyone come up with a solution, to have the VPN running, but use the normal network connection for Thunderbird?

/Peter

---

### Post by dwmw2 on 2011-10-31
NetworkManager allows you to configure the routing so that not all addresses go via the VPN. Click on the IPv4 tab in the configuration, and then 'advanced', I think.

---

### Post by mvs1207 on 2011-10-31
In the VPN settings on "IPv4 Setting" tab, click on "Routes", then check the "Use this connection only for resources on its Network".  

You may need to check your routing table after connecting to the VPN server to ensure that your default route is unchanged. 

```
$ route
```

---

### Post by garfieldpbj on 2011-11-01
> **VMUKKAMALA said:**
> In the VPN settings on "IPv4 Setting" tab, click on "Routes", then check the "Use this connection only for resources on its Network".  

I tried that, but it did not work at all.. 


> **VMUKKAMALA said:**
> 
You may need to check your routing table after connecting to the VPN server to ensure that your default route is unchanged. 

```
$ route
```
How do I manually edit the routing table so that only specific addresses uses the vpn? 

/Peter

---

### Post by mvs1207 on 2011-11-02
Did you try the other option "Ignore automatically obtained routes".  It is quite possible that your VPN server is changing your default route to go through the VPN tunnel.

Please refer to the man pages of route.
```
$ man route
```

for example
```
route add -net remote_vpn_ip netmask 255.255.255.255 dev ppp0
```

---

### Post by garfieldpbj on 2011-11-02
> **VMUKKAMALA said:**
> Did you try the other option "Ignore automatically obtained routes".  It is quite possible that your VPN server is changing your default route to go through the VPN tunnel.

Please refer to the man pages of route.
```
$ man route
```

for example
```
route add -net remote_vpn_ip netmask 255.255.255.255 dev ppp0
```

No I did not check the manual (I did not think about it :-( )

But I will look into it, and also the specific command you suggested..

I will let you all know the result, as soon as I have tested it..

/Peter

---

