---
title: "Multiple PCs on IPREDator"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by allywilson on 2010-04-10
This is a bit of an FYI for those who come across this issue...

I recently signed up for the IPREDator service, and one limitation I've found is that having 2 computers I cannot have both of them connected at the same time. So, I decided to have 1 of them connected (my 'server'), and have the other route all of its traffic over the 'servers' VPN.

My server connects to the IPREDator VPN on interface *ppp0*.
My server will allocate *ppp1* for the VPN from my client.
My server's LAN address is *192.168.1.1*.
My client's LAN address is *192.168.1.2*.

On the server perform the following...
```
sudo apt-get install pptpd
```
Modify */etc/pptpd.conf* to have the following options:
```
option /etc/ppp/pptpd-options
logwtmp
localip 192.168.1.1
remoteip 192.168.1.100
```

Modify */etc/ppp/pptpd-options* to have:
```
name MYVPN
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 8.8.8.8 #These DNS servers are googles...not required.
ms-dns 8.8.4.4
proxyarp
nodefaultroute
lock
nobsdcomp

```

Modify */etc/ppp/chap-secrets*
```
username MYVPN password *
```

Modify */etc/rc.local*
```
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o ppp0 -j MASQUERADE 
```

Now on the client you need to install the ppptp VPN service. 
```
sudo apt-get install pptp-linux
```

Within Network Manager Add a new VPN, select PPTP as the type.
Settings:
```
Gateway: 192.168.1.1
User name: username
Password: leave blank
Leave the rest as default.
Open Advanced...
Untick everything in the box except MSCHAPv2
Tick Use Point-to-Point encryption (MPPE)
Untick all the boxes beneath that. Press OK, Press Apply, Press Close. 
```

We need to restart the PPTPD and Networking on the server (I would just restart the server). 
Make sure you connect to the IPREDator VPN on the server first (otherwise ppp0 won't be assigned to it).
Click Network Manager, VPN Connections click on your new VPN.

You should be prompted for your password (default in this guide is just 'password'). You should now be connected via PPTP to your server, which is in turn connected to the IPREDator VPN, and all of your traffic should be tunnelled as such.

I've probably made a ton of mistakes in this guide, and there's no doubt a hundred different ways to make this more elegant. Just thought I should share what I've done (google wasn't much help regarding my specific requirements).

---

### Post by voltage223 on 2010-04-22
"remoteip 192.168.1.100"

"Gateway: 192.168.1.65"

Could you explain what the purpose of these addresses are in your guide? Thanks.

Also, very interested in setting up something just like this on a Windows platform as I have several Windows computers lying around and need some kind of solution so if anyone can direct me to some instructions or program that would be helpful with that please let me know.

---

### Post by allywilson on 2010-04-23
Apologies, instead of *192.168.1.65* it should have been *192.168.1.1*.

The *remoteip 192.168.1.100* is the IP address that my server assigns to my client when it connects to it via pptp. It can be any IP, I just chose that one randomly.

You could probably set this up on Windows in an easier way, but I don't think this is the forum for that...

Hope that clears it up.

---

