---
title: "No internet after crash on suspend"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by Sander1979 on 2012-07-10
Hi all,

When I manually suspended my laptop today, the system crashed (backlight stayed on and no response whatsoever). After a hard reboot, my wireless reconnected normally, but I can access no websites, no mailservers, not even my router interface, nothing.

I am running Ubuntu 12.04 LTS

I have tried the following:
```

sudo service network-manager stop
sudo rmmod iwl3945
sudo modprobe iwl3945
sudo service network-manager start

```After that, the wireless icon reappears, and the network manager reports having successfully reconnected, but still no internet.

Now I vaguely remember having a similar problem a year ago, and that there is some setting that gets disabled before entering suspend mode and enabled after waking up, that you have to manually reset in some config file if your computer crashes during suspend in order to get internet back, but I can't seem to remember what it was.

Normally suspend works fine on my system, and I expect the crash was caused by a VPN connection manager that I started using recently (Cisco AnyConnect VPN Client) which was still running a connection when I suspended my laptop.

Please let me know if there is additional information that I could supply from the terminal in order to fix this. Any tips would be greatly appreciated, thanks!

---

### Post by Sander1979 on 2012-07-10
I fixed it. The VPN client had modified my resolv.conf and didn't get a chance to change it back because of the crash.

---

