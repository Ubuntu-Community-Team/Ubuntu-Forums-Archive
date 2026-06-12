---
title: "Dell d600 broadcom 4306 rev 03 wireless issues and Jaunty"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Greslore on 2009-04-23
Greetings all, 

Having a bit of trouble with wireless.  Under Intrepid, the wireless worked fine, but just installed Jaunty, and wireless is a no go.  After installing Jaunty, I went into SYSTEM > ADMINISTRATION > HARDWARE DRIVERS > and activated Broadcom B43 wireless driver.  Didnt work.

My laptop is a Dell D600 Latitude, Broadcom B4306 rev 03 Wireless NIC.

Anyone have any ideas?  I seem to have the right bw43 drivers installed...  Not sure what is causing this.

Here are some outputs:
>lspci
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

>lshw
*-network:0
     description: Ethernet interface
     product: NetXtreme BCM5705M Gigabit Ethernet
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:02:00.0
     logical name: eth0
     version: 01
     serial: 00:0f:1f:b5:48:07
     width: 64 bits
     clock: 66MHz
     capabilities: bus_master cap_list ethernet physical
     configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 latency=32 mingnt=64 module=tg3 multicast=yes
*-network:1
     description: Network controller
     product: BCM4306 802.11b/g Wireless LAN Controller
     vendor: Broadcom Corporation
     physical id: 3
     bus info: pci@0000:02:03.0
     version: 03
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master
     configuration: driver=b43-pci-bridge latency=32 module=ssb
*-network:0
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:90:96:be:85:e4
     capabilities: ethernet physical wireless
     configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
     description: Ethernet interface
     physical id: 3
     logical name: pan0
     serial: ae:00:36:80:e0:fe
     capabilities: ethernet physical
     configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

>iwconfig
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

>ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:b5:48:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:be:85:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-96-BE-85-E4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Ayuthia on 2009-04-23
Are you able to scan for wireless sites?  Also are you using WEP/WPA?  Can you post the results of:
```
dmesg|grep b43
```

---

### Post by Greslore on 2009-04-23
No WEP/WPA enabled on my WAP.  I just have an SSID enabled.  Strange thing is that it does seem to scan for the WAP, and it stays at 0% connection signal, so I think it is a false positive?

>dmesg |grep bw43

[    3.325763] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   11.730151] b43-phy0: Broadcom 4306 WLAN found
[   22.624517] input: b43-phy0 as /devices/virtual/input/input9
[   22.652244] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   22.796245] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   22.885216] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   22.943370] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   23.100054] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   23.165916] Registered led device: b43-phy0::tx
[   23.165937] Registered led device: b43-phy0::rx
[   23.165958] Registered led device: b43-phy0::radio
[   23.180063] b43-phy0: Radio turned on by software
[ 4246.977382] input: b43-phy0 as /devices/virtual/input/input10
[ 4247.124282] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 4247.183232] Registered led device: b43-phy0::tx
[ 4247.183285] Registered led device: b43-phy0::rx
[ 4247.183336] Registered led device: b43-phy0::radio

---

### Post by Ayuthia on 2009-04-24
It might be a bug.  There is another person with your card that is having problems also:
[http://ubuntuforums.org/showthread.php?t=1134787](http://ubuntuforums.org/showthread.php?t=1134787)

I'll try to see if I can get my old Dell up and running to see if I can figure out what is happening.

---

### Post by Greslore on 2009-04-24
> **Ayuthia said:**
> It might be a bug.  There is another person with your card that is having problems also:
[http://ubuntuforums.org/showthread.php?t=1134787](http://ubuntuforums.org/showthread.php?t=1134787)

I'll try to see if I can get my old Dell up and running to see if I can figure out what is happening.

Your efforts are much appreciated and I am most obliged.  :)

---

### Post by Greslore on 2009-04-24
Got it working!

I finally found the problem was that in the bios, the wireless was set to "off".  On the D600 Dell laptops, you need to use FN-F2 to turn off/on the wireless nic.  But, there is no indicator light to show status.  And it seems that if you enable the wireless to ON via the FN-F2 combo, then only a reboot will allow Ubuntu to actually use it.

---

### Post by flapinux on 2009-07-30
Wow... I struggled with dif't driver versions for 2 hrs before coming across the Fn+F2 thing...  Wireless has never been turned off on this thing so I had no idea!  And you're right, there's no indicator light or anything... Thanks!

---

