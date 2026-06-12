---
title: "Wifi not working- Dell inspirion mini"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by sujitrjadhav on 2011-10-16
Here is output

sujit@sujit-Inspiron-1018:~$ rfkill unblock all
sujit@sujit-Inspiron-1018:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

sujit@sujit-Inspiron-1018:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
sujit@sujit-Inspiron-1018:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:36:fc:ab
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0f2c000-f0f2cfff memory:f0f18000-f0f1bfff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:f1:5b:11
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:f0100000-f0103fff

sujit@sujit-Inspiron-1018:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        5C:26:0A:36:FC:AB

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        1C:65:9D:F1:5B:11

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Point

sujit@sujit-Inspiron-1018:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

---

### Post by sujitrjadhav on 2011-10-16
Can anyone help me solve this problem?

---

### Post by sujitrjadhav on 2011-10-16
Hey guys I found the solution. This is third time that this has worked. twice on my dell mini and once on brothers acer aspire laptop. This is what I did. Started backtrack live cd and tried following command
```
airmon-ng stop wlan0

```
I dont know why wifi go in monitor mode automatically. Specially when I am using gnome shell and I flap down my mini without shutting it down, something like this happen.

---

### Post by Sargatana on 2012-01-26
I tried all of those, and none of  them worked.  Any other suggestions?:confused:

---

