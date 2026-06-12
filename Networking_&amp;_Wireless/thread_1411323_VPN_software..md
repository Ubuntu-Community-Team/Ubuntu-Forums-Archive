---
title: "VPN software."
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by A_M_S on 2010-02-19
Hello.

What are the best VPN programs available on Ubuntu?

Can i use a VPN with Linux and Windows machines?

Tnx.

---

### Post by isharabash on 2010-02-19
I *just* got done setting up a pptp vpn myself, which is what windows machines use to connect (apparently).

I haven't even tested it with another comp yet but out of 4-5 guides I tried/looked at, the best was [this guide]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")

Word of caution, if you're using a d-link router it can get hairy, the solution I found (on another site, not my own) was to:

untick IPsec under advanced > firewall settings
and then create two virtual servers under advanced > virtual server

The first with a protocol of other, 47, and pointing to your vpn server
The second pointing port 1723 (tcp) to your vpn server

---

### Post by pirateghost on 2010-02-19
i prefer openvpn.  its easy to setup, and works cross platform.

---

### Post by A_M_S on 2010-02-19
Thank you for the replies. :)

---

### Post by SoFl W on 2010-02-19
I have used hamachi with Windows, but haven't used it in a while.  Long before the last upgrade.  I was able to get it to work under Damn Small but haven't tried it under any other linux.

---

### Post by psyke83 on 2010-02-20
Don't forget that Network Manager support VPN connections when you install the support packages:
```
$ sudo apt-get install network-manager-vpnc-gnome network-manager-vpnc network-manager-pptp-gnome network-manager-pptp network-manager-openvpn-gnome network-manager-openvpn
```

---

### Post by A_M_S on 2010-02-22
> **psyke83 said:**
> Don't forget that Network Manager support VPN connections when you install the support packages:
```
$ sudo apt-get install network-manager-vpnc-gnome network-manager-vpnc network-manager-pptp-gnome network-manager-pptp network-manager-openvpn-gnome network-manager-openvpn
```

Thanks, i'll try it. :)

---

### Post by whit on 2010-03-10
Depends on where you're connecting to. If you control both ends, OpenVPN works well, and on many platforms. If you're stuck with IPsec, you're into wilder territory, with interoperability hurdles if the platforms vary. I'm currently running OpenVPN for road warriors to connect to an office network, and Openswan (IPsec) for connecting an office network to a network behind a remote Cisco. IPsec is almost a black art. Other ways of doing IPsec include vpnc - if you just need to run a VPN client, StrongSwan - if you prefer the more Germanic attitude of another branch (along with Openswan) from the original FreeS/WAN project (YMMV there). There's also KAME, ported from BSD, in the ipsec-tools package, which some swear by and others swear at. None of the current IPsec implementations are adequately documented, so expect trial-and-error. OpenVPN is much easier to use, but isn't IPsec. It only talks to other OpenVPN instances. Also, the OpenVPN people have sort of hidden some of the support for the free product, because they're more focused on the commercial side of it now.

---

