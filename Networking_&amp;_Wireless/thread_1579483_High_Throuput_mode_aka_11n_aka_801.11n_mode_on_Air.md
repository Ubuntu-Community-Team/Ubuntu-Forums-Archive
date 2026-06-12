---
title: "High Throuput mode aka 11n aka 801.11n mode on Airlink101 AWLL6075"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by rayperkins on 2010-09-21
I ordered this USB 802.11n dongle for about $10 and am having problems.

I found a firmware related bug (Bug #595455) that keeps it from working out of the box and got around that.  I put the right firmware file in the right place and CAN CONNECT TO B or G Access Points.

When I put my AP in N-Only mode, I can see the network, but cannot associate.  With the AP in mixed mode I can Associate using G.


The most interesting thing I found was something that had very few google hits (like 4).  In the dmesg output after associating I see the message:
Successfully associated, ht not enabled(0, 1)
The most interesting thing about this is the (0, 1) at the end.  I don't know what that means but it seems like a clue as to what the problem is.

This device uses the realtek chipset 8191S, there are conflicting reports on this, but all the reported possibilities seem to use the same driver from realtek (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625).

Here is some random info:

Dmesg output:
[85082.620027] usb 1-3: new high speed USB device using ehci_hcd and address 6
[85082.754586] usb 1-3: configuration #1 chosen from 1 choice
[85082.755456] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[85082.755460] ==>RtInPipes:3  
[85082.755465] ==>RtOutPipes:4  6  13  
[85082.755472] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[85082.755475] 1  1  0  0  2  2  2  2  2  
[85082.942556] Dot11d_Init()
[85082.969679] rtl819xU: --->FirmwareDownload92S()
[85082.969682] 
[85082.969689] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[85082.972735] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[85082.972738] 
[85082.972786] rtl819xU:--->FirmwareDownloadCode()
[85082.972788] 
[85082.972828] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[85082.974187] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[85082.974189] 
[85082.974193] rtl819xU:--->FirmwareDownloadCode()
[85082.974195] 
[85082.974231] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[85082.975553] rtl819xU:-->FirmwareEnableCPU()
[85082.975555] 
[85082.977552] rtl819xU:IMEM Ready after CPU has refilled.
[85082.977554] 
[85082.977558] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[85082.977560] 
[85082.977563] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[85082.977565] 
[85082.977568] rtl819xU:--->FirmwareDownloadCode()
[85082.977569] 
[85082.977575] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[85082.977802] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[85082.977804] 
[85082.978927] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[85082.978929] 
[85082.979928] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[85082.979930] 
[85082.980202] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[85082.980204] 
[85082.980207] rtl819xU:Firmware Download Success!!
[85082.980209] 
[85085.639777] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[85105.337004] Linking with TV,channel:4, qos:0, myHT:1, networkHT:1, mode:10
[85105.337017] Linking with TV,channel:4, qos:0, myHT:1, networkHT:1, mode:10
[85105.337217] =====>rtl8192SU_link_change 1
[85105.340028] <=====rtl8192SU_link_change 2
[85105.340037] ===>ieee80211_associate_procedure_wq(), chan:4
[85105.379987] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[85105.379991] 
[85105.394518] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[85105.394528] =================>ieee80211_authentication_req():auth->algorithm is 0
[85105.398524] rtl819xU:rtl8192_qos_association_resp: network->flags = 2,0
[85105.398527] 
[85105.398541] rtl819xU:qos active process with associate response received
[85105.398543] 
[85105.398551] Associated successfully
[85105.398555] Using G rates:108
[85105.398558] Successfully associated, ht not enabled(0, 1)
[85105.398562] =====>rtl8192SU_link_change 1
[85105.401143] =============>ARFR0+rate_index*4:0x5
[85105.409516] <=====rtl8192SU_link_change 2
[85105.409520] ============>normal associate
[85105.409855] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[85106.465840] =====>rtl8192SU_link_change 1
[85106.466911] <=====rtl8192SU_link_change 2
[85108.060185] =====>rtl8192SU_link_change 1
[85108.062430] =============>ARFR0+rate_index*4:0x5
[85108.071057] <=====rtl8192SU_link_change 2





sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:4f:47:c3:cc
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-1 ip=192.168.1.118 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:febe0000-febfffff memory:febdb000-febdbfff ioport:ecc0(size=32)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:2f:34:92:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.169 multicast=yes wireless=802.11b/g/n  li








iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     802.11b/g/n  li  ESSID:"TV"  
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:1C:F0:EA:EE:B3   
          Bit Rate=130 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-54 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by rayperkins on 2010-09-26
Bump.

---

