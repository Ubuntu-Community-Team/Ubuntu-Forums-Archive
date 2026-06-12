---
title: "AR5001 driver"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by louisgonick on 2011-07-11
I installed 11.04 some time ago. I got my printer to work, but I have tried to use wireless and I cant. I can perfectly connect using a wired connection but on the network menu in the taskbar it tells me that wireless is turned off by hardware switch. I am suspecting that I don't have the drivers for my atheros wireless card, but when I click on additional driers it tells me that there are no drivers to download. Any clues on how to configure my wireless card to work with natty?

---

### Post by sakishrist on 2011-07-11
I am kind of new to linux so I might not be of any help here, but could you please post what the result of iwconfig is? [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by louisgonick on 2011-07-11
> **sakishrist said:**
> I am kind of new to linux so I might not be of any help here, but could you please post what the result of iwconfig is? [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by sakishrist on 2011-07-11
It is the same output I get when I turn off my wifi from the HW  switch ... so I doubt it is a driver matter!

Anyway, as I said, I am new so I can not think of anything else that can be the cause of this :( . I will leave it to to the experts.

Good luck!

---

### Post by louisgonick on 2011-07-12
I have a compaq cq60 with an atheros wireless card. I have posted many times on this forum asking for help but nobody answers... I have tried almost everything, and yet nothing works. With windows it works pretty good but with natty its a pain in the ***. I've spent almost 2 hours already trying to find a solution and nothing. Is anybody out there willing to help me???

---

### Post by linuxman94 on 2011-07-12
Please don't create multiple threads on the same topic.  You'll get help, just be patient:)

Could you post the results of these commands?

```
sudo lshw
sudo iwconfig
sudo lspci
```

---

### Post by louisgonick on 2011-07-12
> **linuxman94 said:**
> Please don't create multiple threads on the same topic.  You'll get help, just be patient:)

Could you post the results of these commands?

```
sudo lshw
sudo iwconfig
sudo lspci
```

lshw:
```
 description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:16:77:19:6d
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:92600000-936fffff ioport:91500000(size=16777216)
           *-network DISABLED
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wifi0
                version: 01
                serial: 00:24:2b:e5:00:33
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
                resources: irq:17 memory:92600000-9260ffff

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by linuxman94 on 2011-07-12
It should be working.  What does network manager say?

---

### Post by louisgonick on 2011-07-12
> **linuxman94 said:**
> It should be working.  What does network manager say?

wireless is disabled by hardware switch

---

### Post by linuxman94 on 2011-07-12
Are you sure the hardware switch is on?

---

### Post by louisgonick on 2011-07-12
> **linuxman94 said:**
> Are you sure the hardware switch is on?

The thing is that with windows I've had times in which I press the button to turn wifi on and it doesn't turn on. A little popup appears telling me wireless is disabled, but at least i get a response. In natty I press the button for like 10 minutes and nothing. Is there a way to turn it on through software?

---

### Post by wildmanne39 on 2011-07-12
Hi, this looks like what you need to get you going, read carefully it can be confusing.
[http://ubuntuforums.org/showthread.php?t=1790779](http://ubuntuforums.org/showthread.php?t=1790779)

---

### Post by linuxman94 on 2011-07-12
@wildmanne That is probably gonna help in the future but we need to figure out why network manager says the hardware switch is off.

OP: If you right click on network manager, is there a check next to enable wireless?

---

### Post by louisgonick on 2011-07-12
> **linuxman94 said:**
> @wildmanne That is probably gonna help in the future but we need to figure out why network manager says the hardware switch is off.

OP: If you right click on network manager, is there a check next to enable wireless?

@wildmanne I tried to run the 1st line in root and it tells me this: ```
svn: invalid option: 
Type 'svn help' for usage
```

@linuxman94 yes there is that option but I cant click on it

---

### Post by wildmanne39 on 2011-07-12
Hi, that is one of the things that link address, they unintalled network manager because it does not work with that card. and replaced it with wicd.

---

### Post by louisgonick on 2011-07-12
> **wildmanne39 said:**
> Hi, that is one of the things that link address, they unintalled network manager because it does not work with that card. and replaced it with wicd.

I already have wicd and it tells me that there are no wireless networks found

---

### Post by linuxman94 on 2011-07-12
When you ran the svn command, did you copy and paste it?

EDit: remove the "- madwifi" part and it should work

---

### Post by louisgonick on 2011-07-12
> **linuxman94 said:**
> When you ran the svn command, did you copy and paste it?

yup

---

### Post by louisgonick on 2011-07-12
> **linuxman94 said:**
> When you ran the svn command, did you copy and paste it?

EDit: remove the "- madwifi" part and it should work

I'm sorry but its really late at night. And i'm half asleep. I tried skipping the wicd part and I get this: ```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'ath5k'
WARNING: /etc/modprobe.d/ndiswrapper line 1: ignoring bad line starting with 'sudo'
root@louis-Compaq-Presario-CQ60-Notebook-PC:~# modprobe ath_pci
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'ath5k'
WARNING: /etc/modprobe.d/ndiswrapper line 1: ignoring bad line starting with 'sudo'

```

can somebody just tell me what to type?

---

### Post by lisati on 2011-07-12
Threads merged

---

### Post by louisgonick on 2011-07-12
I already updated the drivers in windows and now it works fine on windows. But Windows tells me that I have a AR5007 not a 5001.

---

