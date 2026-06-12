---
title: "unable to connect to wireless network in XUBUNTU"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by lightfile on 2011-12-14
Hi,

i have installed XUBUNTU 11.10 few days ago. and i'm a newbie to the Linux world. i cannot see any active wireless networks , and the wireless network label is grayed out.

i have an intel computer, with a wireless card EDIMAX - EW-7711LN .
when i li am the administrator of the XUBUNTU.

i installed the ndiswrapper but when trying to run it - 
ndiswrapper -l

results in:
autorun : invalid driver!


lightfile@lightfile-PH67A-UD3:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



also i ran few more commands:



1)sudo lshw -C Network  
results in:


*-network               
       
description: Ethernet interface
       
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
     
  vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
    
   bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
  
     serial: 1c:6f:65:88:29:0a
       size: 10Mbit/s
       capacity: 1Gbit/s
     
  width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list 

ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
      
 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half 
firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       
resources: irq:41 ioport:ee00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff
  

*-network
       description: Wireless interface
       product: RT3060 Wireless 802.11n 1T/1R
     
 vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: 
wlan0
     
  version: 00
       serial: 00:1f:1f:b2:14:06
       width: 32 bits
       clock: 33MHz
    
   capabilities: pm bus_master cap_list ethernet physical wireless
      
 configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-12-generic firmware=0.34 latency=32
 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
      
 resources: irq:19 memory:fbef0000-fbefffff




2) sudo ifconfig wlan0
results in:
wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:b2:14:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


3)
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation H67 Express Chipset Family LPC Controller [8086:1c4a] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller [8086:1c00] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
00:1f.5 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller [8086:1c08] (rev 04)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
03:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
05:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
06:00.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]




4)
lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  4 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  5 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd                    55902  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               663211  2 
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   192226  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
floppy                 60310  0 
xhci_hcd               72915  0 



5)
sudo apt-get install gedit
Reading package 
lists... 
Done
Building dependency tree     

Reading state information... 
Done
E: Unable to locate package gedit

for some reason i don't have the gedit application...


ALSO , when i try to edit the blacklist, it doesn't allow me to save the edited file. 

Please help me, i'm working on this, for the last couples of days and i don't have a clue.
i'm not sure whether the linux is identifying the edimax card or not - cause i see Ralink corp. RT3060 in the network controller but for the driver i see - rt2800pci. why doesn't it specifically write EDIMAX? and why there is a difference anyway between the driver and the network controller

appreciate your help!!

---

### Post by lightfile on 2011-12-16
anyone?

---

### Post by lightfile on 2011-12-18
anybody?

---

### Post by Jose Catre-Vandis on 2011-12-18
Seems to recognise the hardware...what type of network are you trying to connect to?

So what happens when you try to connect to a wireless network using the gui (Network Manager)? Do you see your network / other networks around you?

Try dropping security if you can to first make a connection?

---

### Post by lightfile on 2011-12-18
wireless - using WPA security.
the problem is that i don't see any wireless networks at all (either mine or other networks)

and as i wrote before, i don't know if there is any significant but -it can be seen from the linux commands that RT3060 is identified as the network controller but for the driver i see - rt2800pci. should it be this way?

---

### Post by Jose Catre-Vandis on 2011-12-19
Try blacklisting that driver:
```
sudo nano /etc/modprobe.d/blacklist.conf
```
Add this to the bottom of the file and then save:
```
# blacklisted by lightfile
blacklist rt2800pci
```
Try a reboot see if anything works?

If not you may have to compile your driver, see this link, or just google your network controller line, lots of info out there.
[http://ubuntuforums.org/showthread.php?t=1867986](http://ubuntuforums.org/showthread.php?t=1867986)

---

### Post by wildmanne39 on 2011-12-20
Hi, your card uses the rt2800pci driver if you blacklisted it you will need to unblacklist it then please post the results of:
```
iwconfig
rfkill list all
nm-tool
sudo iwlist scan
ndiswrapper -l
```
Thanks

---

### Post by lightfile on 2011-12-20
blacklisting rt2800pci didn't help. i'm adding the results of some commands before and after blacklisting:

_**before blaclisting:**_
[COLOR=Black]iwconfig[/COLOR]
      lo        no wireless extensions.

      eth0      no wireless extensions.

 rfkill list all
            0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

 nm-tool

      NetworkManager Tool

      State: disconnected

    - Device: eth0 -----------------------------------------------------------------
      Type:              Wired
      Driver:            r8169
      State:             unavailable
      Default:           no
      HW Address:        1C:6F:65:88:29:0A

      Capabilities:
      Carrier Detect:  yes
       Speed:           10 Mb/s

      Wired Properties
       Carrier:         off


    - Device: wlan0 ----------------------------------------------------------------
      Type:              802.11 WiFi
      Driver:            rt2800pci
      State:             disconnected
      Default:           no
      HW Address:        00:1F:1F:B2:14:06

      Capabilities:

     Wireless Properties
        WEP Encryption:  yes
        WPA Encryption:  yes
       WPA2 Encryption: yes

        Wireless Access Points 


        wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

sudo iwlist scan
[sudo] password for lightfile: 
      lo        Interface doesn't support scanning.

      eth0      Interface doesn't support scanning.

      wlan0     No scan results

ndiswrapper -l
       autorun : invalid driver!




_**after blacklisting the rt2800pci**_
iwconfig:    
          lo        no wireless extensions.
          eth0      no wireless extensions.

rfkill list all:   
didn't seem to do anything - didn't show any reaction on screen

nm-tool:

    NetworkManager Tool

    State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        1C:6F:65:88:29:0A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


ndiswrapper -l
autorun : invalid driver!




Thanks

---

### Post by praseodym on 2011-12-20
Hi,

normally you dont need ndiswrapper, so remove it completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
Update the system, there is also a new kernel available:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Put rt2800pci onto the blacklist (again) and reboot into the new kernel. After that try this driver, support for network-manager and wpa_supplicant is activated:

```
sudo apt-get install linux-headers-generic build-essential 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install
sudo modprobe rt3562sta 
```
Check:
```
iwconfig
sudo iwlist scan
rfkill list
lsmod
dmesg | egrep 'rt2|rt3|country'
iwlist chan
```

---

### Post by lightfile on 2011-12-21
unfortunately, this didn't help eiter.
to start with - i couldn't update the kernel - since there is no internet, or from some other reason.
blacklist the rt2800pci, again didn't help after running these commands.


**sudo apt-get update:**
----------------------------

Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric InRelease
  
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates InRelease
  
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-backports InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
  
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric Release.gpg
  Could not resolve 'il.archive.ubuntu.com'
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates Release.gpg
  Could not resolve 'il.archive.ubuntu.com'
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-backports Release.gpg
  Could not resolve 'il.archive.ubuntu.com'
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Reading package lists... Done
W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/InRelease](http://archive.canonical.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://il.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'il.archive.ubuntu.com'

W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://il.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve 'il.archive.ubuntu.com'

W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://il.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Could not resolve 'il.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.




code:
**sudo apt-get upgrade**
-----------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




[B]sudo apt-get install linux-headers-generic build-essential:
[/B]--------------------------------------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source




** iwconfig**
----------------
lo        no wireless extensions.

eth0      no wireless extensions.



**sudo iwlist scan**
-----------------------
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.




**rfkill list**
-------------
no response

** lsmod**
------------------------------------
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  4 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  5 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               663211  2 
soundcore              12600  1 snd
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
serio_raw              12990  0 
drm                   192226  4 nouveau,ttm,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
floppy                 60310  0 
r8169                  43104  0 
xhci_hcd               72915  0 


 **dmesg | egrep 'rt2|rt3|country'**
-------------------------------------------
no response



**iwlist chan**
---------------------
lo        no frequency information.

eth0      no frequency information.

---

### Post by lightfile on 2011-12-23
?

---

### Post by lightfile on 2011-12-24
?

---

### Post by praseodym on 2011-12-24
Please show:

```
uname -a
iwconfig
lsmod
```
Add the installation CD/DVD to the software sources and install the package "build-essential" from there.

---

### Post by lightfile on 2011-12-24
i think that the cd / dvd installtion is already marked up as a source. but i don't know where to find what you called  "build-essential". i didn't find a place where i can install specificlly from the cd .

bare in mind that the rt2800 is blacklisted now, the results of the commands u gave me are:

uname -a
-------------
Linux lightfile-PH67A-UD3 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux


iwconfig
--------------
lo        no wireless extensions.

eth0      no wireless extensions.


lsmod
---------------------------------
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  4 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  5 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               663211  2 
snd                    55902  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   192226  4 nouveau,ttm,drm_kms_helper
mei                    36466  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
floppy                 60310  0 
r8169                  43104  0 
xhci_hcd               72915  0

---

### Post by praseodym on 2011-12-24
Ok, try to install the package:
```
sudo apt-get install build-essential
```
and install the kernel headers by double clicking:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12-generic_3.0.0-12.20_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12-generic_3.0.0-12.20_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12_3.0.0-12.20_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12_3.0.0-12.20_all.deb)

After that download the driver from

[http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz)

and compile it as described

---

### Post by lightfile on 2011-12-25
sudo apt-get install build-essential
--------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'build-essential' has no installation candidate


the header kernel (which i downloaded when i was logged in windows 7) , i tried to install , nothing happened , but i can see from the system , that they are already installed.

---

### Post by praseodym on 2011-12-25
Please show:

```
cat /etc/apt/sources.list
```

---

### Post by lightfile on 2011-12-25
cat /etc/apt/sources.list
-----------------------------------
deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse #Added by software-properties

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by praseodym on 2011-12-25
Try the following: Save this file:

```
sudo mv /etc/apt/sources.list /etc/apt/sources.bak
```
Create a new one:
```
gksu gedit /etc/apt/sources.list
```
Insert:
```
deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
```
save, close the editor and:
```
sudo apt-get update
sudo apt-get install build-essential
```
If it works, compile the driver as decribed and copy the file back:
```
sudo mv /etc/apt/sources.bak /etc/apt/sources.list
sudo apt-get update
```

---

### Post by lightfile on 2011-12-25
how to compile?

---

### Post by praseodym on 2011-12-25
Did it work? See #9

---

### Post by lightfile on 2011-12-25
no it didn't.
first of all i don't have gedit for some reason. but i used nano command instead.
and once again, the command sudo apt-get install build-essential didn't work

should i install the xubuntu from the start? a different version?

---

### Post by praseodym on 2011-12-25
Did/do you have any connection using the Live-CD? If yes, try there:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```
After that copy any files from the folder /var/cache/apt/archives to an USB-stick. Boot into the "real" system, copy these files to "Downloads" and install them via:

```
sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by lightfile on 2011-12-25
there is/was no connection, even with the installation CD

---

### Post by praseodym on 2011-12-25
Not even wired?

---

### Post by lightfile on 2011-12-25
can't reach the wire, since it sits in a different room, and i my computer is not a laptop

---

### Post by praseodym on 2011-12-25
You can also try the install from #23 from the other computer with Live-CD. The installed systems are not affected from that (until you click on "install" ;-) )

---

