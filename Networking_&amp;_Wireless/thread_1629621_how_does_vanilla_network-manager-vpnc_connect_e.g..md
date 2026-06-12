---
title: "how does vanilla network-manager-vpnc connect? e.g. IPSec or SSL?"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by tlroche on 2010-11-23
The Cisco VPN to which I connect has licenses for a small number of SSL connections and a large number of IPSec connections. According to its maintainers, VPN usage of SSL connections is nearing the limit, but no more SSL licenses will be bought, so folks attempting to connect via SSL will likely start failing to connect. Accordingly I'd like to know how I'm connecting. How to check that? Alternatively, perhaps one determine the mode of VPN connection from the following information about my OS, vpnc, and Network Manager usage:

> 
$ lsb_release -ds
> Ubuntu 10.04.1 LTS
$ uname -rv
> 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010
$ vpnc --version
> vpnc version 0.5.3
...
> Built with certificate support.
> Supported DH-Groups: nopfs dh1 dh2 dh5
> Supported Hash-Methods: md5 sha1
> Supported Encryptions: null des 3des aes128 aes192 aes256
> Supported Auth-Methods: psk psk+xauth hybrid(rsa)


I connect (manually--I don't need to connect automatically) using the GUI for network-manager-vpnc: Network Manager>VPN Connections>[my VPN entry name], i.e.

[LIST=1]
[*]click on the NM panel icon
[*]in the resulting menu, click on "VPN Connections"
[*]in the resulting menu, click on my VPN entry name
[/LIST]

I created my VPN entry (e.g., when I upgraded karmic -> lucid) by

[LIST=1]
[*]Network Manager>Edit Connections...>VPN>Add...>Cisco Compatible VPN (vpnc)>Create...
[*]in detailed connection dialog, tab=VPN, set
[LIST]
[*]VPN name
[*]VPN gateway
[*]VPN group name
[*]User password=<null> (IT wants us entering it every time)
[*]VPN group password
[*]VPN user name
[/LIST]
[*]leave unchecked="Connect automatically"
[*]for rest, take defaults
[*]in detailed connection dialog, tab="IPv4 Settings": hit button=Routes...
[*]in resulting dialog, check box="Use this connection only for resources on its network" is unchecked (default=unchecked), hit button=OK
[*]apply, close
[/LIST]

TIA, Tom Roche [Tom_Roche@pobox.com]

---

