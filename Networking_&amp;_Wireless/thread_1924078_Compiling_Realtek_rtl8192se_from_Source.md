---
title: "Compiling Realtek rtl8192se from Source"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by IrrationlArtist on 2012-02-11
So, I just installed Debian. I realized that this is an Ubuntu forum, but whatever, I don't have an account on the Debian forums and I've spend the large majority of today trying to do this.

Everything has gone great, except for installing wireless drivers.
I followed the instructions on these two pages to try and install them:

[http://wiki.debian.org/WiFi](http://wiki.debian.org/WiFi)
[http://wiki.debian.org/WiFi/HowToUse](http://wiki.debian.org/WiFi/HowToUse)

No dice. The packages wireless-tools and firmware-realtek apparently don't include the rtl8192se modules.

I tried compiling several different drivers from source, and I keep getting this error: 

drew@salazaar:~/Downloads/rtl8192se_linux_2.6.0010.1211.2009$ sudo make
make[1]: Entering directory `/lib/modules/2.6.32-5-amd64/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.32-5-amd64/build'
make: *** [all] Error 2

I've installed build-essentials, linux-devel, and the linux headers for my kernel, and tried many other random fixes, most of which I can't remember because I applied them several hours ago.

I currently managing everything through Wicd (or trying).

If anyone can post a fix or a link to a amd64 .deb, I officially love you.

Edit: here's some information I forgot to include, sorry.


drew@salazaar:~$ sudo lspci -nn | grep Wireless
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)



eth0      Link encap:Ethernet  HWaddr c8:0a:a9:96:aa:1d  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fe96:aa1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89572512 (85.4 MiB)  TX bytes:2448479 (2.3 MiB)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8756 (8.5 KiB)  TX bytes:8756 (8.5 KiB)


drew@salazaar:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


drew@salazaar:~$ lsmod
Module                  Size  Used by
sco                     7225  2 
bridge                 39646  0 
stp                     1440  1 bridge
bnep                    9427  2 
rfcomm                 29629  0 
l2cap                  24752  6 bnep,rfcomm
bluetooth              41827  6 sco,bnep,rfcomm,l2cap
rfkill                 13044  2 bluetooth
acpi_cpufreq            5571  0 
cpufreq_stats           2740  0 
cpufreq_conservative     5162  0 
cpufreq_userspace       1992  0 
parport_pc             18855  0 
ppdev                   5030  0 
cpufreq_powersave        902  0 
lp                      7462  0 
parport                27954  3 parport_pc,ppdev,lp
nfsd                  254782  11 
lockd                  57619  1 nfsd
nfs_acl                 2031  1 nfsd
auth_rpcgss            33508  1 nfsd
sunrpc                161621  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3170  1 nfsd
uinput                  6376  1 
fuse                   50924  1 
loop                   11799  0 
joydev                  8459  0 
snd_hda_codec_intelhdmi    10695  1 
snd_hda_codec_realtek   235698  0 
i915                  256094  2 
drm_kms_helper         20369  1 i915
drm                   142279  3 i915,drm_kms_helper
i2c_algo_bit            4209  1 i915
snd_hda_intel          20035  0 
video                  17445  1 i915
snd_hda_codec          54244  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               52127  0 
videodev               30041  1 uvcvideo
v4l1_compat            11442  2 uvcvideo,videodev
v4l2_compat_ioctl32     8474  1 videodev
output                  1692  1 video
i2c_i801                7830  0 
snd_hwdep               5380  1 snd_hda_codec
psmouse                49937  0 
i2c_core               15819  6 i915,drm_kms_helper,drm,i2c_algo_bit,videodev,i2c_i801
snd_pcm                60487  2 snd_hda_intel,snd_hda_codec
evdev                   7352  21 
serio_raw               3752  0 
pcspkr                  1699  0 
snd_timer              15598  1 snd_pcm
wmi                     4323  0 
snd                    46526  7 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               4598  1 snd
snd_page_alloc          6249  2 snd_hda_intel,snd_pcm
ac                      2192  0 
battery                 4998  0 
button                  4650  1 i915
processor              29935  3 acpi_cpufreq
ext4                  288382  1 
mbcache                 5050  1 ext4
jbd2                   67079  1 ext4
crc16                   1319  2 l2cap,ext4
sg                     24069  0 
sd_mod                 29937  3 
sr_mod                 12602  0 
crc_t10dif              1276  1 sd_mod
cdrom                  29415  1 sr_mod
uhci_hcd               18521  0 
ahci                   32870  2 
libata                133776  1 ahci
scsi_mod              126725  4 sg,sd_mod,sr_mod,libata
r8169                  36840  0 
mii                     3210  1 r8169
ehci_hcd               32097  0 
thermal                11674  0 
thermal_sys            11942  3 video,processor,thermal
usbcore               123122  4 uvcvideo,uhci_hcd,ehci_hcd
nls_base                6377  1 usbcore



drew@salazaar:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d3500000-d3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:96:aa:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:2000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)

---

### Post by praseodym on 2012-02-12
Hi,

maybe the driver is too old (2009)? Tried a later version from the Realtek homepage?

---

### Post by IrrationlArtist on 2012-02-12
No joy. Got the latest driver from this page: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=230&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=230&DownTypeID=3&GetDown=false&Downloads=true)

And I still get the same error upon compile.

I tried running a script called autoconf_rtl8172_usb_linux.h and got this error: 

drew@salazaar:~/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401$ ./autoconf_rtl8712_usb_linux.h 
./autoconf_rtl8712_usb_linux.h: line 1: /bin: is a directory
./autoconf_rtl8712_usb_linux.h: line 2: autoconf_rtl8712_usb_linux.h: command not found
./autoconf_rtl8712_usb_linux.h: line 3: syntax error near unexpected token `('
./autoconf_rtl8712_usb_linux.h: line 3: ` * Copyright(c) 2007 - 2010 Realtek Corporation. All rights reserved.'


I also tried installing using another script, found in the ./compat directory of the downloaded and unpacked driver, and that didn't do anything either.

---

### Post by praseodym on 2012-02-12
Try the compilation with

```
make
sudo make install
```
and reboot after that.

---

### Post by IrrationlArtist on 2012-02-12
> **praseodym said:**
> Try the compilation with

```
make
sudo make install
```
and reboot after that.

Wait, what? That was the first thing I tried. the whole point is that those commands aren't working.

Anyways, after some more Googling, I found this thread:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/realtek-rtl8192se-install-make-errors-debian-907650/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/realtek-rtl8192se-install-make-errors-debian-907650/)

The OP in this thread eventually got the driver to compile by copying the contents of /usr/src/linux-headers-2.6.32-5-amd64 and some other directory he refers to as 'source' to /lib/modules/2.6.32-amd64/build. I tried installing linux-source-2.6.23 (or whatever the package was called) and no magic 'source' directory appeared, but I now get this output while trying to compile:

drew@salazaar:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$ sudo make
make -C /lib/modules/2.6.32-5-amd64/build M=/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/lib/modules/2.6.32-5-amd64/build'
  CC [M]  /home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o
In file included from /home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:32:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/wifi.h: In function ‘rtl_find_sta’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/wifi.h:2094: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
/usr/src/linux-headers-2.6.32-5-common/include/net/mac80211.h:2091: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:34:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.h: At top level:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.h:143: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.h:143: warning: its scope is only this definition or declaration, which is probably not what you want
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘_rtl_init_mac80211’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:322: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:322: error: (Each undeclared identifier is reported only once
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:322: error: for each function it appears in.)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_tx_agg_start’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:991: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
/usr/src/linux-headers-2.6.32-5-common/include/net/mac80211.h:2038: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_tx_agg_stop’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1020: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
/usr/src/linux-headers-2.6.32-5-common/include/net/mac80211.h:2079: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1274: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: At top level:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1332: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1332: error: parameter 2 (‘smps’) has incomplete type
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_make_smps_action’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1352: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1354: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1355: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1357: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1359: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1361: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1363: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1365: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1367: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: At top level:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1376: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1376: error: parameter 3 (‘smps’) has incomplete type
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function ‘rtl_send_smps_action’:
/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:1404: error: type of formal parameter 2 is incomplete
make[4]: *** [/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o] Error 1
make[3]: *** [_module_/home/drew/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/lib/modules/2.6.32-5-amd64/build'
make: *** [all] Error 2


So, anyone else have ideas? A huge thank you prior.

---

### Post by IrrationlArtist on 2012-02-12
EDIT: I'm an idiot. He details exactly what he copied below. 

"sudo cp /usr/include/linux/* /lib/modules/${KVER}/build/"

However, this doesn't help 'make && make install' to work any better.

---

### Post by praseodym on 2012-02-12
Can you try this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```
from the german forum (scroll down)

[http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#post-2844083](http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#post-2844083)

---

### Post by IrrationlArtist on 2012-02-12
Upon running make, I get an error related to permissions, and upon running 'sudo make', I get a similar error the the one before.

---

