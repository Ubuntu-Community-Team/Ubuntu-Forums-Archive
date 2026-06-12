---
title: "OpenVPN, how to use cryptodev engine?"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by pakjebakmeel on 2010-06-16
Hi all,

I've been playing around with Lucid for a while now and so good so far. I've been able to solve most of my issues by browsing this wonderful forum.

Anyhow, here's one I haven't been able to crack yet. I'm running a PfSense OpenVPN server on an ALIX board, it turns out that OpenVPN can utilize my Geode's cryptographic acceleration capabilities. To get this working you need to configure the VPN to use AES-128-CBC encryption and add the line "engine cryptodev" to both server and client config files like so:

[http://doc.pfsense.org/index.php/Are_cryptographic_accelerators_supported](http://doc.pfsense.org/index.php/Are_cryptographic_accelerators_supported)

Easy peasy, I've added it to the server config and the log shows it's being initialized server-side:

```

Jun 16 12:10:44     openvpn[37506]: Initializing OpenSSL support for engine 'cryptodev'
Jun 16 12:10:44     openvpn[37506]: OpenVPN 2.0.6 i386-portbld-freebsd7.2 [SSL] [LZO] built on Dec 4 2009

```

As for Ubuntu I have set-up the VPN through Gnome-network-manager and found that there IS NO config file to add this line to like in Windows.

After some investigation it turns out that the connections can be found in gconf-editor under System --> Networking --> Connections

ok, now how the !@#(&*) :confused: can I add this line to the config here? I've played around with some string values which don't seem to be accepted. I wasn't able to find ANY info related to utilizing the cryptodev engine using OpenVPN through the gnome-network-manager.

Any idea's?

---

