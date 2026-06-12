---
title: "Ubuntu 9.10 / Dell latitude D630 / Wireless problem"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by nimish.bhargava on 2010-01-11
Hi

I have recently installed Ubuntu 9.10 but am unable to connect to any of the wireless networks. Network manager does not shows any of the available wireless networks and upon clicking the network connection icon, under Wireless networks category it shows "Device not ready".

Following are the results of some of the commands :

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


**lspci**

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

**iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.


**lshw -C network**

*-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:a4:0b:01
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5755m-v3.29 ip=172.16.26.232 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:fe7f0000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:69:02:78:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Let me know if any other information is also required.

Thanks
Nimish

---

### Post by homeuser1 on 2010-01-11
see what the output of "rfkill list" is.

I bet you have a hard block like I do.  I have been trying to find a solution that works to fix this.

[HTML]dell@dell-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
dell@dell-laptop:~$ 
[/HTML]

---

### Post by NewfieRich on 2010-02-14
Hello, I am having the same issue as nimish.bhargava. My computer is a dell latitude 830d with a NetXtreme BCM5755M Gigabit Ethernet PCI Express Card. This is the first time I have had this problem, 9.04 had worked as well as older versions of ubuntu.

---

### Post by NewfieRich on 2010-02-15
Update: I tried 9.04 with a fresh install again and everything worked fine. I then updated to 9.10 via update manager and rebooted using new kernel (2.6.31-16-generic) and network manager no longer picks up any wireless networks. I rebooted through grub using 2.6.28-11 kernel and wireless works but my touch pad does not... go figure. Anyone have any insight on what to do? (I know I can just run Ubuntu 9.04, but feel that this bug should be able to be resolved somehow.)

---

### Post by morty9352 on 2010-03-06
I was having the same issue with the D630 wireless card using 9.10 Karmic.  I fixed it by going to:

   [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and downloading the driver.  I followed the README carefully, using sudo where # prompt was mentioned.

---

### Post by morty9352 on 2010-03-07
I noticed after each reboot, the wireless is not detected.  I do the following at it works again:

   $ sudo lsmod | grep "b43\|ssb\|wl"

I then see b43 and ssb and do:

  $sudo modprobe -r b43
  $sudo modprobe -r ssb
  $sudo lib80211_crypt_tkip
  $sudo insmod ~/hybrid.wl/wl.ko

The wireless then automatically connects.

Can anyone tell me how to make this permanent?

Thanks.

---

### Post by avguy on 2010-03-07
try using the ndisgtk package from Synapatic Package Manager under System-Administration. Have the Ubuntu disk inside the computer. If it's not in synapatic, get it from packages.ubuntu.org

---

### Post by bkratz on 2010-03-07
> **morty9352 said:**
> I noticed after each reboot, the wireless is not detected.  I do the following at it works again:

   $ sudo lsmod | grep "b43\|ssb\|wl"

I then see b43 and ssb and do:

  $sudo modprobe -r b43
  $sudo modprobe -r ssb
  $sudo lib80211_crypt_tkip
  $sudo insmod ~/hybrid.wl/wl.ko

The wireless then automatically connects.

Can anyone tell me how to make this permanent?

Thanks.

Posts 13 and 14 of this thread may provide some guidance.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533&page=2)

---

### Post by morty9352 on 2010-03-07
> **bkratz said:**
> Posts 13 and 14 of this thread may provide some guidance.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533&page=2)


thanks for the quick response avguy and bkratz.  I thought I had covered all of that, but I discovered that I was missing bmcwl-kernel-source.  I got it from Synaptic, then followed the rest of the instructions:

    sudo dpkg-reconfigure bcmwl-kernel-source
    sudo modprobe -r b43 ssb wl
    sudo modprobe wl

Now it works after restarts.

Thanks again.

---

