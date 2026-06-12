---
title: "Acer Aspire One wireless disabled"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by jonesy29847 on 2009-04-24
Hello,

I have an Aspire One and I replaced linpus with ubuntu 8.10, I am having trouble with the wireless network adaptor.  I am getting very close, I think all I have to do is find a way to enable it.

I am also concerned that I have more than one driver installed.

The code below is my last session in terminal.

Thanks you in advance for your help.

```
tom@tom-laptop:~$ sudo iwconfig

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


tom@tom-laptop:~$ sudo lshw

  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:23:15:49:a7:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

tom@tom-laptop:~$ lspci -v | grep Ethernet
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


```

---

