---
title: "Broadcom 4306 working, but not connecting"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Guitarmaster316 on 2009-04-14
HI all.

I have an HP laptop with a Broadcom 4306 (Rev2) card.  I just installed Jaunty. The b43legacy driver only works a little (slow speeds and dropping of connection).  I was able to get the card working with ndiswrapper thanks to a very helpful post.

Now the card is working like it was in windows as far as link speed, but...  it won't connect to any networks, secured or not.

when I input "dmesg | grep -e ndis -e wlan"  all looks good except for the line "encryption modes supported: none"

```
matt@matt-laptop:~$ dmesg | grep -e ndis -e wlan
[   19.270721] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.377039] usbcore: registered new interface driver ndiswrapper
[   23.896335] usbcore: deregistering interface driver ndiswrapper
[   23.914034] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   23.951922] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   23.952882] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   24.043121] ndiswrapper: using IRQ 10
[   24.257380] wlan0: ethernet device 00:90:4b:42:d4:a8 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   24.257528] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   24.257533] wlan0: encryption modes supported: none
[   24.261042] usbcore: registered new interface driver ndiswrapper
[   32.884810] ADDRCONF(NETDEV_UP): wlan0: link is not ready
matt@matt-laptop:~$ 
```







I believe this is the problem, but I don't know how to fix it.

ANy ideas??

Thanks 
 

P.S.  I am brand new to Ubuntu / Linux.  LIke it so far, but frustrated with the wireless.

---

