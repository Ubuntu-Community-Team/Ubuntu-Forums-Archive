---
title: "Rosewill RNX-N150UBE Driver doesn't work"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by gtsorbo on 2010-12-05
I downloaded the Linux driver from the Rosewill website. I followed the instructions which say:

In driver folder - uncompress the tar.gz file
then (from terminal):
[LIST]
[*]make
[*]./clean
[*]insmod 8712u.ko
[/LIST]

I did the make command, which created the 8712u.ko file in the driver's folder. When I attempt ./clean, I get this error:

ERROR: Module ieee80211_rsl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules

When I try insmod 8712u.ko, that fails as well (probably because I couldn't do the previous step).
Any ideas about what the issue is? I haven't been able to find anything from Googling.

---

### Post by chili555 on 2010-12-05
What is the version of the file you downloaded from Rosewill? What is your kernel version?```
uname -r
```You might be better off with a newer version from Realtek.

---

### Post by gtsorbo on 2010-12-05
I have Kernel version 2.6.31-14-generic
The driver version that I have is version 2.6.0006.20100511. There was a newer version available on Realtek's website that I just found, but i get an error when clicking the download link (brings me to a page that says I don't have permission to download this).

---

### Post by chili555 on 2010-12-05
That looks recent enough. Can you please open Synaptic and confirm you have installed *linux-headers-generic* and *build-essential*? Also, please post the README as an attachment to your reply. Were there any errors or even scary warnings when you ran 'make?'

I downloaded and ran 'make' on the Realtek package and it made without a whimper on my 2.6.35-23-generic kernel.

---

### Post by gtsorbo on 2010-12-05
I have linux-headers-2.6.31-14-generic installed, but not build-essential

I get multiple warnings that say "warning: cast from pointer to integer of different size"

I attached the README

---

### Post by chili555 on 2010-12-05
I see no instructions that give installation steps. Is there an 'Install' document included? Where did you read the installation instructions?

Strangely enough, there is no instruction at all in the package I downloaded. Silly me, I simply did:```
cd Downloads/rtl8712/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625
sudo su
make
make install
exit
```I believe you will need the appropriate build tools installed, i.e. *build-essential*.

---

### Post by gtsorbo on 2010-12-05
In the document folder, there is a powerpoint file which has instructions for installation. I converted it to PDF so I could attach it.

How should I go about installing build-essential? Since I don't have internet access on my Ubuntu machine, I can't download it directly onto that box.

---

### Post by chili555 on 2010-12-05
Do you have the install CD? If so, you can drop it in the drive and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```In the 'clean' file in my downloaded package, it only unloads modules that may already be loaded, so as to load the proper newly-built modules. Since you have no working wireless device, I am not surprised they are not loaded and thus aren't found in the systems list of loaded modules. I think you can safely ignore this:> ERROR: Module ieee80211_rsl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules
Let's identify your device and see if there is an easier way. Please run:```
lsusb
```I'd like to see the line relating to your Rosewill (nee Realtek).

---

### Post by gtsorbo on 2010-12-06
The line is:

> 0bda:8171 Realtek Semiconductor Inc.

I'll try installing build-essential and post again.

---

### Post by chili555 on 2010-12-06
> 0bda:8171 Realtek Semiconductor Inc. This device works with the driver module *r8192s_usb*. I assume, since you are running Ubuntu 9.10, it's not incorporated yet in your version. Check with:```
modinfo r8192s_usb
```Unless you'd consider upgrading, I think compiling is the most practical solution.

---

### Post by gtsorbo on 2010-12-06
When I do modinfo r8192s_usb , I get this response. (attached picture)
This looks to me like it is installed.  Should I do insmod 8192s_usb from the directory specified?

---

### Post by chili555 on 2010-12-06
It is installed, however, your usb.id is not listed. Here is the same command from my computer; I have highlighted your usb.id:> modinfo r8192s_usb 
filename:       /lib/modules/2.6.35-23-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
firmware:       RTL8192SU/rtl8192sfw.bin
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
srcversion:     93926278505B0EDEC322B52
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8171[/COLOR]d*dc*dsc*dp*ic*isc*ip*
depends:        eeprom_93cx6
staging:        Y
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686 
parm:           debug:debug output mask (int)
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware security support.  (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)We could make an attempt to force your usb.id to be used by r8192s_usb. It might or might not work.

We could compile. It would probably work.

You could upgrade to the latest version of Ubuntu and it would almost certainly work. I will do whatever you wish. I have plenty of time and quite a bit of patience! 

By the way, if you want to load a module, simply do:```
sudo modprobe <your_module>
```No path or file extension (.ko) is required.

---

### Post by gtsorbo on 2010-12-06
I would prefer to upgrade. I only installed 9.10 in the first place because when I tried to initially install 10.04, it would freeze up. I still have a 10.04 disc. Can I upgrade from within Ubuntu?

---

### Post by chili555 on 2010-12-06
> Can I upgrade from within Ubuntu?It is a bit tricky and has some risk. If you have any important data, be sure to back it up. Open System > Administration > Update Manager and select Distribution Upgrade at the top. It depends on internet access. Do you have it? Do you have an idea what caused the lockups?

---

### Post by gtsorbo on 2010-12-06
No, I don't have internet access on this machine, but I guess I could carry it to my router and directly connect it if necessary. And no I'm not sure what the deal was with the lockups - I would press enter and it would freeze. 

I don't have any valuable info on this machine, it can be formatted as many times as necessary.

---

### Post by chili555 on 2010-12-06
Can you use another machine to download the live CD and try it out before you install? You can check for lockups as well as the wireless. If that's an issue, we can compile.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by gtsorbo on 2010-12-06
I booted from the 10.10 dvd I just burned. I plugged in the adapter, then went to terminal and typed in modinfo r8192s_usb.  I checked the list, and the 0bda:8171 ID was there, but it still didnt recognize my device in ubuntu. I am not able to connect to any wifi networks.

---

### Post by chili555 on 2010-12-07
When you do:```
sudo modprobe r8192s_usb
iwconfig
dmesg | grep 819
```Are there any interesting messages?

---

### Post by gtsorbo on 2010-12-07
sudo modprobe r8192s_usb returns nothing

iwconfig returns this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

dmesg | grep 819 returns 

```
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    1.181900]   Magic number: 6:52:11
[    1.181976] rtc_cmos 00:05: setting system clock to 2010-12-07 05:02:00 UTC (1291698120)
[    1.181978] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.181979] EDD information not available.
[    6.094165] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    6.096840] Linux kernel driver for RTL8192 based WLAN cards
[    6.354449] usbcore: registered new interface driver rtl819xU
[   13.846937] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   13.847217] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   13.861308] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   13.861551] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   13.861554] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   14.698670] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   14.698926] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   14.713177] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   14.713425] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   14.713429] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1261.760785] rtl819xU:=============>wlan driver to be removed
[ 1261.771088] rtl819xU:wlan driver removed
[ 1271.944582] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1271.944849] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1271.961458] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1271.961710] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1271.961720] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1271.984332] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1271.984593] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1272.002154] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1272.002499] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1272.002510] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2796.809012] JFS: nTxBlock = 8192, nTxLock = 65536
```

---

### Post by chili555 on 2010-12-07
Interesting message, indeed. It is missing firmware. Here is the solution:  [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

You can do this on a live CD, however it will be gone at reboot. 

So are you now confident that you can install Ubuntu 10.10 without lockups and with a working wireless device?

---

### Post by gtsorbo on 2010-12-07
This did the trick!!
i installed Ubuntu 10.10 and ran the terminal commands from the link. Now I'm able to connect to Wi-Fi.
Thanks again!

---

### Post by chili555 on 2010-12-07
Awesome! Glad it's working. Have fun.

---

### Post by topdownjimmy on 2011-01-06
> **chili555 said:**
> Interesting message, indeed. It is missing firmware. Here is the solution:  [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

You can do this on a live CD, however it will be gone at reboot. 

So are you now confident that you can install Ubuntu 10.10 without lockups and with a working wireless device?

the command lines given at this link worked for me too

```
wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```

---

### Post by MarlonNelson on 2011-07-07
I'm running 10.04 - Lucid Lynx - and the following commands worked for me:

```
cd /lib/firmware
sudo mkdir RTL8192SU
sudo cp RTL8192SE/* RTL8192SU/

```

That's all that was necessary.

---

