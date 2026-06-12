---
title: "astone wifi RTL 8192SU"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by dragon99 on 2011-11-23
Hi All,

Having a few probs getting 11.10 to use an astone wifi dongle that uses RTL 8192SU chipset. The network tools show  'device not ready'. I have looked through the other threads for a solution, but no success. Following is some of the results I get :

With lsusb I get :

paul@sports:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 5a57:0290 Zinwell ZW-N290 802.11n [Realtek RTL8192SU]**
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser


Kernel

paul@sports:~$ uname -r
3.0.0-12-generic

Module

paul@sports:~$ lsmod | grep 819
r8192u_usb            248351  0

iwconfig

paul@sports:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg

paul@sports:~$ dmesg | grep 819
[   10.998819] usbcore: registered new interface driver usbhid
[   11.111049] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   11.116793] Linux kernel driver for RTL8192 based WLAN cards
[   11.528197] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-1/input0
[   13.325150] usbcore: registered new interface driver rtl819xU
[   13.666583] rtl819xU:request firmware fail!
[   13.666590] rtl819xU:ERR in init_firmware()
[   13.666595] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   13.666600] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   13.922593] rtl819xU:request firmware fail!
[   13.922599] rtl819xU:ERR in init_firmware()
[   13.922604] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   13.922610] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!


I can see from this that firmware is failing to load. I copied the f/w to another directory RTL8192SU as suggested by other threads, rebooted but still no go. 

Any help would be very appreciated.

dragon

---

### Post by chili555 on 2011-11-23
> I copied the f/w to another directory RTL8192SU as suggested by other threads, rebooted but still no go.It needs to be in /lib/firmware/RTL8192U, not RTL8192[COLOR="Red"]S[/COLOR]U. Please see modinfo:```
$ modinfo r8192u_usb
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
firmware:       [COLOR="Red"]RTL8192U[/COLOR]/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img
license:        GPL

```Would you please move it and reboot?

---

### Post by dragon99 on 2011-11-23
[/CODE]Would you please move it and reboot?[/QUOTE]

Ok, I have moved it & rebooted, but still get errors

paul@sports:~$ lsmod | grep 819
r8192u_usb            248351  0 
paul@sports:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

paul@sports:~$ dmesg | grep 819
[   11.956911] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   12.014844] Linux kernel driver for RTL8192 based WLAN cards
[   13.349345] usbcore: registered new interface driver rtl819xU
[   13.675828] rtl819xU:request firmware fail!
[   13.675834] rtl819xU:ERR in init_firmware()
[   13.675839] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   13.675844] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   13.945024] rtl819xU:request firmware fail!
[   13.945032] rtl819xU:ERR in init_firmware()
[   13.945037] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   13.945042] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
paul@sports:~$


The contents of the RTL8192U directory show 3 files - 
-rtl8192sfw.bin
-rtl8192sfw74.bin
-rtl8192sfw492

Am I missing the actual driver?

---

### Post by chili555 on 2011-11-23
> The contents of the RTL8192U directory show 3 files -
-rtl8192sfw.bin
-rtl8192sfw74.bin
-rtl8192sfw492But that's not what you need:> $ modinfo r8192u_usb
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
firmware:       RTL8192U/[COLOR="Red"]data.img[/COLOR]
firmware:       RTL8192U/[COLOR="Red"]main.img[/COLOR]
firmware:       RTL8192U/[COLOR="Red"]boot.img[/COLOR]
license:        GPLDo you have these in /lib/firmware/RTL8192[COLOR="Red"]E[/COLOR]? Can you try copying over these?

---

### Post by dragon99 on 2011-11-23
Ok, yes these were sitting in the RTL8192E directory. Copied them to RTL8192U directory, removed dongle, re inserted dongle, and now have a wireless connection.:) Thank you chili555

---

### Post by chili555 on 2011-11-24
Awesome! Glad it's working. Have fun.

---

