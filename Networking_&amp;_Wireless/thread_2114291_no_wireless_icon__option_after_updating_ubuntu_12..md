---
title: "no wireless icon / option after updating ubuntu 12.10"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by shaital on 2013-02-09
i have no wireless option at all!!
I saw many posts but coulnd solve the problem.
what do i need to do in order to get the wireless option to my ubuntu?

here is out put :
  	 	 	 	 	 	   $ lspci 
 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
 00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) 
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04) 
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) 
 00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4) 
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) 
 00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 04) 
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 04) 
 00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04) 
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
 lsusb 
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse 
 Bus 001 Device 004: ID 2001:3c1e D-Link Corp.  
  ifconfig 
 eth0      Link encap:Ethernet  HWaddr ec:a8:6b:72:ac:d1   
           inet addr:192.168.0.181  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::eea8:6bff:fe72:acd1/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:53899 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:44322 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:57644288 (57.6 MB)  TX bytes:5508243 (5.5 MB) 
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:4473 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4473 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:393381 (393.3 KB)  TX bytes:393381 (393.3 KB) 
 lsmod 
 Module                  Size  Used by 
 rt73usb                26663  0  
 crc_itu_t              12628  1 rt73usb 
 rt2x00usb              19980  1 rt73usb 
 rt2x00lib              48602  2 rt73usb,rt2x00usb 
 b43                   347311  0  
 mac80211              461203  3 rt2x00usb,rt2x00lib,b43 
 cfg80211              175574  3 rt2x00lib,b43,mac80211 
 bcma                   34484  1 b43 
 ssb                    50088  1 b43 
 rfcomm                 37277  0  
 bnep                   17708  2  
 bluetooth             183270  10 rfcomm,bnep 
 parport_pc             31969  0  
 ppdev                  12818  0  
 coretemp               13169  0  
 kvm_intel             126746  0  
 kvm                   357807  1 kvm_intel 
 snd_hda_codec_realtek    63496  1  
 snd_hda_intel          32516  3  
 snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13273  1 snd_hda_codec 
 snd_pcm                80235  2 snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13133  0  
 snd_rawmidi            25383  1 snd_seq_midi 
 snd_seq_midi_event     14476  1 snd_seq_midi 
 snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event 
 microcode              18210  0  
 snd_timer              24412  2 snd_pcm,snd_seq 
 snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq 
 mac_hid                13038  0  
 snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i915                  457247  3  
 mei                    35797  0  
 drm_kms_helper         47304  1 i915 
 lpc_ich                16926  0  
 soundcore              14600  1 snd 
 snd_page_alloc         14037  2 snd_hda_intel,snd_pcm 
 drm                   238811  4 i915,drm_kms_helper 
 serio_raw              13032  0  
 i2c_algo_bit           13198  1 i915 
 video                  18848  1 i915 
 lp                     13300  0  
 parport                40754  3 parport_pc,ppdev,lp 
 hid_generic            12485  0  
 usbhid                 41734  0  
 hid                    82179  2 hid_generic,usbhid 
 r8169                  55977  0  
 

 

 

  

 dmesg 

 mBm) 
 [ 1214.148410] Broadcom 43xx driver loaded [ Features: PNL ] 
 [ 3103.468073] usbcore: registered new interface driver rt73usb 
 [ 3111.030796] init: network-manager main process (746) killed by KILL signal
 sudo lshw -C network 
 [sudo] password for shai:  
   *-network                
        description: Ethernet interface 
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 06 
        serial: ec:a8:6b:72:ac:d1 
        size: 100Mbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.181 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
        resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff 
 uname -mr 
 3.5.0-23-generic i686

---

### Post by praseodym on 2013-02-09
There are two drivers loaded:
```

sudo modprobe -rfv b43
sudo modprobe -rfv rt73usb
sudo modprobe -v rt73usb
```

---

### Post by shaital on 2013-02-10
so what should i do next to fix it?

---

### Post by praseodym on 2013-02-10
Is it working?

---

### Post by shaital on 2013-02-10
i ran the code 
still dosent work

---

### Post by shaital on 2013-02-11
please help

---

### Post by praseodym on 2013-02-11
Obviously it a Ralink chipset, try this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/42/20/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA
```
Unload the others:```


sudo modprobe -rfv rt73usb
sudo modprobe -rfv b43
sudo modprobe -v rt5370sta
```
Check:```

iwconfig
dmesg | grep rt53
iwlist chan
sudo iwlist scan
```

---

### Post by shaital on 2013-02-11
thanks, here is the output after did what you mentioned
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

i:~$ dmesg | grep rt53
:~$ iwlist chan
lo        no frequency information.
eth0      no frequency information.

~$ sudo iwlist scan 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2013-02-12
Please show:
```

lsmod
modinfo rt5370sta | grep 2001
```

---

### Post by shaital on 2013-02-12
shai@shai:~$ lsmod
Module                  Size  Used by
parport_pc             31969  0 
ppdev                  12818  0 
bnep                   17708  2 
rfcomm                 37277  0 
bluetooth             183270  10 bnep,rfcomm
coretemp               13169  0 
kvm_intel             126746  0 
kvm                   357807  1 kvm_intel
snd_hda_codec_realtek    63496  1 
binfmt_misc            17261  1 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
microcode              18210  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13038  0 
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457247  3 
b43                   347311  0 
mac80211              461203  1 b43
cfg80211              175574  2 b43,mac80211
bcma                   34484  1 b43
ssb                    50088  1 b43
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18848  1 i915
serio_raw              13032  0 
soundcore              14600  1 snd
lp                     13300  0 
lpc_ich                16926  0 
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
parport                40754  3 parport_pc,ppdev,lp
mei                    35797  0 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
r8169                  55977  0 
shai@shai:~$ modinfo rt5370sta | grep 2001
shai@shai:~$ modinfo rt5370sta
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.1
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     D85CA1F0346F5026BC54513
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
shai@shai:~$

---

### Post by praseodym on 2013-02-12
Try to add the product and vendor ID to the driver rt2800usb:
```

echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "2001 3c1e" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
```
This is one line, you better copy/paste it. Reload the driver:
```

sudo modprobe -rfv b43
sudo modprobe -v rt2800usb
```
Check:```

iwconfig
lsmod
dmesg | grep rt2
rfkill list
sudo iwlist scan
```

To uninstall the wrong driver:```

sudo dkms remove -m Ralink_5370sta -v 2.5.0.3 --all
```

---

### Post by shaital on 2013-02-12
I have no words, great thank you:guitar:
can you explain what I just did and how to avoid it on the next update

---

### Post by shaital on 2013-02-12
oops, after restart the wireless is gone again

---

### Post by praseodym on 2013-02-12
Please show after rebooting:
```

lsmod
egrep 'rt2|b43|rt5|rt7' /etc/modprobe.d/*
cat /etc/modules
```
You added the ID of the stick 2001:3c1E to the native driver rt2800usb, when this stick is plugged in.

---

### Post by shaital on 2013-02-12
ok did it,but it doesnt stick after restart.
still no wireless

---

### Post by praseodym on 2013-02-12
Please show the outputs.

---

### Post by shaital on 2013-02-12
here:
shai@shai:~$ lsmod
Module                  Size  Used by
bnep                   17708  2 
rfcomm                 37277  0 
coretemp               13169  0 
kvm_intel             126746  0 
parport_pc             31969  0 
kvm                   357807  1 kvm_intel
bluetooth             183270  10 bnep,rfcomm
ppdev                  12818  0 
snd_hda_codec_realtek    63496  1 
binfmt_misc            17261  1 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13038  0 
microcode              18210  0 
b43                   347311  0 
mac80211              461203  1 b43
serio_raw              13032  0 
cfg80211              175574  2 b43,mac80211
bcma                   34484  1 b43
lpc_ich                16926  0 
ssb                    50088  1 b43
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
mei                    35797  0 
i915                  457247  3 
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18848  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
r8169                  55977  0 
shai@shai:~$ egrep 'rt2|b43|rt5|rt7' /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist rt2800usb
/etc/modprobe.d/blacklist.conf:blacklist rt2870sta
/etc/modprobe.d/blacklist.conf~:# replaced by b43 and ssb.
/etc/modprobe.d/rt2800usb.conf:install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "2001 3c1e" > /sys/bus/usb/drivers/rt2800usb/new_id
shai@shai:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
b43

---

### Post by praseodym on 2013-02-12
Open the file:
```

gksu gedit /etc/modprobe.d/blacklist.conf
```
and remove the line:```

blacklist rt2800usb
```
Save and close. After that open this file:
```

gksu gedit /etc/modules
```
and remove **b43**. Save, close and reboot. Or instead of rebooting, load the driver:
```

sudo modprobe -rfv b43
sudo modprobe rt2800usb
```
Check again:
```

iwconfig
dmesg | grep rt2
sudo iwlist scan
rfkill list
```

---

### Post by Tony812 on 2013-02-12
I had this SAME PROBLEM AND FIXED IT!  Stop using the Windows/Proprietary driver and use the generic one included with Ubuntu. BAM! Should work....

---

### Post by shaital on 2013-02-12
OK did it still after restart wireless is gone
shai@shai:~$ lsmod
Module                  Size  Used by
rfcomm                 37277  0 
parport_pc             31969  0 
ppdev                  12818  0 
bnep                   17708  2 
bluetooth             183270  10 rfcomm,bnep
snd_hda_codec_realtek    63496  1 
coretemp               13169  0 
kvm_intel             126746  0 
kvm                   357807  1 kvm_intel
binfmt_misc            17261  1 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13038  0 
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              18210  0 
i915                  457247  3 
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18848  1 i915
serio_raw              13032  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lpc_ich                16926  0 
mei                    35797  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
r8169                  55977  0 
shai@shai:~$ egrep 'rt2|b43|rt5|rt7' /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist rt2870sta
/etc/modprobe.d/blacklist.conf~:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf~:blacklist rt2800usb
/etc/modprobe.d/blacklist.conf~:blacklist rt2870sta
/etc/modprobe.d/rt2800usb.conf:install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "2001 3c1e" > /sys/bus/usb/drivers/rt2800usb/new_id
shai@shai:~$ cat /etc/modules

---

### Post by praseodym on 2013-02-12
Open the file manager:
```

gksu nautilus /etc/modprobe.d/
```
and remove the file with [COLOR="Red"]~
[/COLOR]
```
blacklist.conf~
```
Load the driver by hand:
```

sudo modprobe -v rt2800usb
```
and replug the stick (or reboot)

---

### Post by shaital on 2013-02-12
when i load the driver with this
sudo modprobe -v rt2800usb then it is ok but when i resart, the wireless is gone again

---

### Post by praseodym on 2013-02-12
Force the driver to load at boot-up:
```

echo rt2800usb | sudo tee -a /etc/modules
```

---

### Post by shaital on 2013-02-17
hi,
that a bump.I see the wireless icon but the broblem is that it doesnt find any netwok. even if i try to connect to hidden wireless i get ubuntu error massege.
I wish i could understand how to fix it...

---

