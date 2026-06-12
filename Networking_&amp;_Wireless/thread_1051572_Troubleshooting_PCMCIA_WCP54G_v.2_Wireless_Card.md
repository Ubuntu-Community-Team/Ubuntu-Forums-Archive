---
title: "Troubleshooting PCMCIA WCP54G v.2 Wireless Card"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by helium3 on 2009-01-26
I'm a complete linux n00b and I just installed 8.10 on my laptop. Everything's working fine so far but there's something wrong with my wireless connection. I would like some assistance in fixing this problem.

From what I can tell from my research in the forums I'm probably going to need to install Ndiswrapper or something. For now, I just need some help walking through what's going wrong.

I know the wireless card works. The machine is an XP/Linux dual boot and when in XP the card works just fine.

Here's the info I've got:

Machine: Dell Inspiron 1000 (Dual boot with XP and Ubuntu 8.10)
Wireless Brand: Linksys
Model: WPC54G ver.2
Chipset: Texas Instruments ACX 111

I'm working on getting the rest of the information that [this thread]("http://ubuntuforums.org/showthread.php?p=6183681") says I should have.

---

### Post by helium3 on 2009-01-26
Here's the rest of the info.

> 
**$ ifconfig wlan0**
wlan0     Link encap:Ethernet  HWaddr 00:12:17:14:7a:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17


> 
**$ iwconfig wlan0**
wlan0     IEEE 802.11b+/g+  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=31/100  Signal level=3/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0


> 
**$ lsmod | grep 'pcmcia'**
pcmcia            43052   0
pcmcia_core       43412   3 pcmcia,yenta_socket,rsrc_nonstatic


> 
**dmesg | grep wlan0**
[   25.537249] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-7-generic
[  158.052170] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  338.064924] wlan0: tx error 0x20, buf 00! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
[  338.064950] wlan0: tx error 0x20, buf 01! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
[  338.064963] wlan0: tx error 0x20, buf 02! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
[  338.064976] wlan0: several excessive Tx retry errors occurred, attempting to recalibrate radio. Radio drift might be caused by increasing card temperature, please check the card before it's too late!
[  338.064990] wlan0: tx error 0x20, buf 03! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
[  338.096235] wlan0: recalibrating radio
[  338.144040] wlan0: successfully recalibrated radio
[  735.644046] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
[  735.644060] wlan0: issue_cmd(cmd:0x0016) FAILED
[  761.516041] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
[  761.516056] wlan0: issue_cmd(cmd:0x0016) FAILED
[ 1103.568054] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
[ 1103.568069] wlan0: issue_cmd(cmd:0x0016) FAILED
[ 1327.564047] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x2000 irq_status:0x2000 timeout:49ms cmd_status:1 (Success)
[ 1327.564063] wlan0: issue_cmd(cmd:0x0016) FAILED


> 
**$ sudo lshw -C network**
  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:c2:22:89
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:12:17:14:7a:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:6d:4d:4a:34:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


> 
**$ iwlist scan | grep 'wlan0'**
wlan0     No scan results


> 
**$ lsb_release -d**
Description:	Ubuntu 8.10


> 
**$ uname -mr**
2.6.27-7-generic i686


> 
**$ sudo /etc/init.d/networking restart**
Uhhh . . . nothing happened. Was something supposed to happen?


---

