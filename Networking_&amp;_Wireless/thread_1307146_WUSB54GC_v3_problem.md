---
title: "WUSB54GC v3 problem"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by tmun52 on 2009-10-30
Hey guys,

I'm trying to install the rt3070 drivers for my wusb54gc v3 wireless card, but I get this weird error when trying to run make.
I used the instructions found in this thread:

[http://ubuntuforums.org/showthread.php?t=1155941&page=1](http://ubuntuforums.org/showthread.php?t=1155941&page=1)

```
#uname -r
2.6.31-14-generic
```

```
root@taher-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0# make
make -C tools
make[1]: Entering directory `/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_wep.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/action.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_data.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/eeprom.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/dfs.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/spectrum.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rt_channel.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_profile.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_asic.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.c: In function ‘wext_notify_event_assoc’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.c:1401: warning: pointer targets in passing argument 5 of ‘RtmpOSWrielessEventSend’ differ in signedness
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:7025: note: expected ‘PUCHAR’ but argument is of type ‘char *’
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/auth.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:651: warning: the frame size of 1252 bytes is larger than 1024 bytes
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:1429: warning: the frame size of 1312 bytes is larger than 1024 bytes
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:929: warning: the frame size of 1260 bytes is larger than 1024 bytes
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sanity.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/wpa.o
  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
root@taher-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0# make install
make -C /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [install] Error 2
root@taher-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0# 
root@taher-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0# 


```

Thanks in advance.

---

### Post by andreh8 on 2009-10-31
Hello,

I'm trying to do a similar thing (building the driver in 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2) and I get a similar error message.
I just upgraded to Karmic Koala yesterday.

From a post I found somewhere else ([http://www.virtualbox.org/ticket/4264](http://www.virtualbox.org/ticket/4264)) it looks to me like the kernel used in Karmic Koala (I have 2.6.31-14-generic) seems to remove a compatibility API which the ralink driver seems to rely on... (I think Jaunty used kernel 2.6.28 so maybe the compatibility api was still present).

I would guess that ubuntu/debian had to patch the original sources for the RT2870STA
driver (in my case, version 1.4.0.0 comes built in a binary package).

best regards,

Andre

---

### Post by tmun52 on 2009-10-31
Ok, I found a patch on this thread:

[http://www.backports.ubuntuforums.org/showthread.php?t=1285828]("http://www.backports.ubuntuforums.org/showthread.php?t=1285828")

in order to fix the rt3070 compatibility problem. I'm going to try to see if it works on my adapter.

---

### Post by andreh8 on 2009-10-31
Hello, 

thanks for the link to the thread. I think this patch corresponds to the following link rpmfusion.org's CVS repository: [http://cvs.rpmfusion.org/viewvc/rpms/rt3070-kmod/F-11/rt3070-2.6.31-compile.patch?root=free&view=markup](http://cvs.rpmfusion.org/viewvc/rpms/rt3070-kmod/F-11/rt3070-2.6.31-compile.patch?root=free&view=markup) .

I see that there seems to be a similar patch for the rt2870: [http://cvs.rpmfusion.org/viewvc/rpms/rt2870-kmod/F-11/rt2870-2.6.31-compile.patch?root=free&view=log](http://cvs.rpmfusion.org/viewvc/rpms/rt2870-kmod/F-11/rt2870-2.6.31-compile.patch?root=free&view=log) .

I'll have a look at this later...

thanks for the link !

best regards,

Andre

---

### Post by tmun52 on 2009-10-31
So, I successfully was able to INSTALL the module, but it doesn't recognize my card.

```
root@taher-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


```
root@taher-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux# lsmod
Module                  Size  Used by
rt3070sta             507980  0 
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
arc4                    1660  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ecb                     2524  0 
snd_seq_dummy           2656  0 
led_class               4096  0 
input_polldev           3716  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
mac80211              181236  0 
iptable_filter          3100  0 
snd_rawmidi            22208  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   6688  0 
soundcore               7264  1 snd
x_tables               16544  1 ip_tables
parport_pc             31940  1 
dell_wmi                2564  0 
cfg80211               93052  1 mac80211
psmouse                56180  0 
lp                      8964  0 
crc_ccitt               1852  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
dcdbas                  7292  0 
shpchp                 32272  0 
serio_raw               5280  0 
parport                35340  3 ppdev,parport_pc,lp
radeon                636000  1 
ttm                    36212  1 radeon
e100                   32452  0 
mii                     5212  1 e100
floppy                 54916  0 
drm                   159584  3 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp

```


any ideas?

---

### Post by tmun52 on 2009-10-31
Extra Info (!)
```
taher@taher-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:46:8d:78  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe46:8d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40654653 (40.6 MB)  TX bytes:2923133 (2.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```

```
taher@taher-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by andreh8 on 2009-10-31
Hello,

I got mine compiling as well but it seems not to solve my problem (WPA support for the DWA-140 under karmic).

I noticed that modinfo seems to show a list of vendor/product ids of USB devices.
What do you get when you do:

```

  modinfo rt3070sta

```?

---

### Post by andreh8 on 2009-10-31
Searching for "1737:0077 linux" (the vid/pid of your wireless card), I found the following
but on launchpad:

"Linksys WUSB54GC v3 (ID 1737:0077) doesn't work"
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

Comment #21 seems to have a patch which seems to remove VID/PID  0x1737/0x0077 from
rt2800usb.c and adds it to rt2870.h ...

---

### Post by tmun52 on 2009-10-31
> **andreh8 said:**
> Hello,

I got mine compiling as well but it seems not to solve my problem (WPA support for the DWA-140 under karmic).

I noticed that modinfo seems to show a list of vendor/product ids of USB devices.
What do you get when you do:

```

  modinfo rt3070sta

```?

I get
```
taher@taher-desktop:~$   modinfo rt3070sta
filename:       /lib/modules/2.6.31-14-generic/updates/rt3070sta.ko
version:        2.1.1.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     BA3EF7EBC5E09C7D18AC654
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```

---

### Post by tmun52 on 2009-10-31
Also, I did
```
ifconfig ra0 up
```
and then
```
iwlist ra0 scan
```

And it scanned the nearby networks! (Woohoo!)

```
ra0       Scan completed :
          Cell 01 - Address: 00:18:01:E8:AA:26
                    Protocol:802.11b/g
                    ESSID:"TRAK1"
                    Mode:Managed
                    Channel:1
                    Quality:78/100  Signal level:-59 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
          Cell 02 - Address: 00:18:01:EC:62:C4
                    Protocol:802.11b/g
                    ESSID:"SAK82"
                    Mode:Managed
                    Channel:11
                    Quality:18/100  Signal level:-83 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s

```

Unfortunately, NetworkManager still doesn't recognize my adapter :-(.

I'll see what happens when I connect manually (I have a WEP connection fyi)

EDIT:

It also blinks :)

---

### Post by tmun52 on 2009-10-31
I got it! (Yes!)

Basically what I did was apply the patch found earlier and apply the steps found on post #98 of the page:

[http://ubuntuforums.org/showthread.php?t=1155941&highlight=wusb54gc+v3&page=10]("http://ubuntuforums.org/showthread.php?t=1155941&highlight=wusb54gc+v3&page=10")

---

