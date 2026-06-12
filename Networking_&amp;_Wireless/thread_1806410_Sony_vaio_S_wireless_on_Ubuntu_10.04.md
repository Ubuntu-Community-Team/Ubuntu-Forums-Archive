---
title: "Sony vaio S wireless on Ubuntu 10.04"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by coldman239 on 2011-07-17
Hi!

I installed Ubuntu 10.04 on my new Sony Vaio serie S but it does not recognize my wireless card(i think). The button is on, but the light does not turn on,  and it does not detect the wireless card.
The wireless card, an Intel Centrino Advanced -n 6205, does work in ubuntu and when i run the command: lshw -C network, it appears UNCLAIMED, that i think it means the drivers are not in the Ubuntu libraries.

What can I do to make it work? I've been struggling but i cannnot make it work. Please, could you help me?

---

### Post by wildmanne39 on 2011-07-17
> **coldman239 said:**
> Hi!

I installed Ubuntu 10.04 on my new Sony Vaio serie S but it does not recognize my wireless card(i think). The button is on, but the light does not turn on,  and it does not detect the wireless card.
The wireless card, an Intel Centrino Advanced -n 6205, does work in ubuntu and when i run the command: lshw -C network, it appears UNCLAIMED, that i think it means the drivers are not in the Ubuntu libraries.

What can I do to make it work? I've been struggling but i cannnot make it work. Please, could you help me?
Hi, run these commands in a terminal one at a time
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by coldman239 on 2011-07-18
sudo lshw -C network

 *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c7400000-c7401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: f0:bf:97:5f:7e:24
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:3000(size=256) memory:c3404000-c3404fff(prefetchable) memory:c3400000-c3403fff(prefetchable)


#
lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4b] (rev 04)
00:1f.2 RAID bus controller [0104]: Intel Corporation Mobile 82801 SATA RAID Controller [8086:282a] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6741]
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0082] (rev 34)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
04:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



rfkill list All

Bogus list argument 'All'

lsmod

Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  0 
tpm_infineon            9217  0 
ndiswrapper           244800  0 
snd_hda_intel          25805  4 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                 9912  0 
tpm                    16304  2 tpm_infineon,tpm_tis
sony_laptop            33788  0 
tpm_bios                6402  1 tpm
snd                    71283  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  20623  0 
output                  2503  1 video
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
soundcore               8052  1 snd
xhci                   42519  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
psmouse                64576  0 
serio_raw               4918  0 
lp                      9336  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
parport                37160  2 ppdev,lp
usb_storage            50377  1 
ahci                   38030  4 
r8169                  39714  0 
mii                     5237  1 r8169

---

### Post by wildmanne39 on 2011-07-18
Hi, ok I need to get a little more information please run these two commands in a terminal
```
lspci -nn | grep 0280
```
```
dmesg | grep ipw
```
and post the results here.

---

### Post by coldman239 on 2011-07-18
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0082] (rev 34)


dmesg | grep ipw

No output here! What does it mean?

---

### Post by wildmanne39 on 2011-07-18
> **coldman239 said:**
> lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0082] (rev 34)


dmesg | grep ipw

No output here! What does it mean?Hi, it means your wireless card driver is not installed, I am looking to see if I can find one for your card, you can also make sure you are plugged into the internet with a wire and check in additional drivers and see if there is a driver for your card in there.

---

### Post by wildmanne39 on 2011-07-18
Hi, the information is not showing the complete chip name for your card try this and post the results it might show what I need.
```
sudo lspci -nn
```

---

### Post by coldman239 on 2011-07-18
This is what i get:
sudo lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4b] (rev 04)
00:1f.2 RAID bus controller [0104]: Intel Corporation Mobile 82801 SATA RAID Controller [8086:282a] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6741]
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0082] (rev 34)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
04:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

---

### Post by wildmanne39 on 2011-07-18
Hi, if this is a usb card run this command
```
lsusb
```

---

### Post by nm_geo on 2011-07-18
This is one of those really new boxes?  right?
With Intel wireless that is not in the Lucid Kernel 10.04 automagizcally.

Do a 

```
uname -a
```

in terminal please

---

### Post by chili555 on 2011-07-18
Here's a hint, guys:```
$ modinfo iwlagn | grep 0082
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]0082[/COLOR]sv*sd00001326bc*sc*i*

```> 02:00.0 Network controller [0280]: Intel Corporation Device [8086:0082] (rev 34)If iwlagn won't grab it and drive it, I'd check dmesg:```
sudo modprobe iwlagn
dmesg | grep iwl
```It may need firmware.

---

### Post by nm_geo on 2011-07-18
Yeah I think his kernel don't have that yet ..
SOOOO compat-wireless trick again...
He is running Lucid so he said..

**Intel® Centrino® Advanced-N 6205 (2.6.35)**

---

### Post by chili555 on 2011-07-18
> Yeah I think his kernel don't have that yet ..It has iwlagn but not for that pci.id. compat is your leetle fren.

---

### Post by wildmanne39 on 2011-07-18
Hi, run these two commands one at a time as chilli555 posted.
```
sudo modprobe iwlagn
dmesg | grep iwl
```
and post the results back here. Hopefully the first command will get the wireless working if not we will continue on.

---

### Post by coldman239 on 2011-07-19
lsusb


Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ca:18c0 Ricoh Co., Ltd 
Bus 001 Device 003: ID 08ff:168f AuthenTec, Inc. 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by coldman239 on 2011-07-19
uname -a
Linux alex 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux


sudo modprobe iwlagn
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release


dmesg | grep iwl
[  325.945643] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[  325.945654] iwlagn: Copyright(c) 2003-2009 Intel Corporation

---

### Post by coldman239 on 2011-07-19
But nothing's working yet :(

---

### Post by wildmanne39 on 2011-07-19
Hi, you need to download the compat-wirless drivers from here.[http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Thin install linux-headers and build-essential from synaptic if you have a wired connection if not you can do it from the livecd.

Extract the package in a terminal then 
```
cd Desktop/compat
```

You can press the tab key to fill in the rest:I believe it will give you the name of the driver.
```
./scripts/driver-select your driver name
make
sudo make install
sudo modprobe your diver name
```

---

### Post by coldman239 on 2011-07-19
How do i know the name of the wireless?

I'm in the directory i made but there are many files...What do I have to do with synaptics? I didn't understand this step

---

### Post by chili555 on 2011-07-19
> **coldman239 said:**
> How do i know the name of the wireless?

I'm in the directory i made but there are many files...What do I have to do with synaptics? I didn't understand this stepOpen Synaptic. Use the search function and look for *build-essential*. If it is not already installed, indicated by a little filled in box, click the empty box and select for installation. Do the same with *linux-headers-generic*. Click the Apply button and let these packages get downloaded and installed on your system.

Next, go here: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Download the package compat-wireless-2.6.tar.bz2. Download or drag and drop it to your desktop. Right-click it and select Extract Here.

Now open a terminal and do:```
cd Desktop/compat
```Press Tab and the remainder will fill in magically!```
./scripts/driver-select iwlagn
make 
sudo make install
```Reboot and tell us if your wireless is working.

Post back if there is anything you don't understand or need more help. The doctors are in.

---

### Post by coldman239 on 2011-07-19
I did it and still is not working...

Which linux-headers-generic should i have? I already had one of them installed, but i do not know if they are the right ones.


Appart, when i do the make and the sudo make install some error appears:


Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
alex@alex:~/Desktop/compat-wireless-2011-07-18$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.32-32-generic/build M=/home/alex/Desktop/compat-wireless-2011-07-18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
  LD      /home/alex/Desktop/compat-wireless-2011-07-18/compat/built-in.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/main.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat-2.6.33.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat-2.6.35.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat-2.6.36.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/kfifo.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat-2.6.37.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat-2.6.38.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat-2.6.39.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/kstrtox.o
  LD [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/compat/compat_firmware_class.o
  LD      /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/built-in.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn.o
/home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn.c:30:1: warning: "pr_fmt" redefined
In file included from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/alex/Desktop/compat-wireless-2011-07-18/include/linux/compat-2.6.29.h:5,
                 from /home/alex/Desktop/compat-wireless-2011-07-18/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/kernel.h:366:1: warning: this is the location of the previous definition
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-ucode.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-tx.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-lib.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-calib.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-io.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-tt.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-sta.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-eeprom.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-core.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-hcmd.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-rx.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-tx.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-sta.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-scan.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-led.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-rxon.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-hcmd.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-agn-ict.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-6000.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-1000.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-2000.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-pci.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwl-trans.o
  LD [M]  /home/alex/Desktop/compat-wireless-2011-07-18/drivers/net/wireless/iwlwifi/iwlagn.o
  LD      /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/built-in.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/main.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/status.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/sta_info.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/wep.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/wpa.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/scan.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/offchannel.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/ht.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/agg-tx.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/agg-rx.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/ibss.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/mlme.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/work.o
  CC [M]  /home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/iface.o
/home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/iface.c: In function ‘ieee80211_if_add’:
/home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/iface.c:1147: error: implicit declaration of function ‘alloc_netdev_mqs’
/home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/iface.c:1148: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211/iface.o] Error 1
make[2]: *** [/home/alex/Desktop/compat-wireless-2011-07-18/net/mac80211] Error 2
make[1]: *** [_module_/home/alex/Desktop/compat-wireless-2011-07-18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
make: *** [modules] Error 2

---

### Post by chili555 on 2011-07-19
That's a new one on me! I am not sure if it's an error in the source code or a reflection of your older kernel version: 2.6.32-32-generic. Move the file you downloaded to the Trash. Next, go here:  [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

Scroll down towards the end and download an earlier version, say 7-15-2011.tar.bz2 and try again. I compiled 7-15 on my Natty system running kernel version 2.6.38-10 just now. I had a couple of warnings but no errors.

---

### Post by coldman239 on 2011-07-19
Now there was no error. Everything went smoothly...he asked to do: sudo modprobe my-driver-name, but i do not know the name of the driver...I rebooted, but still not working...

What do i do next?

---

### Post by chili555 on 2011-07-19
The module name is iwlagn.```
sudo modprobe iwlagn
```Rarely, the module does not get installed in the right place, so let's check:```
sudo updatedb
locate iwlagn.ko
modinfo iwlagn
```Thanks.

---

### Post by coldman239 on 2011-07-19
alex@alex:~$ sudo updatedb
alex@alex:~$ locate iwlagn.ko
/home/alex/Desktop/compat-wireless-2011-07-15/drivers/net/wireless/iwlwifi/.iwlagn.ko.cmd
/home/alex/Desktop/compat-wireless-2011-07-15/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.32-32-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alex@alex:~$ modinfo iwlagn
filename:       /lib/modules/2.6.32-32-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-IWL135_UCODE_API_MAX.ucode
firmware:       iwlwifi-105-5.ucode
firmware:       iwlwifi-2030-5.ucode
firmware:       iwlwifi-2000-5.ucode
srcversion:     5E7A849211C4F5C784F4078
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        led-class,mac80211,cfg80211,compat_firmware_class,compat
vermagic:       2.6.32-32-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer (default: 0 [enabled]) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

---

### Post by coldman239 on 2011-07-19
It's working!! Thank you so much! This is a great community :)

The only thing that is left is that i need to execute 
sudo modprobe iwlagn

Each time I restart the computer, How can I fix this bug? Does it have something to do with the following warning?

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by chili555 on 2011-07-19
> $ modinfo iwlagn
filename: /lib/modules/2.6.32-32-generic/[COLOR="Red"]updates/drivers/net[/COLOR]/wireless/iwlwifi/iwlagn.ko
license: GPL
author: Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version: in-tree:
description: Intel(R) Wireless WiFi Link AGN driver for Linux
firmware: iwlwifi-5150-2.ucode
firmware: iwlwifi-5000-5.ucode
firmware: iwlwifi-6000g2b-5.ucode
firmware: iwlwifi-6000g2a-5.ucode
firmware: iwlwifi-6050-5.ucode
firmware: iwlwifi-6000-4.ucode
firmware: iwlwifi-100-5.ucode
firmware: iwlwifi-1000-5.ucode
firmware: iwlwifi-135-IWL135_UCODE_API_MAX.ucode
firmware: iwlwifi-105-5.ucode
firmware: iwlwifi-2030-5.ucode
firmware: iwlwifi-2000-5.ucode
srcversion: 5E7A849211C4F5C784F4078
<snip>
alias: pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]0082[/COLOR]sv*sd00001326bc*sc*i*
<snip>
Great news! It installed in the right place and drives your device. The fact that it doesn't start and run suggests another issue. Let's check for kernel messages:```
sudo modprobe iwlagn
dmesg | grep iwl
```We're close!

---

### Post by coldman239 on 2011-07-19
[   48.202032] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   48.202035] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   48.202159] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   48.202213] iwlagn 0000:02:00.0: setting latency timer to 64
[   48.202686] iwlagn 0000:02:00.0: irq 31 for MSI/MSI-X
[   48.202798] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   48.219894] iwlagn 0000:02:00.0: device EEPROM VER=0x715, CALIB=0x6
[   48.219896] iwlagn 0000:02:00.0: Device SKU: 0X1f0
[   48.219897] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   48.219906] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   48.274384] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.2 build 35905
[   48.307035] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   48.317118] iwlagn 0000:02:00.0: Radio type=0x1-0x2-0x0
[   48.624965] iwlagn 0000:02:00.0: Radio type=0x1-0x2-0x0

---

### Post by chili555 on 2011-07-19
> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Arrrgh!! And I thought I had a clean getaway...oh, well.

May I assume you installed ndiswrapper trying to get the wireless going? Let's kick it out of town!```
sudo apt-get remove --purge ndis*  [COLOR="Red"]**See note below**[/COLOR]
sudo rm /etc/modprobe.d/ndiswrapper
sudo gedit /etc/modprobe.d/blacklist.conf
```Look to see if iwlagn is blacklisted. If so remove it. In any event, proofread carefully, save and close gedit. Now do:```
sudo su
echo iwlagn >> /etc/modules
exit
```Now does it work as expected? If so, use thread tools at the top and Mark Solved.

Your dmesg looks perfect.

EDIT:  The correct command should have been:```
sudo apt-get remove --purge ndiswrapper*
```

---

### Post by coldman23 on 2011-07-19
We were close but everything's messed up now...It seems the first command I used, deleted much more than my ndiswrapper libraries. When i did it many programs were deleted: evolution, firefox,... the buttons were not not working. I restarted and then Ubuntu cannot go into the graphical mode :( And I don't know why but not even my account on Ubuntu forums did not work either

This is a neverending story, What do you recommend me? Re-install everything?

---

### Post by chili555 on 2011-07-19
I am very sorry. I would not have suspected that. Do you have an ethernet connection so you can download packages? If so, get to the command line and do:```
ifconfig eth0 up
dhclient eth0
apt-get-install ubuntu-desktop
```Let it install, reboot and let's go from there.

---

### Post by coldman23 on 2011-07-19
It seems the ethernet does not work either now, because i follow the steps, but when it restarts it's go back to the terminal mode and not to the Desktop mode.

---

### Post by chili555 on 2011-07-19
Let's check if the ethernet works:```
ifconfig eth0 up
dhclient eth0
```Did it get an IP address or time out? If it got an IP address, do:```
ping -c3 www.google.com
```If you get ping returns, it's working. Now try:```
apt-get install xserver-xorg-video-all* gnome-panel* gdm
```I am hoping that one of these will get everything back by installing dependencies.

Then reboot.

---

### Post by coldman23 on 2011-07-19
I don't get an IP-adress

---

### Post by chili555 on 2011-07-19
I'm very sorry. We could mess with it for a couple of hours or reinstall in 15 minutes. Do you have critical items on it? I'll be glad to help either way.

---

### Post by coldman23 on 2011-07-19
I'll reinstall again I think. Thanks, I'll keep you informed

---

### Post by chili555 on 2011-07-19
Until we have you going again and happy, you are my only client. I will be here. Please check Private Messages at the top of the page.

---

### Post by mmghd on 2012-05-13
Hi Chili

Have you fixed this problem? I have the same problem with my new S series laptop. 
My wireless network is unrecognized.
Would you please  help.

Regards

---

### Post by chili555 on 2012-05-13
> **mmghd said:**
> Hi Chili

Have you fixed this problem? I have the same problem with my new S series laptop. 
My wireless network is unrecognized.
Would you please  help.

RegardsThere are at least two different cards discussed here. Yours may or may not be the same with the same fix. Would you please start your own new thread and post:```
lspci -nn | grep 0280
rfkill list all
```Leave the link here and I'll be very happy to help.

---

### Post by mmghd on 2012-05-13
Thank you for your quick reply chili.
Here is the new thread:
[http://ubuntuforums.org/showthread.php?p=11932213#post11932213](http://ubuntuforums.org/showthread.php?p=11932213#post11932213)

---

