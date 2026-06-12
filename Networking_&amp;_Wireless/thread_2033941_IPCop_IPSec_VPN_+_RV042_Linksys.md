---
title: "IPCop IPSec VPN + RV042 Linksys"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by balagosa on 2012-07-27
So I did a little search here on the forums and haven't found anything solid solution to my problem yet. 

**Here goes, the situation. I want a Gateway-to-Gateway (or as IPCop calls Site-to-Site) VPN installation.**

RV042 Linksys Gateway
WAN IP: 112.202.70.X (THIS IS IN A DYNAMIC IP)
Local IP: 172.16.0.0/24
Gateway IP: 172.16.0.1
Additional Info: THE FIREWALL OF THE NETWORK (DIRECT INTERFACE TO INERNET)

IPCop v1.4.21
WAN IP: 222.127.117.X (THIS IS A STATIC IP)
Local IP: 192.168.100.0/24
Gateway IP: 192.168.100.254
Additional Info: Same as Above. The FIREWALL of entire NETWORK


**TIMELINE **
First, I tried OpenVPN ROADWARRIOR (Host-to-Net) following this guide [OpenVPN Guide]("http://www.mikestechblog.com/joomla/networking-section/ipcop/67-vpn-with-an-ipcop-firewall-in-windows-xp.html?start=1"). It worked but the problem is I can't ping from RV042 --> IPCop network **BUT** ping works in IPCop --> RV042. So I tried to re-read the instructions and found I missed a step from the guide. You can see below that the IP is "192.168.101.0/24". This is the OpenVPN IP I use for the RV042. But I wont explain that since the problem is not that one. eth0 by the way is my LAN Interface for my IPCop network.

**/etc/rc.d/rc.firewall.local file**
```
#!/bin/sh
# Used for private firewall rules

# See how we were called.
case "$1" in
  start)
        ## add your 'start' rules here
    #Added for zerina start - BEGIN
    /usr/local/bin/openvpnctrl --create-chains-and-rules
    #Added for zerina start - END
    #
    # Line below is added to allow Windows PC's access thru the VPN
    [COLOR="Red"]iptables -t nat -A CUSTOMPOSTROUTING -s 192.168.101.0/24 -o eth0 -j MASQUERADE[/COLOR]


```

After I did this step it worked. The OpenVPN was a **SUCCESS**. So from translating the above RED code. I am to translate the RV042 IP that can be understood by my IPCop.

**Day 2. SWITCH FROM OPENVpn to ACTUAL VPN**
So you might wonder why get VPN when you already got OpenVPN working. Again, my MAIN goal is a SITE-to-SITE VPN. So here goes VPN.

I found numerous sources for this and they were one-way successful just like above issue of OpenVPN. I can't ping from RV042 --> IPCop network **BUT** ping works in IPCop --> RV042.

so I tried to add a second line for the code above hoping it would work. You may notice below in GREEN (VPN) and RED (OpenVPN). Also notice how I set SOURCE as the ACTUAL IP SUBNET of RV042.

**/etc/rc.d/rc.firewall.local file**
```
#!/bin/sh
# Used for private firewall rules

# See how we were called.
case "$1" in
  start)
        ## add your 'start' rules here
    #Added for zerina start - BEGIN
    /usr/local/bin/openvpnctrl --create-chains-and-rules
    #Added for zerina start - END
    #
    # Line below is added to allow Windows PC's access thru the VPN
    [COLOR="Red"]iptables -t nat -A CUSTOMPOSTROUTING -s 192.168.101.0/24 -o eth0 -j MASQUERADE[/COLOR]

    [COLOR="GReen"]iptables -t nat -A CUSTOMPOSTROUTING -s 172.16.0.0/24 -o eth0 -j MASQUERADE[/COLOR]

```

This did not work. I researched more and found many sources.

[(1) My most concrete source]("https://forum.openwrt.org/viewtopic.php?id=9517"). But I was not satisfied because he was making rules in the INPUT Chain. I prefer the NAT way. So I research more. [(2) Not IPCop but an IDEA]("http://wiki.mikrotik.com/wiki/Manual:IP/IPsec#NAT_Bypass") nevertheless. So If I understand it right, its the code below.

```

iptables -t nat -I REDNAT -j ACCEPT -s 192.168.100.0/24 -d 172.16.0.0/24

```

**NOTE: I HAVENT TRIED THIS YET.** I just posted this so I know what you guys think.

[(3) I need help explaining this SOURCE]("http://unbeknownst.net/?p=253")

Any help/advice/suggestion is helpful. :cheers:

---

### Post by balagosa on 2012-08-09
ONE week and still nothing.

---

