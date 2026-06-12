---
title: "[elementary os] broadcom bcm4313 chip driver installation"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by rrgjl on 2013-08-30
I was having some problems with my wireless chip driver, for the broadcom bcm4313 b/g/n wireless chip. At home it usually stayed connected according to the system, but lost the connection for about 10 seconds every few minutes in practice. After 10 seconds everything would work again. Furthermore, at my parents home I can't connect to the wireless which is wpa/wpa2 secured. It asks for the password, but does not finish the connection process for some reason even though I know the password is correct (other laptops with windows working just fine).
So I decided to install a new driver and see if that helps. I found a bug report on my specific NIC and found this driver in the report, which should work: [https://launchpad.net/ubuntu/raring/amd64/bcmwl-kernel-source/6.20.155.1+bdcom-0ubuntu6](https://launchpad.net/ubuntu/raring/amd64/bcmwl-kernel-source/6.20.155.1+bdcom-0ubuntu6)

I installed it through the Software Center of Elementary OS; after I downloaded the file it automatically opened up in there. Now I'm just not sure if it is also automatically activated, or if I have to manually active the driver somehow. Or do I need to reboot for example? Of course I could find out in other ways if it's working now, but I'd also just like to know the standard procedure for driver installation and activation.

---

### Post by carl4926 on 2013-08-30
I'd like to see the wireless part of

```
lspci -nnk
```

---

### Post by rrgjl on 2013-08-30
Here you go:

24:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:145c]
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac

---

### Post by rrgjl on 2013-08-30
PS I had been using the Broadcom STA wireless proprietary driver, which had the same issues, so I disabled it again. Maybe that's something you can tell from the above info.

---

### Post by carl4926 on 2013-08-30
```
[TABLE="class: devtable, width: 742"]
[TR]
[TD]14e4:4727
[/TD]
[TD="bgcolor: #FF9090"]no (WIP)
[/TD]
[TD]BCM4313
[/TD]
[TD]b/g/n
[/TD]
[TD]LCN (r1)
[/TD]
[TD]wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211")
[/TD]
[/TR]
[/TABLE]

```

See at
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by rrgjl on 2013-08-30
So wha does this mean exactly? I don't understand.
Ok, there's no support. No support by what/whom? A specific driver, or any driver at all?

---

### Post by carl4926 on 2013-08-30
> **rrgjl said:**
> So wha does this mean exactly? I don't understand.
Ok, there's no support. No support by what/whom? A specific driver, or any driver at all?

No b43
wl is supported

---

### Post by chili555 on 2013-09-01
This may be helpful: [http://askubuntu.com/questions/339831/cannot-connect-to-wifi-with-ubuntu-13-04/339840?noredirect=1#comment433863_339840](http://askubuntu.com/questions/339831/cannot-connect-to-wifi-with-ubuntu-13-04/339840?noredirect=1#comment433863_339840)> If signal strength is still low, try an earlier bcmwl-kernel-source as mentioned here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1110139/comments/42](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1110139/comments/42)

...and the instructions following. Please let us know if it works for you.

---

