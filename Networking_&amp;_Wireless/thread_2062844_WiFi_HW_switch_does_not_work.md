---
title: "WiFi HW switch does not work"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by Kyslosh on 2012-09-25
Hello there :)

I just did clean install on my Lenovo E420s, everything seems work fine but wireless (again).

I can not turn on wireless by simple pressing hardware button (in my case combination of buttons fn* + f9)

*I switched buttons fn and lctrl in BIOS but I hope this won't be the issue.

ok some informations here :)

```
kyslik@KyslikNB:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 88:9f:fa:ff:c0:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:e2600000-e2603fff
```


pressing fn+f9

```
kyslik@KyslikNB:~$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

pressing fn+f9 again

```
kyslik@KyslikNB:~$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

my hardware is 

```
kyslik@KyslikNB:~$ sudo lspci | grep RTL
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

It seems when I press HW switch it turns on/off only BlueTooth (which I do not even use at all).

thanks for any advices

---

### Post by Kyslosh on 2012-09-28
bump

---

