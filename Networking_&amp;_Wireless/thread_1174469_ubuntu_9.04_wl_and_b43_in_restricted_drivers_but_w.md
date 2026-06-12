---
title: "ubuntu 9.04 wl and b43 in restricted drivers but wireless network not working"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by lalitgaur on 2009-05-31
hi 
I have both wl and b43 drivers appearing in the restricted drivers manager
and b43 is activated but i cannot get anything in the wireless networks which is deactivated

---

### Post by lalitgaur on 2009-05-31
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lshw -C network
```

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:79:1d:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=24.107.98.32 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:84:19:bb:49:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:19:7e:43:b5:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
iwconfig
```

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
sudo iwlist wlan0 scanning
```

wlan0     No scan results

```

---

### Post by Ayuthia on 2009-05-31
Can you post the results of the following:
```
dmesg|grep b43
lsmod|grep -e b43 -e wl
```

The first command will check and see if there are any error messages with the b43 module.  The next command will check to see if the wl module is enabled.  If it is, it could prevent the b43 module from working.

There could also be the possibility that NetworkManager is having some issues also and is not able to make the connection work.

---

### Post by lalitgaur on 2009-05-31
dmesg |grep b43
```

[    2.617776] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.617807] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   12.661076] b43-phy0: Broadcom 4311 WLAN found
[   26.980288] input: b43-phy0 as /devices/virtual/input/input9
[   27.032141] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.219280] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   27.264204] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   27.303646] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   27.497112] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   27.597673] Registered led device: b43-phy0::tx
[   27.597700] Registered led device: b43-phy0::rx
[   27.597737] Registered led device: b43-phy0::radio
[   27.617051] b43-phy0: Radio turned on by software
[   27.985318] b43-phy0: Radio hardware status changed to DISABLED
[   28.004072] b43-phy0: Radio turned on by software
[   28.004077] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  300.506802] b43-phy1: Broadcom 4311 WLAN found
[  304.873768] input: b43-phy1 as /devices/virtual/input/input10
[  304.964051] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  304.995871] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  305.075762] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  305.085964] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  305.224119] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  305.316644] Registered led device: b43-phy1::tx
[  305.316672] Registered led device: b43-phy1::rx
[  305.316706] Registered led device: b43-phy1::radio
[  305.336065] b43-phy1: Radio turned on by software
[  305.892105] b43-phy1: Radio hardware status changed to DISABLED

```
lsmod|grep -e wl -e b43
```
b43                   131484  0 
mac80211              217208  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ssb                    41220  2 b43,b44

```

---

### Post by Ayuthia on 2009-05-31
> [   28.004077] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
By any chance, have you checked to see if your wireless switch is turned on?

---

### Post by lalitgaur on 2009-05-31
> **Ayuthia said:**
> By any chance, have you checked to see if your wireless switch is turned on?The wifi light is glowing brightly.

---

### Post by Ayuthia on 2009-05-31
You can try the following:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
sudo modprobe b44
sudo ifconfig eth1 up

```
This set of commands will reload (not reinstall) your wired and wireless drivers.  I am just curious to see if the b43 module will work without the wired driver there.  The commands will unload the wired and wireless drivers, then it loads the wireless driver and sees if it can get it started.  After that, it will load the b44 driver.  If it does not work, you will need to reconnect your wired card through NetworkManager or else you can try:
```
sudo dhclient eth0
```If that does not work, you can reboot and your wired card should work again.

I also have a 4311 rev 01 card and just tried using the liveCD version of Ubuntu with it just to see if I can duplicate the issue (I am a Kubuntu user) and I was able to connect without any problems.  The only difference is that I do not have a Broadcom wired card.

---

### Post by lalitgaur on 2009-05-31
Uninstalling both b43 and wl and then activating b43 again and then rebooting seems to work.
Thanks a lot

---

### Post by Steogede on 2009-06-01
> **lalitgaur said:**
> The wifi light is glowing brightly.

The light might well be glowing, but the output from dmesg tells a different story.  I had the same problem with my HP DV8000 (DV8025ea).  After reading Ayuthia's post, I grepped dmesg and got a very similar output to lalitgaur.  So I tried pressing the button to turn the wireless off (actually it turned it on because it was already off), which fixed it.

---

