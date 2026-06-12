---
title: "problem realtek 8723 driver"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by Seldon on 2012-07-05
Hello,

Im just trying to install ubuntu on a new computer. I installed ubuntu 12 but did not recognize the wireless device. It is a realtek 8723. I already found the drivers on other topic but I can not install them.

When I do make I get the following error:

make -C /lib/modules/3.2.0-23-generic/build M=/home/seldon/realtek driver/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
make[1]: *** No rule to make target `driver/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2


I can not find a solution

I have already installed build-essentials and linux-headers-3.2.0-23-generic 

unname-e gives me 3.2.0-23-generic 

Anyone out there that can help me please

Thanks

---

### Post by chili555 on 2012-07-05
> I have already installed build-essentialAre you sure it's all in place?```
sudo dpkg -s build-essential
```I am very interested in your device, old driver dawg that I am. Please post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by Seldon on 2012-07-06
Thanks for answering

I did as you say:

When I do sudo dpkg -s build-essential I get:

Package: build-essential
Status: install ok installed
Multi-Arch: foreign
Priority: optional
Section: devel
Installed-size: 37
Maintainer: Ubuntu Developers
Architecture: amd64
Version: 11.5ubuntu2
Depends: libc6-dev | libc-dev, gcc (>= 4:4.4.3), make, dpkg-dev (>= 1.13.5)
Description: .....


When I do lspci -nn | grep 0280 I get

[0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]


It seems the package is well installed, no idea why I can not do make.

Thanks for the help

---

### Post by chili555 on 2012-07-06
I downloaded the packages here: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

I extracted and made the files perfectly without even a warning. The only thing that may be different is that I built after sudo su:```
cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
[COLOR="Red"]sudo su[/COLOR]
make
etc., etc.
```I don't know if the 'make install' installs the firmware properly, we'll need to look at that.

Please try with sudo su.

---

### Post by Seldon on 2012-07-06
The files I am trying to install I got them from the same thread you mention.

I also used sudo su before running make and getting the error on the first message.

Thanks for the help

---

### Post by chili555 on 2012-07-06
Please try, with a wired ethernet connection:```
sudo apt-get install --reinstall build-essential
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Now try again.

---

### Post by Seldon on 2012-07-06
I did as you say and I still have the problem when I do make (after sudo su)

The error is still:

make -C /lib/modules/3.2.0-23-generic/build M=/home/seldon/realtek driver/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
make[1]: *** No rule to make target `driver/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2

Any other ideas?  Thanks

---

### Post by chili555 on 2012-07-06
> make[1]: *** No rule to make target `[COLOR="Red"]driver[/COLOR]/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .2012'. Stop.I am still mystified. What directory are you starting from? Is the Makefile located in the working directory?```
ls
```I get, for comparison:> root@LAPTOP60:/home/chili/Desktop/Forum/Seldon/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.2.0-26-generic-pae/build M=/home/chili/Desktop/Forum/Seldon/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
  CC [M]  /home/chili/Desktop/Forum/Seldon/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
  CC [M]  /home/chili/Desktop/Forum/Seldon/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rc.o
  CC [M]  /home/chili/Desktop/Forum/Seldon/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/debug.o
etc., etc.Yikes!! By any chance, is the directory named 'realtek driver'? Linux and the terminal don't like spaces in directory names very well. If so, please rename the directory to realtek and try again:```
cd ~/realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
sudo su
make
make install
modprobe rtl8723e
exit
```

---

### Post by Seldon on 2012-07-06
EXCELENT!! it was the space in the folder, a really stupid error. I am writing this reply using wi fi conection. 

Thanks a lot for the help and for being patient and for spending time reading my posts.

Thanks.

Now I need to see how to make the sound work (new computer!)

Regards!

---

### Post by chili555 on 2012-07-06
Glad it's working and I'm glad to know how to get this new device working. Have fun!

---

### Post by mossman79 on 2012-07-13
Hello. I am having the same problem that Sheldon was having, but I don't have any spaces in the directory names I am trying to compile from. Is there any chance you can help me to get my wifi working? 

A point to note, I have been trying to compile rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 (not rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .2012). 

A further point to note, I am new to Linux and I am working in Ubuntu 10.04.

---

### Post by mossman79 on 2012-07-13
Sorry. The above relates to the following thread...
[http://ubuntuforums.org/showthread.php?t=2017622](http://ubuntuforums.org/showthread.php?t=2017622)

---

### Post by chili555 on 2012-07-13
> **mossman79 said:**
> Hello. I am having the same problem that Sheldon was having, but I don't have any spaces in the directory names I am trying to compile from. Is there any chance you can help me to get my wifi working? 

A point to note, I have been trying to compile rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 (not rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .2012). 

A further point to note, I am new to Linux and I am working in Ubuntu 10.04.Do you have linux-headers-generic and build-essential installed? What is the error given on the terminal?

---

### Post by mossman79 on 2012-07-14
Hi. 

Thanks very much for your reply. 

I have followed your instructions up to the point you say "Yikes!!". All fine using my wired connection, I have installed linux-headers-generic and build-essential, and the other one listed below linux-headers-`uname -r` (do I need this one?).

My driver is saved in "/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011", hence my comment about no spaces in my folder location. But when I go...

sudo su
make

I get the following code...

```
make -C /lib/modules/2.6.32-41-generic/build M=/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-41-generic'
  CC [M]  /home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o
In file included from /home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:32:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/wifi.h: In function ‘rtl_find_sta’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/wifi.h:2094: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
include/net/mac80211.h:2086: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:34:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.h: At top level:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.h:143: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.h:143: warning: its scope is only this definition or declaration, which is probably not what you want
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘_rtl_init_mac80211’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:322: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:322: error: (Each undeclared identifier is reported only once
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:322: error: for each function it appears in.)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_tx_agg_start’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:991: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2033: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_tx_agg_stop’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1020: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2074: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1274: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: At top level:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1332: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1332: error: parameter 2 (‘smps’) has incomplete type
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_make_smps_action’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1352: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1354: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1355: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1357: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1359: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1361: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1363: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1365: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1367: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: At top level:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1376: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1376: error: parameter 3 (‘smps’) has incomplete type
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_send_smps_action’:
/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1404: error: type of formal parameter 2 is incomplete
make[2]: *** [/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o] Error 1
make[1]: *** [_module_/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-41-generic'
make: *** [all] Error 2
root@david-laptop:/home/david/Drivers/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# ^C

```

---

### Post by chili555 on 2012-07-14
You have:> Entering directory `/usr/src/linux-headers-[COLOR="Red"]2.6.32[/COLOR]-41-generic'The *readme* for your package says, in part:> We don't support kernel 2.6.24-2.6.34 directly, Because there are
lots of issues in mac80211 from kernel 2.6.24-2.6.34,
So we suggest you to use the latest kernel >= 2.6.35.

but if you want to use our driver in an old kernel,
you can use compat-wireless. this methord can support all kernel
versions higher than 2.6.24, and you can use all functions
of our driver like you use it in the latest kernel version.A version of compat-wireless is included in the package as well as instructions to compile it. I suggest you try it unless you are ready to upgrade to Ubuntu 12.04 where your device will probably work right out of the box!

---

### Post by mossman79 on 2012-07-15
Hi there. 

Thanks for getting back to me yesterday, I've been looking into your suggestions. 

I tried the first to install compat-wireless, no change! :(

I then upgraded to 12.04, but still no wireless. :(

I have tried to install the same driver again in 12.04, and the compat-wireless, but to no avail! So looked again to see if I am installing the correct driver...in Win7 the wifi works fine and is using the following card:

Realtek RTL8723AE Wireless LAN 802.11n PCI-E NIC version 2002.2.110.2012

I've had a look to see if I can download a linux driver for this card, but again to no avail. I'm now stuck. 

If you have any suggestions that would be great. Thanks...

---

### Post by chili555 on 2012-07-15
> I then upgraded to 12.04, but still no wireless.Let's have a look at:```
lspci -nn | grep 0280
```Thanks.

---

### Post by mossman79 on 2012-07-15
david@david-SATELLITE-C855-14R:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

---

### Post by chili555 on 2012-07-15
> **mossman79 said:**
> david@david-SATELLITE-C855-14R:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:[COLOR="Red"]8723[/COLOR]]You need this file:> rtl_92ce_92se_92de_[COLOR="Red"]8723[/COLOR]ae_linux_mac80211_0006.0514 .2012And *NOT* this file:> rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011Please download it and compile as linked above.

---

### Post by mossman79 on 2012-07-15
Hurrah! Wifi working! I couldn't find that driver at first, but eventually found a link to download it in the following thread...

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized) 

Thanks very much for your help. :D

---

### Post by chili555 on 2012-07-15
Awesome! Glad it's working. Have fun.

---

### Post by rob62 on 2012-07-15
On Ubuntu 12.04 I've managed to make and install the RTL8723e drivers in 8723AE_8723AU_Linux_support_0419.tar.gz and rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz.

However the wireless networking still fails to work.
Boot.log contains the following related entries:

[   15.487227] usbcore: registered new interface driver btusb
[   15.489817] rtl8723e: disagrees about version of symbol efuse_read_1byte
[   15.489820] rtl8723e: Unknown symbol efuse_read_1byte (err -22)
[   15.489831] rtl8723e: Unknown symbol rtl_process_phyinfo (err 0)
[   15.489834] rtl8723e: disagrees about version of symbol rtl_cam_reset_all_entry
[   15.489836] rtl8723e: Unknown symbol rtl_cam_reset_all_entry (err -22)
[   15.489841] rtl8723e: disagrees about version of symbol rtl_cam_empty_entry
[   15.489843] rtl8723e: Unknown symbol rtl_cam_empty_entry (err -22)
[   15.489845] rtl8723e: disagrees about version of symbol rtl_cam_del_entry
[   15.489847] rtl8723e: Unknown symbol rtl_cam_del_entry (err -22)
[   15.489851] rtl8723e: disagrees about version of symbol rtl_cam_mark_invalid
[   15.489853] rtl8723e: Unknown symbol rtl_cam_mark_invalid (err -22)
[   15.489861] rtl8723e: disagrees about version of symbol ieee80211_find_sta
[   15.489862] rtl8723e: Unknown symbol ieee80211_find_sta (err -22)
[   15.489866] rtl8723e: disagrees about version of symbol rtl_pci_disconnect
[   15.489868] rtl8723e: Unknown symbol rtl_pci_disconnect (err -22)
[   15.489870] rtl8723e: disagrees about version of symbol rtl_pci_suspend
[   15.489872] rtl8723e: Unknown symbol rtl_pci_suspend (err -22)
[   15.489878] rtl8723e: Unknown symbol rtl_signal_scale_mapping (err 0)
[   15.489886] rtl8723e: disagrees about version of symbol rtl_ps_enable_nic
[   15.489888] rtl8723e: Unknown symbol rtl_ps_enable_nic (err -22)
[   15.489890] rtl8723e: disagrees about version of symbol rtl_pci_resume
[   15.489892] rtl8723e: Unknown symbol rtl_pci_resume (err -22)
[   15.489897] rtl8723e: Unknown symbol rtl_evm_db_to_percentage (err 0)
[   15.489901] rtl8723e: disagrees about version of symbol rtl_cam_add_one_entry
[   15.489902] rtl8723e: Unknown symbol rtl_cam_add_one_entry (err -22)
[   15.489908] rtl8723e: Unknown symbol rtl_query_rxpwrpercentage (err 0)
[   15.489911] rtl8723e: disagrees about version of symbol rtl_efuse_shadow_map_update
[   15.489913] rtl8723e: Unknown symbol rtl_efuse_shadow_map_update (err -22)
[   15.489915] rtl8723e: disagrees about version of symbol rtl_get_tcb_desc
[   15.489917] rtl8723e: Unknown symbol rtl_get_tcb_desc (err -22)
[   15.489919] rtl8723e: disagrees about version of symbol rtl_ps_disable_nic
[   15.489920] rtl8723e: Unknown symbol rtl_ps_disable_nic (err -22)
[   15.489925] rtl8723e: disagrees about version of symbol rtl_cam_get_free_entry
[   15.489927] rtl8723e: Unknown symbol rtl_cam_get_free_entry (err -22)
[   15.489929] rtl8723e: disagrees about version of symbol rtl_pci_probe
[   15.489930] rtl8723e: Unknown symbol rtl_pci_probe (err -22)
[   15.489933] rtl8723e: disagrees about version of symbol rtl_cam_delete_one_entry
[   15.489935] rtl8723e: Unknown symbol rtl_cam_delete_one_entry (err -22)

---

### Post by chili555 on 2012-07-15
> On Ubuntu 12.04 I've managed to make and install the RTL8723e drivers in 8723AE_8723AU_Linux_support_0419.tar.gz and rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .2012.tar.gz.Why both? You should only need the second one.

Please try again:```
cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012  [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
sudo su
make clean
make
make install
exit
```Any errors?

---

### Post by rob62 on 2012-07-15
Thanks for the quick response, Chili555.

I did as suggested but still get the very same error.
The error does not present in /var/log/boot.log, but in /var/log/dmesg.

---

### Post by chili555 on 2012-07-15
Do you have *linux-backports-modules-cw* installed? On my test mule, I get the same error with cw installed but it loads without drama after I removed it. Please remove it and reboot; then reload rtl8723e and let me have your report tomorrow.

Don't ask me how I know this. I need to get a real life!

---

### Post by rob62 on 2012-07-16
Thanks again for the advice chili555.

Unfortunately I don't have *linux-backports-modules-cw* installed.

---

### Post by chili555 on 2012-07-16
Let's see:```
lsb_release -d
arch
lsusb
```Thanks.

---

### Post by rob62 on 2012-07-16
Hi chili555

I've got a clean 12.04 install with the network driver installed and working, but wireless realtek 8723e installed but not working.

Additional Drivers shows *Qualcomm Atheros Gigabit Ethernet Driver* activated and currently in use, but *Realtek 8723e 802.11n PCI wireless* activated but not currently in use.

Here is the requested output:

robin@robin-comp:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS

robin@robin-comp:~$ arch
x86_64

robin@robin-comp:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c50d Logitech, Inc. Cordless Mouse
Bus 003 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 003: ID 0930:021d Toshiba Corp. 
Bus 001 Device 004: ID 10f1:1a43 Importek 
Bus 001 Device 005: ID 1164:1ee9 YUAN High-Tech Development Co., Ltd

Thanks,
Robin

---

### Post by chili555 on 2012-07-17
> robin@robin-comp:~$ arch
x86_[COLOR="Red"]64[/COLOR]I don't think the driver was written for 64-bit. You could email Realtek:> description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>Or you could try a 32-bit live CD and see if it compiles and loads without error, as I am confident it will.

If you have more than 2 Gb of RAM, as most of us do, it will be recognized with a 32-bit pae kernel. From my machine:> chili@LAPTOP60:~$ free
             total       used       free     shared    buffers     cached
[COLOR="Red"]Mem:       3914384[/COLOR]    3558076     356308          0     280312    2503648
-/+ buffers/cache:     774116    3140268
Swap:      6914044       7112    6906932
chili@LAPTOP60:~$ uname -r
3.2.0-26-generic-[COLOR="Red"]pae[/COLOR]
chili@LAPTOP60:~$ arch
[COLOR="Red"]i686[/COLOR]


---

### Post by rob62 on 2012-07-17
Thanks chili555,

I've taken your advice and emailed the authors of the driver package the relevant information.

I'll test 32bit Ubuntu 12.04 LTS later today when I get a chance and get back to you.

Much appreciated,
Robin

---

### Post by szbab on 2012-07-17
Hello
Sorry for my English (translated with google)
Here is the latest realtek driver from the month of May to compile:

[http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ](http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ)

---

### Post by rob62 on 2012-07-18
Hi Chili555

32bit Ubuntu 12.04LTS exhibits exactly the same behaviour as the 64bit version with regard to realtek 8723 driver on my Toshiba P870/027 notebook computer.

It looks like I'll continue using a 15 metre ethernet cable for a while longer yet ...

Thanks for all the advice though. 

I would never have thought of attempting the 32bit install and it did have a real chance of fixing the issue.

I've also emailed the authors of the driver package. Maybe that will pan out.

Regards,
Robin

---

### Post by rob62 on 2012-07-18
> **szbab said:**
> Hello
Sorry for my English (translated with google)
Here is the latest realtek driver from the month of May to compile:

[http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ](http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ)

Thanks for your suggestion szbab. That driver package is the one that I have installed.

Regards,
Robin

---

### Post by rob62 on 2012-08-21
I have finally managed to install rtl8723e.

Problem I had was that Atheros Ethernet on my notebook also required me to install a driver package **compat-wireless-2012-07-03-pc**

That package compiles and installs an **rtlwifi.ko** that is incompatible with the **rtlwifi.ko** compiled with the rtl8723e package **rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012**

I did a sudo make uninstall and sudo make clean on both aforementioned packages, then was successful installing **rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012**

At this stage I can't install both driver packages successfully. So now I've got rtl8723e wireless, but no atheros ethernet. I expect this will be fixed in a future kernel release.

---

### Post by Suncoaster on 2012-11-01
I had this working in 12.04 but now in 12.10 the driver will not compile. I get an error HW_BEACON_FILTER not defined or something like that, I forget the exact wording.  So I have gone back to a long cable.

When will this module be included in the kernel, so that we will not have to jump through these hoops just to get our wireless card to work.:rolleyes:

---

### Post by chili555 on 2012-11-01
> **Suncoaster said:**
> I had this working in 12.04 but now in 12.10 the driver will not compile. I get an error HW_BEACON_FILTER not defined or something like that, I forget the exact wording.  So I have gone back to a long cable.

When will this module be included in the kernel, so that we will not have to jump through these hoops just to get our wireless card to work.:rolleyes:Please open the file base.c with any text editor; gedit for example. Go down to line 320 and comment out the line as I've indicated here:> 	/* <5> set hw caps */
	hw->flags = IEEE80211_HW_SIGNAL_DBM |
	    IEEE80211_HW_RX_INCLUDES_FCS |
[COLOR="Red"]/*[/COLOR]	    IEEE80211_HW_BEACON_FILTER | [COLOR="Red"]*/[/COLOR]
	    IEEE80211_HW_AMPDU_AGGREGATION |
	    IEEE80211_HW_REPORTS_TX_ACK_STATUS |
	    IEEE80211_HW_CONNECTION_MONITOR |
	    /* IEEE80211_HW_SUPPORTS_CQM_RSSI | */
	    IEEE80211_HW_MFP_CAPABLE | 0;

	/* swlps or hwlps has been set in diff chip in init_sw_vars */Everything before and after is unchanged. Proofread, save and close the text editor. Now back to the terminal:```
cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012  [COLOR="Red"]<--or wherever you extracted the package[/COLOR]
make clean
make
sudo make install
sudo modprobe rtl8723e
```It will probably be included soon. We are not the developers here, so I have no control over what's included and how soon.

Reference: [http://askubuntu.com/questions/203078/wireless-card-realtek-rtl8723ae-bt-driver-not-compiling-on-quetzal](http://askubuntu.com/questions/203078/wireless-card-realtek-rtl8723ae-bt-driver-not-compiling-on-quetzal)

---

### Post by Suncoaster on 2012-11-01
Thank you, followed advice and all is now working.:guitar:

As for my whinge I know you guys are not the developers, it was more in the line of a rhetorical question:)

Once again thanks for your help

---

### Post by tonino99 on 2012-12-08
> **chili555 said:**
> You need this file:And *NOT* this file:Please download it and compile as linked above.

Hi chilli555, thaks for your help about Realtek 8723.
I have followed waht you have said with this probem. and i succeed to intall the driver but i cant turn on the wifi. My computer is Toshiba Satellite C855-21L with ubuntu 12.04.01 and realtek 8723 for wireless. Can you help me?

This i what i get:

pilar@pilar-SATELLITE-C855-21L:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

pilar@pilar-SATELLITE-C855-21L:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

---

### Post by chili555 on 2012-12-08
What does this tell us?

```
rfkill list all
dmesg | grep rtl
```

---

### Post by tonino99 on 2012-12-08
Thaks for replying:

pilar@pilar-SATELLITE-C855-21L:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by tonino99 on 2012-12-08
I forgot the other command:

pilar@pilar-SATELLITE-C855-21L:~$ dmesg | grep rtl
[   14.013931] rtl8723e 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.013945] rtl8723e 0000:02:00.0: setting latency timer to 64
[   14.031260] firemare: rtl8723fw_B.bin
[   14.516161] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.516603] rtlwifi: wireless switch is on

---

### Post by chili555 on 2012-12-08
'Hard blocked:yes' suggests the wireless switch has the wireless turned off. Can you please find it and switch it to On?

---

### Post by tonino99 on 2012-12-09
Thanks chilli555, problem solved with Realtek 8723 driver. This last part was the easiest one, just unblocked clicking the f12.-
Now, let's go for the other problem I found with installing ubuntu 12.04 in Toshiba satellite c855-21L: when I shutdown the computer it gets restart by itself unless I close the cover before it gets completely shutted down. Let's go for it.
Thanks again.

---

### Post by chili555 on 2012-12-09
> **tonino99 said:**
> Thanks chilli555, problem solved with Realtek 8723 driver. This last part was the easiest one, just unblocked clicking the f12.-
Now, let's go for the other problem I found with installing ubuntu 12.04 in Toshiba satellite c855-21L: when I shutdown the computer it gets restart by itself unless I close the cover before it gets completely shutted down. Let's go for it.
Thanks again.That's a question for General Help and for someone smarter than me! [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by hjolli on 2012-12-21
I have RTL8723AE and I am though running Linux Mint, this should also work on ubuntu, since Mint is just ubuntu with gnome
And this is what got it working for me, but I followed this forum here (which is a bit confusing and on a SUSE forum, so I put it here step by step what was needed)[http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell.html)

1. sudo su -

2. cd /home/hjolli/Downloads (I just want to have everything I download there, then it's never lost, but it doesn't really matter where you save your stuff as long you know where it is)

3. Download compat-wireless:  
  wget [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-10-03.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-10-03.tar.bz2)

4. Download rtl8723aa_master_patch: 
  wget [http://www.lwfinger.com/realtek_drivers/rtl8723ae_master_patch](http://www.lwfinger.com/realtek_drivers/rtl8723ae_master_patch)

5. Download a proper kernel that is compatible with those pathces: 
   wget [http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.6.7](http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.6.7) -O linux-kernel-3.6.7

6. Download and install the firmware for this card, you will need to install git as well if you don't have it.
  apt-get install git
  git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
  mkdir /lib/firmware/rtlwifi
  cp -v linux-firmware/rtlwifi/rtl8723* /lib/firmware/rtlwifi/


And now compile and install this stuff

7. start with the kernel (this will take some time)
 chmod +x linux-kernel-3.6.7 
 sh ./linux-kernel-3.6.7
 reboot

8. now the compat-wireless stuff (remember that I have everything in my Downloads folder)
   cd /home/hjolli/Downloads/compat-wireless-2012-10-03/ 
   patch -p1 < ../rtl8723ae_master_patch 
   make
   make install
   modprobe -v rtl8732ae

Now it should be working, but if not then just reboot (that's what I did)
   reboot

And now I can see all the wireless networks around me and connect (though it does take some time to connect and doesn't allwyas connect and just gives me the popup window to enter the encription key again and again untill I moved closer to the router (which I don't have to on any other computer/phone in the home)

---

### Post by Sean Moran on 2012-12-26
> **hjolli said:**
>  ... this is what got it working for me ...
Many thanks Hjolli.  I've been searching and searching since yesterday and no luck until I found your solution.  

New Toshiba U840W with the Realtek 8723 wireless, and 12.04 Precise w/GNOME, 3.2.0-35 kernel so I took a chance and omitted the kernel build, and the rest worked like a charm.

Much appreciate your help as I'll be losing this local mobile broadband stick on Monday and back to the hotel wifi when I move countries on Tuesday, so just in the nick of t-t-t-time.
:popcorn:

---

### Post by lnxusr351 on 2012-12-30
> **hjolli said:**
> I have RTL8723AE and I am though running Linux Mint, this should also work on ubuntu, since Mint is just ubuntu with gnome
And this is what got it working for me, but I followed this forum here (which is a bit confusing and on a SUSE forum, so I put it here step by step what was needed)[http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell.html)

1. sudo su -

2. cd /home/hjolli/Downloads (I just want to have everything I download there, then it's never lost, but it doesn't really matter where you save your stuff as long you know where it is)

3. Download compat-wireless:  
  wget [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-10-03.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-10-03.tar.bz2)

4. Download rtl8723aa_master_patch: 
  wget [http://www.lwfinger.com/realtek_drivers/rtl8723ae_master_patch](http://www.lwfinger.com/realtek_drivers/rtl8723ae_master_patch)

5. Download a proper kernel that is compatible with those pathces: 
   wget [http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.6.7](http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.6.7) -O linux-kernel-3.6.7

6. Download and install the firmware for this card, you will need to install git as well if you don't have it.
  apt-get install git
  git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
  mkdir /lib/firmware/rtlwifi
  cp -v linux-firmware/rtlwifi/rtl8723* /lib/firmware/rtlwifi/


And now compile and install this stuff

7. start with the kernel (this will take some time)
 chmod +x linux-kernel-3.6.7 
 sh ./linux-kernel-3.6.7
 reboot

8. now the compat-wireless stuff (remember that I have everything in my Downloads folder)
   cd /home/hjolli/Downloads/compat-wireless-2012-10-03/ 
   patch -p1 < ../rtl8723ae_master_patch 
   make
   make install
   modprobe -v rtl8732ae

Now it should be working, but if not then just reboot (that's what I did)
   reboot

And now I can see all the wireless networks around me and connect (though it does take some time to connect and doesn't allwyas connect and just gives me the popup window to enter the encription key again and again untill I moved closer to the router (which I don't have to on any other computer/phone in the home)

In my case, should I go this route? Especially seeing that I did have wireless up and functional until late last night. After running all the tests in this thread, there should be no reason why I cannot connect. 
I read a bit on here about uninstalling backports... I'm not sure how to undo that, if I did install them. Any help would be greatly apreciated.

---

### Post by chili555 on 2012-12-30
> **lnxusr351 said:**
> In my case, should I go this route? Especially seeing that I did have wireless up and functional until late last night. After running all the tests in this thread, there should be no reason why I cannot connect. 
I read a bit on here about uninstalling backports... I'm not sure how to undo that, if I did install them. Any help would be greatly apreciated.Let's begin at the beginning. What device do you have?```
lspci -nn | grep 0280
```If you had the device working, what did you do to get it working? What did you compile? Can you load the driver now?```
sudo modprobe rtl8723ae
```Is a wireless interface created?```
iwconfig
```

---

### Post by lnxusr351 on 2012-12-30
> **chili555 said:**
> Let's begin at the beginning. What device do you have?```
lspci -nn | grep 0280
```If you had the device working, what did you do to get it working? What did you compile? Can you load the driver now?```
sudo modprobe rtl8723ae
```Is a wireless interface created?```
iwconfig
```

I have a Toshiba Satallite L855 (Christmas present). Dual boot Windows 8 and Ubuntu 12.10. 64bit system, i7 processor, blah, blah.

lspci -nn is:```
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
```

I compiled the latest driver for my Realtek 8723 (rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012) using info found on ask ubuntu. It built and installed without any issues. It worked great last night, but I did a reboot and now, no wifi. I also had to compile drivers for ethernet connection as well, which became a serious chore when doing so without any data connection. I did figure out though, that I could tether to my Asus TF101 tablet in order to gain access.

I tried to load the driver using the sudo modprobe command, but it gives me an error.

iwconfig gives me ```
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```

BTW, chili, I appreciate the time. You are far more knowledgeable than I, but I'm usually able to fix most of what I mess up.... It helps to ask questions when you get stuck, you know?

The website I used to get the nfo I needed.
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

More information: 
I did a sudo lshw -C network -numeric and this is what came up:
```
  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet [1969:1091]
       vendor: Atheros Communications Inc. [1969]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:26:6c:1e:3b:44
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx firmware=alx latency=0 multicast=yes port=twisted pair
       resources: irq:42 memory:c8500000-c853ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd. [10EC:8723]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 20:68:9d:a2:23:e6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723e driverversion=3.5.0-21-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:c8400000-c8403fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 1a:98:89:7f:a2:7b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.92 multicast=yes
```

---

### Post by chili555 on 2012-12-30
> wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:offLooks like you have wireless to me!> I tried to load the driver using the sudo modprobe command, but it gives me an error.I'd love to know what it is. I'd also love to see:```
sudo modprobe rtl8723ae
dmesg | grep -i rtl
```Thanks.

---

### Post by lnxusr351 on 2012-12-30
> **chili555 said:**
> Looks like you have wireless to me!I'd love to know what it is. I'd also love to see:```
sudo modprobe rtl8723ae
dmesg | grep -i rtl
```Thanks.

OK chili, this is going to sound ridiculous, but I booted into Windoze and the wifi wasn't working there either! I did that fix garbage that windows 8 does and shut down the computer rather than rebooting (I think this computer has some sort of fastboot -- like in android). I waited 10 minutes, walked into my computer room and fired up the computer... I now have wifi working again on both sides. I guess the hardware was the issue (the Military calls this FM -- ie: f'ing magic -- or maybe its SNAFU ie: Situation Normal, All F'ed Up!-lol). If you'd still like me to run the commands in terminal I'd be happy to. Thank you for your assistance, I greatly appreciate it. 
-Mike:D

---

### Post by chili555 on 2012-12-31
In one of my many lurid previous lives, it was known as PFM, where the P stands for 'pure.' That same group also often said it's sometimes better to be lucky than good. I'll take a solved working wireless device however I can get it!

Glad it's working. Have fun!

---

### Post by selopo on 2013-01-02
Same magic here. After struggling until late I realised that it only works when you shutdown. A reboot doesn't show the wifi networks.

I didn't have more time to investigate and I don't know if it's somehow related to the poweroff and reboot bug present in the Toshibas. This other problem is apparently fixed in kernel 3.8. 

I guess it's a matter of wait for the fixes and use the workarounds for the time being.

---

### Post by selopo on 2013-01-07
I discovered that if the wifi is manually disconnected from the panel then it works after reboot.

So what I did is to create a simple script and place it in /etc/rc6.d 

 #! /bin/sh

echo "Killing Wifi upon reboot"
/usr/sbin/rfkill block 1


This is of course temporary until the bloody driver is supported in a new kernel but it makes the trick until then.

Cheers

---

### Post by manee1982 on 2013-01-07
Thnak You very much really .. mister chili555

really very much ... you make my day nice

it's work for me

---

### Post by Prioryjk on 2013-01-09
Thanks Chili555 I had the same issue and this fixed my problem :)

---

### Post by Dayyanah on 2013-01-20
hello
im new to ubuntu
im stil having trouble
i went thru all these steps, but i still cant get the wireless working... the make shows me all error2

---

### Post by chili555 on 2013-01-20
> **Dayyanah said:**
> hello
im new to ubuntu
im stil having trouble
i went thru all these steps, but i still cant get the wireless working... the make shows me all error2Seeing the exact error will help us greatly. 'Error 2' could be any number of things. Please post it.

---

### Post by jimford on 2013-01-29
OK, so I'm sitting here in front of a brand new laptop, on which I've just installed Xubuntu 12.10, and the built-in wireless doesn't work, so I'm having to use an ethernet connection.

lspci tells me that I have the Realtek 8723 controller fitted, so judging by this thread I have problems!

I've tried downloading, compiling and installing the drivers, detailed earlier in the thread, and after modprobing, can see the drivers installed. Dmesg also shows:

firemare: rtl8723fw_B.bin
ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
rtlwifi: wireless switch is on

Also wlan1 is up:

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

I've now run out of ideas and would welcome some assistance to free me of being tethered with a cable to the net, please!

Jim

---

### Post by chili555 on 2013-01-29
We wonder why it is wlan1. Was or is there a possibly conflicting wlan0? Do we need to blacklist something? What does this tell us?```
dmesg | grep rtl
rfkill list all
sudo iwlist wlan1 scan
```

---

### Post by jimford on 2013-01-30
> **chili555 said:**
> We wonder why it is wlan1. Was or is there a possibly conflicting wlan0? Do we need to blacklist something? What does this tell us?```
dmesg | grep rtl
rfkill list all
sudo iwlist wlan1 scan
```

Arrrgh - 'rfkill' (a command I'm not familiar with) gave the clue - it showed the wireless LAN was hard blocked! 'Hard blocked' is again a term I'm not familiar with, but I correctly deduced that it's a hardware switch. 

As a last resort (!) I looked at the manual (such as it is!) and there's a key combination for turning on the wireless LAN. It's all working fine now.

iwconfig still shows that wlan1 is used, instead of wlan0. I'm not sure I know why.

Many thanks, 'Chili555'!

jim

---

### Post by chili555 on 2013-01-30
> **jimford said:**
> Arrrgh - 'rfkill' (a command I'm not familiar with) gave the clue - it showed the wireless LAN was hard blocked! 'Hard blocked' is again a term I'm not familiar with, but I correctly deduced that it's a hardware switch. 

As a last resort (!) I looked at the manual (such as it is!) and there's a key combination for turning on the wireless LAN. It's all working fine now.

iwconfig still shows that wlan1 is used, instead of wlan0. I'm not sure I know why.

Many thanks, 'Chili555'!

jimAll's well that ends well. I'm glad it's working. Hey, I'll take a solved case any way I can get it!

---

### Post by jimford on 2013-01-30
> **chili555 said:**
> All's well that ends well. I'm glad it's working. Hey, I'll take a solved case any way I can get it!

Hmm, maybe I spoke too soon!

Sometimes the wireless LAN comes up on boot, but often it doesn't. I wonder if it's anything to do with a driver conflict, because the interface is still wlan1 instead of wlan0? It needs a bit more looking into - possibly blacklisting a rogue driver. Any ideas of what I should be looking for, please?

Jim

Oh - and if you could possibly punt a bit of your Carolina weather over here, I'd be doubly grateful. It's pretty cold and miserable at the moment!

;^)

---

### Post by chili555 on 2013-01-30
> Oh - and if you could possibly punt a bit of your Carolina weather over here, I'd be doubly grateful. It's pretty cold and miserable at the moment!What part would you most like? The tornado watch or the 70 mph winds?? It is about 74 F, however. Weird.

Does the wireless spring to life if you merely load the driver?```
sudo modprobe rtl8723ae
```If so, let's load it automatically on boot:```
sudo su
echo rtl8723ae >> /etc/modules
exit
```If that doesn't do it, feel free to post back. If my house is still standing, I'll be happy to help.

---

### Post by jimford on 2013-01-31
The driver is loaded on boot, but although wlan1 is shown with iwconfig, wireless LAN is not functioning. If I remove (rmmod) the driver and then modprobe it, the network then comes up. Puzzling!

Thanks for the continuing assistance 'chill555'.

Jim

P.S. I think I'll pass on the tornadoes and 70 MPH winds, but 74 F (Fahrenheit? How quaint!) sounds about right. I could then sit outside drinking whisky and rye with the good ole boys at that temperature!

---

### Post by chili555 on 2013-01-31
I think the wlan1 designation is benign. I wouldn't worry about it. If you are super OCD, it can be changed. Will it make things magically work perfectly? I doubt it.

Let's try something different for now:```
gksudo gedit /etc/rc.local
```Add three lines above exit 0:```
modprobe -r rtl8723ae
sleep 20
modprobe rtl8723ae
```Proofread, save and close gedit. Reboot.

Is it working as expected now?> drinking whisky and rye with the good ole boys And eating American Pie??

---

### Post by jimford on 2013-02-01
<sigh>

I was just about to do as you suggested above, but hey - a new update alert pops up, so let's install that first! I install the update, but it's a new kernel, so there's no rtl8723 driver in the new kernel modules directory. I then go to rebuild the driver but I've previously deleted the source and archive file. So then it's back to an ethernet cable to download the driver file and recompile and install the driver.

I guess I'll have to recompile the driver every time the kernel gets updated, until the driver is eventually  included. I've now made the source immutable so I can't casually delete it again!

So far it looks like the driver is getting recognised on boot, but if I run into problems I'll try your 'unload then reload on start up' fix above.

Thanks again 'chilli555', I owe you one. If you're ever in the London region PM me and I'll take you on some day trips to places of interest.

Jim

---

### Post by chili555 on 2013-02-01
> I guess I'll have to recompile the driver every time the kernel gets updated, until the driver is eventually included. That's correct. I hope it was mentioned back a few pages. That's what's so difficult about these 60-70 reply threads; hardly anybody reads all 70 replies!>  If you're ever in the London region PM me and I'll take you on some day trips to places of interest.I was there in 2001 and loved every moment of it. Are any of the places of interest named 'pub?'

---

### Post by jimford on 2013-02-01
> **chili555 said:**
> I was there in 2001 and loved every moment of it. Are any of the places of interest named 'pub?'

This one's in the next town - about 20 mins drive away:

[http://en.wikipedia.org/wiki/Ye_Olde_Fighting_Cocks](http://en.wikipedia.org/wiki/Ye_Olde_Fighting_Cocks)

I'll take you there!

Jim

---

### Post by chili555 on 2013-02-01
Thank you so much for your kind words and generous offer. If I am able to visit again, I will PM.

---

### Post by NerONLY on 2013-02-11
Had the same problem on toshiba c850, made all the steps according to this thread
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)
 
downloading this version of the driver 
[http://www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](http://www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)
 
Actually the moment of pure happiness of working wi-fi was pretty short.. until first reboot. No wifi after reboot in 12.10 and surprisingly in win8 too.
 
Is there any way of making wifi still alive after reboot ?
Is this the only solution ?:
> **selopo said:**
> I discovered that if the wifi is manually disconnected from the panel then it works after reboot.
 
So what I did is to create a simple script and place it in /etc/rc6.d 
 
#! /bin/sh
 
echo "Killing Wifi upon reboot"
/usr/sbin/rfkill block 1
 
 
This is of course temporary until the bloody driver is supported in a new kernel but it makes the trick until then.
 
Cheers
 
?

---

### Post by chili555 on 2013-02-11
Does it spring to life if you simply load the module?```
sudo modprobe rtl8723ae
```If so, let's load it automatically on boot:```
sudo su
echo rtl8723ae >> /etc/modules
exit
```If that doesn't fix it, please post:```
sudo modprobe rtl8723ae
dmesg | grep rtl
```

---

### Post by NerONLY on 2013-02-11
> **chili555 said:**
> 
Does it spring to life if you simply load the module?
```
sudo modprobe rtl8723ae
```
no 

> **chili555 said:**
> 
If that doesn't fix it, please post:
```
sudo modprobe rtl8723ae
dmesg | grep rtl
```

```

root@Satellite-C850-D2K:/home/strukoff# sudo modprobe rtl8723ae
FATAL: Module rtl8723ae not found.
root@Satellite-C850-D2K:/home/strukoff# dmesg | grep rtl
[   14.767954] firemare: rtl8723fw_B.bin
[   14.933213] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.933430] rtlwifi: wireless switch is on
```

---

### Post by chili555 on 2013-02-11
Let's try again:```
sudo modprobe rtl8723e
rfkill list all
dmesg | grep rtl
```

---

### Post by NerONLY on 2013-02-11
> **chili555 said:**
> Let's try again:```
sudo modprobe rtl8723e
rfkill list all
dmesg | grep rtl
```

strukoff@Satellite-C850-D2K:~$ sudo modprobe rtl8723e
[sudo] password for strukoff: 
strukoff@Satellite-C850-D2K:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
strukoff@Satellite-C850-D2K:~$ dmesg | grep rtl
[    8.537871] firemare: rtl8723fw_B.bin
[    8.679856] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.680101] rtlwifi: wireless switch is on
strukoff@Satellite-C850-D2K:~$

---

### Post by chili555 on 2013-02-11
It all looks pretty solid. Let's dig deeper:```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by NerONLY on 2013-02-11
> **chili555 said:**
> It all looks pretty solid. Let's dig deeper:```
iwconfig
sudo iwlist wlan0 scan
```

```

strukoff@Satellite-C850-D2K:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
strukoff@Satellite-C850-D2K:~$ sudo iwlist wlan0 scan
[sudo] password for strukoff: 
wlan0     No scan results

```

---

### Post by chili555 on 2013-02-11
Please reboot so we have a clean slate and then run:```
dmesg > neronly.txt
```Find the text file in your user directory and paste it here and give us the link. Something weird is happening and so far, it eludes us.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by NerONLY on 2013-02-11
> **chili555 said:**
> Please reboot so we have a clean slate and then run:```
dmesg > neronly.txt
```Find the text file in your user directory and paste it here and give us the link. Something weird is happening and so far, it eludes us.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

[http://paste.ubuntu.com/1637429/](http://paste.ubuntu.com/1637429/)

---

### Post by chili555 on 2013-02-11
Studying...back later.

---

### Post by NerONLY on 2013-02-12
> **chili555 said:**
> Studying...back later.

looking forward to hearing some good news from you
I  guess  my case is not hopeless

---

### Post by chili555 on 2013-02-12
Your case is not hopeless at all. It is my favorite kind of case. Everything looks awesomely perfect...except it won't work. 

Does the wireless still not start and run if the ethernet is detached during boot? I see this in your pastebin:> [   16.054681] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.055371] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.247678] r8169 0000:09:00.0: eth0: link down
[   16.247764] r8169 0000:09:00.0: eth0: link down
[   16.247982] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.248395] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.969721] r8169 0000:09:00.0: eth0: link up
[   17.971058] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
...almost like 'I'm not going to worry about wireless because wired is available and preferred.' This is actually the default behavior in Network Manager.

When you re-compiled the driver, were there many warnings? Did you include the 'make clean' step?```
cd Desktop/rtl_whatever
sudo su
make clean
make
make install
exit
```If not, would you please try it and copy and paste any warnings to pastebin and reboot without ethernet and see if wireless starts.

---

### Post by NerONLY on 2013-02-12
> **chili555 said:**
> Your case is not hopeless at all. It is my favorite kind of case. Everything looks awesomely perfect...except it won't work. 

Does the wireless still not start and run if the ethernet is detached during boot?
yes, the wireless still not start - it doesn't matter whether the ethernet is detached or not

wi fi starts only after shutting down the power, and then turning notebook on again and it works perfectly untill the first reboot

---

### Post by chili555 on 2013-02-12
> **NerONLY said:**
> yes, the wireless still not start - it doesn't matter whether the ethernet is detached or not

wi fi starts only after shutting down the power, and then turning notebook on again and it works perfectly untill the first rebootAnd what about the re-compile?

---

### Post by NerONLY on 2013-02-12
> **chili555 said:**
> 

When you re-compiled the driver, were there many warnings? Did you include the 'make clean' step?```
cd Desktop/rtl_whatever
sudo su
make clean
make
make install
exit
```If not, would you please try it and copy and paste any warnings to pastebin and reboot without ethernet and see if wireless starts.

done again with 'make clean'
[http://paste.ubuntu.com/1640612/](http://paste.ubuntu.com/1640612/)

---

### Post by NerONLY on 2013-02-12
still no wifi after reboot with unplugged ethernet

---

### Post by NerONLY on 2013-02-12
this whole situation brings to mind something like - "this is it....game over, man...." :)

I've been using ubuntu on multiple devices since karmic koala, and this is the first time i couldn't manage the situation

I hope very much that your experience, expertise and genius will solve this issue

---

### Post by chili555 on 2013-02-13
First, thanks for the awesome reference to one of my favorite movies. Second, like Ripley, it isn't over as long as we have any chance whatsoever! I am interested in this:> *wi fi starts* only after shutting down the power, and then turning notebook on again and it works perfectly untill the first rebootSo it will actually start and run from a cold boot, is that correct?

I think we have a few options here. First, forget about reboot and always shut down entirely, and press the power button to start. Second, have a look around the BIOS to see if there are any settings related to wireless that may help us here. Third, we might try a driver parameter:```
gksudo gedit /etc/modprobe.d/rtl8723e.conf
```Add a single line:```
options rtl8723e ips=0
```Proofread, save and close gedit. Shut down. Cold boot. Did the wireless start? Good! Reboot. Does the wireless start..??

I looked at the warnings in the compile and, although my Russian is a bit rusty, I don't think there is much to be concerned about.

Last, there is a compat-wireless package we could try that compiles perfectly for me on 3.5.0-23-generic. Given the behavior above, that seems least likely to help.

---

### Post by NerONLY on 2013-02-13
> I am interested in this:So it will actually start and run from a cold boot, is that correct?exactly
  
> have a look around the BIOS to see if there are any settings related to wireless that may help us here. nothing related to wireless was found in BIOS

 > Third, we might try a driver parameter:```
gksudo gedit /etc/modprobe.d/rtl8723e.conf
```Add a single line:```
options rtl8723e ips=0
```Proofread, save and close gedit.done

>  Shut down. Cold boot. Did the wireless start? yes

> Good! Reboot. Does the wireless start..??nope

looks like it's time for me to get used to
> forget about reboot and always shut down entirely, and press the power button to start

---

### Post by NerONLY on 2013-02-13
All right, take a look at the results of my "private investigation"

this sequence solves the problem of broken wifi after reboot:

1. start with a cold reboot,
 wifi is on

2. perform in command line in terminal before reboot 
```
rfkill block 1
```3. reboot,
still no wifi after the system is loaded

4. perform in command line in trminal
```
rfkill unblock 1
```wifi is on

The question is : how to automate all the steps of the sequence mentioned above ?

---

### Post by chili555 on 2013-02-13
I suspect it only takes the 'unblock' part. Please try this:```
gksudo gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock 1
```Proofread, save and close gedit.

Reboot and see if it's working. If not, we'll tweak a bit more.

---

### Post by NerONLY on 2013-02-14
> **chili555 said:**
> I suspect it only takes the 'unblock' part. Please try this:```
gksudo gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock 1
```Proofread, save and close gedit.

Reboot and see if it's working. If not, we'll tweak a bit more.

it's not working

---

### Post by NerONLY on 2013-02-14
And after adding a line into rc.local, it's necessary to create a script and place it in /etc/rc6.d

```
#! /bin/sh

/usr/sbin/rfkill block 1
```

finally everything is done automatically, and wifi works after reboot

---

### Post by NerONLY on 2013-02-14
oops, wifi is broken again... i guess the magic worked only once (for one reboot)
i'm ready for 
> If not, we'll tweak a bit more. 	
:D

---

### Post by chili555 on 2013-02-15
> #! /bin/sh

/usr/sbin/rfkill block 1I think this should be:```
#! /bin/sh

/usr/sbin/rfkill [COLOR="Red"]un[/COLOR]block 1
```Please try it both with and without the change in /etc/rc.local.

---

### Post by NerONLY on 2013-02-15
> **chili555 said:**
> I think this should be:```
#! /bin/sh

/usr/sbin/rfkill [COLOR=Red]un[/COLOR]block 1
```Please try it both with and without the change in /etc/rc.local.

what exactly should I try ?

at present, the trick is working when
1. with  wifi on, before reboot I run manually the following script:
```
#!/bin/sh

rfkill block 1

```
as a result I can see how wifi indicator turns off in the upper system tray

2. soft  reboot
3. system starts with working wifi
(/etc/rc.local is modified according your first instruction)

What should I do to make the step number one run automatically ?

---

### Post by NerONLY on 2013-02-17
Maybe my persistence in making things working my way looks little bit paranoid, but anyway I'll be very grateful for any answer

---

### Post by chili555 on 2013-02-17
I don't feel it's paranoid in the least. It's just that I don't know an answer or even a wild guess. I think you want to add this to your shutdown and/or reboot scripts and I haven't a clue how to do it. I'm sorry I can't be of more assistance.

---

### Post by gdisastery on 2013-03-07
Hello I got a problem with the driver as well. I have followed the instructions from here: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized) . Now I can connect with the routers, but I always lose the connection and this is really annoying because it only happens in Ubuntu 12.10. I never lose the connection in Windows 7 and I don't know why...

---

### Post by chili555 on 2013-03-07
> **gdisastery said:**
> Hello I got a problem with the driver as well. I have followed the instructions from here: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized) . Now I can connect with the routers, but I always lose the connection and this is really annoying because it only happens in Ubuntu 12.10. I never lose the connection in Windows 7 and I don't know why...Is there any clue in here?```
dmesg | grep -e rtl -e wlan
```

---

### Post by gdisastery on 2013-03-07
I have actually no clue, have been using Linux for not a long time... But here is the output:
> [   18.036048] firemare: rtl8723fw_B.bin[   18.296627] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.296920] rtlwifi: wireless switch is on
[   21.518884] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.521850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.881153] wlan0: authenticate with 00:24:01:38:f4:b7
[   23.913523] wlan0: send auth to 00:24:01:38:f4:b7 (try 1/3)
[   23.915322] wlan0: authenticated
[   23.932412] wlan0: associate with 00:24:01:38:f4:b7 (try 1/3)
[   23.935504] wlan0: RX AssocResp from 00:24:01:38:f4:b7 (capab=0x431 status=0 aid=5)
[   23.936092] wlan0: associated
[   23.936789] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  126.695996] wlan0: Connection to AP 00:24:01:38:f4:b7 lost.
[  127.758860] wlan0: authenticate with 00:24:01:38:f4:b7
[  127.790954] wlan0: send auth to 00:24:01:38:f4:b7 (try 1/3)
[  127.793042] wlan0: authenticated
[  127.809666] wlan0: associate with 00:24:01:38:f4:b7 (try 1/3)
[  127.814370] wlan0: RX AssocResp from 00:24:01:38:f4:b7 (capab=0x431 status=0 aid=5)
[  127.815030] wlan0: associated




---

### Post by chili555 on 2013-03-07
> [ 127.790954] wlan0: send auth to 00:24:01:38:f4:b7 (try 1/3)
[ 127.793042] wlan0: authenticated
[ 127.809666] wlan0: associate with 00:24:01:38:f4:b7 (try 1/3)
[ 127.814370] wlan0: RX AssocResp from 00:24:01:38:f4:b7 (capab=0x431 status=0 aid=5)
[ 127.815030] wlan0: associated
I don't see anything wrong here. It looks like you connected just perfectly. No?

---

### Post by gdisastery on 2013-03-07
I'm getting disconnected every 2nd or 3rd minute. This is my problem :(
And this does not happen to me if I'm working with Windows 7.

---

### Post by chili555 on 2013-03-07
> **gdisastery said:**
> I'm getting disconnected every 2nd or 3rd minute. This is my problem :(
And this does not happen to me if I'm working with Windows 7.I wonder if power management is reducing voltage to the device and it drops. Let's try a temporary fix and, if it works, we'll make it persistent:```
sudo modprobe -r rtl8723e
sudo modprobe rtl8723e ips=0
```Better, worse??

---

### Post by gdisastery on 2013-03-07
I did it and it seems like that it is working much better!

---

### Post by chili555 on 2013-03-07
> **gdisastery said:**
> I did it and it seems like that it is working much better!Awesome. I suggest you test it for a few hours. If it's still working well, we'll write one file and etch it in stone.

---

### Post by gdisastery on 2013-03-07
Yeah I will test it out at school tomorrow because using Ubuntu at school is really terrible due to the internet connection :/

EDIT: I still get disconnected at home, but not so often like before. Maybe 5-10 times in an hour.

---

### Post by gdisastery on 2013-03-08
I am at school right now and have executed the commands you have given me, but I still get disconnected all the time, but not so often as always.

---

### Post by chili555 on 2013-03-08
> **gdisastery said:**
> I am at school right now and have executed the commands you have given me, but I still get disconnected all the time, but not so often as always.Please try:```
sudo modprobe -r rtl8723e
sudo modprobe rtl8723e ips=0
sudo iwconfig wlan0 power off
```In this context, 'power' refers to power management, the often helpful but sometimes maddening scheme to reduce power to various items including the wireless card in order to extend battery power.

---

### Post by gdisastery on 2013-03-08
```
gary@GARY-PC:~$ sudo su[sudo] password for gary: 
root@GARY-PC:/home/gary# modprobe -r rtl8723e
root@GARY-PC:/home/gary# modprobe rtl8723e ips=0
root@GARY-PC:/home/gary# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"TGM1x"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1F:45:4B:5E:A8   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
**          Power Management:off**
          Link Quality=22/70  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23   Missed beacon:0


root@GARY-PC:/home/gary# iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```
I think power management is already off

---

### Post by chili555 on 2013-03-08
Indeed it is. What about this?> wlan0     IEEE 802.11bgn  ESSID:"TGM1x"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1F:45:4B:5E:A8   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=22/70[/COLOR]  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23   Missed beacon:0How far from the router are you? No wonder it drops!

---

### Post by gdisastery on 2013-03-08
I don't know where the router of our school is. But if I work with Windows the connection is more stable.

---

### Post by gdisastery on 2013-03-09
> **chili555 said:**
> Indeed it is. What about this?How far from the router are you? No wonder it drops!
At home it is dropping too.. I really have no clue..
```
wlan0     IEEE 802.11bgn  ESSID:"applesweet86"            Mode:Managed  Frequency:2.427 GHz  Access Point: 00:24:01:38:F4:B7   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          [COLOR=#ff0000]Link Quality=70/70[/COLOR]  Signal level=26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0
```

---

### Post by eyeneedhelp on 2013-03-09
i try to read all posts that relate to my problem. im new here and to ubuntu but not new to computing. started in the 80;s with a heath 3400 trainer using hex keypad!!

do you guys realize how complex your above posts are to me,a newcomer.
im struggling with a usb install and based on the above info this is nto a place for beginneres,or even a seasond operator!
i'd need a degree in sw engineering to follow you!!

so i ask the same ongoing question,"how do i install a new usb device in a fresh new ubuntu computer??

---

### Post by chili555 on 2013-03-09
> **eyeneedhelp said:**
> i try to read all posts that relate to my problem. im new here and to ubuntu but not new to computing. started in the 80;s with a heath 3400 trainer using hex keypad!!

do you guys realize how complex your above posts are to me,a newcomer.
im struggling with a usb install and based on the above info this is nto a place for beginneres,or even a seasond operator!
i'd need a degree in sw engineering to follow you!!

so i ask the same ongoing question,"how do i install a new usb device in a fresh new ubuntu computer??I suggest you continue your ongoing thread with Hadaka.

---

### Post by eyeneedhelp on 2013-03-09
last sat i connected on internet on first try with new usb,no software.
after a week of reinstalls,mods,reboots,new downloads,i get no wireless activation at all,no connection to thiswifi im using 
10 feet away,cant open a game,reboot with cd,reinstall.
i started out connected and went downhill and im certain its not his fault.
im using a solid state drive,?maybe thats it,my last guess!!

---

### Post by chili555 on 2013-03-09
I suggest you continue your ongoing thread with Hadaka.

---

### Post by menonrudhin on 2013-03-12
> **chili555 said:**
> Glad it's working and I'm glad to know how to get this new device working. Have fun!

rudhin@rudhin-Satellite-C850:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/
rudhin@rudhin-Satellite-C850:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ clear


rudhin@rudhin-Satellite-C850:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ sudo su
[sudo] password for rudhin: 
root@rudhin-Satellite-C850:/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.5.0-23-generic/build M=/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [all] Error 2
root@rudhin-Satellite-C850:/home/rudhin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# 

I'm still having above error, please help.

---

### Post by chili555 on 2013-03-12
Please see posts 17 and following here: [http://ubuntuforums.org/showthread.php?t=2040656&page=2&highlight=8723](http://ubuntuforums.org/showthread.php?t=2040656&page=2&highlight=8723)

---

### Post by c.pfarher on 2013-03-24
Hello Chilli, I have a problem similar to others users in posts.... The wireless work fine when power on the PC the first one start, but when restarted it wasn´t work...
This are the output of the commands you post in differents posts of this thread: [http://pastebin.com/yDpERxQR](http://pastebin.com/yDpERxQR)
I try to add the rfkill block 1 or unblock 1 in /etc/rc6.d ... the first time of reboot with rfkill block 1, wireless work, but after that, it isn´t working anymore... any idea how to solve this problem? 
my kernel is 3.5.0-26-generic in ubuntu 12.10 64 bits and the file compiled is rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz => this file also have the drivers for bluetooth?
thank you!...

---

### Post by gdisastery on 2013-03-25
Hey, I still got the problem, but maybe this can bring us forward...
If I'm in a wired network, sometimes it disconnects me as well.

---

### Post by chili555 on 2013-03-25
> **c.pfarher said:**
> Hello Chilli, I have a problem similar to others users in posts.... The wireless work fine when power on the PC the first one start, but when restarted it wasn´t work...
This are the output of the commands you post in differents posts of this thread: [http://pastebin.com/yDpERxQR](http://pastebin.com/yDpERxQR)
I try to add the rfkill block 1 or unblock 1 in /etc/rc6.d ... the first time of reboot with **rfkill block 1**, wireless work, but after that, it isn´t working anymore... any idea how to solve this problem? 
my kernel is 3.5.0-26-generic in ubuntu 12.10 64 bits and the file compiled is rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz => this file also have the drivers for bluetooth?
thank you!...It looks pretty solid, actually. Please run and post:```
rfkill list all
sudo iwlist wlan0 scan
```We don't need all the scan results; just tell us either yes, it scans or no it produces this error and what, if any, the error is.

Why did you need to *block* any part of the wireless?I may be confused.

---

### Post by c.pfarher on 2013-03-26
christian@toshichri:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
christian@toshichri:~$ sudo iwlist wlan0 scan
[sudo] password for christian: 
wlan0     No scan results


I saw a post where said someting about put blok in rc6.d... but I removed it and put unblock...
Thank you...

---

### Post by chili555 on 2013-03-26
> **c.pfarher said:**
> christian@toshichri:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
christian@toshichri:~$ sudo iwlist wlan0 scan
[sudo] password for christian: 
wlan0     No scan results


I saw a post where said someting about put blok in rc6.d... but I removed it and put unblock...
Thank you...This is a long, complicated thread with many different posters. Please start your own new thread and include:```
lspci -nn | grep 0280
sudo modprobe rtl8723e
modinfo rtl8723e | head -n5
```Leave the link here and I'll be happy to help.

---

### Post by c.pfarher on 2013-03-26
I open a thread for my questions: [http://ubuntuforums.org/showthread.php?t=2129662&p=12575676#post12575676](http://ubuntuforums.org/showthread.php?t=2129662&p=12575676#post12575676)

Thank you.

---

### Post by menonrudhin on 2013-03-28
Thank you so much chili555, thank you very very much
it worked at last
but i think i need to modprobe it again and again, don't know why
but it worked. :)

---

### Post by menonrudhin on 2013-03-28
[https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

this one helped, provided by chili555 :D ubuntu is awesome now . . . enjoy and thanks chili555

---

### Post by chili555 on 2013-03-29
> **menonrudhin said:**
> 
but i think i need to modprobe it again and again, don't know why
Did you get this solved? If not, please try:```
sudo su
echo rtl8723e >> /etc/modules
exit
```If that doesn't solve it, post back and we'll get out the welder!

---

### Post by mapx on 2013-03-29
Dear All,

I've followed the below steps as it is suggested at the very beginning of this thread; however, I haven't solved this issue on a Satellite  C485 with ubuntu 12.10 (64bits). Probably, by this time anyone of you have solve it successfully at some part of the 13 pages. I really appreciate any help you can provide.

Yours...



[LIST=1]
[*][COLOR=#000000]$ wget -O- [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) | tar -xz[/COLOR]
[*][COLOR=#000000]$ sudo gedit base.c     /* Commenting the line 320 as /* IEEE80211_HW_BEACON_FILTER | */[/COLOR]
[*][COLOR=#000000]$ sudo make

THE LAST LINES OF THE TERMINAL OUTPUT ARE:
[LIST=1]
[*][COLOR=#000000]  Building modules, stage 2.[/COLOR]
[*][COLOR=#000000]  MODPOST 1 modules[/COLOR]
[*][COLOR=#000000]  CC      /home/alex/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/rtl8723e.mod.o[/COLOR]
[*][COLOR=#000000]  LD [M]  /home/alex/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/rtl8723e.ko[/COLOR]
[*][COLOR=#000000]make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'[/COLOR]
[*][COLOR=#000000]make[1]: Leaving directory `/home/alex/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'[/COLOR]
[*][COLOR=#000000]alex@satelliteC845:~/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$[/COLOR]
[/LIST]

/* THE COMPLETE TERMINAL OUTPUT IS AVAILABLE AT[/COLOR]
[*][COLOR=#000000][http://pastebin.com/wsvbZNnX](http://pastebin.com/wsvbZNnX)
[/COLOR]
[/LIST]

---

### Post by chili555 on 2013-03-29
> **mapx said:**
> 
[*][COLOR=#000000]$ wget -O- [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) | tar -xz[/COLOR]

I suggest you try the newer version. Please see post #127 above.

---

### Post by mapx on 2013-04-01
I have followed what you suggested, and the wifi connections is working now.
Thank you!

---

### Post by chili555 on 2013-04-02
> **mapx said:**
> I have followed what you suggested, and the wifi connections is working now.
Thank you!Awesome! Glad to hear it's working.

---

