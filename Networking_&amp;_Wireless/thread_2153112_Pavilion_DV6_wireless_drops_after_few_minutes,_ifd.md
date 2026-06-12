---
title: "Pavilion DV6 wireless drops after few minutes, ifdown/up needed to reconnect"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by nick4mony on 2013-06-10
I'm trying to use Lucid on a HP Pavilion DV6. When my daughter logs in and runs a few applications, the wireless networking stops working after 5-10 minutes, and doesn't restart on its own. It requires a sequence of [font=courier]sudo ifdown wlan0[/font] and [font=courier]sudo ifup wlan[/font] to get the networking up and running again. It also stops working if we flip the lid to put it to sleep - the networking does not recover when woken up, until we run [font=courier]sudo ifdown wlan0[/font] and [font=courier]sudo ifup wlan0[/font] . It works OK when I log in. 

The system has a Ralink wireless chipset, and because of prior problems, I have removed Network-Manager, then tried and removed wicd (because it hosed all networking including ethernet), and now have it configured in a manually edited [font=courier]/etc/networking/interfaces[/font] .

Details (from following this [thread]6183681[/thread] + some extras)

**Machine type:** HP Pavilion DV6-3131TX NB WIN7 XC8892 (as listed on receipt)

```
$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
**02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

$ lsusb
Bus 002 Device 005: ID 0408:03b2 Quanta Computer, Inc. 
Bus 002 Device 004: ID 138a:0005 DigitalPersona, Inc 
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0159 Realtek Semiconductor Corp. 
**Bus 001 Device 003: ID 148f:1000 Ralink Technology, Corp. **
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lspci -s 02:00 -nn
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

$ sudo lspci -s 02:00 -vv
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Hewlett-Packard Company Device 1453
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at c3400000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number e0-2a-82-19-47-32-00-00
	Kernel driver in use: rt3090
	Kernel modules: rt3090sta

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr e0:2a:82:19:47:32  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e22a:82ff:fe19:4732/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1599150 (1.5 MB)  TX bytes:44249 (44.2 KB)
          Interrupt:16 
*No real difference in output when working or not working*

$ iwconfig
wlan0     RT2860 Wireless  ESSID:"tinakori"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:04:ED:DB:AC:ED   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-41 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
*No real difference in output when working or not working*

$ lsmod     ## extract
Module                  Size  Used by
rt3090sta             751243  1 

$ dmesg | grep 'rt[23]'
[   12.411592] **rt3**090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   12.458049] **rt3**090 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.458123] **rt3**090 0000:02:00.0: setting latency timer to 64
[   12.829328] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== **rt2**8xx_init, Status=0
[   12.831439] ====> **rt3**0xx Read PowerLevelMode =  0x3.
[   12.831441] ====> **rt3**0xx F Write 0x83 Command = 0x3.
[   16.396355] **rt2**8xx_close call RT28xxPciAsicRadioOff fail !!
[   16.525613] <==== **rt2**8xx_init, Status=0
[   16.525865] ====> **rt3**0xx Read PowerLevelMode =  0x3.
[   16.525866] ====> **rt3**0xx F Write 0x83 Command = 0x3.

$ dmesg | grep 'rt[23]'    ## Additional dmesg output after putting to sleep and waking up again
...
[ 1596.642423] **rt3**090 0000:02:00.0: PCI INT A disabled
[ 1599.033783] **rt3**090 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1599.066331] <==== **rt2**8xx_init, Status=0
[ 1599.066567] ====> **rt3**0xx Read PowerLevelMode =  0x3.
[ 1599.066568] ====> **rt3**0xx F Write 0x83 Command = 0x3.

$ dmesg     ## [no grep] Additional dmesg output after ifdown/ifup sequence
...
[ 2628.821077] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 421
[ 3923.954669] RX DESC ffff88003784d000  size = 2048
[ 3923.954842] <-- RTMPAllocTxRxRingMemory, Status=0
[ 3923.958135] Read file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed(errCode=0)!
[ 3923.958142] 1. Phy Mode = 0
[ 3923.958144] 2. Phy Mode = 0
[ 3923.958147] NVM is Efuse and its size =2d[2d0-2fc] 
[ 3923.960091] 3. Phy Mode = 0
[ 3923.962625] MCS Set = 00 00 00 00 00
[ 3923.980714] <==== **rt2**8xx_init, Status=0
[ 3923.980820] 0x1300 = 000a4260
[ 3923.980846]  AUX_CTRL = 0x                            1d42
[ 3923.980853]  Read AUX_CTRL = 0x1d42
[ 3923.980858]  Write AUX_CTRL = 0x1d42
[ 3923.980862]  OSC_CTRL = 0x3ff11
[ 3923.981016] ====> **rt3**0xx Read PowerLevelMode =  0x3.
[ 3923.981017] ====> **rt3**0xx F Write 0x83 Command = 0x3.
[ 3928.947313] ERROR!!!  , b**rt3**0xxBanMcuCmd = 1, Read BBP 3 
[ 3928.947320] ERROR!!!   b**rt3**0xxBanMcuCmd = 1. Write BBP 3 
[ 3930.051478] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 407
[ 3930.051740] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[ 3934.744415] wlan0: no IPv6 routers present

$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: e0:2a:82:19:47:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 ip=192.168.1.4 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:c3400000-c340ffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 64:31:50:60:ac:1f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:c1404000-c1404fff(prefetchable) memory:c1400000-c1403fff(prefetchable) memory:c1410000-c141ffff(prefetchable)

$ iwlist scan wlan0       ## extract, for the AP of interest
                    ESSID:"tinakori"
                    Mode:Managed
                    Channel:4
                    Quality:100/100  Signal level:-31 dBm  Noise level:-83 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
*No real difference in output when working or not working*



```
**Output from lsb_release -d:** Description:	Ubuntu 10.04.4 LTS
**Output from uname -mr:** 2.6.32-47-generic x86_64

**Setup**
I uninstalled network-manager (and wicd) then followed the instructions in [thread]571188[/thread] to manually configure the wifi (with WPA2-PSK) into [font=courier]/etc/networking/interfaces[/font] . I also had to edit the [font=courier]/etc/init/networking.conf[/font] upstart job to add [font=courier]/sbin/ifdown -a[/font] in the pre-start section, to get wireless networking to come up on boot. I can get both of these files if required.

**When the network fails** ... I haven't tried [font=courier]sudo /etc/init.d/networking restart[/font], but using if{down,up} -v wlan0 gives this output
```
$ sudo ifdown -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/upstart
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1724
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/e0:2a:82:19:47:32
Sending on   LPF/wlan0/e0:2a:82:19:47:32
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 1526).
wpa_supplicant: removing /var/run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid

$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /var/run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "tinakori" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP -- OK
wpa_supplicant: wpa-group CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/e0:2a:82:19:47:32
Sending on   LPF/wlan0/e0:2a:82:19:47:32
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPOFFER of 192.168.1.4 from 192.168.1.254
DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.254
bound to 192.168.1.4 -- renewal in 17852 seconds.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
ssh stop/waiting
ssh start/running, process 3155
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
```

**Details of usage**
The wireless fails to wake up from sleep.

The wireless fails within 5-10 minutes when my daughter logs in and uses these applications
[list]
[*]Altered desktop theme (System -> Preferences -> Appearance, Custom - based on a downloaded one, similar to clearlooks)
[*]Firefox - two windows
[*]Chromium - two windows
[*]Skype
[*]Terminal - with a ping command pinging the router.
[/list]She can execute [font=courier]sudo ifdown wlan0[/font] and [font=courier]sudo ifup wlan[/font] courtesy of entries in /etc/sudoers . This gets her networking going again for a few more minutes.

The wireless does not fail when I log in and use these applications
[list]
[*]Default desktop theme
[*]Firefox
[*]Terminal - various tasks
[/list]

What should I try next?

---

