---
title: "Belkin F5D8053 suddenly not recognized properly"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by Tpeter36 on 2011-11-04
Hello everyone!
I recently bought a Belkin F5D8053 USB adapter, which worked out of the box with ubuntu 11.10. On windows, I had to install its drivers manually. After a few days' usage, the device simply disappeared from windows, but I could fix that problem by reinstalling its driver. However, on ubuntu, network manager keeps saying that the device is not ready. 
It shows up as wlan2 in iwconfig, with 1 Mb/s rate (it used to be wlan0). Ifconfig tells me it's down, when I try to bring it up, it claims the device is not available. Driver module loaded is r8192u. I tried disabling and re-enabling it with  modprobe, no success. I tried to unplug and re-plug it, still nothing. Disabled and enabled and removed and reinstalled a couple of times in windows device manager, but everything remains the same. The hardware should be ok, as it works flawlessly on windows.
I also tried ndiswrapper, but it claims the hardware is not present. It also produces the same on a fresh ubuntu installition, and a live USB. (same goes for linux mint)

Any ideas on what to do? I got used to ubuntu, and I love it, but if there's no network, I won't be able to do anything.

Thanks in advance!

Ps.: I don't know if it is related, but my motherboard seems to be dying. A few days ago my integrated sound magically disappeared, leaving no trace. It is enabled in the BIOS, but no OS shows any signs of the hardware. Other USB devices work well, so I guess it's not related to the adapter.

---

### Post by Tpeter36 on 2011-11-05
In addition to that, I just ran dmesg:

```
[   28.993864] rtl819xU:====>error=====dwRegRead: 0, WriteData: fffff027 
[   28.993867] 
[   28.993870] rtl819xU:PHY_RF8256_Config():Check PHY0 Fail!!
[   28.993872] 
[   29.043807] rtl819xU:request firmware fail!
[   29.043809] 
[   29.043813] rtl819xU:ERR in init_firmware()
[   29.043814] 
[   29.043817] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   29.043819] 
[   29.043821] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   29.043823] 
```

Anyone?

---

### Post by chili555 on 2011-11-06
> Driver module loaded is r8192u.Are you sure it's not r8192u_usb?```
lsmod | grep 819
```This module requires firmware, as many drivers do:> chili@LAPTOP60:~$ modinfo r8192u_usb
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
[COLOR="Red"]firmware:       RTL8192U/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img[/COLOR]
license:        GPL
description:    HostAP crypto
Do you have the firmware?```
ls /lib/firmware/RTL8192U
```Do you have it, but in the wrong place?```
sudo updatedb
locate data.img
```updatedb will take a few moments; please be patient.

If you have the right firmware in the right place, then I will suspect a hardware problem; that is, the motherboard.

---

### Post by Tpeter36 on 2011-11-06
First of all, thank you for your time.
The driver loaded is indeed, r8192u_usb.
I have the right firmware (the one I found in an other thread) in /lib/firmware/RTL8192U. The file data.img was in /lib/firmware/RTL8192E. I copied the file over into RTL8192U, which I now guess I shouldn't have. Iwconfig and ifconfig stopped working (black console, does not even respond to ctrl+c), and dmesg gives me a slightly different output.

```
[  281.415231] read_nic_dword TimeOut! status:-19
[  281.415233] rtl819xU:Download Firmware: Put code fail!
[  281.415235] 
[  281.415238] rtl819xU:ERR in CPUcheck_maincodeok_turnonCPU()
[  281.415239] 
[  281.415241] rtl819xU:CPUcheck_maincodeok_turnonCPU fail!
[  281.415243] 
[  281.415245] rtl819xU:ERR in init_firmware()
[  281.415246] 
[  281.415249] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  281.415250] 
[  281.415253] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  281.415254] 
[  281.428062] rtl819xU:=============>wlan driver to be removed
[  281.428066] 
[  281.438436] rtl819xU:wlan driver removed
[  281.438438] 
[  282.420253] usb 1-1.4: new full speed USB device number 8 using ehci_hcd
[  282.512621] usb 1-1.4: not running at top speed; connect to a high speed hub
[  282.552871] rtl819xU:EEPROM ID is invalid(is 0x0(should be 0x8129)
[  282.552873] 
[  282.552877] Dot11d_Init()
[  282.552882] End of initendpoints
[  282.668973] udevd[2301]: renamed network interface wlan0 to wlan2
[  282.783621] rtl819xU:====>error=====dwRegRead: 0, WriteData: fffff027 
[  282.783624] 
[  282.783628] rtl819xU:PHY_RF8256_Config():Check PHY0 Fail!!
[  282.783629] 
[  358.015132] rtl819xU:Download Firmware: Put code fail!
[  358.015136] 
[  358.015140] rtl819xU:ERR in CPUcheck_maincodeok_turnonCPU()
[  358.015142] 
[  358.015144] rtl819xU:CPUcheck_maincodeok_turnonCPU fail!
[  358.015145] 
[  358.015148] rtl819xU:ERR in init_firmware()
[  358.015149] 
[  358.015152] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  358.015154] 
[  358.015156] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  358.015158] 
[  358.136757] rtl819xU:====>error=====dwRegRead: 0, WriteData: fffff027 
[  358.136761] 
[  358.136764] rtl819xU:PHY_RF8256_Config():Check PHY0 Fail!!
[  358.136766] 


```

The first line was repeated a couple of times, and this part should contain a time where I reconnected the USB stick.

It really does seem like a hardware problem, especially taking into account that it worked fine until now, and that not so long ago, both my GN-WPKG (a PCI wireless) and the onboard sound card gave up the fight. Now the only thing I don't understand why it does work on windows.. Maybe there is still a chance we could fix that without replacing hardware?

---

### Post by chili555 on 2011-11-06
Let's have a look at:```
ls -al /lib/firmware/RTL8192U
```For reference, my details are:> chili@LAPTOP60:~$ ls -al /lib/firmware/RTL8192U
total 60
drwxr-xr-x  2 root root  4096 2011-11-06 08:04 .
drwxr-xr-x 62 root root  4096 2011-11-06 08:04 ..
-rw-r--r--  1 root root   344 2011-11-06 08:04 boot.img
-rw-r--r--  1 root root   848 2011-11-06 08:04 data.img
-rw-r--r--  1 root root 42944 2011-11-06 08:04 main.imgWe will be interested in size, ownership and permissions.

---

### Post by Tpeter36 on 2011-11-06
The output is

```
peter@peter-P5PL2:~$ sudo ls -al /lib/firmware/RTL8192U/
&#258;¶sszesen 80
drwxr-xr-x  2 root root  4096 2011-11-06 14:14 .
drwxr-xr-x 63 root root 20480 2011-11-06 14:14 ..
-rw-r--r--  1 root root   344 2011-08-23 15:22 boot.img
-rw-r--r--  1 root root   848 2011-08-23 15:22 data.img
-rw-r--r--  1 root root 42944 2011-08-23 15:22 main.img

```

but I am pretty sure I messed something up. Now when I connect the adapter, there is no sign that ubuntu recognizes it anyhow, except that I could not even run nautilus from  the terminal. Iwconfig and ifconfig still unresponsive, and dmesg produces the same error messages.

---

### Post by chili555 on 2011-11-06
> Now when I connect the adapter, there is no sign that ubuntu recognizes it anyhow, except that I could not even run nautilus from the terminal. Iwconfig and ifconfig still unresponsive, You may want to check over in General Help. I fear it will be difficult to get your wireless going otherwise.

---

### Post by Tpeter36 on 2011-11-06
Thank you for your time and efforts anyways. I think I am going to hand over my computer to someone who has more experience with hardware than me. We'll see if it really is my motherboard that's causing all the trouble.

---

