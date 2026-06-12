---
title: "hardy wireless network unclaimed"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by mngsailing on 2009-01-03
Somebody please give me a hand with my wireless connection 

mng@mng-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:45:ba:c3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.126 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

mng@mng-laptop:~$ dmesg | grep -e ath -e rror
[   17.841762] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.488659] usb 2-2: device not accepting address 2, error -71

mng@mng-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

mng@mng-laptop:~$ lspci -v | grep subordinate
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32

mng@mng-laptop:/etc/modprobe.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mng@mng-laptop:~$ uname -r
2.6.24-22-generic

---

### Post by wmdiem on 2009-01-03
it looks like it doesn't have a driver
do you know whether you have madwifi or ndiswrapper installed (modprobe -l)?
if one is, you can start it with modprobe

---

### Post by melojo on 2009-01-03
have a look here

[http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)

---

### Post by mngsailing on 2009-01-03
Thanks for the responses.  

There is some madwifi around like this:
/lib/modules/2.6.24-22-generic/madwifi/ath_rate_sample.ko
/lib/modules/2.6.24-22-generic/madwifi/ath_rate_amrr.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_xauth.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_scan_sta.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_scan_ap.ko
/lib/modules/2.6.24-22-generic/madwifi/ath_rate_onoe.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_acl.ko
/lib/modules/2.6.24-22-generic/madwifi/ath_rate_minstrel.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_wep.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_ccmp.ko
/lib/modules/2.6.24-22-generic/madwifi/wlan_tkip.ko
/lib/modules/2.6.24-22-generic/madwifi/ath_pci.ko
/lib/modules/2.6.24-22-generic/volatile/ath_hal.ko

But
mng@mng-laptop:~$ modprobe madwifi
FATAL: Module madwifi not found.

I didn't realize madwifi was a driver.  I thought only ath9k was.  I will see if synaptic can find it.  
Synaptic got the madwifi tools but no madwifi driver. 
              Is compat-wireless relevant?

---

### Post by wmdiem on 2009-01-04
sorry 
the madwifi driver is ath_pci

---

### Post by mngsailing on 2009-01-04
I think it was compat-wireless that solved this.  It seems to have left me with an ath9k.
Along the way I needed to add the linux-restricted repository 

Now I have a whole lot of compat-wirelesses on my desktop like
.sh
.tar.bz2
.old
.deb   and
.tar.gz

Can I get rid of them all, or should I keep the one I most likely used ? --
compat-wireless-2.6-old
?

Thanks again.

---

