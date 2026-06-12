---
title: "Releasing a DHCP address on Ubuntu 12.04?"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by theevilsharpie on 2012-10-31
Here's an odd question: How do you release a DHCP address in Ubuntu 12.04?

I had some performance issues with my Internet connection this morning, so I hooked my Ubuntu laptop for some quick diagnostics. Unfortunately, my ISP only assigns one IP address at a time via DHCP. To get my router back online, I'd either have to manually release the DHCP lease from my Ubuntu laptop, or wait several hours for the lease to expire.

I figured it would be as simple as going to Network Manager and disconnecting my Wired Connection before I physically unplug the cable, but while that does bring down the interface, it doesn't release the DHCP lease. I also tried running **sudo dhclient -r**, but that doesn't do anything.

So.... yeah. Now what? :-?

---

### Post by majorcornwallace on 2013-01-16
Basically it's all spelled out in the Ubuntu doc for 12.04:

[https://help.ubuntu.com/12.04/serverguide/network-configuration.html]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html")

---

### Post by jonobr on 2013-01-16
Hello

If you open a terminal and run ifconfig and see no IPv4 address in there then the interface has dropped the IPV4 and your ISP is marking the address as used, I dont think there is a lot you can do about that,

If still have that IP on your interface then I would recommend opening two terminal windows,
in one run a trace

```
tcpdump -vvv -i any -s 1600 port bootps or port bootpc
```

In the other window do your dhclient command as that *should* work.
Looking at the trace you will see if the IP is being relinquished.

---

