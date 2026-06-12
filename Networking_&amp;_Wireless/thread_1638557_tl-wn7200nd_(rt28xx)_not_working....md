---
title: "tl-wn7200nd (rt28xx) not working..."
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by pejal1312 on 2010-12-05
using kernel 2.6.32-21-generic

have this hardware, n having trouble to enable it...

try so many ways to enable it, however none is working

$ lsmod |grep rt28
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
crc_ccitt               1339  1 rt2800usb

dmesg
[   15.929254] r8169: eth0: link up
[   15.931730] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
[   16.170288] ppdev: user-space parallel port driver
[   16.191294] ADDRCONF(NETDEV_UP): wlan4: link is not ready

also tried this one 
 	Code:
 	blacklist rt2800usb
blacklist rt2870sta[FONT=Verdana]
--not working for me either-[/FONT]

---

### Post by pejal1312 on 2010-12-06
i figure it out...

using this

rmmod rt2800usb
unplug the device, the plug in back
(need to this each time to use this device) conflicts?? :?:

sudo iwconfig wlan0
wlan0     RTxx70 Wireless  ESSID:"(T)"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1E:Ex:6x:5x:Dx   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:-87 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmseg

usbcore: deregistering interface driver rt2800usb
[  164.488065] phy1 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[  169.661367] usb 1-3: USB disconnect, address 4
[  176.956075] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  177.106685] usb 1-3: configuration #1 chosen from 1 choice
[  177.108822] 
[  177.108825] 
[  177.108827] === pAd = f84da000, size = 566748 ===
[  177.108829] 
[  177.108835] <-- RTMPAllocAdapterBlock, Status=0
[  177.413575] <-- RTMPAllocTxRxRingMemory, Status=0
[  177.417264] -->RTUSBVenderReset
[  177.417387] <--RTUSBVenderReset
[  177.697157] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
[  177.697165] 1. Phy Mode = 0
[  177.697169] 2. Phy Mode = 0
[  177.741343] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  177.764959] 3. Phy Mode = 0
[  177.772209] MCS Set = 00 00 00 00 00
[  177.815825] <==== RTMPInitialize, Status=0
[  177.817698] 0x1300 = 00073200
[  182.844600] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 735
[  183.515585] DRS: unkown mode,default use 11N 1S AP 
[  183.515597] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)


is this ok???

---

### Post by pejal1312 on 2010-12-07
root@ubuntu:~# echo rt3070sta >> /etc/modules
root@ubuntu:~# dmesg | grep -e rt2 -e rt3
[   11.929663] Registered led device: rt2800usb-phy0::radio
[   11.929680] Registered led device: rt2800usb-phy0::assoc
[   11.929698] Registered led device: rt2800usb-phy0::quality
[   11.930078] usbcore: registered new interface driver rt2800usb
[   11.933163] rt2870sta: module is from the staging directory, the  quality is unknown, you have been warned.
[   11.946445] usbcore: registered new interface driver rt2870
[   19.246529] rt2800usb 1-3:1.0: firmware: requesting rt2870.bin
[   60.494982] usbcore: deregistering interface driver rt2800usb
[   60.536026] p[COLOR=Red]hy0 -> rt2800usb_wait_wpdma_ready:  Error - WPDMA TX/RX busy, aborting.[/COLOR]

===something not right..i think===

@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070sta
cipher@ubuntu:~$ lsmod | grep rt
rt2870sta             461811  1 
rt2x00usb               9703  0 
rt2x00lib              27509  1 rt2x00usb
mac80211              204922  3 b43,rt2x00usb,rt2x00lib
agpgart                31724  2 ttm,drm
cfg80211              126485  3 b43,rt2x00lib,mac80211
led_class               2864  2 b43,rt2x00lib
parport                32635  2 ppdev,lp

dmesg

>[COLOR=Red] Error 2 opening  /etc/Wireless/RT3070STA/RT3070STA.dat[/COLOR]
[   65.472539] 1. Phy Mode = 0
[   65.472541] 2. Phy Mode = 0
[   65.516744] RTMPSetPhyMode: channel is out of range, use first  channel=1 
[   65.540364] 3. Phy Mode = 0
[   65.547611] MCS Set = 00 00 00 00 00
[   65.591102] <==== RTMPInitialize, Status=0
[   65.592728] 0x1300 = 00073200
[   70.614562] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 513
[   71.923741] DRS: unkown mode,default use 11N 1S AP 
[   71.923748] DRS: unkown mode (SupRateLen=0, ExtRateLen=0,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[   75.660792] wlan0: no IPv6 routers present
[   90.472148] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621
[  100.480097] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621
[  100.480504] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  100.596143] DRS: unkown mode,default use 11N 1S AP 
[  100.596153] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  119.708120] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621
[  159.706187] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 519
[  219.708110] ===>rt_ioctl_giwscan. 8( BSS returned, data->length  = 824
[  300.590307] DRS: unkown mode,default use 11N 1S AP 
[  300.590319] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  303.636596] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 622
[  399.706650] ===>rt_ioctl_giwscan. 7(7) BSS returned,  data->length = 722
[  519.706619] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621
[  530.070068] DeQueueRunning[0]= TRUE!
[  557.764323] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621
[  557.764702] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  557.840798] DRS: unkown mode,default use 11N 1S AP 
[  557.840807] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  575.950713] ===>rt_ioctl_giwscan. 7(7) BSS returned,  data->length = 723
[  575.951097] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  590.942212] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 513
[  600.952526] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 513
[  610.960216] ===>rt_ioctl_giwscan. 7(7) BSS returned,  data->length = 723
[  610.960593] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  620.968591] ===>rt_ioctl_giwscan. 4(4) BSS returned,  data->length = 412
[  630.976084] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 513
[  640.981168] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 519
[  640.981539] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  660.466174] ===>rt_ioctl_giwscan. 4(4) BSS returned,  data->length = 418
[  660.466557] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  664.420217] DRS: unkown mode,default use 11N 1S AP 
[  664.420225] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  677.539349] ===>rt_ioctl_giwscan. 7(7) BSS returned,  data->length = 723
[  677.540364] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  687.551384] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 519
[  687.551760] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  687.770333] DRS: unkown mode,default use 11N 1S AP 
[  687.770346] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  692.952602] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 513
[  702.959674] ===>rt_ioctl_giwscan. 8(8) BSS returned,  data->length = 899
[  702.960323] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  703.156621] DRS: unkown mode,default use 11N 1S AP 
[  703.156629] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  714.804082] ===>rt_ioctl_giwscan. 3(3) BSS returned,  data->length = 316
[  714.804452] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04]  (Channel=11)
[  714.903525] DRS: unkown mode,default use 11N 1S AP 
[  714.903537] DRS: unkown mode (SupRateLen=8, ExtRateLen=4,  MCSSet[0]=0x0, MCSSet[1]=0x0)
[  759.706196] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621
[  799.708779] ===>rt_ioctl_giwscan. 7(7) BSS returned,  data->length = 723
[  859.708139] ===>rt_ioctl_giwscan. 4(4) BSS returned,  data->length = 418
[  939.706684] ===>rt_ioctl_giwscan. 8(BSS returned, data->length =  835
[ 1039.708633] ===>rt_ioctl_giwscan. 8( BSS returned, data->length  = 836
[ 1159.711961] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 520
[ 1279.708606] ===>rt_ioctl_giwscan. 7(7) BSS returned,  data->length = 723
[ 1399.712098] ===>rt_ioctl_giwscan. 5(5) BSS returned,  data->length = 520
[ 1519.708811] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 633
[ 1639.708606] ===>rt_ioctl_giwscan. 6(6) BSS returned,  data->length = 621

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          
wlan0     RTxx70 Wireless  ESSID:"TPHEP (USMB)"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point:  00:1E:E5:63:57B   
          Bit Rate=1 Mb/s   
          RTS thr off   Fragment thrff
          Link Quality=70/100  Signal level:-93 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@ubuntu:~# airmon-ng


Interface    Chipset        Driver

wlan1        Broadcom    b43 - [phy1]
[COLOR=Red]wlan0        Unknown         usb[/COLOR]

i cant do packet injection :(


==im using lucid, kernel 2.6.32-21-generic==
adapter model==tl-wn7200nd

---

### Post by TBABill on 2010-12-07
What does the output of ```
lspci
``` and ```
lsusb
``` give? You appear to have both the Broadcom and Ralink driver? not sure...just want to check to see which you need. The mention of B43 is troubling.

---

### Post by Liorb on 2011-10-22
> **pejal1312 said:**
> i figure it out...

using this

rmmod rt2800usb
unplug the device, the plug in back
(need to this each time to use this device) conflicts?? :?:

sudo iwconfig wlan0
wlan0     RTxx70 Wireless  ESSID:"(T)"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1E:Ex:6x:5x:Dx   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:-87 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This worked for me fine for the past week, I've used this whenever i had issues with my wifi on my new Ubuntu box and it solved it. However, starting from today, after a reboot this is no longer working, when I type rmmod rt2800usb I get the following:

ERROR: Module rt2800usb does not exist in /proc/modules

Can anyone please help?

---

