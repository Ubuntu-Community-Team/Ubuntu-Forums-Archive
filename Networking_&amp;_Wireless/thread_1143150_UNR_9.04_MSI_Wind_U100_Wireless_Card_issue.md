---
title: "UNR 9.04 MSI Wind U100 Wireless Card issue"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by 5Euros on 2009-04-29
I've installed Ubuntu UNR 9.04 and almost everything works perfectly. Using the built in wireless card - Realtek 8187SE. Unfortunately some web sites don't render - e.g. [www.rememberthemilk.com](www.rememberthemilk.com).

Another forum / wiki post suggested disabling disabling IPV6. I've tried this in Firefox about:config. But this had not made any difference. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ipv6](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ipv6)

If I use an external wireless card - Belkin - all sites launch perfectly.

I'm a complete novice at this so if you can help I would be most grateful, however, you may need to spell out exactly what steps I need to follow, and how I need to execute them.

Thanks to all who can help.

---

### Post by Zorael on 2009-04-29
To temporarily disable ipv6 (until next reboot), try the following in a terminal.
```
$ echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6
```
If ipv6 is indeed what's causing it, that should hopefully fix everything instantaneously (or after network reconnect, not sure). As for disabling it persistently, stuff changed a bit in Jaunty; I don't think that **/etc/modprobe.d/aliases** file exists anymore.

Try this.
```
$ sudo cp /etc/sysctl.conf /etc/sysctl.conf.backup
$ echo net.ipv6.conf.all.disable_ipv6 = 1 | sudo tee **-a** /etc/sysctl.conf
$ sudo sysctl -p
```

For alternatives, see [http://ubuntuforums.org/showthread.php?t=1137127](http://ubuntuforums.org/showthread.php?t=1137127).

---

