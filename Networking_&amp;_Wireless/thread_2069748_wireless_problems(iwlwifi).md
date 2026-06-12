---
title: "wireless problems(iwlwifi)"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by stuckubu on 2012-10-11
hi,i'm new here):P,and i'm fresh to linux.i have  some problems to get my wireless working,but the wired works fine.
it seems like it havent load the modules,even i have no idea what modules it need.
it is intel wireless centrino n-2230.
```
lemon@lemon:~$ uname -a
Linux lemon 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
lemon@lemon:~$ lspci -nn | grep -i net
03:00.0 Network controller [0280]: Intel Corporation Device [8086:0888] (rev c4)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
lemon@lemon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

lemon@lemon:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
lemon@lemon:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40329  4 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
joydev                 11072  0 
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
nouveau               515131  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
btusb                  12969  2 
v4l2_compat_ioctl32    12020  1 videodev
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
drm                   198770  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
video                  20623  0 
output                  2503  1 video
psmouse                64608  0 
serio_raw               4918  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
xhci                   40958  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
r8169                  39554  0 
mii                     5237  1 r8169
ahci                   37646  2 
lemon@lemon:~$ 

```i have got stuck here for a few days:cry:.it will be nice if someone help me.

---

### Post by stuckubu on 2012-10-13
i have download compat-wireless-2.6.32.16.tar.bz2 from [http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.37_stable_releases]("http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.37_stable_releases")
i follow the step of README from the package,when i try
```
make
```
it got some errors like this
```
/media/B0008017007FE330/compat-wireless-2.6.32.16/drivers/net/wireless/ipw2x00/ipw2100.c: In function ‘ipw2100_alloc_device’:
/media/B0008017007FE330/compat-wireless-2.6.32.16/drivers/net/wireless/ipw2x00/ipw2100.c:6060: error: ‘struct iw_public_data’ has no member named ‘ieee80211’
make[4]: *** [/media/B0008017007FE330/compat-wireless-2.6.32.16/drivers/net/wireless/ipw2x00/ipw2100.o] &#38169;&#35823; 1
make[3]: *** [/media/B0008017007FE330/compat-wireless-2.6.32.16/drivers/net/wireless/ipw2x00] &#38169;&#35823; 2
make[2]: *** [/media/B0008017007FE330/compat-wireless-2.6.32.16/drivers/net/wireless] &#38169;&#35823; 2
make[1]: *** [_module_/media/B0008017007FE330/compat-wireless-2.6.32.16] &#38169;&#35823; 2
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] &#38169;&#35823; 2

```
i think it said i don't have ieee80211 subsystem in my kernel ,so i download ieee80211-1.2.18.tgz ,i try to install it,but it also got error like this :( ```
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.32-21-generic for ieee80211 components...
make -C /lib/modules/2.6.32-21-generic/build M=/media/B0008017007FE330/ieee80211-1.2.18 modules
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
/media/B0008017007FE330/ieee80211-1.2.18/Makefile:17: 
/media/B0008017007FE330/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/media/B0008017007FE330/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/media/B0008017007FE330/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/media/B0008017007FE330/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.o
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING  			page 1


   1              	.file "ieee80211_module.c"
   9              	.Ltext0:

GAS LISTING  			page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/media/B0008017007FE330/ieee80211-1.2.18/ieee80211_module.o] &#38169;&#35823; 1
make[1]: *** [_module_/media/B0008017007FE330/ieee80211-1.2.18] &#38169;&#35823; 2
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] &#38169;&#35823; 2

```
it seems like i have download the wrong version ,am i right?someone help!!!

---

### Post by steeldriver on 2012-10-13
Let's see if we can figure out exactly which Intel device you have and if we can get the correct driver and firmware to load manually with modprobe

```
sudo lshw -C network
```Personally I wouldn't jump into compat modules or source builds until I'd explored all other avenues - it will make your system harder to maintain if you go that route

---

### Post by stuckubu on 2012-10-13
> **steeldriver said:**
> Let's see if we can figure out exactly which Intel device you have and if we can get the correct driver and firmware to load manually with modprobe

```
sudo lshw -C network
```Personally I wouldn't jump into compat modules or source builds until I'd explored all other avenues - it will make your system harder to maintain if you go that route

thanks for your replay 
```
lemon@lemon:~$ sudo lshw -c network
[sudo] password for lemon: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e2900000-e2901fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:12:f0:83
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.4.145.32 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:34 ioport:2000(size=256) memory:e2004000-e2004fff(prefetchable) memory:e2000000-e2003fff(prefetchable)
lemon@lemon:~$ 


```

---

### Post by chili555 on 2012-10-13
I suggest you try going back to the compat-wireless package and do:```
cd /media/B0008017007FE330/
cp compat* Desktop
```I don't know if 'media' is a CD or a USB key or what, but it's generally preferable to work on a location on your harddrive rather than removable media. Now do:```
cd ~/Desktop/compat-wireless-2.6.32.16/
sudo su
make clean
./scripts/driver-select restore
./scripts/driver-select
```You will want either iwlagn or iwlwifi, whichever it's called.```
./scripts/driver-select iwlwifi [COLOR="Red"]<--or whichever you saw above[/COLOR]
make
make install
```Any errors? If so, I then suggest you try the later compat here: [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless.tar.bz2)

I will be traveling for the next 24 hours or so. I'll look for your report then.

---

### Post by stuckubu on 2012-10-14
> **chili555 said:**
> I suggest you try going back to the compat-wireless package and do:```
cd /media/B0008017007FE330/
cp compat* Desktop
```I don't know if 'media' is a CD or a USB key or what, but it's generally preferable to work on a location on your harddrive rather than removable media. Now do:```
cd ~/Desktop/compat-wireless-2.6.32.16/
sudo su
make clean
./scripts/driver-select restore
./scripts/driver-select
```You will want either iwlagn or iwlwifi, whichever it's called.```
./scripts/driver-select iwlwifi [COLOR="Red"]<--or whichever you saw above[/COLOR]
make
make install
```Any errors? If so, I then suggest you try the later compat here: [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless.tar.bz2)

I will be traveling for the next 24 hours or so. I'll look for your report then.
it not a CD or a USB key ,just a harddrive in windows ,i have copied the files to Desktop ,and tap the code you offered
```
./scripts/driver-select
Usage: ./scripts/driver-select [ <driver-name> | <driver-group-name> | restore ]
Supported drivers:
	ath5k
	ath9k
	ar9170
	zd1211rw
Supported group drivers:
	atheros <  ath5k ath9k ar9170 zd1211rw >
	ath <  ath5k ath9k ar9170 >
	intel <  iwl3945 iwlagn ipw2100 ipw2200 >
	iwlwifi <  iwl3945 iwlagn >
	rtl818x <  rtl8180 rtl8187 >
	wl12xx <  wl1251 (SPI and SDIO) wl1271 >
Restoring compat-wireless:
	restore: you can use this option to restore compat-wireless to the original state

```
i don't known which should i choose ,iwlang or iwlwifi (my wireless adapter is intel centrino wireless n-2230 )? i try the iwlwifi,there is no errors,and i reboot ,it still doesn't work:(

---

### Post by chili555 on 2012-10-15
> i try the iwlwifi,there is no errors,and i reboot ,it still doesn't workLet's be sure the version you compiled covers your device:> Intel Corporation Device [[COLOR="Red"]8086:0888[/COLOR]]```
modinfo iwlwifi | grep 0888
```Also please post:```
iwconfig
rfkill list all
dmesg | grep iwl
```

---

### Post by stuckubu on 2012-10-15
> **chili555 said:**
> Let's be sure the version you compiled covers your device:```
modinfo iwlwifi | grep 0888
```Also please post:```
iwconfig
rfkill list all
dmesg | grep iwl
```
thanks,the result seems i haven't load the iwlwifi module
```
lemon@lemon:~$ modinfo iwlwifi | grep 0888
ERROR: modinfo: could not find module iwlwifi
lemon@lemon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

lemon@lemon:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
lemon@lemon:~$ dmesg | grep iwl
lemon@lemon:~$ 
```
what's wrong with it?

---

### Post by chili555 on 2012-10-15
Please try again:```
modinfo iwlagn | grep -e 0888 -e version -e lib
```Thanks.

---

### Post by stuckubu on 2012-10-15
> **chili555 said:**
> Please try again:```
modinfo iwlagn | grep -e 0888 -e version -e lib
```Thanks.
thanks,it likes this .
```
lemon@lemon:~$ modinfo iwlagn | grep -e 0888 -e version -e lib
filename:       /lib/modules/2.6.32-21-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
version:        1.3.27ks
srcversion:     A65DF91449349D909F95354
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
lemon@lemon:~$ 

```
what this mean ? i have install the iwlagn , not the iwlwifi?

---

### Post by chili555 on 2012-10-15
It's starting to look like you missed a step or two. Let's retrace our steps:```
cd ~/Desktop/compat-wireless-2.6.32.16/
sudo su
make clean
./scripts/driver-select restore
./scripts/driver-select iwlwifi
make
make install
exit
modinfo iwlagn | grep 0888
```If you don't see your device listed now, then you'll need to compile the later version I linked above. I checked it and your device *IS* listed.

---

### Post by stuckubu on 2012-10-15
> **chili555 said:**
> It's starting to look like you missed a step or two. Let's retrace our steps:```
cd ~/Desktop/compat-wireless-2.6.32.16/
sudo su
make clean
./scripts/driver-select restore
./scripts/driver-select iwlwifi
make
make install
exit
modinfo iwlagn | grep 0888
```If you don't see your device listed now, then you'll need to compile the later version I linked above. I checked it and your device *IS* listed.
i don't remember whether i missed a step,i traced the steps.
```
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16# make clean
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16# ./scripts/driver-select restore
Restored makefile: ./Makefile (and removed backup)
Restored makefile: ./net/wireless/Makefile (and removed backup)
Restored makefile: ./drivers/misc/eeprom/Makefile (and removed backup)
Restored makefile: ./drivers/ssb/Makefile (and removed backup)
Restored makefile: ./drivers/net/usb/Makefile (and removed backup)
Restored makefile: ./drivers/net/Makefile (and removed backup)
Restored makefile: ./drivers/net/wireless/Makefile (and removed backup)
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16# ./scripts/driver-select iwlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/net/usb/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16# make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.32-21-generic/build M=/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16 modules
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/built-in.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl3945-base.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-3945.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-3945-rs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-3945-led.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-agn.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-4965.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-6000.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-1000.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-core.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-hcmd.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-sta.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-calib.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-scan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-led.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl-spectrum.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlcore.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlagn.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl3945.o
  LD      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/built-in.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/main.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/sta_info.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/wep.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/wpa.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/scan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/ht.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/agg-tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/agg-rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/ibss.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mlme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/iface.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/rate.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/michael.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/tkip.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/aes_ccm.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/aes_cmac.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/cfg.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/spectmgmt.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/key.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/util.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/wme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/event.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/led.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/debugfs_sta.o
/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/debugfs_sta.c: In function ‘sta_agg_status_read’:
/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/debugfs_sta.c:157: warning: the frame size of 1232 bytes is larger than 1024 bytes
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/debugfs_netdev.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/debugfs_key.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mesh.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mesh_plink.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mesh_hwmp.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/pm.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/rc80211_minstrel_debugfs.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mac80211.o
  LD      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/rfkill/built-in.o
  LD      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/built-in.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/core.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/sysfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/radiotap.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/util.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/reg.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/scan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/nl80211.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/mlme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/ibss.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/sme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/chan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/wext-compat.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/wext-sme.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/cfg80211.o
  LD      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/built-in.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlagn.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlagn.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mac80211.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mac80211.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/cfg80211.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/cfg80211.ko
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16# make install
WARNING: -e needs -E or -F
Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

make -C /lib/modules/2.6.32-21-generic/build M=/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16 modules
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
  Building modules, stage 2.
  MODPOST 5 modules
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
make -C /lib/modules/2.6.32-21-generic/build M=/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/mac80211/mac80211.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16/net/wireless/cfg80211.ko
  DEPMOD  2.6.32-21-generic
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
Updating Ubuntu's initramfs for 2.6.31-wl under /boot/ ...
Cannot find /lib/modules/2.6.31-wl
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
depmod will prefer updates/ over kernel/ -- OK!
WARNING: -e needs -E or -F
Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
updates/drivers/net/wireless/iwlwifi/iwl3945.ko
updates/drivers/net/wireless/iwlwifi/iwlagn.ko
updates/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2.6.32.16# exit
exit
lemon@lemon:~/&#26700;&#38754;/compat-wireless-2.6.32.16$ modinfo iwlagn | grep 0888
lemon@lemon:~/&#26700;&#38754;/compat-wireless-2.6.32.16$ modinfo iwlagn | grep 0888
```
it seems like it still can not find the device.Then i tried the later version , it goes like this 
```
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03# make clean
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03# ./scripts/driver-select restore
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03# ./scripts/driver-select iwlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/bcma/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03# make
./scripts/gen-compat-autoconf.sh /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/.config /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.32-21-generic/build M=/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03 modules
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/main.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.33.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.34.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.35.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.36.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/kfifo.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.37.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.38.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-2.6.39.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/kstrtox.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.0.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.1.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.2.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.3.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.4.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.5.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/user_namespace.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat-3.7.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/cordic.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/crc8.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_fq_codel_core.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/flow_dissector.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat_firmware_class.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_codel.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_fq_codel.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwl-io.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwl-drv.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwl-debug.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwl-notif-wait.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwl-eeprom-read.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwl-eeprom-parse.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/drv.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/trans.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/1000.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/2000.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/5000.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/pcie/6000.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwlwifi.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/main.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/rs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/mac80211.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/ucode.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/lib.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/calib.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/tt.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/sta.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/power.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/scan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/led.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/rxon.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/devices.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/iwldvm.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/main.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/status.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/sta_info.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/wep.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/wpa.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/scan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/offchannel.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/ht.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/agg-tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/agg-rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/ibss.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/iface.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rate.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/michael.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/tkip.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/aes_ccm.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/aes_cmac.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/cfg.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/spectmgmt.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/tx.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/key.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/util.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/wme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/event.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/chan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mlme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/led.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/debugfs_sta.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/debugfs_netdev.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/debugfs_key.o
/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/debugfs_key.c:37:1: warning: "KEY_FILE" redefined
In file included from /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/include/linux/compat-2.6.33.h:16,
                 from /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/include/linux/compat-2.6.h:54,
                 from <command-line>:0:
include/linux/input.h:270:1: warning: this is the location of the previous definition
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mesh.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mesh_plink.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mesh_hwmp.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mesh_sync.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/pm.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mac80211.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/core.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/sysfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/radiotap.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/util.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/reg.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/scan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/nl80211.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/mlme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/ibss.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/sme.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/chan.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/ethtool.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/mesh.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/ap.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/debugfs.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/wext-compat.o
  CC [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/wext-sme.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 8 modules
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat_firmware_class.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat_firmware_class.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_codel.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_codel.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_fq_codel.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_fq_codel.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/iwldvm.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwlwifi.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwlwifi.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mac80211.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mac80211.ko
  CC      /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/cfg80211.mod.o
  LD [M]  /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/cfg80211.ko
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03# make install

make -C /lib/modules/2.6.32-21-generic/build M=/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03 modules
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
  Building modules, stage 2.
  MODPOST 8 modules
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
make -C /lib/modules/2.6.32-21-generic/build M=/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: &#27491;&#22312;&#36827;&#20837;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/compat_firmware_class.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_codel.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/compat/sch_fq_codel.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/iwlwifi.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/mac80211/mac80211.ko
  INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/net/wireless/cfg80211.ko
  DEPMOD  2.6.32-21-generic
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-2.6.32-21-generic'
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

root@lemon:/home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03# exit
exit
lemon@lemon:~/&#26700;&#38754;/compat-wireless-2012-10-03$ modinfo iwlagn | grep 0888
```
when i tried "modinfo iwlagn | grep 0888",there is nothing happened.

---

### Post by stuckubu on 2012-10-16
:P,when i reboot ,i works.Now i'm reply you with the wifi , thanks a lots. i think it is the later version works.but  i want to know what "./scripts/driver-select restore " and "./scripts/driver-select iwlwifi " means? if i go straight to the```
make
``` and ```
make install 
``` 
it didn't work.

---

### Post by VK7AY on 2012-10-16
My problem sounds much like yours, and have spent past 2 weeks trying.. 
Today decided to try something different, opened the Bios of the HP Pavilion Laptop Win 7, and under Configuration found NETWORK ADAPTER was showing as DISABLED. Changed to ENABLED. 

Re-booted and hey presto. It works again as it used to do. 
No idea how or why became disabled.

Ubuntu 12.04 within Windows installed using WUBI about 10 months ago, never a problem then refused to connect to WiFi, although wireless networks were being displayed including my own. Connection by wire no problem.

I would suggest well worth a try.

Back to growing finger nails.

donver.

---

### Post by chili555 on 2012-10-16
> **stuckubu said:**
>  i want to know what "./scripts/driver-select restore " and "./scripts/driver-select iwlwifi " means? if i go straight to the```
make
``` and ```
make install 
``` 
it didn't work.'restore' removes any configuration files that were written when you tried other steps. 'driver-select iwlwifi' tells the build that you only need to make up the iwlwifi suite and not to waste time and CPU cycles on ath9k, b43, etc., etc. that you don't have or need.> when i tried "modinfo iwlagn | grep 0888",there is nothing happened. That's because it built the driver iwlwifi:> INSTALL /home/lemon/&#26700;&#38754;/compat-wireless-2012-10-03/drivers/net/wireless/iwlwifi/[COLOR="Red"]iwlwifi.ko[/COLOR]I'm quite certain that if you did:```
modinfo iwlwifi | grep 0888
```...you'd see your device is covered. We know it is because it works now!

Whenever a later kernel is installed by Update Manager, you'll need to recompile:```
cd ~/&#26700;&#38754;/compat-wireless-2012-10-03
sudo su
make clean
./scripts/driver-select restore
./scripts/driver-select iwlwifi
make
make install
exit
```When you upgrade to 12.04LTS, it will work out of the box.

Please use thread tools at the top to mark Solved.

---

### Post by stuckubu on 2012-10-16
thanks again,it is the first difficult problem i met with in ubuntu , it cost much time ,but i learned a lot . thanks you are so patient to answer my question.

---

### Post by chili555 on 2012-10-16
I was happy to help. Thanks for your kind words.

---

### Post by Gabri22 on 2012-12-30
Thank you so much [chili555]("http://ubuntuforums.org/member.php?u=35909"). 

¡Happy Christmas and Happy New Year! :p

---

