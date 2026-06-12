---
title: "Unable to connect to CISCO VPN on Ubuntu 12.10 - Error: Unknown PPTP file extension"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by Webnet on 2013-03-27
On Windows I use Shrewsoft VPN and import a .vpn file given to me by our administrator at work (who unfortunately doesn't support linux since I'm the only one who is interested).  I've followed the guide here: [http://www.ubuntugeek.com/how-to-install-cisco-vpn-client-on-ubuntu-11-10.html](http://www.ubuntugeek.com/how-to-install-cisco-vpn-client-on-ubuntu-11-10.html)

My VPN file fails to import, it says **Error: Unknown PPTP file extension**

I've tried to compare the Windows menus to the Ubuntu ones to try to recreate the configuration, but the settings are so different it doesn't seem like I'm going to be able to make that happen.

My .vpn file looks like:

```
n:version:2
n:network-ike-port:500
n:network-mtu-size:1380
n:client-addr-auto:1
n:network-natt-port:4500
n:network-natt-rate:15
n:network-frag-size:540
n:network-dpd-enable:1
n:client-banner-enable:1
n:network-notify-enable:1
....

```

Any thoughts on why I might be getting this error?

---

