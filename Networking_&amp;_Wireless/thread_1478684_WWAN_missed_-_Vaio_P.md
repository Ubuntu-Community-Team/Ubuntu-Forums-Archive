---
title: "WWAN missed - Vaio P"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by dimonsbo on 2010-05-10
hi,
i've Vaio P39 with Karmic 9.10(2.6.31.21). Everything is ok excluding  the WWAN. It just is missing in available networks list to connect (LAN and WiFi are ok).
Searching gives that WWAN adapter doesn't start at cold reboot and it's proposed to use Win7 to switching WWAN on and then restart. But it looks like ](*,) - must have Win7 only to switching WWAN on...
This kind of solution for some Vaio laptops
```
echo "1" > /sys/devices/platform/sony-laptop/wwanpower
```
looks as not working in Vaio P.
Probably bad searching from my side :) but I've no solution yet. Does it exist at all?

---

### Post by dimonsbo on 2010-05-13
Solved!
1. download **[This fix]("http://www.logic.at/people/preining/software/sony-laptop-zseries-0.9np5.tar.gz")**
2. unarchive e.g. into /tmp/wwan
3. start terminal and do commands
```

cd /tmp/wwan
sudo make
sudo make install

```
4. reboot

WWAN connection will be available in the Connection Manager :KS

---

### Post by quinthar on 2010-11-15
Alas, tried this to no effect.  I have Sony Vaio P VPCP118KX running 10.04.  The Verizon Broadband works flawlessly when it works at all, but the device only appears after I boot into Windows 7 and back (and even then, not 100% reliably).  Any tips?  Can I provide any output of any diagnostic command to help?  Thanks!

-david

---

