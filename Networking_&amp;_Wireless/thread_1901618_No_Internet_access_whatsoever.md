---
title: "No Internet access whatsoever"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by piloteerman on 2011-12-28
Hi, I'm brand new to Ubuntu, and just installed Ubuntu 10.04.

It seems to be working fine except I have no internet access whatsoever, not by ethernet or wireless.

When I connect ethernet it reads "Not connected", even though that connection works on my other windows laptop.

The wireless connection simply reads "device not ready". I have read other forums and can't seem to figure out what my issue is.

Any help is appreciated.

---

### Post by yndesai on 2011-12-28
> **piloteerman said:**
> Hi, I'm brand new to Ubuntu, and just installed Ubuntu 10.04.

It seems to be working fine except I have no internet access whatsoever, not by ethernet or wireless.

When I connect ethernet it reads "Not connected", even though that connection works on my other windows laptop.

The wireless connection simply reads "device not ready". I have read other forums and can't seem to figure out what my issue is.

Any help is appreciated.

Please provide more details to get help
1. what hardware (processor, motherboard, ethernet card)
2. what type of network (DHCP or not)
3. with what settings network is working on the MS windows.?

---

### Post by piloteerman on 2011-12-29
Unfortunately I do not know too much about the hardware in the computer, its an old netbook I got off a friend. Is there a way to bring it up on the computer to find out what kind of motherboard/ethernet card etc i have?
If it helps its a Dell Inspiron Mini 10

I'm on a DHCP network, and what do you mean by what settings on the windows operating system? I'm running windows on a completely separate computer...

---

### Post by praseodym on 2011-12-29
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:

```
uname -a
lspci -nnk
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Does your router allow new clients, means: MAC-address filter is turned off?

---

### Post by piloteerman on 2011-12-29
uname -a outputs:
```
Linux daniel-netbooki 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
```lspci -nnk outputs:
```
 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)  
     Kernel driver in use: agpgart-intel  
     Kernel modules: intel-agp  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)  
     Kernel driver in use: i915  
     Kernel modules: i915  
 00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)  
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
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)  
     Kernel modules: iTCO_wdt, intel-rng  
 00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)  
     Kernel driver in use: ata_piix  
 00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)  
     Kernel modules: i2c-i801  
 03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)  
     Kernel driver in use: b43-pci-bridge  
     Kernel modules: ssb  
 04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
     Kernel driver in use: r8169  
     Kernel modules: r8169  
 
```
lsusb outputs:
```
 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 046d:c52f Logitech, Inc.  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device  
 Bus 001 Device 003: ID 174f:1403 Syntek 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 
```
lsmod outputs:
```
 
Module                  Size  Used by  
 usbhid                 36110  0  
 hid                    67288  1 usbhid  
 nls_iso8859_1           3249  0  
 nls_cp437               4919  0  
 vfat                    8933  0  
 fat                    47767  1 vfat  
 binfmt_misc             6587  1  
 ppdev                   5259  0  
 joydev                  8740  0  
 snd_hda_codec_realtek   203376  1  
 fbcon                  35102  71  
 tileblit                1999  1 fbcon  
 font                    7557  1 fbcon  
 bitblit                 4707  1 fbcon  
 softcursor              1189  1 bitblit 
 vga16fb                11385  0  
 vgastate                8961  1 vga16fb 
 snd_hda_intel          22069  2  
 snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               5412  1 snd_hda_codec  
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss  
 snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           1338  0  
 snd_seq_oss            26722  0  
 snd_seq_midi            4557  0  
 snd_rawmidi            19056  1 snd_seq_midi  
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              19098  2 snd_pcm,snd_seq  
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 dell_wmi                1793  0  
 arc4                    1153  2  
 snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i915                  288611  3  
 drm_kms_helper         29329  1 i915  
 b43                   163556  0  
 uvcvideo               57374  0  
 compal_laptop           2034  0  
 psmouse                63677  0  
 mac80211              205402  1 b43  
 dcdbas                  5422  0  
 drm                   162377  4 i915,drm_kms_helper  
 soundcore               6620  1 snd  
 videodev               34361  1 uvcvideo  
 v4l1_compat            13251  2 uvcvideo,videodev  
 cfg80211              126144  2 b43,mac80211  
 serio_raw               3978  0  
 intel_agp              24375  2 i915  
 snd_page_alloc          7076  2 snd_hda_intel,snd_pcm  
 agpgart                31724  2 drm,intel_agp  
 i2c_algo_bit            5028  1 i915  
 led_class               2864  1 b43  
 video                  17375  1 i915  
 output                  1871  1 video  
 lp                      7028  0  
 parport                32635  2 ppdev,lp  
 usb_storage            39841  0  
 r8169                  34140  0  
 mii                     4381  1 r8169  
 ssb                    38934  1 b43  
 
```ifconfig -a outputs:
```
 eth0      Link encap:Ethernet  HWaddr 00:24:e8:b4:9d:3a   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:27  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:3472 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:3472 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:276204 (276.2 KB)  TX bytes:276204 (276.2 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:25:56:51:34:b7   
           BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
```iwconfig outputs:
```
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
 

 rfkill list
 0: compal-wifi: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
 1: compal-bluetooth: Bluetooth  
     Soft blocked: no  
     Hard blocked: no  
 2: phy0: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
 
```cat/etc/network/interfaces outputs: 

```
 
bash: cat/etc/network/interfaces: No such file or directory  
 
```cat/etc/resolv.conf outputs: 

```
 
bash: cat/etc/resolv.conf: No such file or directory  
 
```
Hope that makes more sense to you than it does to me... 

thanks again for all your help

---

### Post by bogan on 2011-12-29
Hi! PILOTEERMAN,


You Posted:
> cat/etc/network/interfaces outputs: 

     

      
bash: cat/etc/network/interfaces: No such file or directory 
cat/etc/resolv.conf outputs: 

     Code:
      
bash: cat/etc/resolv.conf: No such file or directory 
You do not need the "bash", and there **must **be a space between 'cat' and '/etc/'
Like:
> cat  /etc/resolv.conf

---

### Post by piloteerman on 2011-12-29
Thanks,

cat /etc/resolv.conf still returns 
```
cat: /etc/resolv.conf: no such file or directory
```

cat /etc/network/interfaces returns
```
auto lo
iface lo inet loopback
```

---

### Post by praseodym on 2011-12-29
For the wireless device you need the firmware. It is attached. Save it in /home and unpack it via terminal:

```
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
```
You may need to reload the driver:

```
sudo modprobe -rfv b43
sudo modprobe -v b43
```
After that you should update your system:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Reboot. The new kernel -37 should be shown with "uname -a".

---

### Post by optima4 on 2011-12-29
I will tell you I had this same exact problem when I first installed Ubuntu 10.04 a couple months back. I spent an entire 5 days trying every command, every different work around, ethernet cable, etc. Nothing worked at all. I upgraded to Ubuntu 11.10 and the internet works now. Still I have these minor issues why I am back, but I recommend trying an upgrade Ubuntu, or trying Kubuntu, or a version of the like Fedora, Xbuntu, CentOS, etc. It may resolve this issue of yours as well.

---

### Post by praseodym on 2011-12-29
If the firmware installation doesnt bring you wireless on (the driver b43 works better from Ubuntu 11.04 and on), install the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source** from CD by double clicking. After that activate the Broadcom-STA-driver in "additional drivers" after

```
sudo depmod -a
```

Alternatively download these packages for your 32bit system from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by piloteerman on 2011-12-29
Thanks a tonne. I think that just about did it. 

I installed the firmware via terminal like you said, now my wireless network shows up, and attempts to connect, but doesn't actually connect.
I get prompted for my WPA key which I enter and the wi-fi symbol scrolls up and down as if it is connecting, but it never does connect. A few minutes later I am prompted for my key again. 

Any ideas?

---

### Post by piloteerman on 2011-12-30
Thanks everyone for all the help, i resolved the problem by upgrading to Ubuntu 11.10. 

Thanks for all the help

---

