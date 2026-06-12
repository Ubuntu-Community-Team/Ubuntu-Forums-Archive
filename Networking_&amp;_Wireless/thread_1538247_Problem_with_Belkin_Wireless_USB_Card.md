---
title: "Problem with Belkin Wireless USB Card"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by neofreud on 2010-07-24
I just installed ubuntu on my desktop which was connected with a wireless belkin USB card (part number F7D2101) Does not work by default, and after checking ndiswrapper it is not even listed at all. 

I am not quite sure where to go from here. The Chip set ID is 050D:845A 

Any help would be appreciated.

---

### Post by eteq on 2010-08-24
I managed to get this adapter working under Ubuntu (lucid 64).  Pretty straightforward actually... I got most of this from [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815) , although it required a some slight changes. 

Run this command:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```

And add this line to the file (which may be empty) and save:

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"
```

Then run this command:
```
sudo gedit /etc/modprobe.d/network_drivers.conf 
```

And add this file (and save)
```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xU/new_id
```

Finally, download this file:
[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

and copy it to the directory ```
/lib/firmware/RTL8192SU/ 
```

To summarize, the first two commands tell linux to load the correct driver when that particular USB device is plugged in (which I figured out with the lsusb command), and the firmware is used to load the information the wireless chip needs to run.

---

### Post by ProsperB on 2011-02-05
:p Thanks a lot !
This really saved my day, and the bacon too...

---

### Post by pjm1 on 2011-02-17
Well, I've got an annoying problem when I've tried to start using my F7D2101...

I'm running 10.04 LTS and it seems it's all set up out of the box to support this device (as in all of the steps eteq outlines above have already been carried out.

Only downside is my box now crashes (no response - requires a power cycle) within a couple of minutes of booting up.  Every time without fail.

So, basically, unless I can find a fix I'm stuck using a crappy old USB dongle which is also temperamental but doesn't crash my system... any ideas?  I'll post the results of my dmesg when I can but it'll take a few minutes as I'll have to swap adaptors a couple of times to avoid the crash...

Here are the results of dmesg | grep 819
```
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[   12.819279] lp: driver loaded but no devices found
[   12.819500] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.896990] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   12.964580] Linux kernel driver for RTL8192 based WLAN cards
[   12.964773] usbcore: registered new interface driver rtl819xU
[   13.008819] ==>RtOutPipes:4  6  13  
[   14.431622] rtl819xU: --->FirmwareDownload92S()
[   14.431635] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.521796] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[   14.521865] rtl819xU:--->FirmwareDownloadCode()
[   14.521928] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   14.523245] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[   14.523254] rtl819xU:--->FirmwareDownloadCode()
[   14.523328] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[   14.524862] rtl819xU:-->FirmwareEnableCPU()
[   14.527625] rtl819xU:IMEM Ready after CPU has refilled.
[   14.527636] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[   14.527643] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[   14.527650] rtl819xU:--->FirmwareDownloadCode()
[   14.527663] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[   14.527860] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[   14.529111] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[   14.530107] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[   14.530232] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[   14.530239] rtl819xU:Firmware Download Success!!
[   36.469983] =====>rtl8192SU_link_change 1
[   36.470990] <=====rtl8192SU_link_change 2
[   36.524467] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[   36.550100] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[   36.554250] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[   36.554278] rtl819xU:qos active process with associate response received
[   36.604700] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[   36.621097] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[   36.621117] =====>rtl8192SU_link_change 1
[   36.632470] <=====rtl8192SU_link_change 2
[   37.634940] rtl819xU:EnableHWSecurityConfig8192:, hwsec:1, pairwise_key:4, SECR_value:c
[   37.635134] rtl819xU:====>to setKey(), dev:d5008000, EntryNo:4, KeyIndex:0, KeyType:4, MacAddr94:44:52:68:8d:29
[   37.639256] rtl819xU:====>to setKey(), dev:d5008000, EntryNo:1, KeyIndex:1, KeyType:4, MacAddrff:ff:ff:ff:ff:ff
[   63.254100] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[   67.254102] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[   77.481894] =====>rtl8192SU_link_change 1
[   77.482789] <=====rtl8192SU_link_change 2
[   77.489667] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[   77.503526] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[   79.216988] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[   79.232631] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[   79.237751] =====>rtl8192SU_link_change 1
[   79.247994] <=====rtl8192SU_link_change 2
[   89.253951] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[  107.481308] =====>rtl8192SU_link_change 1
[  107.482550] <=====rtl8192SU_link_change 2
[  107.489670] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[  107.503902] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[  109.212242] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[  109.228382] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[  109.233881] =====>rtl8192SU_link_change 1
[  109.243623] <=====rtl8192SU_link_change 2

```

---

