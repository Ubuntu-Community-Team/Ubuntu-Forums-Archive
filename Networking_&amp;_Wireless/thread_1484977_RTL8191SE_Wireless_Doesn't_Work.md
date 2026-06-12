---
title: "RTL8191SE Wireless Doesn't Work"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by nsteger123 on 2010-05-16
I have tried many guides on getting this working. NDISWrapper, and native linux driver.
Here is my **'iwconfig'**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**'ifconfig'**
```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:3a:c9:d7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe3a:c9d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4213501 (4.2 MB)  TX bytes:333892 (333.8 KB)
          Interrupt:33 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7541946 (7.5 MB)  TX bytes:7541946 (7.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:a9:fd:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:ffffc9001ae60000-ffffc9001ae60100 
```

**'lspci'**
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
03:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

My System: Toshiba A505-S6004
Ubuntu Lucid Lynx 64-Bit with All Updates.
4GB DDR3 RAM
Core i3
RTL8191SE - Wireless Card

I really don't know what to do now. If you need any other information i will gladly post it.

---

### Post by maestrobwh1 on 2010-05-16
[https://launchpad.net/~matt-price/+archive/mattprice](https://launchpad.net/~matt-price/+archive/mattprice)

add the ppa to your software list using synaptic / kpackagekit
search for rtl8192se-dkms and install it.

It should then make network-manager see any wireless signals.  If not, reboot.

You could build the driver from the realtek source,* but the issue there is that every time your kernel upgrades, you need to rebuild the driver.  Using the above, it just rebuilds for you.

I find it odd that the kernel driver makes the interface show up, but not actually work.

If you need more information, go over to the eeeuser forum, scroll down to 1201x and in that topic, find "linux on the 1201N."

*If you are one of the rare people that runs Ubuntu from bootable usb stick using a persistence file, this is the only thing I could find that would make it work, and you have to install the header file relating to the kernel using "uname -r" and you have to install build-essential.  This eats up a large part of the persistence file.

---

### Post by nsteger123 on 2010-05-16
I don't run it off a USB stick. I have installed to a partition.
I built the driver from the Realtek Source, I have tried ndiswrapper.

I just tried your solution, and that didn't work either. When i click the network button thing on the top bar, under the Wireless Section it says 'disabled' in grey letters.

EDIT: In /etc/acpi there is a file named 'tosh-wireless.sh"
Here are the contents:
```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/state-funcs

if isAnyWirelessPoweredOn; then
    if [ -x /usr/bin/toshset ]; then
        if `toshset -bluetooth | grep -q attached`; then
                toshset -bluetooth off
                toggleAllWirelessStates
        else
                toshset -bluetooth on
        fi
    else
	toggleAllWirelessStates
    fi
else
        toggleAllWirelessStates
fi
```

Would that have anything to do with it?

Here is my 'lshw -C network'
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:3a:c9:d7
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:34 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:b6:a9:fd:45
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=49 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:10 ioport:3000(size=256) memory:d6400000-d6403fff

```

---

### Post by nsteger123 on 2010-05-16
Bump, please help!

---

### Post by nsteger123 on 2010-05-16
Bump!

---

