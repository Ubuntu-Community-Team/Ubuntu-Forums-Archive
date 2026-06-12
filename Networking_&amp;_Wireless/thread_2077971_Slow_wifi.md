---
title: "Slow wifi"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by JaySeeJC on 2012-10-29
Getting very slow wifi speeds with Intel Centrino Wireless-N 2230. Full lspci -kv:
```
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at da500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 68-5d-43-ff-ff-d4-69-f8
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

---

### Post by Zorael on 2012-10-30
Slow at connecting/resolving hosts, or slow traffic?

Are there any notable error messages output to **dmesg**?
```
$ dmesg | grep -i 'iwl\|wireless\|wifi\|wlan\|net'
```

Other than dealing with errors, there are a few ways you can tweak your network throughput. Googling shows up a bunch of interesting links, like;
[list][*][http://en.gentoo-wiki.com/wiki/TCP_Tuning](http://en.gentoo-wiki.com/wiki/TCP_Tuning)
[*][http://wwwx.cs.unc.edu/~sparkst/howto/network_tuning.php](http://wwwx.cs.unc.edu/~sparkst/howto/network_tuning.php)
[*][http://fasterdata.es.net/host-tuning/linux](http://fasterdata.es.net/host-tuning/linux)
[*][http://www.cyberciti.biz/faq/linux-tcp-tuning](http://www.cyberciti.biz/faq/linux-tcp-tuning)
[*][http://www.calebscreek.com/2010/05/how-to-increase-your-wireless-network-card-speed-in-debian-linux](http://www.calebscreek.com/2010/05/how-to-increase-your-wireless-network-card-speed-in-debian-linux)
[/list]
Curiously most of them recommend to increase transmit buffers, which I thought was generally a [Bad Thing](https://en.wikipedia.org/wiki/Bufferbloat), but I'm far from knowledgeable in these things.

Some of those pages list ways to benchmark traffic between a client and a server, so if you're really into it you could set up such an environment and try your hand at tweaking. Aside from changing the congestion protocol to one more suitable for wireless networks (Westwood+?), there's a slew of parameters in **/proc/sys/net** to change. I have no idea what most of them do, though **man tcp** is at least somewhat helpful there.

---

### Post by utkjamie on 2012-11-10
Sounds like this may be caused by bug #984552 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984552)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984552") being experienced by myself and others.

You're probably seeing a lot of excessive retries when you run *iwconfig* from the terminal and probably some errors when you run *dmesg | grep iwl*.

If you're experiencing what appears to be a bug, consider submitting a bug report via the terminal by typing: *ubuntu-bug linux*

I've seen various band-aid fixes, one of which is setting your router to wireless-G only. It's not an acceptable fix, considering your limiting your entire network due to a problem with Linux but it might help a bit.

---

