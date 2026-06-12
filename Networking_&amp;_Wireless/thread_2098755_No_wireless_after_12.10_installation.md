---
title: "No wireless after 12.10 installation"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by colmeweb on 2012-12-27
Hey everybody,
  I just installed Ubuntu 12.10 on a toshiba satellite c850d that had Windows 8 pre-installed. For some reason there is no sign of the wireless in the top panel or in the network settings. I have been poking around but haven't found anything that works yet. Below is the output from lspci -nn | grep 0280. Any help would be great, Thanks.

```

colin@colin-Satellite-C850D:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]


```

---

### Post by Abhinav Kumar on 2012-12-27
Hi colmeweb,
Please look at the following similar thread
[http://ubuntuforums.org/showpost.php?p=12164850&postcount=6](http://ubuntuforums.org/showpost.php?p=12164850&postcount=6)
:)

Regards,
Abhinav

---

### Post by ahallubuntu on 2012-12-27
Your wireless card is a Realtek 8723.

Check this out:

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by colmeweb on 2012-12-27
Hey Abhinav I followed those steps but on the last one (sudo modprobe rtl8723e) I got

```

root@colin-Satellite-C850D:/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo modprobe rtl8723e
FATAL: Module rtl8723e not found.


```

I tried it without the e and go the same response, any advice.

---

### Post by chili555 on 2012-12-27
I believe in later versions of the driver it is renamed. Please try:```
sudo modprobe rtl8723[COLOR="DarkRed"]a[/COLOR]e
```

---

### Post by colmeweb on 2012-12-27
Nope rtl8723ae not the answer

How long does this take? After I went through the sequence I tried to close the terminal and it said that it was still working. Also there is a # sign after the ~ that I haven't noticed before.

---

### Post by chili555 on 2012-12-27
> How long does this take? After I went through the sequence I tried to close the terminal and it said that it was still working. Also there is a # sign after the ~ that I haven't noticed before.The little # means you are running as root. The terminal is complaining about closing because when you issued the command 'sudo su' you asked to run some commands as root, also known as **s**uper-**u**ser. The terminal wants to be sure you are done. You could and should tell it you are done with:```
exit
```Then the terminal will close without complaint.> Nope rtl8723ae not the answerPlease go through the compile process again and see what module it builds at the end of 'make', like this:> CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/[COLOR="Red"]rtl8723ae.ko[/COLOR]
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/net/mac80211/mac80211.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/net/mac80211/mac80211.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.ko
  CC      /home/chili/Desktop/Forum/compat-drivers-2012-12-04/net/wireless/cfg80211.mod.o
  LD [M]  /home/chili/Desktop/Forum/compat-drivers-2012-12-04/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'It will be rtl87-something-*.ko*. Modprobe the module without the .ko extension. If 'make' ended in an error, the module never actually got built. Post the error(s) here and we'll troubleshoot.

---

### Post by colmeweb on 2012-12-27
Ah, I think I found the problem.

```

root@Satellite-C850D:/home/colin# cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
root@Satellite-C850D:/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.5.0-21-generic/build M=/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  CC [M]  /home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [all] Error 2
root@Satellite-C850D:/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo make install
make -C /lib/modules/3.5.0-21-generic/build M=/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  CC [M]  /home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [all] Error 2


```

Not sure what is causing this. Could it be because it is the second attempt?
I stopped before the sudo make install step.

---

### Post by chili555 on 2012-12-27
> Could it be because it is the second attempt?Nope.> Not sure what is causing this.This is the problem:> base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)I suggest you try this package instead: [http://www.kernel.org/pub/linux/kernel/projects/backports/2012/12/04/compat-drivers-2012-12-04.tar.gz](http://www.kernel.org/pub/linux/kernel/projects/backports/2012/12/04/compat-drivers-2012-12-04.tar.gz)

Let me hear from you if you get stuck.

---

### Post by colmeweb on 2012-12-27
Yeah, I've never installed drivers from a tar. Could you give me a walk through?

---

### Post by chili555 on 2012-12-27
Download the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:```
cd Desktop/compat-drivers-2012-12-04
sudo su
./scripts/driver-select rtlwifi
make 
make install
modprobe rtl8723ae
exit
```

---

### Post by colmeweb on 2012-12-27
So I take it this is a bad thing

```

colin@Satellite-C850D:~$ cd Downloads/compat-drivers-2012-12-04
colin@Satellite-C850D:~/Downloads/compat-drivers-2012-12-04$ sudo su
[sudo] password for colin: 
root@Satellite-C850D:/home/colin/Downloads/compat-drivers-2012-12-04# ./scripts/driver-select rtwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
**Unsupported driver**
root@Satellite-C850D:/home/colin/Downloads/compat-drivers-2012-12-04# make
./scripts/gen-compat-autoconf.sh /home/colin/Downloads/compat-drivers-2012-12-04/.config /home/colin/Downloads/compat-drivers-2012-12-04/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-21-generic/build M=/home/colin/Downloads/compat-drivers-2012-12-04 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  CC [M]  /home/colin/Downloads/compat-drivers-2012-12-04/compat/main.o
  CC [M]  /home/colin/Downloads/compat-drivers-2012-12-04/compat/compat-3.7.o
  LD [M]  /home/colin/Downloads/compat-drivers-2012-12-04/compat/compat.o
  CC [M]  /home/colin/Downloads/compat-drivers-2012-12-04/drivers/bcma/main.o
  CC [M]  /home/colin/Downloads/compat-drivers-2012-12-04/drivers/bcma/scan.o


```

---

### Post by chili555 on 2012-12-27
> ./scripts/driver-select rtwifiIt's rt[COLOR="Red"]l[/COLOR]wifi. Please start over:```
./scripts/driver-select restore
./scripts/driver-select rt[COLOR="Red"]l[/COLOR]wifi
make clean
make
make install
modprobe rtl8723ae
exit
```Off for the evening. See you tomorrow.

---

### Post by colmeweb on 2012-12-27
Done, still no sign of the wireless. Here's the output from everything after make

```

  CC      /home/colin/Downloads/compat-drivers-2012-12-04/net/mac80211/mac80211.mod.o
  LD [M]  /home/colin/Downloads/compat-drivers-2012-12-04/net/mac80211/mac80211.ko
  CC      /home/colin/Downloads/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.mod.o
  LD [M]  /home/colin/Downloads/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.ko
  CC      /home/colin/Downloads/compat-drivers-2012-12-04/net/wireless/cfg80211.mod.o
  LD [M]  /home/colin/Downloads/compat-drivers-2012-12-04/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
root@Satellite-C850D:/home/colin/Downloads/compat-drivers-2012-12-04# make install

make -C /lib/modules/3.5.0-21-generic/build M=/home/colin/Downloads/compat-drivers-2012-12-04 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  Building modules, stage 2.
  MODPOST 17 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make -C /lib/modules/3.5.0-21-generic/build M=/home/colin/Downloads/compat-drivers-2012-12-04 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/compat/compat.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/gpu/drm/drm.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/gpu/drm/drm_kms_helper.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/gpu/drm/i915/i915.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/gpu/drm/nouveau/nouveau.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/net/mac80211/mac80211.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.ko
  INSTALL /home/colin/Downloads/compat-drivers-2012-12-04/net/wireless/cfg80211.ko
  DEPMOD  3.5.0-21-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'

Note: iwl4965 detected, we're going to disable it. If you would like to enable it later you can run:
    sudo iwl-load iwl4965

Running iwl-enable iwlagn...
Disabling iwl4965 ...	[OK]	Module disabled:
kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

root@Satellite-C850D:/home/colin/Downloads/compat-drivers-2012-12-04# modprobe rtl8723ae
root@Satellite-C850D:/home/colin/Downloads/compat-drivers-2012-12-04# exit
exit
colin@Satellite-C850D:~/Downloads/compat-drivers-2012-12-04$ 


```

Thanks, I'll try again tomorrow.

---

### Post by chili555 on 2012-12-28
> Note: [COLOR="Red"]iwl4965[/COLOR] detected, we're going to disable it.What explains this?

Please post:```
modinfo rtl8723ae | grep 8723
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by colmeweb on 2012-12-28
I have no idea what iwl4965 is I thought it was the previous driver.

Here is the readout you wanted

```

colin@Satellite-C850D:~$ modinfo rtl8723ae | grep 8723
filename:       /lib/modules/3.5.0-21-generic/updates/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723aefw_B.bin
firmware:       rtlwifi/rtl8723aefw.bin
description:    Realtek 8723E 802.11n PCI wireless
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
colin@Satellite-C850D:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

colin@Satellite-C850D:~$ sudo iwlist wlan0 scan
[sudo] password for colin: 
wlan0     Interface doesn't support scanning.

```

---

### Post by Abhinav Kumar on 2012-12-28
> **colmeweb said:**
> Hey Abhinav I followed those steps but on the last one (sudo modprobe rtl8723e) I got

```

root@colin-Satellite-C850D:/home/colin/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo modprobe rtl8723e
FATAL: Module rtl8723e not found.


```I tried it without the e and go the same response, any advice.
Hi colmeweb,
Sorry for the late response. Now the real doctor chili555 is with you.  :)

And Thankyou chili555 for joining this discussion.

Regards,
Abhinav

---

### Post by chili555 on 2012-12-28
Let's load the module and see if there are any complaints:```
sudo modprobe rtl8723ae
dmesg | grep rtl
ls /etc/modprobe.d
```Thanks.

---

### Post by colmeweb on 2012-12-28
Here's the output

```

colin@Satellite-C850D:~$ sudo modprobe rtl8723ae
[sudo] password for colin: 
colin@Satellite-C850D:~$ dmesg | grep rtl
[   17.759782] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   17.811073] rtlwifi: Firmware rtlwifi/rtl8723fw_B.bin not available
colin@Satellite-C850D:~$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         iwlwifi.conf
blacklist.conf           blacklist-oss.conf           vmwgfx-fbdev.conf
blacklist-firewire.conf  blacklist-rare-network.conf
colin@Satellite-C850D:~$ 

```

---

### Post by srekcahrai on 2012-12-28
Try to install from additional drivers. Settings> Software Sources > Additional drivers

---

### Post by chili555 on 2012-12-28
No firmware? Let's get some. Please download the attached to your desktop. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/rtlwifi
```The file may already exist. Please proceed.```
sudo cp Desktop/rtlwifi/*.bin /lib/firmware/rtlwifi/
```Now, we unload and reload the driver so it sees the needed firmware:```
sudo modprobe -r rtl8723ae
sudo modprobe rtl8723ae
```Now we check for any improvement:```
iwconfig 
sudo iwlist wlan0 scan
```Now let's do some housekeeping:```
sudo rm /etc/modprobe.d/iwlwifi.conf
```And let's check:```
cat /etc/modules | tail -n5
```

---

### Post by chili555 on 2012-12-28
> **srekcahrai said:**
> Try to install from additional drivers. Settings> Software Sources > Additional driversThere is no additional driver available for his device.

---

### Post by colmeweb on 2012-12-28
YESSSSS! Chili you are the driver guru. I am doing this over the wireless. I am going to mark as solved and Thank You. Am I going to need to redo this when the kernel updates?

Here is the output just in case.

```

colin@Satellite-C850D:~$ sudo mkdir /lib/firmware/rtlwifi
mkdir: cannot create directory `/lib/firmware/rtlwifi': File exists
colin@Satellite-C850D:~$ sudo cp Downloads/rtlwifi/*.bin /lib/firmware/rtlwifi/
colin@Satellite-C850D:~$ sudo modprobe -r rtl8723ae
colin@Satellite-C850D:~$ sudo modprobe rtl8723ae
colin@Satellite-C850D:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
colin@Satellite-C850D:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:B8:CA:08
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"toshiba200"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001558fb50916
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A746F7368696261323030
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3537383830371054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 08:86:3B:64:58:64
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"toshiba200_xt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004831f712dc
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000D746F73686962613230305F7874
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD9C0050F204104A0001101044000102103B00010310470010B57BDDDEFEAA5A232877A6E9E245C1671021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303620763110240007312E30302E31301042000E31323131333642463130303139341054000800060050F204000110110017576972656C6573732052616E676520457874656E646572100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

colin@Satellite-C850D:~$ sudo rm /etc/modprobe.d/iwlwifi.conf
colin@Satellite-C850D:~$ cat /etc/modules | tail -n5
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
colin@Satellite-C850D:~$ 

```

---

### Post by chili555 on 2012-12-28
Awesome! You have a wireless interface and it scans. Can you click the Network Manager icon and connect?!?!

---

### Post by chili555 on 2012-12-28
> Am I going to need to redo this when the kernel updates?Yes, indeed. ```
cd Desktop/compat-drivers-2012-12-04
sudo su
./scripts/driver-select rtlwifi
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rtl8723ae
exit
```

---

### Post by colmeweb on 2012-12-28
Yes I can access wireless networks through the top panel and the network settings. It even autoconnects on startup. 

Thank you again for all the effort.

---

### Post by karnival8 on 2012-12-30
Hi,
On post #21, I am getting this error:
 ```
 sudo modprobe rtl8723ae
FATAL: Error inserting rtl8723ae (/lib/modules/3.5.0-21-generic/updates/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko): Invalid argument
```

---

### Post by karnival8 on 2012-12-30
aye!
been toying with this all morning... can't get it workin. wlan0 doesn'g show up in iwconfig, dmesg |grep rtl shows nothing... 

commence ripping hair out. 

r

---

### Post by chili555 on 2012-12-30
> **karnival8 said:**
> aye!
been toying with this all morning... can't get it workin. wlan0 doesn'g show up in iwconfig, dmesg |grep rtl shows nothing... 

commence ripping hair out. 

rWe can fix it. No need losing hair; it's pretty hard to get back once it's gone.

Please repeat the sequence in post #25 and post any errors here. We'll get it.

---

### Post by karnival8 on 2012-12-30
it's almost all gone anyways. 
here, top got cut off by the buffer but should be good.
```
deon_fence.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_ttm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_object.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_gart.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_legacy_crtc.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_legacy_encoders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_connectors.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_encoders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_display.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_cursor.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_i2c.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_clocks.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_fb.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_gem.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_ring.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_irq_kms.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_cs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_bios.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_benchmark.o
  HOSTCC  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/mkregtable
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r100_reg_safe.h
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rn50_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r100.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r300_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r300.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r420_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r420.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rs400.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rs600_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rs600.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rs690.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rv515_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rv515.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r520.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/rv770.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_test.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r200_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r200.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_legacy_tv.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_cs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_blit.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_blit_shaders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_blit_kms.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_pm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/atombios_dp.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_audio.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/r600_hdmi.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/evergreen.o
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/evergreen_reg_safe.h
  MKREGTABLE /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/cayman_reg_safe.h
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/evergreen_cs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/evergreen_blit_shaders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/evergreen_blit_kms.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/evergreen_hdmi.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_trace_points.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/ni.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/cayman_blit_shaders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/atombios_encoders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_semaphore.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_sa.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/atombios_i2c.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/si.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/si_blit_shaders.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_prime.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_atpx_handler.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon_acpi.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_agp_backend.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_memory.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_tt.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_bo.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_bo_util.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_bo_vm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_module.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_object.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_lock.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_execbuf_util.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_page_alloc.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_bo_manager.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm_page_alloc_dma.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/base.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/cam.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/core.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/debug.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/efuse.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/ps.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rc.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/regd.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/stats.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/pci.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/usb.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/main.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/dm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/hw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/led.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/phy.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rf.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/sw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/table.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/trx.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/dm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/hw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/led.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/mac.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/phy.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rf.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/sw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/table.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/trx.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/dm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/fw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/hw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/led.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/phy.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rf.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/sw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/table.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/trx.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/dm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/fw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/hw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/led.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/phy.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rf.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/sw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/table.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/trx.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/dm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/fw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/hal_btc.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/hal_bt_coexist.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/hw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/led.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/phy.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/pwrseq.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/pwrseqcmd.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rf.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/sw.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/table.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/trx.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/main.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/status.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/sta_info.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/wep.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/wpa.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/scan.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/offchannel.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/ht.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/agg-tx.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/agg-rx.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/vht.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/ibss.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/iface.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rate.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/michael.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/tkip.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/aes_ccm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/aes_cmac.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/cfg.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rx.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/spectmgmt.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/tx.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/key.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/util.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/wme.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/event.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/chan.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mlme.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/trace.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/led.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/debugfs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/debugfs_sta.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/debugfs_netdev.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/debugfs_key.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mesh.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mesh_plink.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mesh_hwmp.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mesh_sync.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/pm.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mac80211.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/core.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/sysfs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/radiotap.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/util.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/reg.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/scan.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/nl80211.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/mlme.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/ibss.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/sme.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/chan.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/ethtool.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/mesh.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/ap.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/trace.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/debugfs.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/wext-compat.o
  CC [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/wext-sme.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 17 modules
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/compat/compat.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/compat/compat.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/drm.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/drm.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/drm_kms_helper.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/drm_kms_helper.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/i915/i915.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/i915/i915.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/nouveau/nouveau.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/nouveau/nouveau.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mac80211.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mac80211.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.ko
  CC      /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/cfg80211.mod.o
  LD [M]  /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
root@RyanYoga:/home/ryan/Desktop/compat-drivers-2012-12-04# make install

make -C /lib/modules/3.5.0-21-generic/build M=/home/ryan/Desktop/compat-drivers-2012-12-04 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  Building modules, stage 2.
  MODPOST 17 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make -C /lib/modules/3.5.0-21-generic/build M=/home/ryan/Desktop/compat-drivers-2012-12-04 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/compat/compat.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/drm.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/drm_kms_helper.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/i915/i915.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/nouveau/nouveau.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/radeon/radeon.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/gpu/drm/ttm/ttm.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/drivers/net/wireless/rtlwifi/rtlwifi.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/net/mac80211/mac80211.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/net/rfkill/rfkill-regulator.ko
  INSTALL /home/ryan/Desktop/compat-drivers-2012-12-04/net/wireless/cfg80211.ko
  DEPMOD  3.5.0-21-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.


root@RyanYoga:/home/ryan/Desktop/compat-drivers-2012-12-04# modprobe rtl8723ae
root@RyanYoga:/home/ryan/Desktop/compat-drivers-2012-12-04# 

```

---

### Post by chili555 on 2012-12-30
> root@RyanYoga:/home/ryan/Desktop/compat-drivers-2012-12-04# modprobe rtl8723ae
root@RyanYoga:/home/ryan/Desktop/compat-drivers-2012-12-04#Loaded perfectly this time! Is your wireless working? Did you do the firmware part?

---

### Post by karnival8 on 2012-12-30
I know! This is what happens every time I retry!
Appears to have worked, no wireless connection message, no found ssid's, nada. 


Retrying firmware once again with wired conn.

---

### Post by karnival8 on 2012-12-30
Reloaded the firmware

on iwconfig there is NO listing for lwan0. there is only lo and eth0 - "no wireless extensions"

that is after modprobe -r and then modprobe

---

### Post by chili555 on 2012-12-30
Any interesting messages here?```
dmesg | grep rtl
```

---

### Post by karnival8 on 2012-12-30
if by interesting you mean nothing at all, just blank, then yes!

---

### Post by chili555 on 2012-12-30
It certainly ought to show the result of loading the module; how about now?```
sudo modprobe rtl8723ae
dmesg | grep rtl
```

---

### Post by karnival8 on 2012-12-30
both return an empty result.
should i remove everything and do it all over again? did that a few times already, always ends up here.

---

### Post by chili555 on 2012-12-30
> **karnival8 said:**
> both return an empty result.
should i remove everything and do it all over again? did that a few times already, always ends up here.No. You built it perfectly before and there is no reason to rebuild it ... perfectly ... again. Let's troubleshoot:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep rtl
dmesg | grep -i rtl
```

---

### Post by karnival8 on 2012-12-30
the sad results:

```
ryan@RyansYoga:~$ lspci -nn | grep 0280
ryan@RyansYoga:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
ryan@RyansYoga:~$ lsmod | grep rtl
rtl8723ae              80935  0 
rtlwifi                64892  1 rtl8723ae
mac80211              508150  1 rtlwifi
cfg80211              440554  2 rtlwifi,mac80211
compat                 14557  4 rtl8723ae,rtlwifi,mac80211,cfg80211
ryan@RyansYoga:~$ dmesg | grep -i rtl
ryan@RyansYoga:~$ ^C
ryan@RyansYoga:~$ 
```

---

### Post by chili555 on 2012-12-31
> ryan@RyansYoga:~$ lspci -nn | grep 0280
ryan@RyansYoga:~$ Whaaaa...?? That suggests you have *NO* PCI wireless device! Let's dig deeper:```
lspci -nn
lsusb
```This, however, suggests maybe you do:> 0: ideapad_wlan: [COLOR="Red"]Wireless LAN[/COLOR]
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: noWeird.

---

### Post by karnival8 on 2012-12-31
Here you go Chil, 
Remember this is built in. No USB. Lenovo Yoga 13


```
ryan@RyansYoga:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0153] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation QS77 Express Chipset LPC Controller [8086:1e56] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
00:1f.6 Signal processing controller [1180]: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller [8086:1e24] (rev 04)
ryan@RyansYoga:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:1402 Apple, Inc. Ethernet Adapter [A1277]
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 04f3:000a Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
ryan@RyansYoga:~$ 

```

---

### Post by chili555 on 2012-12-31
Not a USB? It may not be conspicuously sticking out the side of your computer, but it appears to be attached to a USB bus internally:> 0bda:1724 Realtek Semiconductor Corp. Please see: [http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724](http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724)

Frankly, I doubt it's an 8723ae device. I also am not yet aware of any method to drive the device. We might try ndiswrapper or reluctantly admit defeat and try to troubleshoot the Netgear WNA1000M USB adapter.

8723ae devices can be made to work; this just isn't, as far as I can tell, one of them. 

**Sigh**

---

### Post by karnival8 on 2012-12-31
Okay well at least we know now. I am totally good with this little netgear one. 

How shall we proceed?

R

---

### Post by chili555 on 2012-12-31
> **karnival8 said:**
> Okay well at least we know now. I am totally good with this little netgear one. 

How shall we proceed?

RI'd uninstall the rtl8723ae driver:```
cd Desktop/RTL8whatever  [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
sudo su
make uninstall
modprobe -r rtl8723ae
exit
```Now insert the Netgear and post:```
lsusb
lsmod
iwconfig
```Thanks.

---

### Post by karnival8 on 2012-12-31
ryan@RyansYoga:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:1402 Apple, Inc. Ethernet Adapter [A1277]
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 04f3:000a Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
ryan@RyansYoga:~$ lsmod
Module                  Size  Used by
rtl8723ae              80935  0 
rtlwifi                64892  1 rtl8723ae
mac80211              508150  1 rtlwifi
cfg80211              440554  2 rtlwifi,mac80211
compat                 14557  4 rtl8723ae,rtlwifi,mac80211,cfg80211
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_conexant    52202  1 
hid_generic            12445  0 
hid_multitouch         13007  0 
usbhid                 41702  1 hid_multitouch
hid                    82142  3 hid_generic,hid_multitouch,usbhid
joydev                 17161  0 
rts5139               281367  0 
coretemp               13168  0 
kvm                   357806  0 
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
asix                   22274  0 
usbnet                 25169  1 asix
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              18209  0 
ideapad_laptop         13670  0 
sparse_keymap          13658  1 ideapad_laptop
bnep                   17707  2 
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18590  0 
rfcomm                 37276  0 
psmouse                84843  0 
mac_hid                13037  0 
bluetooth             183228  10 bnep,rfcomm
serio_raw              13031  0 
mei                    35796  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
parport_pc             31968  0 
lpc_ich                16925  0 
i915                  457161  3 
ppdev                  12817  0 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
ryan@RyansYoga:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ryan@RyansYoga:~$

---

### Post by chili555 on 2012-12-31
> ryan@RyansYoga:~$ lsmod
Module Size Used by
rtl8723ae 80935 0
rtlwifi 64892 1 rtl8723ae
mac80211 508150 1 rtlwifi
cfg80211 440554 2 rtlwifi,mac80211
compat 14557 4 rtl8723ae,rtlwifi,mac80211,cfg80211It doesn't look like you got the rtl8723ae uninstalled quite yet. Since the Netgear is also a Realtek,I suspect we'll avoid conflicts if rtl8723ae is removed. Please try again.

---

### Post by karnival8 on 2012-12-31
forgot to mention terminal says "no rule to make target 'uninstall'"

urgh. 

i'm so new to this i have no idea what the hell i'm doing. 

okay to rip hair out now?

r

---

### Post by chili555 on 2012-12-31
> forgot to mention terminal says "no rule to make target 'uninstall'"Make sure you are in the directory with the extracted files:```
cd Desktop/compat-drivers-2012-12-04
```...or wherever you extracted the package to compile. Make sure you see the Makefile with *ls*:```
$ ls
code-metrics.txt  drivers               [COLOR="Red"]Makefile[/COLOR]       Module.symvers  scripts
compat            enable-older-kernels  Makefile.bk    net             udev
config.mk         include               modules        patches
COPYRIGHT         MAINTAINERS           modules.order  README.md
```Now we are ready to uninstall:```
sudo su
make uninstall
exit
```Your extracted package may be named something different than *compat-drivers-blah-blah* but the process is exactly the same.

---

### Post by karnival8 on 2012-12-31
i was in the wrong dir...

okay did the uninstall, it just returned me to the command prompt which i assume the command was completed. 

check this out. in lsmod i still see it. modprobe -r returns the result below. 

```
ryan@RyansYoga:~$ lsmod
Module                  Size  Used by
rtl8723ae              80935  0 
rtlwifi                64892  1 rtl8723ae
mac80211              508150  1 rtlwifi
cfg80211              440554  2 rtlwifi,mac80211
compat                 14557  4 rtl8723ae,rtlwifi,mac80211,cfg80211
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_conexant    52202  1 
hid_generic            12445  0 
hid_multitouch         13007  0 
usbhid                 41702  1 hid_multitouch
hid                    82142  3 hid_generic,hid_multitouch,usbhid
joydev                 17161  0 
rts5139               281367  0 
coretemp               13168  0 
kvm                   357806  0 
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
asix                   22274  0 
usbnet                 25169  1 asix
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              18209  0 
ideapad_laptop         13670  0 
sparse_keymap          13658  1 ideapad_laptop
bnep                   17707  2 
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18590  0 
rfcomm                 37276  0 
psmouse                84843  0 
mac_hid                13037  0 
bluetooth             183228  10 bnep,rfcomm
serio_raw              13031  0 
mei                    35796  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
parport_pc             31968  0 
lpc_ich                16925  0 
i915                  457161  3 
ppdev                  12817  0 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
ryan@RyansYoga:~$ sudo modprobe -r rtl8723ae
[sudo] password for ryan: 
FATAL: Module rtl8723ae not found.

```

---

### Post by chili555 on 2012-12-31
> ryan@RyansYoga:~$ lsmod
Module                  Size  Used by
rtl8723ae              80935  0 
rtlwifi                64892  1 rtl8723ae
mac80211              508150  1 rtlwifi
cfg80211              440554  2 rtlwifi,mac80211
compat                 14557  4 rtl8723ae,rtlwifi,mac80211,cfg80211I'm afraid we still have a bit of work to do. Did you install it from any other package? Is it declared in /etc/modules?```
gksudo gedit /etc/modules
```If it appears in there, remove it, proofread and save gedit.

Let's be really OCD and blacklist it!```
sudo su
echo "blacklist rtl8723ae" >> /etc/modprobe.d/blacklist.conf
exit
```

We really need to get to the place where the only Realtek diver that loads is the Netgear. Reboot with the Netgear inserted and show us a good report!```
lsmod
```

---

### Post by karnival8 on 2012-12-31
yes!
cleared from lsmod
lsusb showing netgear 

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:1402 Apple, Inc. Ethernet Adapter [A1277]
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 04f3:000a Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
```

---

### Post by chili555 on 2013-01-01
Excellent. We're getting there. The USB is supposed to work with rtl9182cu. Load it, connect and let us have a report. Is it fast and stable? If not, we'll make a few changes.```
sudo modprobe rtl8192cu
iwconfig
ping -c3 www.google.com
```

---

### Post by karnival8 on 2013-01-01
okay, not quite there. i'm doing something wrong. I downloaded drivers from realtek, here is my output:

```
ryan@RyansYoga:~$ cd Desktop
ryan@RyansYoga:~/Desktop$ cd rtl
ryan@RyansYoga:~/Desktop/rtl$ ls
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
ryan@RyansYoga:~/Desktop/rtl$ cd rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ ls
clean  core  hal  ifcfg-wlan0  include  Kconfig  Makefile  os_dep  wlan0dhcp
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ sudo make install
[sudo] password for ryan: 
install -p -m 644 8192cu.ko  /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/
install: cannot stat `8192cu.ko': No such file or directory
make: *** [install] Error 1
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ makemake ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.o
  LD [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.mod.o
  LD [M]  /home/ryan/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ sudo make install
install -p -m 644 8192cu.ko  /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.5.0-17-generic
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ lsmod | grep rtl
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ lsmod | grep 8192
8192cu                506828  0 
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ sudo modprobe 8192cu
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 05ac:1402 Apple, Inc. Ethernet Adapter [A1277]
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 04f3:000a Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
ryan@RyansYoga:~/Desktop/rtl/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105$ 

```

---

### Post by chili555 on 2013-01-01
What do you imagine went wrong? I don't see anything in error yet. What does this tell us?```
iwconfig
sudo iwlist wlan0 scan
```I'm a bit mystified that you didn't follow my suggestions above but downloaded and compiled a possibly better, possibly not better driver from Realtek.

---

### Post by karnival8 on 2013-01-01
do you think maybe its the wrong driver? did i build it right?
```

ryan@RyansYoga:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ryan@RyansYoga:~$ sudo iwlist wlan0 scan
[sudo] password for ryan: 
wlan0     Interface doesn't support scanning.

ryan@RyansYoga:~$ 

```

---

### Post by chili555 on 2013-01-01
> **karnival8 said:**
> do you think maybe its the wrong driver? did i build it right?
```

ryan@RyansYoga:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ryan@RyansYoga:~$ sudo iwlist wlan0 scan
[sudo] password for ryan: 
wlan0     Interface doesn't support scanning.

ryan@RyansYoga:~$ 

```You built it right, but what's wrong with the [COLOR="Red"]rtl[/COLOR]8192cu built in to 12.10? Why did you feel the need to try something different?```
$ modinfo rtl8192cu
filename:       /lib/modules/3.5.0-21-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     E4744F57D346A06B1CB1065
<snip>
alias:          usb:v[COLOR="Red"]0846[/COLOR]p[COLOR="Red"]9041[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.5.0-21-generic SMP mod_unload modversions 686 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```

---

### Post by karnival8 on 2013-01-01
because i have no idea what i'm doing yet :)
i am learning though. 
ryans linux lesson #422763: install included drivers. 

ready when you are!

---

### Post by chili555 on 2013-01-01
> **karnival8 said:**
> because i have no idea what i'm doing yet :)
i am learning though. 
ryans linux lesson #422763: install included drivers. 

ready when you are!Please do:```
sudo modprobe -r 8192cu
```Then proceed to post #52.

---

### Post by karnival8 on 2013-01-01
right... did this already:
FATAL: Module rtl8192cu not found.

---

### Post by chili555 on 2013-01-01
Please try:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

You have been very busy, haven't you!

Now try again:```
sudo modprobe rtl8192cu
iwconfig
ping -c3 www.google.com
```

---

### Post by karnival8 on 2013-01-01
```
an@RyansYoga:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo apt-get install --reinstall linux-image-`uname -r`
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 216 not upgraded.
Need to get 11.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/main linux-image-3.5.0-17-generic i386 3.5.0-17.28 [11.4 MB]
Fetched 11.4 MB in 6s (1,733 kB/s)                                             
(Reading database ... 175245 files and directories currently installed.)
Preparing to replace linux-image-3.5.0-17-generic 3.5.0-17.28 (using .../linux-image-3.5.0-17-generic_3.5.0-17.28_i386.deb) ...
Done.
Unpacking replacement linux-image-3.5.0-17-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Setting up linux-image-3.5.0-17-generic (3.5.0-17.28) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.5.0-17.28 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.5.0-17.28 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done
ryan@RyansYoga:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo modprobe rtl8192cu
FATAL: Module rtl8192cu not found.
ryan@RyansYoga:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ 

```

---

### Post by chili555 on 2013-01-02
Please show me:```
ls /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rtlwifi/
```Isn't there a folder in there called rtl8192cu? If so, show me:```
/lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu
```If there is neither, I will take a strong tranquilizer and we'll build it.

This just gets weirder.

---

### Post by bb2013 on 2013-01-02
Sorry for bumping in, but I am having the same problem with the rtl8723 device.

I freshly installed ubuntu 12.10 and downloaded the latest version of compat-drivers:  compat-drivers-2012-12-19-u.tar.gz

Aafter completed the steps at #21, everything work find apart from 

sudo iwlist wlan0 scan
[COLOR=Red]wlan0     No scan results[/COLOR]

Does anyone have any idea what could cause the problem?

Any help will be appreciated.


thanks in advance,
BB

---

### Post by karnival8 on 2013-01-02
chilli:
i've got neither!
:(

r

---

### Post by rafaelhsn on 2013-01-03
..

---

### Post by chili555 on 2013-01-03
> **bb2013 said:**
> Sorry for bumping in, but I am having the same problem with the rtl8723 device.

I freshly installed ubuntu 12.10 and downloaded the latest version of compat-drivers:  compat-drivers-2012-12-19-u.tar.gz

Aafter completed the steps at #21, everything work find apart from 

sudo iwlist wlan0 scan
[COLOR=Red]wlan0     No scan results[/COLOR]

Does anyone have any idea what could cause the problem?

Any help will be appreciated.


thanks in advance,
BBSorry, you haven't the same problem. This thread involves rtl8192cu. Please check:```
dmesg | grep -i rtl
```Post the result, if that doesn't give you the answer, in your own new thread.

---

### Post by chili555 on 2013-01-03
> **karnival8 said:**
> chilli:
i've got neither!
:(

rAre you running 12.10? Here is the result from a 12.10 live CD:> ubuntu@ubuntu:/lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rtlwifi$ lsrtl8192c  rtl8192ce  [COLOR="Red"]rtl8192cu[/COLOR]  rtl8192de  rtl8192se  rtlwifi.koI just wish I knew a little something about Ubuntu....sigh...

Back in a few moments, after I reboot, and we'll build it from scratch.

EDIT: Let's try the easy way first:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
sudo modprobe rtl8192cu
```

---

### Post by bb2013 on 2013-01-03
> **chili555 said:**
> Sorry, you haven't the same problem. This thread involves rtl8192cu. Please check:```
dmesg | grep -i rtl
```Post the result, if that doesn't give you the answer, in your own new thread.


Thanks chilli,

BB@BB:~$ sudo modprobe rtl8723ae
BB@BB:~$ dmesg | grep -i rtl
[  180.895430] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[  180.898479] ieee80211 phy0: >Selected rate control algorithm 'rtl_rc'
[  180.898906] rtlwifi: wireless switch is on


wishes,
BB

---

### Post by bb2013 on 2013-01-03
Hi Chilli,

In order to provide you with the most updated output as above, I removed the driver, ie sudo modprobe -r rtl8723ae
then set it back, ie sudo modprobe rtl8723ae

Then the wireless is working...........OM.......(jumping over the moon)

thanks for looking into it.


kind regards,
BB

---

### Post by chili555 on 2013-01-03
> Sorry, you haven't the same problem. This thread involves rtl8192cu.I was quite wrong and I apologize for my mis-step. Post away your 8723 questions, please. 

This is an 8723 thread that I allowed to get hijacked. Chili hangs his head...> Then the wireless is working...........OM.......(jumping over the moon)I'm not quite sure I understand. Are you saying you reloaded rtl8723ae and it started working as expected? If it is simply not loading, we can fix that easily.

---

### Post by bb2013 on 2013-01-03
> **chili555 said:**
> 
This is an 8723 thread that I allowed to get hijacked.

LOL

Yes, reloaded rtl8723ae and it works as expected.  (honestly I have  reloaded and unloaded it last night many times too but it didnt work...........  plus lots of restarting / shutdown laptop........sigh)

The good news is I have tested the 12/12/19 compat-drivers out, the conclusion is it is working  :grin:  


thanks,
BB

---

### Post by bb2013 on 2013-01-04
Hi Chili,

The wireless connection is working but I noticed the connection is not consistence even the top right corner on the screen shows the wireless is still connected, ie firefox believe there is no connection and page wont load (which does not happen with wired connection).

The inconsistency happens quite often.......

I will be grateful for any help.


thanks,
Bonnie

---

### Post by chili555 on 2013-01-04
> **bb2013 said:**
> Hi Chili,

The wireless connection is working but I noticed the connection is not consistence even the top right corner on the screen shows the wireless is still connected, ie firefox believe there is no connection and page wont load (which does not happen with wired connection).

The inconsistency happens quite often.......

I will be grateful for any help.


thanks,
BonnieWhen the connection seems to drop out, run these terminal commands:```
dmesg | tail -n20 > bb2013.txt
nm-tool >> bb2013.txt
```Look in your user directory and find the text file bb2013.txt and post it here. Hopefully, we will see some clues as to what's wrong.

---

### Post by bb2013 on 2013-01-04
Hi Chili,

My wireless connection doesnt connect any more (switch off laptop, went out, come back and switch it on, doesnt connect anymore).  No new app has been installed.  I am now with eth0.


[COLOR=Red]dmesg | tail -n20 > bb2013.txt[/COLOR]

[ 5404.480911] usb 1-1.2: >Product: USB Optical Mouse
[ 5404.480914] usb 1-1.2: >Manufacturer: Logitech
[ 5404.485033] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input66
[ 5404.485242] hid-generic 0003:046D:C00C.0038: >input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.2/input0
[ 5407.238884] usb 1-1.2: >USB disconnect, device number 61
[ 5407.447114] usb 1-1.2: >new low-speed USB device number 62 using ehci_hcd
[ 5407.544914] usb 1-1.2: >New USB device found, idVendor=046d, idProduct=c00c
[ 5407.544921] usb 1-1.2: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5407.544924] usb 1-1.2: >Product: USB Optical Mouse
[ 5407.544927] usb 1-1.2: >Manufacturer: Logitech
[ 5407.549104] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input67
[ 5407.549488] hid-generic 0003:046D:C00C.0039: >input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.2/input0
[ 5449.168207] usb 1-1.2: >USB disconnect, device number 62
[ 5449.372828] usb 1-1.2: >new low-speed USB device number 63 using ehci_hcd
[ 5449.470726] usb 1-1.2: >New USB device found, idVendor=046d, idProduct=c00c
[ 5449.470733] usb 1-1.2: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5449.470736] usb 1-1.2: >Product: USB Optical Mouse
[ 5449.470739] usb 1-1.2: >Manufacturer: Logitech
[ 5449.475143] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input68
[ 5449.475363] hid-generic 0003:046D:C00C.003A: >input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.2/input0


[COLOR=Red]nm-tool >> bb2013.txt[/COLOR]

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        74:E5:43:ED:BB:47

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:90:F5:D8:6D:F8

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

Extra information, hope it helps:

[COLOR=Red]dmesg | grep -i rtl[/COLOR]
[ 2123.763875] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[ 2123.766387] ieee80211 phy0: >Selected rate control algorithm 'rtl_rc'
[ 2123.766679] rtlwifi: wireless switch is on


[COLOR=Red]iwconfig[/COLOR]
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off



[COLOR=Red]sudo iwlist wlan0 scan[/COLOR]
wlan0     No scan results

---

### Post by chili555 on 2013-01-04
May I see with the ethernet *disconnected*:```
rfkill list all
nm-tool
```So far, we see nothing obviously wrong.

---

### Post by bb2013 on 2013-01-04
Hi Chili,

Sure

[COLOR=Red]rfkill list all[/COLOR]

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



[COLOR=Red]nm-tool[/COLOR]

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        74:E5:43:ED:BB:47

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        00:90:F5:D8:6D:F8

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on


```
So far, we see nothing obviously wrong.
```

Agreed.


thanks,
BB

---

### Post by chili555 on 2013-01-05
My favorite kind of problem: everything looks just perfect, except it doesn't work! I wonder if there is any clue here:```
dmesg | grep -i rtl
cat /var/log/syslog | grep -i -e rtl -e etwork | tail -n20
```Please run all tests with the ethernet detached.

---

### Post by colmeweb on 2013-01-05
Hey Chili,
   I have been having the same consistency problems. The wireless will work for an hour, sometimes all day, but then it will just drop out for 3-4 minutes and then pop back again.I thought it was just the wireless at my parents place but it has followed me home. Should I do what you suggest in post #73?

One other thing. When the wireless is down I can get it to start up sometimes by activating transmission. It doesn't work every time, and it will still go down if transmission is already active.

---

### Post by chili555 on 2013-01-05
> **colmeweb said:**
> Hey Chili,
   I have been having the same consistency problems. The wireless will work for an hour, sometimes all day, but then it will just drop out for 3-4 minutes and then pop back again.I thought it was just the wireless at my parents place but it has followed me home. Should I do what you suggest in post #73?Yes, please.

---

### Post by colmeweb on 2013-01-05
Here it is.

```

[ 8181.357780] sd 4:0:0:0: [sdd] 31334400 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 8181.359931] sd 4:0:0:0: [sdd] Write Protect is off
[ 8181.359946] sd 4:0:0:0: [sdd] Mode Sense: 2f 00 00 00
[ 8181.361415] sd 4:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 8181.367929]  sdd: sdd1
[ 8181.373296] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[ 8295.288294] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:20:aa:4b:53:cd:51:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8346.146590] usb 5-1: USB disconnect, device number 2
[ 8354.380145] sdd: detected capacity change from 16043212800 to 0
[ 8357.521888] usb 5-2: USB disconnect, device number 3
[ 8379.796769] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=66.169.253.220 DST=192.168.1.115 LEN=58 TOS=0x00 PREC=0x20 TTL=114 ID=8323 PROTO=UDP SPT=28729 DPT=51413 LEN=38 
[ 8379.802261] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=646 PROTO=UDP SPT=23590 DPT=51413 LEN=28 
[ 8379.827226] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=653 PROTO=UDP SPT=23590 DPT=51413 LEN=28 
[ 8379.861641] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=884 PROTO=UDP SPT=23590 DPT=51413 LEN=28 
[ 8379.862065] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=887 PROTO=UDP SPT=23590 DPT=51413 LEN=28 
[ 8379.888457] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=1151 PROTO=UDP SPT=23590 DPT=51413 LEN=28 
[ 8379.991260] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=1369 PROTO=UDP SPT=23590 DPT=51413 LEN=28 
[ 8379.998284] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=108.219.1.216 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=24588 PROTO=UDP SPT=57900 DPT=51413 LEN=28 
[ 8380.006504] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=108.219.1.216 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=24788 PROTO=UDP SPT=57900 DPT=51413 LEN=28 
[ 8380.006890] [UFW BLOCK] IN=wlan0 OUT= MAC=20:16:d8:47:f5:88:20:aa:4b:53:cd:51:08:00 SRC=202.60.90.194 DST=192.168.1.115 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=1629 PROTO=UDP SPT=23590 DPT=51413 LEN=28 

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:8C:FA:2D:8A:6B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [MercuryMongoose] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             connected
  Default:           yes
  HW Address:        20:16:D8:47:F5:88

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *MercuryMongoose:Infra, 20:AA:4B:53:CD:53, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    forsgrenfamily5: Infra, 00:26:F3:DB:04:78, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    NETGEAR:         Infra, 00:1E:2A:56:BC:2A, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.115
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76
    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fd03:5b02:c487:0:468:5731:e1e3:b326
    Prefix:          64
    Gateway:         fe80::22aa:4bff:fe53:cd51

    Address:         fd03:5b02:c487:0:2216:d8ff:fe47:f588
    Prefix:          64
    Gateway:         fe80::22aa:4bff:fe53:cd51

    Address:         fe80::2216:d8ff:fe47:f588
    Prefix:          64
    Gateway:         fe80::22aa:4bff:fe53:cd51




```

---

### Post by chili555 on 2013-01-05
> *MercuryMongoose:Infra, 20:AA:4B:53:CD:53, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 [COLOR="Red"]WPA WPA2[/COLOR]You may have better stability if the router is set to WPA2 only; not WPA and WPA2 mixed mode.> IPv6 Settings:
    Address:         fd03:5b02:c487:0:468:5731:e1e3:b326
    Prefix:          64
    Gateway:         fe80::22aa:4bff:fe53:cd51

    Address:         fd03:5b02:c487:0:2216:d8ff:fe47:f588
    Prefix:          64
    Gateway:         fe80::22aa:4bff:fe53:cd51

    Address:         fe80::2216:d8ff:fe47:f588
    Prefix:          64
    Gateway:         fe80::22aa:4bff:fe53:cd51You may also have better stability with IPv6 set to Ignore in Network Manager; please see attached. I know IPv6 is the way of the future but I'm not sure all Linux drivers are quite ready.

If you could, please try these changes and let us hear your report.

---

### Post by nickm1 on 2013-01-05
I am new to Linux, finally got to install it on a small ssd. i used a cd version 6.0 and had Internet, I installed 12.10 and nothing, I download drivers i guess for my connection, I guess i am so used to clicking on a exec file and it installs my drivers. looking at all this code and not familiar with linux version of installing drivers.  I do like it wanted to convert my laptop over to it, but as of now, i need more smarts on linux systems.  will have to figure out what i am doing. i havnt done dos type stuff sinc4e late 80"s  lol  most asnwers and questions are not not helping me any. I will play around for  awhile to see what happens. One said to go to settings and all the things they said to do i dont see. well enough, if i get internet the sys is what i need

---

### Post by colmeweb on 2013-01-05
I reset the IPv6 to ignore and will work on the router settings. Its my room-mate's so it may not be an option. I'll check back tomorrow with an update.

---

### Post by chili555 on 2013-01-05
> **nickm1 said:**
> I am new to Linux, finally got to install it on a small ssd. i used a cd version 6.0 and had Internet, I installed 12.10 and nothing, I download drivers i guess for my connection, I guess i am so used to clicking on a exec file and it installs my drivers. looking at all this code and not familiar with linux version of installing drivers.  I do like it wanted to convert my laptop over to it, but as of now, i need more smarts on linux systems.  will have to figure out what i am doing. i havnt done dos type stuff sinc4e late 80"s  lol  most asnwers and questions are not not helping me any. I will play around for  awhile to see what happens. One said to go to settings and all the things they said to do i dont see. well enough, if i get internet the sys is what i needI suggest you start your own new thread. Open a terminal and run this command:```
lspci -nn
```That means 'list all the PCI devices and include all the numeric identifiers.' Pick out items 0200 and 0280 and include them in your post. I'll be happy to help. 

Here is a sample showing what you'll get and post.> chili@LAPTOP410:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
[COLOR="Red"]00:19.0 Ethernet controller [**0200**]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)[/COLOR]
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b07] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
[COLOR="Red"]03:00.0 Network controller [**0280**]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)[/COLOR]
0d:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
0d:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [1180:e230] (rev 01)
0d:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller [1180:e832] (rev 01)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
We just need those two highlighted items, your ethernet and wireless devices.

---

### Post by nickm1 on 2013-01-06
I am on the INTERNET now running off the DVD i installed 12 over on fresh drive, wont go to Internet, but Internet works off just using the dvd, why does it work off dvd but not new install on SSD drive, shouldn't it work there as well as on dvd.. , hard to run code cause i have never done it through this, not like run in windows, or the little bit of DOS i remember. i would start new thread bit it wont let me. I did not do my normal 25 posts. or something like that.

---

### Post by nickm1 on 2013-01-06
OK i disconnected my pc from my wireless router its a Microsoft m700 kind of old, and i went right to cable modem to pc, it works there, I am not making it thru my router to net, So i have to figure out why it can make it thru the dvd version but not off hard-drive install....

---

### Post by chili555 on 2013-01-06
> So i have to figure out why it can make it thru the dvd version but not off hard-drive install....What driver is loaded in one but not the other? Compare from each:```
lsmod
```

---

### Post by nickm1 on 2013-01-07
thanks for your help. My router is from microsoft wireless. I had a net gear one new i bought with no manuals or software in white box for 7 new from egghead two yrs ago, i decided to take that one and add it to my pc, and do away with microsofts, took care of it, loaded it and all worked fine. But i appreciate the help and using old done thread. makes it easier, thanks

---

### Post by chili555 on 2013-01-07
> **nickm1 said:**
> thanks for your help. My router is from microsoft wireless. I had a net gear one new i bought with no manuals or software in white box for 7 new from egghead two yrs ago, i decided to take that one and add it to my pc, and do away with microsofts, took care of it, loaded it and all worked fine. But i appreciate the help and using old done thread. makes it easier, thanksAwesome! Glad it's working.

---

### Post by bb2013 on 2013-01-07
Hi Chili,

```
My favorite kind of problem: everything looks just perfect, except it doesn't work! 
```OM, if so, I bet you will like to hear what I am going to say here.

After leaving my laptop over weekend, I switched it on and run the following (with ethernet cable attached)

sudo modprobe -r rtl8723ae
sudo modprobe rtl8723ae

the wireless just works/connected........no doubt I have tried the above method quite a few times in the past but didnt work then......


```
dmesg | grep -i rtl
cat /var/log/syslog | grep -i -e rtl -e etwork | tail -n20
```Please run all tests with the ethernet detached.[/QUOTE]

with the wlan0 currently working (ethernet detached), the following is what I got.....

[COLOR=Red]cat /var/log/syslog | grep -i -e rtl -e etwork | tail -n20[/COLOR]
Jan  7 16:07:03 BB NetworkManager[849]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jan  7 16:07:03 BB NetworkManager[849]: <info>   address 192.xxx.x.x
Jan  7 16:07:03 BB NetworkManager[849]: <info>   prefix 24 (255.255.255.0)
Jan  7 16:07:03 BB NetworkManager[849]: <info>   gateway 192.xxx.x.x
Jan  7 16:07:03 BB NetworkManager[849]: <info>   nameserver '194.168.4.100'
Jan  7 16:07:03 BB NetworkManager[849]: <info>   nameserver '194.168.8.100'


Thanks for looking into it.

thanks,
BB

---

### Post by colmeweb on 2013-01-07
So my connection is better, but it still drops out once in a while. I am still not sure why opening Transmission kicks it back on, but that is my goto rite now.

---

### Post by tanghus on 2013-02-19
FYI: It seems the newest kernel update to 3.5.0-24 killed wifi on Toshiba Satellite C850D-121. 3.5.0-23 still works OK.

---

### Post by chili555 on 2013-02-19
> **tanghus said:**
> FYI: It seems the newest kernel update to 3.5.0-24 killed wifi on Toshiba Satellite C850D-121. 3.5.0-23 still works OK.Any chance you'd like to troubleshoot?

---

### Post by tanghus on 2013-02-22
> **chili555 said:**
> Any chance you'd like to troubleshoot?
Sure, but you would have to guide me ;) 3.5.0-25 has the same problem btw.
Sorry for the late reply. I had forgotten to enable notifications.

---

### Post by chili555 on 2013-02-23
> **tanghus said:**
> Sure, but you would have to guide me ;) 3.5.0-25 has the same problem btw.
Sorry for the late reply. I had forgotten to enable notifications.First, tell us about your wireless card details. Open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by tanghus on 2013-02-23
Currently using 3.5.0-23 to be able to be on the net ;)
```

$ dmesg | grep rtl
[   18.453598] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   19.173679] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.174224] rtlwifi: wireless switch is on
```


```

$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
```

```
$ lsmod | grep rtl
rtl8723ae              86362  0 
rtlwifi                79634  1 rtl8723ae
mac80211              601721  1 rtlwifi
cfg80211              516149  2 rtlwifi,mac80211
compat                 19339  4 rtl8723ae,rtlwifi,mac80211,cfg80211
```

And the following is running 3.5.0-25

```
$ lsmod | grep rtl
rtl8723ae              86362  0 
rtlwifi                79594  1 rtl8723ae
mac80211              612116  1 rtlwifi
cfg80211              526015  2 rtlwifi,mac80211
compat                 19589  4 rtl8723ae,rtlwifi,mac80211,cfg80211
```

```
$ dmesg | grep rtl
[   18.147458] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   19.008647] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.009122] rtlwifi: wireless switch is on
```

/var/log/syslog:

```
Feb 23 16:57:47 tanghus-laptop polkitd[1163]: started daemon version 0.104 using authority implementation `local' version `0.104'
Feb 23 16:57:47 tanghus-laptop dbus[1037]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: init!
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: update_system_hostname
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPluginIfupdown: management mode: unmanaged
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/net/wlan0, iface: wlan0)
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/net/wlan0, iface: wlan0): no ifupdown configura
tion found.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.2/0000:07:00.0/net/eth0, iface: eth0)
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.2/0000:07:00.0/net/eth0, iface: eth0): no ifupdown configurati
on found.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: end _init.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    Ifupdown: get unmanaged devices count: 0
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: (26470192) ... get_connections.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    SCPlugin-Ifupdown: (26470192) ... get_connections (managed=false): return empty list.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile: parsing Felix-II ... 
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile:     read connection 'Felix-II'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile: parsing SPX-Guest ... 
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile:     read connection 'SPX-Guest'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile: parsing Tanghus ... 
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile:     read connection 'Tanghus'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile: parsing NETGEAR ... 
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile:     read connection 'NETGEAR'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile: parsing Nokia_950_tanghus ... 
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile:     read connection 'Nokia_950_tanghus'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile: parsing Wired connection 1 ... 
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    keyfile:     read connection 'Wired connection 1'
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]:    Ifupdown: get unmanaged devices count: 0
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> modem-manager is now available
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/ieee80211/phy0/rfkill1) (driver (unknown))
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> WiFi enabled by radio killswitch; enabled by state file
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> WWAN enabled by radio killswitch; enabled by state file
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> WiMAX enabled by radio killswitch; enabled by state file
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> Networking is enabled by state file
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> (wlan0): using nl80211 for WiFi device control
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <warn> (wlan0): driver supports Access Point (AP) mode
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8723ae' ifindex: 3)
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> (wlan0): now managed
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 23 16:57:47 tanghus-laptop NetworkManager[1128]: <info> (wlan0): bringing up device.
Feb 23 16:57:48 tanghus-laptop acpid: starting up with proc fs
Feb 23 16:57:48 tanghus-laptop cron[1245]: (CRON) INFO (pidfile fd = 3)
Feb 23 16:57:48 tanghus-laptop acpid: 33 rules loaded
Feb 23 16:57:48 tanghus-laptop acpid: waiting for events: event logging is off
Feb 23 16:57:48 tanghus-laptop cron[1281]: (CRON) STARTUP (fork ok)
Feb 23 16:57:48 tanghus-laptop cron[1281]: (CRON) INFO (Running @reboot jobs)
Feb 23 16:57:48 tanghus-laptop anacron[1275]: Anacron 2.3 started on 2013-02-23
Feb 23 16:57:48 tanghus-laptop anacron[1275]: Normal exit (0 jobs run)
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0): preparing device.
Feb 23 16:57:48 tanghus-laptop kernel: [   19.969753] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0): deactivating device (reason 'managed') [2]
Feb 23 16:57:48 tanghus-laptop dbus[1037]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 23 16:57:48 tanghus-laptop kernel: [   19.972386] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): carrier is OFF
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): now managed
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): bringing up device.
Feb 23 16:57:48 tanghus-laptop acpid: client connected from 1341[0:0]
Feb 23 16:57:48 tanghus-laptop acpid: 1 client rule loaded
Feb 23 16:57:48 tanghus-laptop dbus[1037]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Feb 23 16:57:48 tanghus-laptop kernel: [   20.194967] r8169 0000:07:00.0: eth0: link down
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): preparing device.
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb 23 16:57:48 tanghus-laptop kernel: [   20.196662] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 23 16:57:48 tanghus-laptop kernel: [   20.197587] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> wpa_supplicant started
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0) supports 4 scan SSIDs
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0): supplicant interface state: starting -> ready
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <warn> Trying to remove a non-existant call id.
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0): supplicant interface state: ready -> inactive
Feb 23 16:57:48 tanghus-laptop NetworkManager[1128]: <info> (wlan0) supports 4 scan SSIDs
```

---

### Post by chili555 on 2013-02-23
> And the following is running 3.5.0-25I don't see much wrong here. What I don't see that I wish I was seeing is the result of clicking on one of these networks, asking for a connection and it refusing. What happens when you try to connect?```
keyfile: parsing Felix-II ... 
keyfile:     read connection 'Felix-II'
keyfile: parsing SPX-Guest ... 
keyfile:     read connection 'SPX-Guest'
keyfile: parsing Tanghus ... 
keyfile:     read connection 'Tanghus'
keyfile: parsing NETGEAR ... 
keyfile:     read connection 'NETGEAR'
keyfile: parsing Nokia_950_tanghus ... 
keyfile:     read connection 'Nokia_950_tanghus'
```Please be a little more specific than 'newest kernel update to 3.5.0-24 killed wifi.'

---

### Post by tanghus on 2013-02-23
> **chili555 said:**
> What happens when you try to connect?

It's quite long, so I've made a pastebin [http://pastebin.com/qgHUDcsa](http://pastebin.com/qgHUDcsa)

KDEs network manager pops up asking for password two time during this log session, but connection still fails. The only difference is that I select a different kernel version at grub menu.

> **chili555 said:**
> Please be a little more specific than 'newest kernel update to 3.5.0-24 killed wifi.'

Yeah, sorry about that. I was on my way out, and just wanted to warn any that a kernel update could break wifi.

---

### Post by chili555 on 2013-02-23
I googled the message:> wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded...and I found this: [http://www.spinics.net/lists/linux-wireless/msg103577.html](http://www.spinics.net/lists/linux-wireless/msg103577.html)> Yeah, it's obvious that this would happen for drivers not supporting
TDLS -- will send a patch. Notice the date is just a few days ago; Sun, 2013-02-17 at 00:31.

You could just use the previous kernel and wait for a fix or you could try linux-backports-modules-cw. Frankly, for a flaw that was discovered so recently, I doubt backports would have been updated by now.

You might also try a driver parameter:```
sudo modprobe -r rtl8723ae
sudo modprobe rtl8723ae swenc=1
```If it helps, we can write a quick file to make it persistent.

---

### Post by tanghus on 2013-02-23
> **chili555 said:**
> Frankly, for a flaw that was discovered so recently, I doubt backports would have been updated by now.

Ah, great that it is already known of.

The driver parameter didn't work, so I'll just keep using .23 and download backports once in a while to see what happens :)

Thanks for your help - I wouldn't know where to look.

/Thomas

---

### Post by chili555 on 2013-02-23
Please keep us, in particular the searchers, posted.

---

### Post by tanghus on 2013-02-23
> **chili555 said:**
> Please keep us, in particular the searchers, posted.

Will do :)

---

### Post by colmeweb on 2013-02-27
Its me again, so after the last kernel update I ran through the normal process and it still doesn't work. Here is the readout form 
lspci -v

```
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 2000 [size=256]
	Memory at f0104000 (64-bit, prefetchable) [size=4K]
	Memory at f0100000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 5c-02-00-00-36-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```

I think I might need a new driver file.
Any help would be great.

---

### Post by chili555 on 2013-03-01
> Its me again, so after the last kernel update I ran through the normal process and it still doesn't work.Are you taliking about wireless? You posted details of your wired ethernet. Please try again:```
lspci -nn | grep 0280
```Did you re-compile the driver? Any errors, warnings, smoke or sparks??

What exactly doesn't work? It didn't compile? It won't connect? It's slow? Or ... what?

---

### Post by colmeweb on 2013-03-05
Thanks chili, 
My wireless has been dropping in and out for no reason. I think it might be a hardware thing.

---

### Post by chili555 on 2013-03-06
Does it work well or drop out unexpectedly on That Other Operating System?

---

### Post by phantomlord69 on 2013-04-02
> **chili555 said:**
> Download the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:```
cd Desktop/compat-drivers-2012-12-04 sudo su ./scripts/driver-select rtlwifi make  make install modprobe rtl8723ae exit
```  Thanks a lot ! After 2 days it's the only way to make it work for me ! Again, thank you very much :)

---

### Post by colmeweb on 2013-04-15
It also drops out randomly when I am using Windows 7 and 8.

I was wondering if there has been a release of an update to the driver I am currently using? 
or if  13.04 will have native support for this modem?

---

### Post by chili555 on 2013-04-16
> **colmeweb said:**
> 
or if  13.04 will have native support for this modem?Ubuntu 13.04 includes the module rtl8723ae by default.

---

