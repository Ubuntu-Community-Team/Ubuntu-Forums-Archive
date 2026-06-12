---
title: "How To Get the Official Cisco VPN Installed in 8.10"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by excalq on 2009-01-12
After spending quite a bit of time in these forums and elsewhere on the internet, trying to install the official Cisco VPN client, I noticed there was a severe lack on information on how to do this in Ubuntu 8.10 (Intrepid Ibex). Most of the howtos involve very kernel version specific patches for 8.04 and earlier.

I am running a fresh, but updated install of 8.10 with Kernel version 2.6.27-9. I require the official Cisco client as opposed to an open solution like vpnc because I am given .pcf files with encrypted passwords in them by my employer clients and don't want the hassle of avoiding that.

Anyway, download this version of the Cisco client (Not the most recent version!):

[http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz]("http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")

And apply this patch to it (Not the one marked "final"):
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24.diff]("http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24.diff")

Save the patch file with the extracted vpnclient files and apply the patch:
```
cd vpnclient/
patch < ./vpnclient-linux-2.6.24.diff

```

Then compile the client:
```
./vpn_install

```

This is specific to 32-bit installs, however this seemed to handle that case: [http://forum.tuxx-home.at/viewtopic.php?f=15&t=670]("http://forum.tuxx-home.at/viewtopic.php?f=15&t=670")

EDIT: This is a great resource which walks through the same process in detail:
[http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/]("http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/")

---

