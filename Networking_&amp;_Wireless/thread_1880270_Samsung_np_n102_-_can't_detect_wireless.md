---
title: "Samsung np n102 - can't detect wireless"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by User1138 on 2011-11-13
I'm using a Samsung np n102 netbook, and I can't seem to detect any wireless networks.

I'm using kernel 2.6.38-12-generic, and the output of the lspci command is as follows:

```


00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation Device 08ae
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)



```Any help would be greatly appreciated.

Thanks in advance.

---

### Post by praseodym on 2011-11-13
Hi,

your device seems too new for Ubuntu 11.04. You need to update the driver via cable connection:

```
sudo apt-get install --reinstall linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select iwlagn
```
If the last command doesnt work properly, undo it via
```
./scripts/driver-select restore
```
and continue with:
```
make
sudo make install 
```
You also need the newest firmware:
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz
sudo tar xvf Intel_Firmware.tar.gz -C /lib/firmware
```
Reboot. Your wireless should work now.
Dont delete the driver folder, after a kernel upgrade you need to compile again:
```
cd compat-wireless-20*
make clean
make
sudo make install
```

---

### Post by User1138 on 2011-11-14
Thanks for the reply, I'll try it later and update the thread!

---

### Post by User1138 on 2011-11-14
Ok, I got as far as make, but it gave me the following error:

```

make: *** /lib/modules/2.6.38-12-generic/build: No such file or directory. Stop.

make: *** [modules] Error 2 

```

How should I proceed?

---

### Post by praseodym on 2011-11-14
Ok, do a

```
./scripts/driver-select restore
```

and continue with

```
make clean
make
sudo make install
```

---

### Post by User1138 on 2011-11-14
Managed to make, install and unload, but I'm still not detecting any wireless networks. Thanks for your help anyway, guess I'll stick to ethernet for the time being :(

---

### Post by praseodym on 2011-11-14
Did you install the firmware, too? Reboot after that and show:

```
iwconfig
lsmod
sudo iwlist scan
route -n
dmesg | grep iwl
rfkill list
```

---

### Post by User1138 on 2011-11-14
Oops. Forgot about that step, running it now.

You, sir, are an absolute genius. I'm now connected. Thank-you! :)

---

### Post by Tanvile on 2012-01-05
Hi, I am also unable to connect to wifi. I tried your method, but 
```
barboruzeles@barboruzeles-laptop:~/compat-wireless-2012-01-04$ ./scripts/driver-select iwlagn
Processing new driver-select request...
Backing up makefile: Makefile.bk
cp: cannot create regular file `Makefile.bk': Permission denied
Unsupported driver
barboruzeles@barboruzeles-laptop:~/compat-wireless-2012-01-04$ sudo ./scripts/driver-select iwlagn
[sudo] password for barboruzeles: 
Processing new driver-select request...
Backing up makefile: Makefile.bk
Unsupported driver

```I'm using a Samsung N100 Notebook, Lucid 10.04.

My output:
```
barboruzeles@barboruzeles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

barboruzeles@barboruzeles-laptop:~$ lsmod
Module                  Size  Used by
easy_slow_down_manager     4081  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
acpi_cpufreq            6130  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289715  3 
snd                     54244  20  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r8101                  78318  0 
drm_kms_helper         29329  1 i915
psmouse                63677  0 
drm                   163747  4 i915,drm_kms_helper
uvcvideo               57438  0 
r8169                  34140  0 
samsung_backlight       2917  0 
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
mii                     4381  1 r8169
intel_agp              24375  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32680  2 
barboruzeles@barboruzeles-laptop:~$ sudo iwlist scan
[sudo] password for barboruzeles: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

barboruzeles@barboruzeles-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
barboruzeles@barboruzeles-laptop:~$ dmesg | grep iwl
barboruzeles@barboruzeles-laptop:~$ rfkill list
barboruzeles@barboruzeles-laptop:~$ ^C

```

My Meego OS on the same notebook had the same drivers and worked well, though now it has crashed and requires manual fsck :sad:

---

### Post by praseodym on 2012-01-05
Please show

> lspci -nnk
lsusb

---

### Post by Tanvile on 2012-01-05
> **praseodym said:**
> Please show

```
barboruzeles@barboruzeles-laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    Kernel modules: i2c-i801
**# it's this one, isnt?**
**05:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]** 
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8101, r8169
barboruzeles@barboruzeles-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2232:1006  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
barboruzeles@barboruzeles-laptop:~$ 

```I'm do not have wifi atm, but still, if it worked, I should receive a suggestion of an encrypted conn. of my neighbours, so :(

Also, what do these might be? They dont have drivers as well:
```
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)

```

---

### Post by praseodym on 2012-01-05
Hi,

your device is "too new" for 10.04 and its kernel 2.6.32. Install the latest driver via LAN:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
make
sudo make install 
```
and reboot. Check if the download was 100 %, otherwise remove the file via:
```
rm -r compat-wireless-2.6.tar.bz2
```
and start again with "wget". Dont remove the driver folder, you need to compile again after a kernel upgrade. Also you should install the metapackage of the kernel headers suitable to your kernel architecture (linux-headers-generic, -generic-pae, whatever).

---

### Post by Tanvile on 2012-01-07
Installed linux headers, but still:

```
barboruzeles@barboruzeles-laptop:~/compat-wireless-2012-01-04$ sudo make
[sudo] password for barboruzeles: 
make -C /lib/modules/2.6.32-37-generic/build M=/home/barboruzeles/compat-wireless-2012-01-04 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic'
  CC [M]  /home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.o
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c:5:1: warning: "pr_fmt" redefined
In file included from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/barboruzeles/compat-wireless-2012-01-04/include/linux/compat-2.6.29.h:5,
                 from /home/barboruzeles/compat-wireless-2012-01-04/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/kernel.h:366:1: warning: this is the location of the previous definition
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c: In function &#8216;if_usb_suspend&#8217;:
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c:1139:  error: implicit declaration of function &#8216;olpc_ec_wakeup_clear&#8217;
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c:1141:  error: implicit declaration of function &#8216;olpc_ec_wakeup_set&#8217;
make[4]: *** [/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/barboruzeles/compat-wireless-2012-01-04] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic'
make: *** [modules] Error 2
barboruzeles@barboruzeles-laptop:~/compat-wireless-2012-01-04$ sudo make install
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
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
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
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_pci.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl12xx/wl1251.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/net/atl1c/atl1c.ko

Your old bluetooth subsystem modules were left intact:

kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/sco.ko

make -C /lib/modules/2.6.32-37-generic/build M=/home/barboruzeles/compat-wireless-2012-01-04 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic'
  CC [M]  /home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.o
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c:5:1: warning: "pr_fmt" redefined
In file included from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/barboruzeles/compat-wireless-2012-01-04/include/linux/compat-2.6.29.h:5,
                 from /home/barboruzeles/compat-wireless-2012-01-04/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/kernel.h:366:1: warning: this is the location of the previous definition
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c: In function &#8216;if_usb_suspend&#8217;:
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c:1139:  error: implicit declaration of function &#8216;olpc_ec_wakeup_clear&#8217;
/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.c:1141:  error: implicit declaration of function &#8216;olpc_ec_wakeup_set&#8217;
make[4]: *** [/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/barboruzeles/compat-wireless-2012-01-04/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/barboruzeles/compat-wireless-2012-01-04] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic'
make: *** [modules] Error 2

```

---

### Post by praseodym on 2012-01-07
Ok, try this driver version:

```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf # Ubuntu 10.04 only
sudo modprobe -rfv iwlagn 
wget [http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz](http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz)
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install
sudo modprobe iwlwifi      # Ubuntu 10.04 only, from 10.10 the module name is still "iwlagn"
ifconfig
iwconfig
iwlist chan
sudo iwlist scan
lsmod
dmesg | grep iwl
```

---

### Post by Tanvile on 2012-04-06
> **praseodym said:**
> Ok, try this driver version:

```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf # Ubuntu 10.04 only
sudo modprobe -rfv iwlagn 
wget [http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz](http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz)
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install
sudo modprobe iwlwifi      # Ubuntu 10.04 only, from 10.10 the module name is still "iwlagn"
ifconfig
iwconfig
iwlist chan
sudo iwlist scan
lsmod
dmesg | grep iwl
```

I'm so sorry I didn't reply to you sooner!! :)

[It worked! It worked! ]("http://yeeeeeeeeeeeeeees.com/"):D

:guitar:

Sorry again. I tried over and over again with the former compat-wireless link, yet it didn't work and I just gave up as I had too much to do at that time ;)

Thank youuuu!!!! :KS
Remind me to treat you with my famous homemade chocolate pie when I pass by Berlin, ok? :popcorn:

---

### Post by NekoMaster on 2012-05-21
ok i hate to dig up old threads but i've been having problems with my Intel centrino N100 card and the above commands work up until "make" at which it complains about this...
```
ubuntu@ubuntu:~/compat-wireless-2011-10-29_patched_ubuntu$ make
/home/ubuntu/compat-wireless-2011-10-29_patched_ubuntu/config.mk:213: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.32-28-generic/build M=/home/ubuntu/compat-wireless-2011-10-29_patched_ubuntu modules
make: *** /lib/modules/2.6.32-28-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I really need to get my wireless going

---

### Post by praseodym on 2012-05-21
Did you install the necessary tools?
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
You should update your system, kernel -41 is up-to-date

---

### Post by NekoMaster on 2012-05-22
Alright so I finally got everything compiled and everything went smoothly without errors up to the end. I rebooted just to make sure it loads the drivers but I still get nothing.

Still using Xubuntu 10.04.02 with latest kernal (2.6.32-41) and latest updates.

EDIT : Ok I solved my problem on another thread i made, this patch plus the ucode  definatly made sure my wifi works. At this time im posting on my internal Wifi card, so no more problems here :)

(clicks the yes yes button) XD

---

### Post by Solle on 2012-09-01
> **Tanvile said:**
> Hi, I am also unable to connect to wifi. I tried your method, but 
```
barboruzeles@barboruzeles-laptop:~/compat-wireless-2012-01-04$ ./scripts/driver-select iwlagn
Processing new driver-select request...
Backing up makefile: Makefile.bk
cp: cannot create regular file `Makefile.bk': Permission denied
Unsupported driver
barboruzeles@barboruzeles-laptop:~/compat-wireless-2012-01-04$ sudo ./scripts/driver-select iwlagn
[sudo] password for barboruzeles: 
Processing new driver-select request...
Backing up makefile: Makefile.bk
Unsupported driver

```I'm using a Samsung N100 Notebook, Lucid 10.04.

My output:
```
barboruzeles@barboruzeles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

barboruzeles@barboruzeles-laptop:~$ lsmod
Module                  Size  Used by
easy_slow_down_manager     4081  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
acpi_cpufreq            6130  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289715  3 
snd                     54244  20  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r8101                  78318  0 
drm_kms_helper         29329  1 i915
psmouse                63677  0 
drm                   163747  4 i915,drm_kms_helper
uvcvideo               57438  0 
r8169                  34140  0 
samsung_backlight       2917  0 
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
mii                     4381  1 r8169
intel_agp              24375  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32680  2 
barboruzeles@barboruzeles-laptop:~$ sudo iwlist scan
[sudo] password for barboruzeles: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

barboruzeles@barboruzeles-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
barboruzeles@barboruzeles-laptop:~$ dmesg | grep iwl
barboruzeles@barboruzeles-laptop:~$ rfkill list
barboruzeles@barboruzeles-laptop:~$ ^C

```My Meego OS on the same notebook had the same drivers and worked well, though now it has crashed and requires manual fsck :sad:


The main problem was the firmware for Intel I00B wireless chipset, after downloading the proper firmware the WIFI works

---

### Post by Solle on 2012-09-01
> **praseodym said:**
> Ok, try this driver version:

```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf # Ubuntu 10.04 only
sudo modprobe -rfv iwlagn 
wget [http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz](http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz)
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install
sudo modprobe iwlwifi      # Ubuntu 10.04 only, from 10.10 the module name is still "iwlagn"
ifconfig
iwconfig
iwlist chan
sudo iwlist scan
lsmod
dmesg | grep iwl
```


Awesome it works finally. Thanks for the post. WiFi works on my Samsung N100 with Intel 100B wifi chipset on Ubuntu 10.04.

---

