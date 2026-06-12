---
title: "Unable to resolve internal hostnames after connecting to VPN"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by aselder on 2013-02-27
Hi all,

I have a fresh install of Ubuntu 12.10 and I'm attempting to get it working with my work's VPN.

I installed network-manager-openconnect-gnome, and configured the VPN. Connection works fine and I can access protected assets via their IP address. However I am unable to resolve any internal domain names.

Looking at the syslog ouput ([https://gist.github.com/anonymous/5053608](https://gist.github.com/anonymous/5053608)), it appears to be getting the networking information from the VPN server fine, including the internal DNS server.

nmcli ([https://gist.github.com/anonymous/5053618](https://gist.github.com/anonymous/5053618)) and nm-tool ([https://gist.github.com/anonymous/5053622](https://gist.github.com/anonymous/5053622)) show no sign of the internal DNS server.

I'm probably missing something pretty simple, but I can't seem to figure it out.

---

### Post by tayloryork on 2013-05-26
Did you ever figure this out?  I just hit the same isssue.

---

