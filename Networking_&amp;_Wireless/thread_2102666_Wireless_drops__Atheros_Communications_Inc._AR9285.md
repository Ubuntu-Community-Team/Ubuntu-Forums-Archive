---
title: "Wireless drops : Atheros Communications Inc. AR9285/Ubuntu 12.04/Asus N53SM"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by iamchrismoran on 2013-01-07
At unpredictable intervals my laptop drops its wireless. Initially it will continue to try to connect to the network and ask for the password, but eventually gives up. When I select the network icon, under Wireless Networks is says "device not ready".
Restarting returns the wireless, but randomly it shuts down again.
This has only been happening for about 2 weeks.
This system is dual-boot with Windows 7 (for gaming) and I do not have the same wireless issues within windows.
Below I'm including the suggested output and information.
Thanks for your help,
Chris

System: Asus N53SM laptop
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
When dropped, ifconfig returns no wireless
iwconfig returns:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lsmod | grep "wlan_module_name" returns nothing

dmesg returns the following:
[ 3523.854471] ath: Failed to stop TX DMA, queues=0x10f!
[ 3523.867927] ath: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 3523.867930] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 3523.987634] ath: Chip reset failed
[ 3523.987638] ath: Unable to reset channel (2437 MHz), reset status -22
[ 3525.497317] ath: Failed to wakeup in 500us

and basically repeats the wakeup and additional attempts.

sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:08:ca:34:58:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-35-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:ddc00000-ddc0ffff

iwlist scan
wlan0     Failed to read scan data : Network is down

lsb_release -d
Description:    Ubuntu 12.04.1 LTS

sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

### Post by iamchrismoran on 2013-01-16
Update: realized that it IS happening in Windows 7 as well. The big difference is that in Windows I can click on the broken wifi icon and tell it to fix the situation, which apears to be restarting the wireless adapter. It's a temporary fix, but better than asus telling me I have to send it in, that they will likely do an OS recovery (pretty much screwing up my months and months of setup for the dual boot system.

BUT... I do not see any comparable method in linux/ubuntu. It's like a hardware kickstart or something. Is there something similar in linux?

---

