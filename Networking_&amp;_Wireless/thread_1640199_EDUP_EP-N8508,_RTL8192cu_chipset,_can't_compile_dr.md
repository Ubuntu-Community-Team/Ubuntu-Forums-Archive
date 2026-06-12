---
title: "EDUP EP-N8508, RTL8192cu chipset, can't compile driver"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by nssone on 2010-12-07
OK, so I got this new nano usb wireless wifi adapter with the RTL8192cu chipset and have been trying to compile the drivers for it. Every time I try and compile it I get the same errors. I have searched up and down for a solution on google and on these forums. It seems to have worked for people if they have the latest headers and build essentials, but even after I updated those and rebooted even, I get the same errors.

Here's an output of the make
```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.37-8-generic/build M=/home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.37-8-generic'
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_security.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_debug.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_io.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_ioctl_query.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_ioctl_set.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/ieee80211.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_mlme.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_mlme_ext.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_wlan_util.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_pwrctrl.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_rf.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_recv.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_sta_mgt.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_xmit.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/efuse/rtl8712_efuse.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/led/rtl8192c_led.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/hal_init.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c_d_hal_init.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o
/home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c: In function ‘_rwlock_init’:
/home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:291:2: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/tg37/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.37-8-generic'
make: *** [modules] Error 2

```

What's funny to me is that it seems to have a problem with it comes to the file osdep_service.c, which reminds me of the problem I had with a previous usb wifi dongle which had an rtl8172 chipset. It used to not compile until I came across this link: [http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html) It helped me get my old dongle driver working perfectly. I'm wondering if I'm having a similar problem again. But I'm just not experienced enough to make heads or tails of a lot of this. This is a pastebin of the header file [http://pastebin.com/ffWwyzEw](http://pastebin.com/ffWwyzEw)

If anybody has any ideas for me to get this driver to compile, feel free to suggest them. I would really like to try and get this up and running.

---

### Post by nssone on 2010-12-08
Hate to just bump this, but I really would like to get this up and running.

Running Natty 11.04 with 2.6.37-8-generic.

---

### Post by Marzata on 2010-12-09
Just compiled it from scratch in Ubuntu 10.04.1 LTS (lucid) where it works as a second wireless adapter. Kernel: 2.6.32-26-generic-pae.

---

### Post by nssone on 2010-12-09
Yeah, after some research, it seems to be something revolving around these newer headers. It's kind of frustrating that I can't seem to find a solution yet.

---

### Post by Marzata on 2010-12-20
Yes, it seems to be something about these newer headers. Any particular reason to run 11.04 alpha?

---

### Post by nousernameavailable on 2011-01-22
just replace the init_MUTEX(prwlock) in os_dep/osdep_service.c with a sema_init(prwlock,1)

works like a charm

---

### Post by pedro.nariyoshi on 2011-01-29
New drivers released yesterday, gonna try now.

PS.: I believe it's init_MUTEX(pmutex) and sema_init(pmutex,1)

EDIT: Works great on Ubuntu 10.10 i386 (tested on 2.6.35-generic and 2.6.37-liquorix), will test on AMD64 later and post the results

---

### Post by pedro.nariyoshi on 2011-01-29
Yes, they work (on both i386 and AMD64)

Very exciting

---

### Post by gwoodruff on 2011-04-09
Hello all, anyone out there get this to work on a 2.6.38 on up? I am using driver v2.0.1324.20110126. Would also like to get this working on 11.04! Still get error 2 after changing init_MUTEX(pmutex) (although seems to make it much further then without the change). Any and all help is greatly appreciated.

Gary

---

### Post by MooPi on 2011-04-09
I'm using an Edimax 7811 that has the same chip and it works perfectly. Download the driver from Realtek and decompress the tar.gz folder.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU") Navigate to the driver folder in the decompress folder and open a terminal. Type ```
make
```
```
sudo make install
```
```
sudo modprobe 8192cu
```
This worked for the Edimax and probably should work  for same chips. After a new upgrade in kernel you'll need to refresh your install. In the RTL8192 folder open a terminal and 
```
make clean
make
sudo make install
sudo modprobe 8192cu
```

---

### Post by ernia on 2011-04-09
compat-wireless-2.6.39-rc1-3 does support RTL8192cu:
```
root@tm2:/home/fabio# lsmod | grep 8192
rtl8192cu              83647  0 
rtl8192c_common        56788  1 rtl8192cu
rtlwifi                77461  1 rtl8192cu
mac80211              253969  3 rtl8192cu,rtlwifi,brcmsmac
root@tm2:/home/fabio# iwconfig wlan4
wlan4     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off

```
I'm on maverick. I did not test it because i have no router right now, so i can't tell you if it's stable enough for browsing

---

### Post by gwoodruff on 2011-04-09
This is the same driver I am trying to compile using 2.6.38-6-generic but I still get error 2 when trying make the module. The problem does seem to be with the headers, I have tried changing the osdep file using both suggestions above but still encounter error 2. Can you confirm you are running 2.6.38 or above? (Natty, 11.04)

Thanks, Gary

---

### Post by ernia on 2011-04-09
please, forgive me, i forget about a missing header, maybe the row you are searching for is
#include <linux/sched.h>
in the 
compat-wireless-2.6.39-rc1-3-s/compat/compat-2.6.39.c
if you are bulding the same version as me.

---

### Post by gwoodruff on 2011-04-09
I am trying to compile the driver under 2.6.38-6-generic. Can you tell me what folder this file is in and what changes to make? I am willing to try anything to get this to work I just need a little more direction.
Thanks,
Gary

---

### Post by ernia on 2011-04-09
if you download [http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-rc1-3.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-rc1-3.tar.bz2) and extract it you will have compat-wireless-2.6.39-rc1-3-s/compat/compat-2.6.39.c
edit it add to it, at the end of the include rows, the one of my previous post:
#include <linux/sched.h>
now 
make && make install
you will have the latest wireless driver.
you should load the module (ore reboot) and your card should work

edit: the url is [http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-rc1-3-s.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-rc1-3-s.tar.bz2)

---

### Post by gwoodruff on 2011-04-09
Thank you! That worked great. I did not have to edit the file. I downloaded from your link and make & make install, loaded my driver and I now have my wifi working under Natty!

Thanks again,
Gary

---

### Post by Green_Star on 2011-04-14
I tried by altering headers (as explained in this thread) and also tried without altering, with no luck. After the installation i can see related items in 'lsmod' after modprobing, but after the reboot, that item also gone. Help me in setting up my wireless. My machine is Ubuntu 10.04, 
 
I bought following wireless card
[http://www.dealextreme.com/p/ultra-mini-nano-usb-2-0-802-11n-150mbps-wifi-wlan-wireless-network-adapter-48166](http://www.dealextreme.com/p/ultra-mini-nano-usb-2-0-802-11n-150mbps-wifi-wlan-wireless-network-adapter-48166)

> 
....................
......................
...............
updates/drivers/bluetooth/hci_vhci.ko
updates/drivers/bluetooth/hci_uart.ko
kernel/net/bluetooth/l2cap.ko
updates/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/sco.ko

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:7d04 Hewlett-Packard DeskJet F2100 Printer series
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c51e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ dmesg | grep wlan

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ lsmod | grep 8192

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ sudo modprobe 8192cu

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ lsmod | grep 8192
8192cu                320753  0 
sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ dmesg | grep wlan

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:7d04 Hewlett-Packard DeskJet F2100 Printer series
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c51e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:7d04 Hewlett-Packard DeskJet F2100 Printer series
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c51e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
vboxnet0  no wireless extensions.
pan0      no wireless extensions.

sadhira@Sadhira:/tmp/compat-wireless-2.6.39-rc1-3-s$ uname -r
2.6.32-30-generic


---

### Post by ernia on 2011-04-14
i don't have the adapter with me so i'm not sure if what i'm saying is true.
check with

*dmesg | grep firmware*

if you have some errore related to

*/lib/firmware/rtlwifi/rtl8192cufw.bin*

or something similar.
if this is the case you can try to install linux-firmware and linux-firmware-nonfree from repo and load the module.
if it does not work download the latest linux-firmware files following

[http://lwn.net/Articles/294308/](http://lwn.net/Articles/294308/)    (you need git)

and put the required files in

*/lib/firmware/rtlwifi/rtl8192cufw.bin*

the firmware is pretty new:

[http://help.lockergnome.com/linux/PATCH-linux-firmware-Add-firmware-file-RTL8192CU--ftopict529890.html](http://help.lockergnome.com/linux/PATCH-linux-firmware-Add-firmware-file-RTL8192CU--ftopict529890.html)

after this try again to unload-reload the module

altering compat-wireless is not required anymore, probably they fixed something somewhere


EDIT check if you can download it from here:
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=rtlwifi/rtl8192cufw.bin;h=3aa75065747e546ba593195423ffb1f931337d6a;hb=4844fa169c8d8562289243b54e822a00a0a01082](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=rtlwifi/rtl8192cufw.bin;h=3aa75065747e546ba593195423ffb1f931337d6a;hb=4844fa169c8d8562289243b54e822a00a0a01082)

---

### Post by Green_Star on 2011-04-14
Thanks for your reply ernia,

I downloaded the bin file from the link you provided at end of your previous post and copied it to /lib/firmware/RTL8192SE/ , I do not know how to unload module(I am still learning linux), so I reboted, still no luck.

before copy the file and after copying and reboot I did not get anything when I tried the command *[COLOR="DarkRed"]dmesg | grep firmware[/COLOR]*, so I did *[COLOR="DarkRed"]sudo modprobe 8192cu[/COLOR]*, still nothing happenes for *[COLOR="DarkRed"]dmesg | grep firmware[/COLOR]*

---

### Post by ernia on 2011-04-15
i still think that it's a firmware problem and i still don't have the device here to be sure about that. :)
/lib/firmware/RTL8192SE/
is different from
/lib/firmware/rtlwifi/rtl8192cufw.bin
:)
if you have installed compat-wireless the correct module name should be rtl8192cu and not 8192cu, 8192cu is the proprietary driver ;)
you can check this with
modprobe -l | grep 8192cu   (let me know if you have both proprietary and compat wireless modules).
try again with correct path and module and check if it works.
if it does not work check dmesg with 
dmesg | grep 8192
or check the whole dmesg with
dmesg | less
and scroll the output to find where the problem is.
if the problem is still there maybe there is more than a firmware file to be loaded and you need to install the whole linux-firmware to be sure about that.
the command to unload a module is "sudo rmmod modulename".

---

### Post by Green_Star on 2011-04-15
> **ernia said:**
> i still think that it's a firmware problem and i still don't have the device here to be sure about that. :)
/lib/firmware/RTL8192SE/
is different from
/lib/firmware/rtlwifi/rtl8192cufw.bin
:)
if you have installed compat-wireless the correct module name should be rtl8192cu and not 8192cu, 8192cu is the proprietary driver ;)
you can check this with
modprobe -l | grep 8192cu   (let me know if you have both proprietary and compat wireless modules).
try again with correct path and module and check if it works.
if it does not work check dmesg with 
dmesg | grep 8192
or check the whole dmesg with
dmesg | less
and scroll the output to find where the problem is.
if the problem is still there maybe there is more than a firmware file to be loaded and you need to install the whole linux-firmware to be sure about that.
the command to unload a module is "sudo rmmod modulename".

Surprisingly I dont have a folder you mentioned, [COLOR="Purple"]/lib/firmware/rtlwifi/[/COLOR], instead I have [COLOR="Purple"]/lib/modules/2.6.32-30-generic/updates/drivers/net/wireless/rtlwifi/rtl8192cu[/COLOR].

I tried installing the compact drivers again, still no luck with wiress or folder which you expected. 


So, I guess I have to install linux-firmware, but donno how to do that, could you please? Please check belwo for the output of commands which you asked me.

---

### Post by Green_Star on 2011-04-18
> **ernia said:**
> i still think that it's a firmware problem and i still don't have the device here to be sure about that. :)
/lib/firmware/RTL8192SE/
is different from
/lib/firmware/rtlwifi/rtl8192cufw.bin
:)
if you have installed compat-wireless the correct module name should be rtl8192cu and not 8192cu, 8192cu is the proprietary driver ;)
you can check this with
modprobe -l | grep 8192cu   (let me know if you have both proprietary and compat wireless modules).
try again with correct path and module and check if it works.
if it does not work check dmesg with 
dmesg | grep 8192
or check the whole dmesg with
dmesg | less
and scroll the output to find where the problem is.
if the problem is still there maybe there is more than a firmware file to be loaded and you need to install the whole linux-firmware to be sure about that.
the command to unload a module is "sudo rmmod modulename".

Thanks man, finally your method worked by using following commands,

> 
sudo rmmod rtl8192cu
sudo modprobe 8192cu
sudo /etc/init.d/networking restart


---

### Post by katletz on 2011-04-30
Hi,

I stumbled across this forum when trying to install the driver for my EDUP EP-N8508 (USB) on a dual-core AMD64.

stock kernel
Linux cerberus 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
from Natty.

drivers
RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126
from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

Unfortunately no compilation out of the box. So I changed:

1. in: os_dep/osdep_service.c (line 305)
replace "init_MUTEX(pmutex)" with "sema_init(pmutex,1)"

2. in: os_dep/linux/usb_intf.c (line 917)
comment (or delete) the line
//pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time

(error: &#8216;struct usb_device&#8217; has no member named &#8216;autosuspend_delay&#8217;)

then the driver compiles and loads with
insmod ./8192cu.ko

(make install works too, now the module is automatically loaded upon boot)

I am not sure if this will break something (setting a non-existent variable to 0 shouldn't have a big influence...)
Maybe edup or the kernel maintainers can fix this (and actually get the drivers into the stock kernel).

thanks for your help,
Stefan

PS: you could get rid of two warnings if you also change in hal/rtl8192c/usb/rtl8192c_cmd.c
replace "%d" with "%lu" in lines 2045 and 2124

DBG_871X("Set RSVD page location to Fw Len(%d).\n",sizeof(RsvdPageLoc)); 
printk("%s H2C len(%d)\n",__FUNCTION__,sizeof(JoinBssRptParm));
(warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;)

still one to go:
os_dep/linux/ioctl_linux.c:478:1: warning: the frame size of 1072 bytes is larger than 1024 bytes

---

### Post by DerLonG on 2011-05-13
> **katletz said:**
> 
Unfortunately no compilation out of the box. So I changed:

1. in: os_dep/osdep_service.c (line 305)
replace "init_MUTEX(pmutex)" with "sema_init(pmutex,1)"

2. in: os_dep/linux/usb_intf.c (line 917)
comment (or delete) the line
//pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time

(error: ‘struct usb_device’ has no member named ‘autosuspend_delay’)


Thanks for that information! That worked fine!

---

### Post by gfuggs on 2011-10-01
> **nousernameavailable said:**
> just replace the init_MUTEX(prwlock) in os_dep/osdep_service.c with a sema_init(prwlock,1)

works like a charm

This worked to get my EW-7811UN going.  Make was giving an error in line 291 of osdep_service.c.

Running Mint 11, 2.6.38-11-generic-pae, downloaded driver version 2.0.939.20100726 from Edimax website today.

Per the suggestion above, I changed line 291 from "init_MUTEX(pwrlock)" to "sema_init(pwrlock,1)" in rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c

Works great.  Thanks.

---

### Post by saugeais25 on 2011-10-10
i have a problem with oneiric (10.10) i think because it' kernet 3.0...
the operation "make" do this result at the end :
```
"In file included from /home/nathalie/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/core/rtw_cmd.c:24:0:
/home/nathalie/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/include/osdep_service.h:49:29: erreur fatale: linux/smp_lock.h : Aucun fichier ou dossier de ce type
compilation terminée.
make[2]: *** [/home/nathalie/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/core/rtw_cmd.o] Erreur 1
make[1]: *** [_module_/home/nathalie/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.0.0-12-generic-pae »
make: *** [modules] Erreur 2"
```

a solution ???

sorry for my bad english

---

### Post by Xavi López on 2011-11-09
In order to compile the propietary Realtek 8192CU driver in a 3.0 kernel, you need to modify the following files in the tar.gz under the /driver directory: 

 - include/osdep_service.h (line 49): Change "linux/smp_lock.h" to "linux/smp.h"
 - include/rtw_io.h (line 36): Change "linux/smp_lock.h" to "linux/smp.h"

---

### Post by dazcom on 2011-11-24
Xavi López, your solution is really work (for me under LMDE x64)! Thnx a lot!

---

### Post by princ_zuku on 2011-12-11
hello, I have 11.04 Ubuntu 2.6.38-13.52-generic 2.6.38.8
and ew-7811un. Succesfully compiled and installed (make && make install) after editing the "mutex to semi"...

and entered:
   modprobe 8192cu (don't know what does it do, probably driver load)
rebooted
but iwconfig neither ifconfig does not see and there is no life symptoms
but if I unplug and plug it in, ubuntu shows me message "network disconnected", and if I turn wireless off thorough laptop fn keys, it causes kernel panic and reboots
help pls

---

### Post by princ_zuku on 2011-12-11
already working!))
here is the solution [http://ubuntuforums.org/showthread.php?p=11531292#post11531292](http://ubuntuforums.org/showthread.php?p=11531292#post11531292)

---

### Post by Donaldus on 2012-01-31
Hello Guys and Ladies, 


I've tried to follow your expanations without success. The problem being, I can't even make it through the "make" command. It says (in a nutshell, my main computer is only connected wirelessly) 

Entering directory '/lib/modules/3.0.0-15-generic-pae/build'
*** No rule to make target 'modules'. Stop
Leaving directory '/lib/modules/..../build'
make : ***[modules] Error 2

Do you have any idea?

---

### Post by chili555 on 2012-01-31
> **Donaldus said:**
> Hello Guys and Ladies, 


I've tried to follow your expanations without success. The problem being, I can't even make it through the "make" command. It says (in a nutshell, my main computer is only connected wirelessly) 

Entering directory '/lib/modules/3.0.0-15-generic-pae/build'
*** No rule to make target 'modules'. Stop
Leaving directory '/lib/modules/..../build'
make : ***[modules] Error 2

Do you have any idea?Yes. I have the idea that you may not have build-essential and linux-headers-generic installed. Can you check and install if not already and try again?

I also believe that rtl8192cu is installed by default in 11.10. Is it not working for you? Please post:```
lsusb
dmesg | grep 819
```

---

