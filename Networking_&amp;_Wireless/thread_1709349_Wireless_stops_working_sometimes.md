---
title: "Wireless stops working sometimes"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by ekeis98 on 2011-03-18
Hi folks,

I think I got an issue with the network-manager and the wireless function.

On my UBUNTU-10.10-netbook (details see at the end of this thread) the wireless connection stops working e.g. in case of 
- unplugging the power supply (and activation of gnome-power-properties ???), 
- reactivation after hibernation,
- reactivation after standby
- switching between different wlan-networks
Not always, but randomly very often.

Sometimes (!) you heal the wireless function if you disable networking via the network-manager and enable it again. The console command "sudo /etc/init.d/networking restart" does not work at any time.

You can make the wireless-function work if you completely reboot the system. This works everytime, but it is very annoying.

I don't want to use wicd, because I love the OpenVPN-plugin of the network-manager.

Does anybody else have this problem?
I've read a lot about advanced drivers. How do I install them? Or are they on my UBUNTU out-of-the-box?
Is there any help out there?

Thanks in advance for your help and the time you're spending to my problem.

Regards,
Oliver.


Details of my system and logs:

```

[B]sudo lspci
[/B]00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: RaLink RT2860

[B]sudo lshw -C network
[/B]  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:15:18:a5
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:d000(size=256) memory:ffd10000-ffd10fff memory:ffd00000-ffd0ffff memory:dfd00000-dfd1ffff
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:21:97:36:86
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-27-generic firmware=N/A ip=192.168.178.40 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:dfc00000-dfc0ffff

**sudo iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:81:3E:68   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**cat /etc/lsb-release **
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

**uname -sr**
Linux 2.6.35-27-generic

**syslog**
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0/wireless): connection 'Auto WLAN' has security, and secrets exist.  No new secrets needed.
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Config: added 'ssid' value 'WLAN'
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Config: added 'scan_ssid' value '1'
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Config: added 'psk' value '<omitted>'
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> Config: set interface ap_scan to 1
Mar 18 09:34:12 tuxnetbook NetworkManager[860]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Mar 18 09:35:13 tuxnetbook NetworkManager[860]: <warn> Activation (wlan0/wireless): association took too long.
Mar 18 09:35:13 tuxnetbook NetworkManager[860]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Mar 18 09:35:13 tuxnetbook NetworkManager[860]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar 18 09:35:13 tuxnetbook NetworkManager[860]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Mar 18 09:35:17 tuxnetbook NetworkManager[860]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Mar 18 09:35:17 tuxnetbook NetworkManager[860]: <warn> Activation (wlan0) failed for access point (WLAN)
Mar 18 09:35:17 tuxnetbook NetworkManager[860]: <info> Marking connection 'Auto WLAN' invalid.
Mar 18 09:35:17 tuxnetbook NetworkManager[860]: <warn> Activation (wlan0) failed.

```

---

### Post by Moskitostich on 2011-03-18
Hey
I have a quit similar problem. My internet connection also breaks randomly... really weird. And i think it happens more often lately. Sometimes just for a few minutes, but also for hours... which is really annoying. And there is no problem with the Internet itself, works fine on the other laptops. 
I have a Compaq Presario CQ56, quit new, and it runs with Ubuntu 10.10
Does anybody has an idea what causes that problem?

---

### Post by ekeis98 on 2011-03-23
So, I found a solution. In my case I've put the driver rt2800pci on the blacklist and restarted.

```
**sudo nano /etc/modprobe.d/blacklist.conf**

# http://forum.ubuntuusers.de/topic/wlan-treiber-in-10-10-instabil/2/
# WLAN is instable
blacklist rt2800pci
```So the driver rt2860 became active.

```
**lspci -nnk | grep -i net -A2**

02:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6890]
    Kernel driver in use: rt2860
```Standby, switching WLANs etc. is working now.

Thanks to the community.

Regards,
Oliver.

---

