---
title: "[SOLVED] Ndiswrapper modprobe issues."
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by earle79 on 2008-12-22
Ok, i have ndiswrapper working, stays connected and works fine, until rebooting.  I have it where ndiswrapper works on boot like one of the tutorials showed me how to.  and that would be great, but when i login, it doesnt work, its loaded but not working. and i can't use the "sudo" command in the terminal, which is weird.  when i try to use "sudo" it just sits there blinking at me not even asking for a password.

the only way i can get it to work is by booting to recover and drop to the root shell and stop modprobe ndiswrapper and then continue the boot, then open terminal and modprobe ndiswrapper it connects and works just fine.

im clueless to know where to start to fix this issue.

---

### Post by earle79 on 2008-12-22
here is some dmesg outputs after i boot with wireless connection working and able to access internet.  

**dmesg | grep wlan0**
```
earle@linuxBox:~$ dmesg | grep wlan0
[   40.035184] wlan0: ethernet device 00:0f:3d:03:86:5b using NDIS driver: mrv8k51, version: 0x2030001, NDIS version: 0x500, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[   40.035463] wlan0: encryption modes supported: WEP; TKIP with WPA
[   80.912748] ndiswrapper: device wlan0 removed
[  186.228820] wlan0: ethernet device 00:0f:3d:03:86:5b using NDIS driver: mrv8k51, version: 0x2030001, NDIS version: 0x500, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[  186.310622] wlan0: encryption modes supported: WEP; TKIP with WPA
[  191.132341] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  198.798807] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  209.508075] wlan0: no IPv6 routers present
earle@linuxBox:~$ 

```

**earle@linuxBox:~$ dmesg | grep ndiswrapper**
```
earle@linuxBox:~$ dmesg | grep ndiswrapper
[   39.601813] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   39.750690] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[   39.751704] ndiswrapper 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[   39.755827] ndiswrapper: using IRQ 9
[   40.035360] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   40.035752] usbcore: registered new interface driver ndiswrapper
[   80.912748] ndiswrapper: device wlan0 removed
[   80.912813] ndiswrapper 0000:01:09.0: PCI INT A disabled
[   80.913081] usbcore: deregistering interface driver ndiswrapper
[  185.861418] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  185.930939] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[  185.933354] ndiswrapper 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[  185.933417] ndiswrapper 0000:01:09.0: setting latency timer to 64
[  185.937836] ndiswrapper: using IRQ 9
[  186.309512] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[  186.312304] usbcore: registered new interface driver ndiswrapper
[  191.135392] ndiswrapper (set_essid:53): setting essid failed (C0010015)
[  192.516673] ndiswrapper (set_essid:53): setting essid failed (C0000001)
earle@linuxBox:~$ 

```

---

### Post by earle79 on 2008-12-23
can anyone help?????

---

### Post by earle79 on 2008-12-24
please??

---

