---
title: "OpenVPN VPN Client"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by omgimdrunk on 2012-11-16
I have set up a simple Openvpn server in the amazon cloud, I have used this several times on my other Liunx box but with my Ubuntu 12.04 I am getting an odd error.

I have a static key and in my client.conf I have a line:

```

secret /etc/openvpn/static.key
```

that key was generated on the server itself and copied over via sftp and has been chmod to 600

While using the networkmanager, ubuntu insists to use a username password instead of reading the freaking static key and giving me an Error of " Authentication Failed"
I can ping the remotes ip address set up in the nat just fine as well.

Any ideas?

---

### Post by ahallubuntu on 2012-11-16
If you are using Network Nanager, why are you editing an OpenVPN conf file?   Do one or the other: use Network Manager to setup your OpenVPN connection (and let it find/use the static key file) or use a conf file and connect to the VPN manually.  If using Network Manager, use the Static Key authentication (instead of "Password" or "Certificates (TLS)").

---

### Post by omgimdrunk on 2012-11-16
> **ahallubuntu said:**
> If you are using Network Nanager, why are you editing an OpenVPN conf file?   Do one or the other: use Network Manager to setup your OpenVPN connection (and let it find/use the static key file) or use a conf file and connect to the VPN manually.  If using Network Manager, use the Static Key authentication (instead of "Password" or "Certificates (TLS)").

The reason I created the conf file is because within the network manager I cannot see anywhere to enter a static key file, here is my options:
[IMG]http://i.imgur.com/3QeHd.jpg[/IMG]

---

### Post by ahallubuntu on 2012-11-17
Install the OpenVPN Network Manager plugin so Network Manager can work directly with OpenVPN configurations.

I have it installed in 10.04 LTS - it's called network-manager-openvpn .  Haven't used it in 12.04 LTS but it works great for me.

---

