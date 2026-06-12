---
title: "OpenVPN: Avoid &quot;WARNING: No server certificate verification&quot;"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by txapelgorri on 2009-01-24
Hi:

I'm using "network-manager-openvpn" to manage different OpenVPN connections. It works, it does it's job very well, but I'm trying to avoid a disturbing WARNING, as I mentioned in the subject of this post, but not only because it's disturbing, also because the configuration is insecure as mentioned here: [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm)

At OpenVPN.net the documentation says that there are five ways of securing this, but you need to add some directives to client.conf file (supposing that you're using openvpn directly, without network-manager). And here comes the problem: how can I add "ns-cert-type" directive or "tls-remote" for example to openvpn client, if I use network-manager?.

Cheers, Ibon.

---

### Post by txapelgorri on 2010-10-04
I respond myself: this warning is shown with Karmic and Lucid. The solution in Lucid is to use gconf-editor to add at /system/networking/connections/number_of_your_connection/vpn another key with name "tls-remote", type string, and value, the name of your OpenVPN server.

With Karmic I was unable to achieve this solution, even with the packages of this PPA: [https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa) :(

Cheers, Ibon.

---

