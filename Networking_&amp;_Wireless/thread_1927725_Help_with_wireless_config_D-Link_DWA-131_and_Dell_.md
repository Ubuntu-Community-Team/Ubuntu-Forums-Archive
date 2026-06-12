---
title: "Help with wireless config D-Link DWA-131 and Dell Dimension"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by shermantank on 2012-02-18
[FONT=Liberation Sans, sans-serif][SIZE=2]I installed Ubuntu 11.10 and have been unable to see any networks with DWA-131 adapter.  I have tried following similar threads in support but nothing seems to work.  Thanks in advance for any help you can provide.
[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]I have posted details below:
[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]
[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]Dell Dimension 4700C[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]Bus 001 Device 005: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU][/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]Ubuntu 11.10 [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]3.0.0-16-generic i686 [/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]**ifconfig**:[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]wlan0     Link encap:Ethernet  HWaddr f0:7d:68:cc:b1:7c   [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]UP BROADCAST MULTICAST  MTU:1500  Metric:1 [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]RX packets: 0 errors: 0 dropped:0 overruns:0 frame:0 [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]collisions:0 txqueuelen:1000  [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) [/SIZE][/FONT]
 

 **[FONT=Liberation Sans, sans-serif][SIZE=2]iwconfig:[/SIZE][/FONT]**
 [FONT=Liberation Sans, sans-serif][SIZE=2]wlan0     unassociated  Nickname:"rtl_wifi" [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0   [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]Retry: off   RTS thr: off   Fragment thr: off [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]Power Management: off [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]Link Quality:0  Signal level:0  Noise level:0 [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 [/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/SIZE][/FONT]
 

 **[FONT=Liberation Sans, sans-serif][SIZE=2]lsmod:[/SIZE][/FONT]**
 [FONT=Liberation Sans, sans-serif][SIZE=2]r8712u                163310  0  [/SIZE][/FONT]
 

 **[FONT=Liberation Sans, sans-serif][SIZE=2]dmesg:[/SIZE][/FONT]**
 [FONT=Liberation Sans, sans-serif][SIZE=2]287.860020] usb 1-5: new high speed USB device number 5 using ehci_hcd [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  287.994958] r8712u: DriverVersion: v7_0.20100831 [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  287.994985] r8712u: register rtl8712_netdev_ops to netdev_ops [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  287.994991] r8712u: USB_SPEED_HIGH with 4 endpoints [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  287.995495] r8712u: Boot from EFUSE: Autoload OK [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  288.385921] r8712u: CustomerID = 0x0000 [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  288.385928] r8712u: MAC Address from efuse = f0:7d:68:cc:b1:7c [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  288.462881] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin" [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  289.228500] r8712u: 1 RCR=0x153f00e [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  289.229245] r8712u: 2 RCR=0x553f00e [/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][  289.336438] ADDRCONF(NETDEV_UP): wlan0: link is not ready [/SIZE][/FONT]
 

 **[FONT=Liberation Sans, sans-serif][SIZE=2]sudo lshw -C network:[/SIZE][/FONT]**
 [FONT=Liberation Sans, sans-serif][SIZE=2]description: Wireless interface [/SIZE][/FONT]
        [FONT=Liberation Sans, sans-serif][SIZE=2]physical id: 1 [/SIZE][/FONT]
        [FONT=Liberation Sans, sans-serif][SIZE=2]bus info: usb@1:5 [/SIZE][/FONT]
        [FONT=Liberation Sans, sans-serif][SIZE=2]logical name: wlan0 [/SIZE][/FONT]
        [FONT=Liberation Sans, sans-serif][SIZE=2]serial: f0:7d:68:cc:b1:7c [/SIZE][/FONT]
        [FONT=Liberation Sans, sans-serif][SIZE=2]capabilities: ethernet physical wireless [/SIZE][/FONT]
        [FONT=Liberation Sans, sans-serif][SIZE=2]configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated [/SIZE][/FONT]
 

 **[FONT=Liberation Sans, sans-serif][SIZE=2]iwlist scan:[/SIZE][/FONT]**
 [FONT=Liberation Sans, sans-serif][SIZE=2]wlan0     No scan results[/SIZE][/FONT]

---

