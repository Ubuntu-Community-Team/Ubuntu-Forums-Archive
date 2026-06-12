---
title: "Wireless connects, but doesn work (?),"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by FelixWinter on 2012-03-28
Hello. 

I use the 12.04 beta on a x220 thinkpad. If I should post this in the Ubuntu+1 forum, please tell me so. But I think the network/wireless forum is a good place to start.

When I try to connect to an encrypted wireless network, everything seems to work. I can connect, get an IP-Address and the correct DNS Route and Subnet Mask, etc.

But when I open a web browser, I can't access any site, not even my router. This is not a dns-Problem (I suppose) as it makes no difference whether I enter an URL or an IP-Address.

I tried nm-tool and got the following output

```

- Device: wlan0  [MyNetwork] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        08:11:96:51:EA:58

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

```sudo iwconfig results in:
```
wlan0     IEEE 802.11abgn  ESSID:"MyNetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:08:9B:F6:09   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0
```and cat/proc/net/wireless results in: 
```

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   70.  -39.  -256        0      0      0      0     39        0

```sudo lshw -C network gives: ```
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 08:11:96:51:ea:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-20-generic firmware=17.168.5.3 build 42301 ip=192.168.2.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f2500000-f2501fff
```I think the packages are somehow discarded, maybe the encryption does not work.  Do you have any idea what I could do? 

Thanks.

Felix

---

### Post by cybpabeofm on 2012-03-28
Try a different browser such as chrome for ubuntu

---

### Post by FelixWinter on 2012-03-28
Solved it. 

Actually, there still seems to be a bug in the way, wireless-n connections are handled. The bug is described here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836250](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836250)

Disabling the n-driver did the trick.

Nevertheless, thanks.

---

