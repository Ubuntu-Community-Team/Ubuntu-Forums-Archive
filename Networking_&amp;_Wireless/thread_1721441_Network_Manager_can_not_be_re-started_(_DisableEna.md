---
title: "Network Manager can not be re-started ( Disable/Enable )"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by Minimal Hank on 2011-04-04
**Adapter:** Ralink RT3090 802.11b/g/n Wi-Fi

Basically, whenever I disable it, I can't get it to turn back on. If I hit Enable, it says *device is not ready*.

What can I do to make it work ?

[COLOR=Gray]** I assume I'm not the only one experiencing this problem ..[/COLOR]

---

### Post by matt_symes on 2011-04-04
Hi

> **Minimal Hank said:**
> **Adapter:** Ralink RT3090 802.11b/g/n Wi-Fi

Basically, whenever I disable it, I can't get it to turn back on. If I hit Enable, it says *device is not ready*.

What can I do to make it work ?

[COLOR=Gray]** I assume I'm not the only one experiencing this problem ..[/COLOR]

Could you please clarify how you are disabling it ? Is it through network manager (wicd ?) or via networking ?

Please post the output of (from a terminal and it's case sensitive)

```
lspci -nnk | grep Network
```

Also post the output of this command before and after disabling/enabling.

```
sudo lshw -C network
```

Enter you password. It will not be echoed to the screen. This is normal. Please wrap all this output between code tags. To do this highlight the text wrap and press the # button above where you type.

Kind regards

---

### Post by Minimal Hank on 2011-04-04
```
03:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

``````
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 90:fb:a6:b1:8f:49
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=46.109.96.142 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:2000(size=256) memory:b0410000-b0410fff(prefetchable) memory:b0400000-b040ffff(prefetchable) memory:b0420000-b043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:b2400000-b240ffff
``````
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Any ideas on what's going on here ?

I tried to set ESSID with:
```
iwconfig wlan0 essid HP
```but it failed with *SIOCSIFFLAGS operation not permitted*.

---

### Post by matt_symes on 2011-04-04
Hi

```
*-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:b2400000-b240ffff
```

I assume this was after you tried to re-enable networking? The interface is still disabled and that is causing the problem.

Does 

```
sudo ifconfig wlan0 up
```

get you any nearer ?

```
iwconfig wlan0 essid HP
<SIOCSIFFLAGS operation not permitted>
```

This requires admin privilages.

```
sudo iwconfig wlan0 essid HP
```

Not quite sure why it's happening but have you tried dropping and upping networking or reloading the kernel modules as well ? If you need instruction on this post back.

If one of those 3 ideas fixes it, it may provide a clue to what is going on.

The kernel message buffer may also provide clues.

Kind regards

---

### Post by Minimal Hank on 2011-04-04
> **matt_symes said:**
> Hi

```
*-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:b2400000-b240ffff
```I assume this was after you tried to re-enable networking? The interface is still disabled and that is causing the problem.

Does 

```
sudo ifconfig wlan0 up
```get you any nearer ?

```
iwconfig wlan0 essid HP
<SIOCSIFFLAGS operation not permitted>
```This requires admin privilages.

```
sudo iwconfig wlan0 essid HP
```Not quite sure why it's happening but have you tried dropping and upping networking or reloading the kernel modules as well ? If you need instruction on this post back.

If one of those 3 ideas fixes it, it may provide a clue to what is going on.

The kernel message buffer may also provide clues.

Kind regards

I can't up/down it as well. Not sure what's wrong with it but everything I try fails .. 

How do I reload ( as I don't know which one exactly, I assume all of them ) kernel modules ?

---

### Post by matt_symes on 2011-04-04
Hi

Try this

```
sudo modprobe -r rt3090
sudo modprobe rt3090
```

Does that enable networking ?

Also, type this

```
lspci -knn | grep -A3 Network
```

This will give a bit more info than the last lspci command you typed and is what i meant to ask you to post. It's late here.

This will return output similar to

```
matthew@matthew-laptop:~$ lspci -knn | grep -A3 Network
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
        Kernel driver in use: ath9k
        Kernel modules: ath9k
```

This is from mine. If the kernel driver is different than the kernel module post back and tell me.

Kind regards

---

