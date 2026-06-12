---
title: "Network Manager"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by ssmokn on 2009-03-06
Hi,

I've got 8.10 desktop with all current errata applied.

The machine is a desktop with wired ethernet (no wireless).  I was using Network Manager and vpnc (with the NM plugin for vpnc) for quite some time with good success.  My connection was DHCP.

Recently I removed Network Manager and vpnc (including all settings) via Synaptic and I configured a static IP address.

This was working fine but I then found a workaround (use MAC and create a new connection) to allow Network Manager to work properly with a static IP address.

So I changed my /etc/network/interfaces file back to 

auto lo
iface lo intet loopback
iface eth0 inet dhcp

I then reinstalled Network Manager and vpnc

No matter what I do now I have an "x" in Network Manager and it says it is an "unmanaged device".

Any tips to point me in the right direction.  I've searched here and via google but I can't seem to get back to where I need to be.

I'd be happy for now with Network Manager managing the adapter using DHCP.  Then I could work on getting the static config working with Network Manager.

I've uninstalled and reinstalled NM on other machines running 8.10 in the past and I've never run into this issue.

Thanks.

---

### Post by Iowan on 2009-03-06
Check NM config files: */etc/NetworkManager/nm-system-settings.conf*

---

### Post by sehrgut on 2009-03-06
This happened to me on a Xubuntu lappy. In the config file mentioned by the previous poster, make sure the ifupdown plugin is loaded, and its "managed" flag is set to "true". For instance, here's my /etc/NetworkManager/nm-system-settings.conf .

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```

---

