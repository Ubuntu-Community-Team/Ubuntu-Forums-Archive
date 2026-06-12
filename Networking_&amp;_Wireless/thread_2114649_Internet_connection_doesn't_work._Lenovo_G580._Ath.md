---
title: "Internet connection doesn't work. Lenovo G580. Atheros AR8162/AR9285."
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by Jot-z on 2013-02-10
Despite my attempts, I can't establish Internet connection on my laptop (Lenovo G580). Both, wireless and wired connections don't work. I have Ubuntu 12.10 installed. I have tried following:

```
joachim@ubuntu:~$ cd compat-wireless-2012-02-28-p/
joachim@ubuntu:~/compat-wireless-2012-02-28-p$ sudo scripts/driver-select alx
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
Backup exists: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
joachim@ubuntu:~/compat-wireless-2012-02-28-p$ sudo make
/home/joachim/compat-wireless-2012-02-28-p/config.mk:242: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make: Nothing to be done for `all'.
joachim@ubuntu:~/compat-wireless-2012-02-28-p$ sudo make install
/home/joachim/compat-wireless-2012-02-28-p/config.mk:242: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."

make -C /lib/modules/3.5.0-17-generic/build M=/home/joachim/compat-wireless-2012-02-28-p modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory. Stop.
make: *** [modules] Error 2
joachim@ubuntu:~/compat-wireless-2012-02-28-p$ sudo modprobe alx
FATAL: Module alx not found.
``````
joachim@ubuntu:~$ cd compat-wireless-3.6.8-1-snp/
joachim@ubuntu:~/compat-wireless-3.6.8-1-snp$ sudo scripts/driver-select alx
[sudo] password for joachim: 
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
Backup exists: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
joachim@ubuntu:~/compat-wireless-3.6.8-1-snp$ sudo make
make -C /lib/modules/3.5.0-17-generic/build M=/home/joachim/compat-wireless-3.6.8-1-snp modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory. Stop.
make: *** [modules] Error 2
joachim@ubuntu:~/compat-wireless-3.6.8-1-snp$ sudo make install
Updating Ubuntu's initramfs for 3.5.0-17-generic under /boot/ ...
Warning: No support for locale: en_GB.utf8
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
done

make -C /lib/modules/3.5.0-17-generic/build M=/home/joachim/compat-wireless-3.6.8-1-snp modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory. Stop.
make: *** [modules] Error 2
joachim@ubuntu:~/compat-wireless-3.6.8-1-snp$ sudo modprobe alx
FATAL: Module alx not found.
```Can somebody help me, please?

```
joachim@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation Device 1140 (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 08)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
``````
joachim@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23488 (23.4 KB)  TX bytes:23488 (23.4 KB)
``````
joachim@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
``````
joachim@ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_conexant    57842  1 
joydev                 17457  0 
hid_generic            12493  0 
coretemp               13400  0 
psmouse                95552  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
microcode              22803  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 131308  0 
serio_raw              13215  0 
mac80211              539908  1 ath9k
lpc_ich                17061  0 
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
nouveau               895609  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
i915                  520519  3 
ttm                    83595  1 nouveau
cfg80211              206566  3 ath9k,mac80211,ath
mxm_wmi                12979  1 nouveau
drm_kms_helper         46784  2 nouveau,i915
wmi                    19070  2 nouveau,mxm_wmi
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
drm                   275528  6 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13413  2 nouveau,i915
mei                    40690  0 
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
parport_pc             32688  0 
ppdev                  17073  0 
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
video                  19335  2 nouveau,i915
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
``````
joachim@ubuntu:~$ sudo lshw -C network
[sudo] password for joachim: 
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d353ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:43:ca:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d3400000-d340ffff
``````
joachim@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
``````
joachim@ubuntu:~$ uname -mr
3.5.0-17-generic x86_64
```EDIT:

I have downloaded these packages and installed them.

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb)

Ethernet works now but wireless is still broken.

```
joachim@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:e5:26:b7  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fee5:26b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107893 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:236989816 (236.9 MB)  TX bytes:8957308 (8.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:231547 (231.5 KB)  TX bytes:231547 (231.5 KB)
``````
joachim@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
``````
joachim@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 08
       serial: dc:0e:a1:e5:26:b7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:d3500000-d353ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:43:ca:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d3400000-d340ffff
``````
joachim@ubuntu:~$ uname -mr
3.5.0-23-generic x86_64
```

I managed to install wireless drivers successfully and it works now.

---

### Post by Shunmugavel on 2013-02-27
Hi,

Please post how did you manage to install wireless drivers? what are the drivers required?

I am in the same problem now and would like to get it fixed. Thanks.

---

### Post by chili555 on 2013-02-27
@Shunmugavel--

Do you have any internet access at all? Please post:```
lspci -nn | grep 0200
lsb_release -d
```Thanks.

---

### Post by Shunmugavel on 2013-03-01
Hi,

Please the output of the commands below,

```

lspci -nn | grep 0200


01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

lsb_release -d


Description:	Ubuntu 12.04.2 LTS




```

I have internet connection and i am unable to connect to it through Windows 7 installed in the same laptop.

---

### Post by chili555 on 2013-03-01
Your ethernet device is covered by the module alx. In the latest kernels of Ubuntu 12.10, 3.5.0-24 and beyond, it's included by default. 

If you do have internet access and don't wish to upgrade to 12.10 at this time, I'd install this, preceded by linux-headers-generic  and build-essential. Let me know if you need additional guidance.

[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2)

---

### Post by Shunmugavel on 2013-03-02
Hi Chili,

I have got the below errors during the installation of [COLOR=#000000] linux-headers-generic and build-essential.
[/COLOR]```
linux-headers-generic_3.2.0.38.46_amd64.deb - Installation


vel@vel-Satellite-C850:~/vel-home$ sudo dpkg -i linux-headers-generic_3.2.0.38.46_amd64.deb
[sudo] password for vel: 
(Reading database ... 141393 files and directories currently installed.)
Preparing to replace linux-headers-generic 3.2.0.38.46 (using linux-headers-generic_3.2.0.38.46_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-38-generic; however:
  Package linux-headers-3.2.0-38-generic is not installed.
dpkg: error processing linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic
vel@vel-Satellite-C850:~/vel-home$ 



```
```

build-essential_11.4build1_amd64.deb - Installation


vel@vel-Satellite-C850:~/vel-home$ sudo dpkg -i build-essential_11.4build1_amd64.deb
(Reading database ... 141393 files and directories currently installed.)
Preparing to replace build-essential 11.4build1 (using build-essential_11.4build1_amd64.deb) ...
Unpacking replacement build-essential ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.3.1); however:
  Package g++ is not installed.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential

```[COLOR=#000000]

Please advice what needs to be done to resolve this error and successfully installed.[/COLOR]

---

### Post by Shunmugavel on 2013-03-02
I have installed linux-headers-3.5.0-23-generic_3.5.0-23.35~precise1_amd64, but however i am unable to install any build essentials version at all(build-essential_11.5ubuntu2.1_amd64) it keeps on giving dependencies errors with g++, dpkg-dev packages. So i have completed lost my hope in installing these drivers and for just to enable internet in ubuntu. 

Not sure how to proceed??

---

### Post by chili555 on 2013-03-02
> linux-headers-generic depends on linux-headers-3.2.0-38-generic; however:
  Package linux-headers-3.2.0-38-generic is not installed.Go get it: [http://packages.ubuntu.com/precise/linux-headers-3.2.0-38-generic](http://packages.ubuntu.com/precise/linux-headers-3.2.0-38-generic) 

Do the same for other missing dependencies. I know, without an internet connection, it's a tough job, but you can do it with patience and perseverance. I have helped others and I know you can do it, too.

---

### Post by Shunmugavel on 2013-03-02
Hi Chili,

Thanks again for helping and bringing confidence to me. I have tried to resolve all the dependencies i have. But blocked by the below one. Please help to resolve this,

I need to install libc6 package, it has dependencies with package libgcc1(so this needs to be configured first). To install libgcc1, you have to configure multiarch-support. But if i tried to install multiarch-support then it checks for libc6(which is yet to be configured) and fails. Please see the below error logs,

Installing libc6
```

vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install/libc6$ sudo dpkg -i libc6_2.15-0ubuntu10.3_amd64.deb 
(Reading database ... 148538 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.3 (using libc6_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not configured yet.
dpkg: error processing libc6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6

```

Installing multiarch-support
```

vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install/libc6/libgcc1/multi rach$ sudo dpkg -i multiarch-support_2.15-0ubuntu10.2_amd64.deb 
(Reading database ... 148538 files and directories currently installed.)
Preparing to replace multiarch-support 2.15-0ubuntu10.2 (using multiarch-support_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement multiarch-support ...
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 multiarch-support

```

What should i do to fix this?

---

### Post by chili555 on 2013-03-02
You can try to install them all at the same time:```
sudo dpkg -i libc6*.deb libgcc1*.deb multiarch-support*.deb
```The wildcard * relieves us of the need to type all the numbers, dashes, underscores, etc.

I think you are getting close!!

---

### Post by Shunmugavel on 2013-03-02
Chili,

Here you go, i have the files under same path and issued the command you have provided. Still it looks like a deadlock

```

sudo dpkg -i libc6*.deb libgcc1*.deb multiarch-support*.deb


vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install$ ll
total 1228
drwx------ 1 vel vel    4096 Mar  3 03:06 ./
drwx------ 1 vel vel   12288 Mar  3 02:40 ../
drwx------ 1 vel vel       0 Mar  3 02:05 gcc-4.6-base/
drwx------ 1 vel vel       0 Mar  3 01:56 header/
drwx------ 1 vel vel    4096 Mar  3 02:03 libc6/
-rw------- 2 vel vel 1180750 Mar  3 02:26 libc-bin_2.15-0ubuntu10.2_amd64.deb
-rw------- 1 vel vel   42608 Mar  3 03:06 libgcc1_4.6.3-1ubuntu5_amd64.deb
-rw------- 1 vel vel    4480 Mar  3 03:06 multiarch-support_2.15-0ubuntu10.2_amd64.deb
vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install$ 
vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install$ 
vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install$ sudo dpkg -i libc6*.deb libgcc1*.deb multiarch-support*.deb
[sudo] password for vel: 
dpkg: error processing libc6*.deb (--install):
 cannot access archive: No such file or directory
(Reading database ... 162418 files and directories currently installed.)
Preparing to replace libgcc1 1:4.6.3-1ubuntu5 (using libgcc1_4.6.3-1ubuntu5_amd64.deb) ...
Unpacking replacement libgcc1 ...
Preparing to replace multiarch-support 2.15-0ubuntu10.2 (using multiarch-support_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement multiarch-support ...
dpkg: dependency problems prevent configuration of libgcc1:
 libgcc1 depends on libc6 (>= 2.14); however:
  Package libc6 is not configured yet.
dpkg: error processing libgcc1 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6*.deb
 libgcc1
 multiarch-support
vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install$ 

```

---

### Post by chili555 on 2013-03-02
> drwx------ 1 vel vel    4096 Mar  3 03:06 ./
drwx------ 1 vel vel   12288 Mar  3 02:40 ../
drwx------ 1 vel vel       0 Mar  3 02:05 gcc-4.6-base/
drwx------ 1 vel vel       0 Mar  3 01:56 header/
drwx------ 1 vel vel    4096 Mar  3 02:03 [COLOR="#FF0000"]libc6/[/COLOR]
-rw------- 2 vel vel 1180750 Mar  3 02:26 libc-bin_2.15-0ubuntu10.2_amd64.deb
-rw------- 1 vel vel   42608 Mar  3 03:06 libgcc1_4.6.3-1ubuntu5_amd64.deb
-rw------- 1 vel vel    4480 Mar  3 03:06 multiarch-support_2.15-0ubuntu10.2_amd64.debYou don't have the *.deb* file for libc6 in this directory. It looks like it's in it's own directory. Drag and drop it or copy and paste it in the same directory with the others and try again.

---

### Post by Shunmugavel on 2013-03-03
You're correct. I am almost close to finish up the installation, still having issues with build essential anyhow i will resolve it. 

One quick question, is there a way i can download all these dependent packs and have them installed? i know, i can do it with internet connection with ubuntu. But just wan to if it is possible without ubuntu?

---

### Post by Shunmugavel on 2013-03-03
Now stuck up with the below errors,

```

vel@vel-Satellite-C850:~/vel-home/compat-wireless-3.6.6-1-snpc$ sudo  make 
[sudo] password for vel: 
make -C /lib/modules/3.5.0-23-generic/build M=/home/vel/vel-home/compat-wireless-3.6.6-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
/usr/src/linux-headers-3.5.0-23-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
  CC [M]  /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/main.o
gcc: error trying to exec 'cc1': execvp: No such file or directory
make[3]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/main.o] Error 1
make[2]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat] Error 2
make[1]: *** [_module_/home/vel/vel-home/compat-wireless-3.6.6-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [modules] Error 2
vel@vel-Satellite-C850:~/vel-home/compat-wireless-3.6.6-1-snpc$ 




vel@vel-Satellite-C850:~/vel-home/compat-wireless-3.6.6-1-snpc$ sudo make install
Updating Ubuntu's initramfs for 3.5.0-23-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


make -C /lib/modules/3.5.0-23-generic/build M=/home/vel/vel-home/compat-wireless-3.6.6-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
/usr/src/linux-headers-3.5.0-23-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
  CC [M]  /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/main.o
gcc: error trying to exec 'cc1': execvp: No such file or directory
make[3]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/main.o] Error 1
make[2]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat] Error 2
make[1]: *** [_module_/home/vel/vel-home/compat-wireless-3.6.6-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [modules] Error 2




vel@vel-Satellite-C850:~/vel-home/compat-wireless-3.6.6-1-snpc$ sudo modprobe alx
FATAL: Module alx not found.





```

Help me please. Its already very late with this issues.

---

### Post by chili555 on 2013-03-03
> Makefile:81: stack protector enabled but no compiler supportSome part of build-essential is missing.I suggest you retrace your steps and check the install status of each of the dependencies; for example:```
sudo dpkg -s g++
```Ideally, for each, you'll see:> chili@Think410:~$ sudo dpkg -s g++
[sudo] password for chili: 
Package: g++
Status: [COLOR="#FF0000"]install ok installed[/COLOR]
Priority: optional
Section: devel
When you see this:> make[3]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/main.o] Error 1
make[2]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat] Error 2
make[1]: *** [_module_/home/vel/vel-home/compat-wireless-3.6.6-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [modules] Error 2...please stop and fix the error as all successive steps will also fail. In other words, that egg is rotten, we're not going to make and eat the omelet. Sure enough:> FATAL: Module alx not found.> is there a way i can download all these dependent packs and have them installed?I wish it were that easy. I know of no such method.

---

### Post by Shunmugavel on 2013-03-03
Thanks chili. I have got the issue but not the solution. gcc-4.6 is not installed.

```

vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install/g++/gcc/binutils/libstdc++6$ dpkg -s gcc-4.6
Package: gcc-4.6
Status: install ok unpacked
Priority: optional
Section: devel
Installed-Size: 15840
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 4.6.1-9ubuntu3
Config-Version: 4.6.3-1ubuntu5
Provides: c-compiler
Depends: gcc-4.6-base (= 4.6.1-9ubuntu3), cpp-4.6 (= 4.6.1-9ubuntu3), binutils (>= 2.21.51~), libgcc1 (>= 1:4.6.1-9ubuntu3), libgomp1 (>= 4.6.1-9ubuntu3), libquadmath0 (>= 4.6.1-9ubuntu3), libc6 (>= 2.11), libgmp10, libmpc2, libmpfr4, zlib1g (>= 1:1.1.4)
Recommends: libc6-dev (>= 2.13-0ubuntu6)
Suggests: gcc-4.6-multilib, libmudflap0-4.6-dev (>= 4.6.1-9ubuntu3), gcc-4.6-doc (>= 4.6.1-8), gcc-4.6-locales (>= 4.6.1-8), libgcc1-dbg, libgomp1-dbg, libquadmath0-dbg, libmudflap0-dbg, binutils-gold (>= 2.21.51~)
Description: GNU C compiler
 This is the GNU C compiler, a fairly portable optimizing compiler for C.
Homepage: http://gcc.gnu.org/
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>


vel@vel-Satellite-C850:/media/E47478CF7478A5C8/install/g++/gcc$ sudo dpkg -i gcc-4.6_4.6.1-9ubuntu3_amd64.deb 
(Reading database ... 162923 files and directories currently installed.)
Preparing to replace gcc-4.6 4.6.1-9ubuntu3 (using gcc-4.6_4.6.1-9ubuntu3_amd64.deb) ...
Unpacking replacement gcc-4.6 ...
dpkg: dependency problems prevent configuration of gcc-4.6:
 gcc-4.6 depends on gcc-4.6-base (= 4.6.1-9ubuntu3); however:
  Version of gcc-4.6-base on system is 4.6.3-1ubuntu5.
 gcc-4.6 depends on cpp-4.6 (= 4.6.1-9ubuntu3); however:
  Version of cpp-4.6 on system is 4.6.3-1ubuntu5.
dpkg: error processing gcc-4.6 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 gcc-4.6



```

Any suggestions??

---

### Post by chili555 on 2013-03-03
It looks like the version of gcc-4.6 you are trying to install in an older version that all the dependencies you have on your system now.Try this one instead: [http://packages.ubuntu.com/precise/gcc-4.6](http://packages.ubuntu.com/precise/gcc-4.6)

> Package: gcc-4.6 (**4.6.3-1ubuntu5**) Notice the other conflicted packages are 4.6.3-1 also.

---

### Post by Shunmugavel on 2013-03-03
Chili,

Thanks. I have installed gcc-4.6 and other dependencies were also resolved. When i was running the compat driver commands i had some permission issues, so i logged as root and configured it and does a reboot as well. still no luck, when does is detect my wireless connection

```

vel@vel-Satellite-C850:~/vel-home/compat-wireless-3.6.6-1-snpc$ make
make -C /lib/modules/3.5.0-23-generic/build M=/home/vel/vel-home/compat-wireless-3.6.6-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/main.o
  CC [M]  /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/compat-3.7.o
/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/compat-3.7.c: In function â&#8364;&#732;pcie_flags_regâ&#8364;&#8482;:
/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/compat-3.7.c:37:2: warning: passing argument 1 of â&#8364;&#732;pci_find_capabilityâ&#8364;&#8482; discards â&#8364;&#732;constâ&#8364;&#8482; qualifier from pointer target type [enabled by default]
include/linux/pci.h:714:5: note: expected â&#8364;&#732;struct pci_dev *â&#8364;&#8482; but argument is of type â&#8364;&#732;const struct pci_dev *â&#8364;&#8482;
  LD [M]  /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/compat.o
/bin/sh: 1: cannot create /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/.tmp_versions/compat.mod: Permission denied
make[3]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/compat.o] Error 2
make[2]: *** [/home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat] Error 2
make[1]: *** [_module_/home/vel/vel-home/compat-wireless-3.6.6-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [modules] Error 2



```

```

Updating Ubuntu's initramfs for 3.5.0-23-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


make -C /lib/modules/3.5.0-23-generic/build M=/home/vel/vel-home/compat-wireless-3.6.6-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make -C /lib/modules/3.5.0-23-generic/build M=/home/vel/vel-home/compat-wireless-3.6.6-1-snpc "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  INSTALL /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/compat/compat.ko
  INSTALL /home/vel/vel-home/compat-wireless-3.6.6-1-snpc/drivers/net/ethernet/atheros/alx/alx.ko
  DEPMOD  3.5.0-23-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
Updating Ubuntu's initramfs for 3.5.0-23-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
depmod will prefer updates/ over kernel/ -- OK!


Now run:


sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules


Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.



```

Also i have a error message in top right corner of the home screen as below,


```

The error message was BrokenCount>0

```


Please suggest.

---

### Post by Shunmugavel on 2013-03-03
Chili,

Finally our hard work has paid off, i am connected to internet through ubuntu using wired network. Still wireless isn't working. But this is fine for now, i can proceed with my work. Please let me know if i can install wireless driver now using apt-get. One more issue, brightness control is not working now (which was working earlier).

Thanks a lot for your help.

---

### Post by chili555 on 2013-03-03
I am not sure if we/you installed the running kernel headers or -generic. I'd clean that up first:```
udo apt-get install linux-headers-generic
```> Please let me know if i can install wireless driver now using apt-get.Probably so. Let's identify the device first:```
lspci -nn | grep 0280
```Update Manager will probably want to install a few dozen updates. Don't allow it until linux-headers is taken care of. One of the updates will probably be linux-image. You compiled alx against your currently running kernel only; e.g. 3.5.0-23-generic. The latest, as of today, is -25. The wonderful news is that *alx* is included by default!```
/lib/modules/3.5.0-25-generic/kernel/ubuntu/alx/*alx.ko*
```

I'm very glad it's working.

---

### Post by Shunmugavel on 2013-03-04
Chili,

Please find the outputs below,

```

vel@vel-Satellite-C850:~$ sudo apt-get install linux-headers-generic
[sudo] password for vel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
vel@vel-Satellite-C850:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
vel@vel-Satellite-C850:~$ 

```

My screen brightness is very high, i am unable to change it using FN keys. Please help.

---

### Post by chili555 on 2013-03-04
For your wireless device, download this file to your desktop: [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz)

Right-click it and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
sudo su
make
make install
modprobe rt8723e
exit
```On my 12.10 system, it compiles with a couple of harmless looking warnings. I can't test further because I don't have the device. Post back if you get stuck.

I don't know much about your display issue; you might ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by Shunmugavel on 2013-03-04
Chili,

I have downloaded the package and getting the below error while installing it.

```

root@vel-Satellite-C850:~/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.5.0-25-generic/build M=/home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/vel/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [all] Error 2
root@vel-Satellite-C850:~/vel-home/wireless/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# 


```

BTW, brightness is resolved now after running a complete update.

---

### Post by chili555 on 2013-03-04
Interesting. The original file I linked makes on 3.5.0-24 but not -25. Please try this instead; it makes, albeit with a few more warnings: [http://www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](http://www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

---

### Post by Shunmugavel on 2013-03-05
Chili,

I have tried the above mentioned driver. I have successfully executed the steps mentioned, but getting the below error in the last command.

```

root@vel-Satellite-C850:/media/E47478CF7478A5C8/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# modprobe rt8723e
FATAL: Module rt8723e not found.
root@vel-Satellite-C850:/media/E47478CF7478A5C8/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# 

```

Please help. Also please let me know how do you find the exact driver for WLAN??

---

### Post by chili555 on 2013-03-05
> root@vel-Satellite-C850:[COLOR="#FF0000"]/media/E47478CF7478A5C8[/COLOR]/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# modprobe rt8723e
FATAL: Module rt8723e not found.Then there was an error further up in the compile process. Are you trying to make and install this from a USB key or CD? I believe you need to drag and drop this to your desktop. Please try again.> Also please let me know how do you find the exact driver for WLAN?? I don't exactly understand. Do you mean how do I find out what to install from the details you've given me?

---

### Post by Shunmugavel on 2013-03-06
> **chili555 said:**
> Then there was an error further up in the compile process. Are you trying to make and install this from a USB key or CD? I believe you need to drag and drop this to your desktop. Please try again.

I did copy it to the local hard disk and compiled it from there. I will give it a try and post the results.

> **chili555 said:**
> I don't exactly understand. Do you mean how do I find out what to install from the details you've given me?

Yes, I mean how do you find out what driver to install from the details i have given.

---

### Post by chili555 on 2013-03-06
> Yes, I mean how do you find out what driver to install from the details i have given. You're asking me to reveal my secrets? Now everyone is going to see how easy it is. If you insist, here goes.

First, the device ID is everything. Find out with:```
lspci -nn
```Or, if it's a USB device:```
lsusb
```Here is an example from my machine:> 03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [[COLOR="#FF0000"]8086:4239[/COLOR]] (rev 35)Next, I search Google for the ID numbers. I see this,for example: [http://wiki.debian.org/iwlwifi](http://wiki.debian.org/iwlwifi)> PCI: 8086:4239 Intel Corporation Centrino Advanced-N 6200This same process, for any networking device, wireless or ethernet, works the same.

Some devices are covered by a driver in a later Ubuntu version, but not an earlier. We can tell if a device is covered with *modinfo*:```
chili@Think410:~$ modinfo iwlwifi | grep 4239
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]4239[/COLOR]sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
```So we can see that this device is covered by iwlwifi in my Ubuntu version, 12.10. Of course, a few years of experience means I recognize many devices immediately without Googling.

In order to test whether the device is covered in earlier versions, I use live CDs for 12.04 and 10.04, etc. I can start up the live CD, compile a driver, etc. and give informed replies in a wide variety of cases.

My favorite cases are the ones where I Google and the first hit includes 'chili555' and 'Solved!'

I look forward to your compile results.

---

### Post by Shunmugavel on 2013-03-06
> **chili555 said:**
> You're asking me to reveal my secrets? Now everyone is going to see how easy it is. If you insist, here goes.

First, the device ID is everything. Find out with:```
lspci -nn
```Or, if it's a USB device:```
lsusb
```Here is an example from my machine:Next, I search Google for the ID numbers. I see this,for example: [http://wiki.debian.org/iwlwifi](http://wiki.debian.org/iwlwifi)This same process, for any networking device, wireless or ethernet, works the same.

Some devices are covered by a driver in a later Ubuntu version, but not an earlier. We can tell if a device is covered with *modinfo*:```
chili@Think410:~$ modinfo iwlwifi | grep 4239
alias:          pci:v0000[COLOR=#FF0000]8086[/COLOR]d0000[COLOR=#FF0000]4239[/COLOR]sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
```So we can see that this device is covered by iwlwifi in my Ubuntu version, 12.10. Of course, a few years of experience means I recognize many devices immediately without Googling.

In order to test whether the device is covered in earlier versions, I use live CDs for 12.04 and 10.04, etc. I can start up the live CD, compile a driver, etc. and give informed replies in a wide variety of cases.


Thanks for revealing your secrets Chili. It was very well explained and organized. As a linux beginner, i would say it is still pain find the drivers(especially for linux) and have them installed successfully. I will continue to explore my knowledge and try to gain to more knowledge in linux (somehow i love linux).

> 
My favorite cases are the ones where I Google and the first hit includes 'chili555' and 'Solved!'


That's awesome to hear 
> 
I look forward to your compile results.


Hurray i just boot my laptop, it figured out my wireless connection and gave me an alert. I was surprised and happy. Now i am sending this message through my wifi connection. Thanks a lot for all your help. However i have USB modem, i hope i will find a driver for that using your above method and have it configured. If i am unable to do so, i will post here and disturb you again!!

---

### Post by chili555 on 2013-03-06
Glad it's working! Please feel free to post back if I can help you at any time.

---

