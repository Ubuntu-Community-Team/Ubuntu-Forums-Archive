---
title: "Realtek RTL8192E on Samsung R420"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by 1fireman1 on 2011-01-11
Sometimes, my wireless connection stops working, but it still shows as connected in the notification area. I have to do reset the driver to fix it. It happens every 10 minutes to a few hours.

When I type lspci it shows:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)

ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:26:b6:63:26:7b  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe63:267b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:fb8b0000-fb8b0100
```

iwconfig:
```
wlan0     802.11bgn  ESSID:"DLINK"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:22:B0:B4:9A:C6   
          Bit Rate=135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=88/100  Signal level=-54 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and this is the driver thing that im using: r8192e_pci

Im on ubuntu 10.10. I cant post the dmesg because its longer than the terminal window, so i cant copy it.

---

### Post by am0rphous on 2011-01-11
Read this (it might help): [http://ubuntuforums.org/showpost.php?p=10343332&postcount=4](http://ubuntuforums.org/showpost.php?p=10343332&postcount=4) 

 I was using the same driver you mention (on the same wireless chipset) and I also had similar problems.

---

### Post by 1fireman1 on 2011-01-11
Um.. Im a newbie so you explain to me step by step on how to install the driver?

I know briefly that im supposed to do sudo make install but I dont know how exactly to combine the 2 files.

---

