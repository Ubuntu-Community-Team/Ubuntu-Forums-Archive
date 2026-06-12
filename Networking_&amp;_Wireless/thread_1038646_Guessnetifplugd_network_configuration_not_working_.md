---
title: "Guessnet/ifplugd network configuration not working propperly"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by slakkie on 2009-01-13
Hello all,

I'm having some problems with something that used to work really well on other laptops I used. But now I've encountered a problem and I'm unable to figure it out..

I use guessnet and ifplugd to configure my wired and wireless networks, I even wrote the following HOWTO in Dutch: [http://wiki.fok.nl/index.php/Dig/linux/wireless](http://wiki.fok.nl/index.php/Dig/linux/wireless)

So my setup is similar as in the howto (wlan0 is now my wireless interface), and it pretty much works, only for one small issue. When I boot my machine (or just simply restart the networking bit) I cannot connect to any site, I need to add my default gateway manually.. Why? I do not know, I have my default gateway listed in the correct section:

```

iface home-wifi inet static
  test wireless essid wnl.opperschaap.net
  address 192.168.1.114
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-domain opperschaap.net
  dns-search opperschaap.net euronet.nl wanadoo.nl online.nl
  dns-nameserver 194.134.5.5 194.134.0.97
  metric 1

```

The interface wlan0 is up and has IP address 192.168.1.114. The only thing not correctly setup is the default gateway for some reason... 

Does anyone know how I can resolve this issue? Much appreciated.

Cheers,
Wesley

Ps.


22:36 pts/1 0 wesleys@eniac:/var/log$ lsb_release -a
uname -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

22:37 pts/1 0 wesleys@eniac:/var/log$ uname -a
Linux eniac 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

---

