---
title: "rtl8192 Driver Not found - Doesn't load"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by vchapman on 2010-07-27
Is there an easy fix for this?

[ 1526.203604] Linux kernel driver for RTL8192 based WLAN cards
[ 1526.203607] Copyright (c) 2007-2008, Realsil Wlan
[ 1526.203966] ==>ep_num:11, in_ep_num:2, out_ep_num:9
[ 1526.203970] ==>RtInPipes:3  9  
[ 1526.203975] ==>RtOutPipes:4  5  6  7  8  10  11  12  13  
[ 1526.203988] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[ 1526.203992] 3  2  1  0  4  8  7  6  5  
[ 1526.237038] Dot11d_Init()
[ 1526.237047] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 1526.237050] 
[ 1526.238947] usbcore: registered new interface driver rtl819xU
[ 1526.344548] rtl819xU: --->FirmwareDownload92S()
[ 1526.344554] 
[ 1526.344570] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 1526.367612] rtl819xU:request firmware fail!
[ 1526.367616] 
[ 1526.368488] rtl819xU:Firmware Download Fail!!4544
[ 1526.368492] 
[ 1526.398944] rtl819xU: --->FirmwareDownload92S()
[ 1526.398950] 
[ 1526.398962] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 1526.413343] rtl819xU:request firmware fail!
[ 1526.413346] 
[ 1526.413847] rtl819xU:Firmware Download Fail!!4544
[ 1526.413851] 
[ 1526.413856] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1526.413859] 
[ 1526.457167] rtl819xU: --->FirmwareDownload92S()
[ 1526.457171] 
[ 1526.457187] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 1526.475455] rtl819xU:request firmware fail!
[ 1526.475459] 
[ 1526.475962] rtl819xU:Firmware Download Fail!!4544
[ 1526.475965] 
[ 1526.499783] rtl819xU: --->FirmwareDownload92S()
[ 1526.499789] 
[ 1526.499800] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 1526.518587] rtl819xU:request firmware fail!
[ 1526.518591] 
[ 1526.519096] rtl819xU:Firmware Download Fail!!4544
[ 1526.519099] 
[ 1526.519105] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1526.519107] 

Thanks.

---

### Post by chili555 on 2010-07-27
The driver is looking for firmware in a directory called RTL8192SU. You probably have the firmware but in the wrong place. Here is a 'locate' from my system:```
$ locate rtl8192sfw.bin
/lib/firmware/RTL8192SE/rtl8192sfw.bin

```As you can see, I have the firmware but it's located in RTL8192S[COLOR="Red"]E[/COLOR]. 

The solution is to copy the firmware to the correct directory:```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Reboot and see if your device is now working. If not, post the relevant lines from *dmesg*.

---

### Post by vchapman on 2010-07-28
> **chili555 said:**
>  If not, post the relevant lines from *dmesg*.


  18.909332] Linux kernel driver for RTL8192 based WLAN cards
[   18.909338] Copyright (c) 2007-2008, Realsil Wlan
[   18.924158] ==>ep_num:11, in_ep_num:2, out_ep_num:9
[   18.924165] ==>RtInPipes:3  9  
[   18.924170] ==>RtOutPipes:4  5  6  7  8  10  11  12  13  
[   18.924183] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[   18.924187] 3  2  1  0  4  8  7  6  5  
[   18.929217] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   18.975484] Dot11d_Init()
[   18.975493] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[   18.975496] 
[   18.977196] usbcore: registered new interface driver rtl819xU

[   19.984935] rtl819xU: --->FirmwareDownload92S()
[   19.984941] 
[   19.984952] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   19.999062] rtl819xU:signature:8192, version:703e, size:30, imemsize:b408, sram size:87c8
[   19.999067] 
[   19.999157] rtl819xU:--->FirmwareDownloadCode()
[   19.999160] 
[   19.999240] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),

[   20.655903] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   20.655908] 
[   20.655911] rtl819xU:FirmwareDownloadCode() fail ! 
[   20.655913] 
[   20.656155] rtl819xU:Firmware Download Fail!!4544
[   20.656157] 
[   20.675775] rtl819xU: --->FirmwareDownload92S()
[   20.675781] 
[   20.675786] rtl819xU:--->FirmwareDownloadCode()
[   20.675788] 
[   20.675886] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),

[   21.155194] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   21.155198] 
[   21.155203] rtl819xU:FirmwareDownloadCode() fail ! 
[   21.155206] 
[   21.155402] rtl819xU:Firmware Download Fail!!4544
[   21.155405] 
[   21.155411] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   21.155413] 

[   21.510704] rtl819xU: --->FirmwareDownload92S()
[   21.510710] 
[   21.510716] rtl819xU:--->FirmwareDownloadCode()
[   21.510718] 
[   21.510802] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   21.585634] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.585653] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.588520] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   21.802850] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   21.802854] 
[   21.802859] rtl819xU:FirmwareDownloadCode() fail ! 
[   21.802861] 
[   21.803123] rtl819xU:Firmware Download Fail!!4544
[   21.803126] 
[   21.819357] rtl819xU: --->FirmwareDownload92S()
[   21.819362] 
[   21.819368] rtl819xU:--->FirmwareDownloadCode()
[   21.819370] 
[   21.819462] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   22.105215] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   22.105219] 
[   22.105224] rtl819xU:FirmwareDownloadCode() fail ! 
[   22.105227] 
[   22.105458] rtl819xU:Firmware Download Fail!!4544
[   22.105461] 
[   22.105466] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   22.105469]

---

### Post by cavalier911 on 2010-07-28
When you click on this link you will download the firmware that is supposed to work.

[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

68533bf8078a9e00966a78c9f2da4b9b  rtl8192sfw.bin  **md5sum**

Move the old firmware out of /lib/firmware/RTL8192SU and replace it with this

---

### Post by vchapman on 2010-07-29
> **cavalier911 said:**
> When you click on this link you will download the firmware that is supposed to work.

[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

68533bf8078a9e00966a78c9f2da4b9b  rtl8192sfw.bin  **md5sum**

Move the old firmware out of /lib/firmware/RTL8192SU and replace it with this

Unfortunately, the result is pretty much the same:

   18.825191] Linux kernel driver for RTL8192 based WLAN cards
[   18.825195] Copyright (c) 2007-2008, Realsil Wlan

[   18.977680] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[   18.977684] 
[   18.979275] usbcore: registered new interface driver rtl819xU
[   19.154905] nvidia: module license 'NVIDIA' taints kernel.
[   19.154913] Disabling lock debugging due to kernel taint
[   19.509170] type=1505 audit(1280415641.410:2):  operation="profile_load" pid=581 name="/sbin/dhclient3"
[   19.510019] type=1505 audit(1280415641.410:3):  operation="profile_load" pid=581 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.510476] type=1505 audit(1280415641.410:4):  operation="profile_load" pid=581 name="/usr/lib/connman/scripts/dhclient-script"
[   20.447902] type=1505 audit(1280415642.346:5):  operation="profile_load" pid=694 name="/usr/share/gdm/guest-session/Xsession"
[   20.466155] type=1505 audit(1280415642.366:6):  operation="profile_replace" pid=695 name="/sbin/dhclient3"
[   20.467031] type=1505 audit(1280415642.366:7):  operation="profile_replace" pid=695 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.467512] type=1505 audit(1280415642.366:8):  operation="profile_replace" pid=695 name="/usr/lib/connman/scripts/dhclient-script"
[   20.546981] type=1505 audit(1280415642.446:9):  operation="profile_load" pid=699 name="/usr/bin/evince"
[   20.631273] type=1505 audit(1280415642.530:10):  operation="profile_load" pid=699 name="/usr/bin/evince-previewer"
[   20.728215] rtl819xU: --->FirmwareDownload92S()
[   20.728221] 
[   20.728230] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   20.736109] type=1505 audit(1280415642.638:11):  operation="profile_load" pid=699 name="/usr/bin/evince-thumbnailer"
[   20.742619] rtl819xU:signature:8192, version:703e, size:30, imemsize:b408, sram size:87c8
[   20.742624] 
[   20.742715] rtl819xU:--->FirmwareDownloadCode()
[   20.742718] 
[   20.742798] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   20.832270]   alloc irq_desc for 21 on node -1
[   20.832276]   alloc kstat_irqs on node -1
[   20.832288] C-Media PCI 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.901666] Console: switching to colour frame buffer device 80x30
[   20.961498] usbcore: registered new interface driver snd-usb-audio
[   21.115575] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   21.115580] 
[   21.115585] rtl819xU:FirmwareDownloadCode() fail ! 
[   21.115587] 
[   21.115813] rtl819xU:Firmware Download Fail!!4544
[   21.115816] 
[   21.132080] rtl819xU: --->FirmwareDownload92S()
[   21.132086] 
[   21.132092] rtl819xU:--->FirmwareDownloadCode()
[   21.132094] 
[   21.132195] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   21.204071] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.204088] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.206373] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   21.423647] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   21.423652] 
[   21.423657] rtl819xU:FirmwareDownloadCode() fail ! 
[   21.423660] 
[   21.424809] rtl819xU:Firmware Download Fail!!4544
[   21.424813] 
[   21.424820] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   21.424823] 
[   21.429856] eth0: link down
[   21.430194] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.580556] rtl819xU: --->FirmwareDownload92S()
[   21.580562] 
[   21.580568] rtl819xU:--->FirmwareDownloadCode()
[   21.580570] 
[   21.580686] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   21.881058] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   21.881062] 
[   21.881068] rtl819xU:FirmwareDownloadCode() fail ! 
[   21.881070] 
[   21.881286] rtl819xU:Firmware Download Fail!!4544
[   21.881289] 
[   21.898043] rtl819xU: --->FirmwareDownload92S()
[   21.898049] 
[   21.898054] rtl819xU:--->FirmwareDownloadCode()
[   21.898056] 
[   21.898151] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   22.163535] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   22.163540] 
[   22.163545] rtl819xU:FirmwareDownloadCode() fail ! 
[   22.163548] 
[   22.163773] rtl819xU:Firmware Download Fail!!4544
[   22.163776] 
[   22.163781] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   22.163783]

---

### Post by vchapman on 2010-08-03
bump

---

### Post by cavalier911 on 2010-08-03
Ndiswrapper didn't work? Any success with that driver must be with earlier versions of the kernel.You can download the driver from realtek,find a tutorial and try to compile/install/load the module against your kernel.

---

### Post by chili555 on 2010-08-03
Please post:```
ls -al /lib/firmware/RTL8192SU
```Thanks.

---

### Post by vchapman on 2010-08-07
I gave up on making this work. I bought a D-Link wireless card that worked right out of the box!

---

### Post by jimmah6786 on 2011-01-28
> **cavalier911 said:**
> When you click on this link you will download the firmware that is supposed to work.

[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

68533bf8078a9e00966a78c9f2da4b9b  rtl8192sfw.bin  **md5sum**

Move the old firmware out of /lib/firmware/RTL8192SU and replace it with this

Worked Perfectly for me, thank you for this!!

---

### Post by jackbnymble on 2011-05-01
> **chili555 said:**
> The driver is looking for firmware in a directory called RTL8192SU. You probably have the firmware but in the wrong place. Here is a 'locate' from my system:```
$ locate rtl8192sfw.bin
/lib/firmware/RTL8192SE/rtl8192sfw.bin

```As you can see, I have the firmware but it's located in RTL8192S[COLOR="Red"]E[/COLOR]. 

The solution is to copy the firmware to the correct directory:```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Reboot and see if your device is now working. If not, post the relevant lines from *dmesg*.
Perfect! I was going crazy trying to find a fix for my new Toshiba NB505. Many thanks for the help.

---

