---
title: "Intel Centrino N 6235"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by avaricious on 2013-02-05
Good time of day, comrads.

At home I've got access point asus rt-g32.
I installed ubuntu server 12.10 on my notebook. During installation I used wired connection (wireless was unavailable to connect. After all my tries to configure networking (eth0 and wlan0) was unsuccessful via terminal.
After I installed gnome. From this moment strange moment begins:

if I connect to my notebook wired network from LAN port of Asus, and boot Ubuntu (and GNOME) - here we go, i see both LAN and Wifi. but connection is extremaly unstable (downloads may stall and starts again without reasons).
and if I DONT connect to my notebook wired network and boot, in echo I can see errors (boot without full network support). 

Please help me to configure networking (wifi is preferred connection).

---

### Post by mikewhatever on 2013-02-06
Since you've installed the desktop, edit your /etc/network/interfaces, and delete all, but the following lines:
```
auto lo
iface lo inet loopback

```

Then reboot, and post the outputs of
```
lspci -nnk | grep -A2 Net

dmesg | grep -e eth0 -e wlan
```

Generally, a wired connection is preferable for a server. I'd only consider wireless when absolutely necessary.

---

### Post by avaricious on 2013-02-07
:~$ lspci -nnk |grep -A2 Net
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi

After deleting lines in ..interfaces there was no errors during boot, and after logon wifi connection is ok. 
Is that all? Or I've to something more to configure my wifi?

---

### Post by mikewhatever on 2013-02-10
> **avaricious said:**
> 
...
After deleting lines in ..interfaces there was no errors during boot, and after logon wifi connection is ok. 
Is that all? Or I've to something more to configure my wifi?

Depends. If everything has been working well, I see no reason looking for more problems. If it breaks or something, let me know.

---

