---
title: "Karmic Alfa AWUS036H rtl8187"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by razta on 2009-12-19
Hello,
I had problems with my previous wireless USB adapter so bought the Alfa AWUS036H on a recommendation, I believe this wireless card needs the rtl8187 drivers which I believe Karmic should already support.

If I plug the alfa into one of the USB interfaces on the back of my machine the LED doesnt even light up, if I plug it into the front the LED flashes. I think this may be because the interfaces on the back are USB 1.0 and not 2.0.

Maybe someone could confirm this:
```
ryan@ryan-desktop:~$ lsusb
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 002: ID 04f2:0618 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 023: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I had the card connected to the internet via the front USB interfaces, however it kept dropping the connection every few minutes. Now it doesnt connect at all.

 ```
wlan127   Link encap:Ethernet  HWaddr 00:c0:ca:33:c1:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'm not sure if the above is normal either, all my other wireless cards were named wlan0. 


Can any one help with this? I'm not sure what to do now.

Thanks in advance.

Ryan

EDIT----

Tried it on my Fedora 12 box and worked fine. Still not working under Karmic.

---

### Post by razta on 2009-12-22
Any one out there having the same problems?

Heres a dmesg:
```
[84299.360028] usb 1-5: new high speed USB device using ehci_hcd and address 92
[84299.500023] usb 1-5: configuration #1 chosen from 1 choice
[84299.683619] phy720: Selected rate control algorithm 'minstrel'
[84299.689233] phy720: hwaddr 00:c0:ca:33:c1:3f, RTL8187vB (default) V1 + rtl8225z2
[84299.718649] udev: renamed network interface wlan0 to wlan127
[84299.726332] rtl8187: Customer ID is 0xFF
[84299.726434] Registered led device: rtl8187-phy720::tx
[84299.726472] Registered led device: rtl8187-phy720::rx
[84301.789792] ADDRCONF(NETDEV_UP): wlan127: link is not ready
[84302.023237] usb 1-5: USB disconnect, address 92
```

---

### Post by brdokoky on 2009-12-22
I have bought same one , and I've got identical problem. I'm still looking for solution , but nothing in Ubuntu. When I use Sabayon that's perfect , same in windowsxp, but in ubuntu I can not solve it. I hope we get it shortly.

---

### Post by razta on 2009-12-22
It's good to know I'm not alone. :)

I installed Linux Mint (latest) on my netbook and tried out the Alfa, it worked. So I am now going through the rigmarole of moving my files around and installing Mint on my main machine.

In short: Linux Mint (latest) works with the Alfa AWUS036H.

---

### Post by razta on 2009-12-22
I take that back. :(

Works great on my netbook with fresh mint installed but not on my desktop with fresh mint installed. The only thing I can think of is that the USB ports are different. Off to try Sabayon...

---

### Post by brdokoky on 2009-12-23
I found many things why is not working. Cause in Karmic is new kernel. Same is when I  installed jaunty 9.04 is working O.K. But after upgrade to Karmic same problem. That the solution is to stay in Jaunty. No upgrade to new kernel.
Just have a look:

[http://forum.aircrack-ng.org/index.php?topic=5755.0]("http://forum.aircrack-ng.org/index.php?topic=5755.0")

---

### Post by razta on 2009-12-23
Jaunty works!!! :)

Thanks for the info and link!

Is there any way I can allow all updates apart from the one that is going to mess up my wireless?

Thanks!

---

