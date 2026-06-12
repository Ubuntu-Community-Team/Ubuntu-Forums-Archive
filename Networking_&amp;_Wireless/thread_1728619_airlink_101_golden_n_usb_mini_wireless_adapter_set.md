---
title: "airlink 101 golden n usb mini wireless adapter setup"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by carv_13 on 2011-04-13
Hi,

I am newbie to ubuntu. I have ubuntu 10.04 LTS. I am trying to seutp wireless usb adapter. I am not really sure how to do that.  I am not really sure if the following info is relevant or not but I thought it might help someone to understand and help me out a bit faster.

I went through this thread

[http://ubuntuforums.org/showthread.php?t=1501914](http://ubuntuforums.org/showthread.php?t=1501914)

The following information are based on that...

[http://ubuntuforums.org/showthread.php?t=1501914](http://ubuntuforums.org/showthread.php?t=1501914)
_**aravind@ubuntu:~$ lsusb**_
Bus 002 Device 003: ID 1c4f:0002 SiGma Micro 
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

_**aravind@ubuntu:~$ dmesg | grep 819**_
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[   11.521370] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   11.537852] Linux kernel driver for RTL8192 based WLAN cards
[   11.903007] usbcore: registered new interface driver rtl819xU
[   13.549983] rtl819xU: --->FirmwareDownload92S()
[   13.549991] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.646540] rtl819xU:request firmware fail!
[   13.648224] rtl819xU:Firmware Download Fail!!a
[   13.664244] rtl819xU: --->FirmwareDownload92S()
[   13.664252] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.669831] rtl819xU:request firmware fail!
[   13.670870] rtl819xU:Firmware Download Fail!!a
[   13.670876] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   13.778238] rtl819xU: --->FirmwareDownload92S()
[   13.778246] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.793441] rtl819xU:request firmware fail!
[   13.793831] rtl819xU:Firmware Download Fail!!a
[   13.805990] rtl819xU: --->FirmwareDownload92S()
[   13.805999] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.812625] rtl819xU:request firmware fail!
[   13.813017] rtl819xU:Firmware Download Fail!!a
[   13.813024] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!



_**aravind@ubuntu:~$ sudo modprobe r8192s_usb**_

_**aravind@ubuntu:~$ iwconfig**_
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

_**aravind@ubuntu:~$ dmesg | grep -i firmware**_
[   13.549983] rtl819xU: --->FirmwareDownload92S()
[   13.549991] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.646540] rtl819xU:request firmware fail!
[   13.648224] rtl819xU:Firmware Download Fail!!a
[   13.664244] rtl819xU: --->FirmwareDownload92S()
[   13.664252] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.669831] rtl819xU:request firmware fail!
[   13.670870] rtl819xU:Firmware Download Fail!!a
[   13.778238] rtl819xU: --->FirmwareDownload92S()
[   13.778246] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.793441] rtl819xU:request firmware fail!
[   13.793831] rtl819xU:Firmware Download Fail!!a
[   13.805990] rtl819xU: --->FirmwareDownload92S()
[   13.805999] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.812625] rtl819xU:request firmware fail!
[   13.813017] rtl819xU:Firmware Download Fail!!a

Please let me know if you need any other information to help me out.

Thanks,
Aravind

---

### Post by chili555 on 2011-04-14
Please see here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Please get a temporary wired ethernet connection and open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

```Detach the ethernet cable, reboot and give us your report.

---

### Post by carv_13 on 2011-04-14
Thanks a bunch.....Did as you said...Wireless also seems to be working.

Here are the reports

aravind@ubuntu:~$ lsusb
Bus 002 Device 003: ID 1c4f:0002 SiGma Micro 
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    1.222819] usb-storage: device found at 5
[   11.577268] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   11.598586] Linux kernel driver for RTL8192 based WLAN cards
[   11.967373] usbcore: registered new interface driver rtl819xU
[   13.596733] rtl819xU: --->FirmwareDownload92S()
[   13.596742] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.747205] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[   13.747244] rtl819xU:--->FirmwareDownloadCode()
[   13.747284] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   13.748644] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[   13.748649] rtl819xU:--->FirmwareDownloadCode()
[   13.748691] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[   13.750372] rtl819xU:-->FirmwareEnableCPU()
[   13.752370] rtl819xU:IMEM Ready after CPU has refilled.
[   13.752377] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[   13.752381] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[   13.752385] rtl819xU:--->FirmwareDownloadCode()
[   13.752392] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[   13.752620] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[   13.753741] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[   13.754779] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[   13.755013] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[   13.755018] rtl819xU:Firmware Download Success!!
[  325.558128] =====>rtl8192SU_link_change 1
[  325.559179] <=====rtl8192SU_link_change 2
[  325.6[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    1.222819] usb-storage: device found at 5
[   11.577268] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   11.598586] Linux kernel driver for RTL8192 based WLAN cards
[   11.967373] usbcore: registered new interface driver rtl819xU
[   13.596733] rtl819xU: --->FirmwareDownload92S()
[   13.596742] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.747205] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[   13.747244] rtl819xU:--->FirmwareDownloadCode()
[   13.747284] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   13.748644] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[   13.748649] rtl819xU:--->FirmwareDownloadCode()
[   13.748691] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[   13.750372] rtl819xU:-->FirmwareEnableCPU()
[   13.752370] rtl819xU:IMEM Ready after CPU has refilled.
[   13.752377] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[   13.752381] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[   13.752385] rtl819xU:--->FirmwareDownloadCode()
[   13.752392] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[   13.752620] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[   13.753741] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[   13.754779] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[   13.755013] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[   13.755018] rtl819xU:Firmware Download Success!!
[  325.558128] =====>rtl8192SU_link_change 1
[  325.559179] <=====rtl8192SU_link_change 2
[  325.600399] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
00399] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[  325.616124] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[  325.621664] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[  325.621695] rtl819xU:qos active process with associate response received
[  325.667621] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[  325.681873] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[  325.681894] =====>rtl8192SU_link_change 1
[  325.692123] <=====rtl8192SU_link_change 2
[  326.653230] rtl819xU:EnableHWSecurityConfig8192:, hwsec:1, pairwise_key:2, SECR_value:c
[  326.653512] rtl819xU:====>to setKey(), dev:ffff8800d5430000, EntryNo:4, KeyIndex:0, KeyType:2, MacAddr1c:af:f7:ce:68:a1
[  326.657683] rtl819xU:====>to setKey(), dev:ffff8800d5430000, EntryNo:2, KeyIndex:2, KeyType:2, MacAddrff:ff:ff:ff:ff:ff
[  340.846649] =====>rtl8192SU_link_change 1
[  340.849280] <=====rtl8192SU_link_change 2
[  342.454131] =====>rtl8192SU_link_change 1
[  342.464631] <=====rtl8192SU_link_change 2
[  380.846804] =====>rtl8192SU_link_change 1
[  380.849298] <=====rtl8192SU_link_change 2
[  382.454147] =====>rtl8192SU_link_change 1
[  382.464646] <=====rtl8192SU_link_change 2
[  440.846598] =====>rtl8192SU_link_change 1
[  440.849151] <=====rtl8192SU_link_change 2
[  442.444547] =====>rtl8192SU_link_change 1
[  442.455046] <=====rtl8192SU_link_change 2
[  520.845941] =====>rtl8192SU_link_change 1
[  520.848459] <=====rtl8192SU_link_change 2
[  325.616124] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[  325.621664] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[  325.621695] rtl819xU:qos active process with associate response received
[  325.667621] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[  325.681873] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[  325.681894] =====>rtl8192SU_link_change 1
[  325.692123] <=====rtl8192SU_link_change 2
[  326.653230] rtl819xU:EnableHWSecurityConfig8192:, hwsec:1, pairwise_key:2, SECR_value:c
[  326.653512] rtl819xU:====>to setKey(), dev:ffff8800d5430000, EntryNo:4, KeyIndex:0, KeyType:2, MacAddr1c:af:f7:ce:68:a1
[  326.657683] rtl819xU:====>to setKey(), dev:ffff8800d5430000, EntryNo:2, KeyIndex:2, KeyType:2, MacAddrff:ff:ff:ff:ff:ff
[  340.846649] =====>rtl8192SU_link_change 1
[  340.849280] <=====rtl8192SU_link_change 2
[  342.454131] =====>rtl8192SU_link_change 1
[  342.464631] <=====rtl8192SU_link_change 2
[  380.846804] =====>rtl8192SU_link_change 1
[  380.849298] <=====rtl8192SU_link_change 2
[  382.454147] =====>rtl8192SU_link_change 1
[  382.464646] <=====rtl8192SU_link_change 2
[  440.846598] =====>rtl8192SU_link_change 1
[  440.849151] <=====rtl8192SU_link_change 2
[  442.444547] =====>rtl8192SU_link_change 1
[  442.455046] <=====rtl8192SU_link_change 2
[  520.845941] =====>rtl8192SU_link_change 1
[  520.848459] <=====rtl8192SU_link_change 2
[[  522.444579] =====>rtl8192SU_link_change 1
[  522.455078] <=====rtl8192SU_link_change 2
[  620.844720] =====>rtl8192SU_link_change 1
[  620.847244] <=====rtl8192SU_link_change 2
[  622.444622] =====>rtl8192SU_link_change 1
[  622.454870] <=====rtl8192SU_link_change 2
[  740.846970] =====>rtl8192SU_link_change 1
[  740.849464] <=====rtl8192SU_link_change 2
[  742.444170] =====>rtl8192SU_link_change 1
[  742.454918] <=====rtl8192SU_link_change 2
[  860.846134] =====>rtl8192SU_link_change 1
[  860.848652] <=====rtl8192SU_link_change 2
[  862.443844] =====>rtl8192SU_link_change 1
[  862.454343] <=====rtl8192SU_link_change 2
[  980.846176] =====>rtl8192SU_link_change 1
[  980.848687] <=====rtl8192SU_link_change 2
[  982.444393] =====>rtl8192SU_link_change 1
[  982.454891] <=====rtl8192SU_link_change 2
[ 1100.846727] =====>rtl8192SU_link_change 1
[ 1100.849230] <=====rtl8192SU_link_change 2
[ 1102.444317] =====>rtl8192SU_link_change 1
[ 1102.454940] <=====rtl8192SU_link_change 2
[ 1206.819788] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1208.862856] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[ 1218.862358] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[ 1220.998199] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1230.850169] =====>rtl8192SU_link_change 1
[ 1230.852615] <=====rtl8192SU_link_change 2
[  522.444579] =====>rtl8192SU_link_change 1
[  522.455078] <=====rtl8192SU_link_change 2
[  620.844720] =====>rtl8192SU_link_change 1
[  620.847244] <=====rtl8192SU_link_change 2
[  622.444622] =====>rtl8192SU_link_change 1
[  622.454870] <=====rtl8192SU_link_change 2
[  740.846970] =====>rtl8192SU_link_change 1
[  740.849464] <=====rtl8192SU_link_change 2
[  742.444170] =====>rtl8192SU_link_change 1
[  742.454918] <=====rtl8192SU_link_change 2
[  860.846134] =====>rtl8192SU_link_change 1
[  860.848652] <=====rtl8192SU_link_change 2
[  862.443844] =====>rtl8192SU_link_change 1
[  862.454343] <=====rtl8192SU_link_change 2
[  980.846176] =====>rtl8192SU_link_change 1
[  980.848687] <=====rtl8192SU_link_change 2
[  982.444393] =====>rtl8192SU_link_change 1
[  982.454891] <=====rtl8192SU_link_change 2
[ 1100.846727] =====>rtl8192SU_link_change 1
[ 1100.849230] <=====rtl8192SU_link_change 2
[ 1102.444317] =====>rtl8192SU_link_change 1
[ 1102.454940] <=====rtl8192SU_link_change 2
[ 1206.819788] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1208.862856] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[ 1218.862358] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[ 1220.998199] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1230.850169] =====>rtl8192SU_link_change 1
[ 1230.852615] <=====rtl8192SU_link_change 2
  522.444579] =====>rtl8192SU_link_change 1
[  522.455078] <=====rtl8192SU_link_change 2
[  620.844720] =====>rtl8192SU_link_change 1
[  620.847244] <=====rtl8192SU_link_change 2
[  622.444622] =====>rtl8192SU_link_change 1
[  622.454870] <=====rtl8192SU_link_change 2
[  740.846970] =====>rtl8192SU_link_change 1
[  740.849464] <=====rtl8192SU_link_change 2
[  742.444170] =====>rtl8192SU_link_change 1
[  742.454918] <=====rtl8192SU_link_change 2
[  860.846134] =====>rtl8192SU_link_change 1
[  860.848652] <=====rtl8192SU_link_change 2
[  862.443844] =====>rtl8192SU_link_change 1
[  862.454343] <=====rtl8192SU_link_change 2
[  980.846176] =====>rtl8192SU_link_change 1
[  980.848687] <=====rtl8192SU_link_change 2
[  982.444393] =====>rtl8192SU_link_change 1
[  982.454891] <=====rtl8192SU_link_change 2
[ 1100.846727] =====>rtl8192SU_link_change 1
[ 1100.849230] <=====rtl8192SU_link_change 2
[ 1102.444317] =====>rtl8192SU_link_change 1
[ 1102.454940] <=====rtl8192SU_link_change 2
[ 1206.819788] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1208.862856] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[ 1218.862358] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[ 1220.998199] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1230.850169] =====>rtl8192SU_link_change 1
[ 1230.852615] <=====rtl8192SU_link_change 2
[ 1232.486742] =====>rtl8192SU_link_change 1
[ 1232.500121] <=====rtl8192SU_link_change 2
(END) 
aravind@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  li  ESSID:"monterey"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 1C:AF:F7:CE:68:A1   
          Bit Rate=130 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-53 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
aravind@ubuntu:~$ dmesg | grep -i firmware
[   13.596733] rtl819xU: --->FirmwareDownload92S()
[   13.596742] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.747244] rtl819xU:--->FirmwareDownloadCode()
[   13.747284] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   13.748644] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[   13.748649] rtl819xU:--->FirmwareDownloadCode()
[   13.748691] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[   13.750372] rtl819xU:-->FirmwareEnableCPU()
[   13.752377] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[   13.752381] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[   13.752385] rtl819xU:--->FirmwareDownloadCode()
[   13.752392] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[   13.753741] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[   13.754779] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[   13.755013] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[   13.755018] rtl819xU:Firmware Download Success!!

dmesg | grep -e eth -e 819

[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.828061] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.828478] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    0.828483] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.222819] usb-storage: device found at 5
[    1.350880] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:19:21:e1:9d:92
[    1.350885] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[   11.577268] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   11.598586] Linux kernel driver for RTL8192 based WLAN cards
[   11.967373] usbcore: registered new interface driver rtl819xU
[   13.596733] rtl819xU: --->FirmwareDownload92S()
[   13.596742] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.747205] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[   13.747244] rtl819xU:--->FirmwareDownloadCode()
[   13.747284] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   13.748644] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[   13.748649] rtl819xU:--->FirmwareDownloadCode()
[   13.748691] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[   13.750372] rtl819xU:-->FirmwareEnableCPU()
[   13.752370] rtl819xU:IMEM Ready after CPU has refilled.
[   13.752377] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[   13.752381] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[   13.752385] rtl819xU:--->FirmwareDownloadCode()
[   13.752392] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[   13.752620] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[   13.753741] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[   13.754779] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)

Thanks.
Aravind

---

