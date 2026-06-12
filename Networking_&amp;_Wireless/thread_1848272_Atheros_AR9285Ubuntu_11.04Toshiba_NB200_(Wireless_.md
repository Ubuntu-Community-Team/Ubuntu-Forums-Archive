---
title: "Atheros AR9285/Ubuntu 11.04/Toshiba NB200 (Wireless Hard Blocked?)"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by metrics on 2011-09-22
My toshiba NB200 laptop shows  no wireless options in the menu on the top right hand side. Wireless is greyed out. Any suggestions om whats wrong  or how i could fix it? It connects to the router via the ethernet  cable. 
rfkill list advises that the card is hard blocked.

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
``````
lsusb
Bus 005 Device 002: ID 054c:01f8 Sony Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```


   sudo lshw -class network
*-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:a9:ba:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:f8:57:15
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

                                                                                                                 


```

---

### Post by gotharious on 2011-09-23
Try the following 

```

sudo apt-get install bcmwl-kernel-source
echo wl | sudo tee -a /etc/modules

```

That should do the trick ;)

---

### Post by praseodym on 2011-09-23
> **gotharious said:**
> Try the following 

```

sudo apt-get install bcmwl-kernel-source
echo wl | sudo tee -a /etc/modules

```

That should do the trick ;)

He is using an Atheros chipset with driver **ath9k**, not Broadcom, this will [COLOR="Red"]not[/COLOR] work!

@metrics:

Please show additionally:

```
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
iwconfig
lsmod
sudo iwlist scan
dmesg | grep ath
```

---

### Post by gotharious on 2011-09-23
> **praseodym said:**
> He is using an Atheros chipset with driver **ath9k**, not Broadcom, this will [COLOR=Red]not[/COLOR] work!


Thanks for the correction, mate :)

---

### Post by metrics on 2011-09-24
Thank you gotharious for your help with this issue

```

 rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
```


cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


```
```


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

``````


lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          28209  2 
joydev                 17322  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
i915                  451068  3 
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
ath9k                 105891  0 
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              259567  1 ath9k
uvcvideo               66851  0 
drm                   184164  4 i915,drm_kms_helper
ath9k_common           13797  1 ath9k
psmouse                59039  0 
videodev               75143  1 uvcvideo
i2c_algo_bit           13184  1 i915
ath9k_hw              311106  2 ath9k,ath9k_common
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     13349  0 
ath                    19147  2 ath9k,ath9k_hw
soundcore              12600  1 snd
serio_raw              12990  0 
video                  18951  1 i915
sparse_keymap          13666  0 
parport                36746  3 parport_pc,ppdev,lp
cfg80211              155552  3 ath9k,mac80211,ath
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
r8169                  46630  0 





``````




sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down




```



```


 dmesg | grep ath
[    1.138086] device-mapper: multipath: version 1.2.0 loaded
[    1.138095] device-mapper: multipath round-robin: version 1.0.0 loaded
[   10.113804] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.113834] ath9k 0000:03:00.0: setting latency timer to 64
[   10.165342] ath: EEPROM regdomain: 0x65
[   10.165349] ath: EEPROM indicates we should expect a direct regpair map
[   10.165357] ath: Country alpha2 being used: 00
[   10.165361] ath: Regpair used: 0x65
[   10.551155] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.555327] Registered led device: ath9k-phy0


```

---

### Post by praseodym on 2011-09-24
"Hard blocked" means there is some button/switch/key combination to press. Check your BIOS settings if wireless can be activated there. Maybe resetting the BIOS to default settings?!

Edit: Try a:

```
sudo rfkill unblock all
```

---

### Post by metrics on 2011-09-24
> **praseodym said:**
> "Hard blocked" means there is some button/switch/key combination to press. Check your BIOS settings if wireless can be activated there. Maybe resetting the BIOS to default settings?!

Edit: Try a:

```
sudo rfkill unblock all
```

Thank you praseodym,
sudo rfkill unblock all -> tried that already and doesn't work for me
Wireless Comm SW: ON -> Wireless was on in the BIOS all the time

---

### Post by praseodym on 2011-09-24
Please do a:

```
dmesg >> dmesg.txt
```

and upload the file or copy it to some "pastebin"-service.

---

### Post by metrics on 2011-09-24
> **praseodym said:**
> and upload the file or copy it to some "pastebin"-service.

can you please explain what i have to do with the file  dmesg.txt

---

### Post by metrics on 2011-09-25
Hi praseodym
Thank you for your assistance so far.
do you know if there is  anything i can do to get the wireless working on my machine at all?

---

### Post by praseodym on 2011-09-25
Did you reset the BIOS?

---

### Post by metrics on 2011-09-25
Hi praseodym,
confirming that Wireless is ON in the bios.
I have done a BIOS reset and the only thing that  i have changed is the "SATA Controller Mode" to "Compatibility"

Unfortunately I can't figure it out why it's still hard blocked.

---

### Post by metrics on 2011-10-02
I have been trying to solve this issue for more than 1 week now and so far, I had no luck in getting the wireless card working. Still Hard blocked for some reason. 
I was wondering,  is there a way to establish if the hardware is still working before i grow old trying to fix the drivers.

---

### Post by kurt18947 on 2011-10-02
Do you have Windows installed in a dual-boot configuration? I don't know if this is your case but some WiFi adapters, if disabled in Windows cannot be enabled in Ubuntu or Linux. They must first be enabled in Windows then the machine rebooted while the WiFi adapter is enabled. There is some sort of switch that only responds to commands in Windows. Good luck getting your network device working. If for some reason your internal Wifi device refuses to wake up, could you use a USB adapter? An internal device is preferred but the mini USB devices aren't too awkward.

---

### Post by metrics on 2011-10-03
Hi kurt18947,
No dual boot. Windows XP crashed and I couldn't reinstall it from USB so I formatted the disk to EXT4 and installed ubuntu only.

---

### Post by praseodym on 2011-10-03
I dont know if it works for Toshiba, but for Fujitsu NBs there is a kernel module for the hardware switch you can try (it makes no harm if it doesnt work)

```
sudo modprobe -v fsam7400 radio=1
sudo rfkill unblock all
rfkill list
```

---

### Post by metrics on 2011-10-04
Unfortunately didn't work, i get the below msg, which i'm not sure what does it mean 

```

Sudo moprobe -v fsam7400 radio=1
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save, it will be ignored in a future release.
insmod /lib/modules/2.6.38-11-generic-pae/kernel/ubuntu/fsam7400/fsam7400.ko radio=1

```

---

### Post by praseodym on 2011-10-04
Please show:

```
grep ath /etc/modprobe.d/*
```

---

### Post by metrics on 2011-10-05
> **praseodym said:**
> Please show:

```
grep ath /etc/modprobe.d/*
```

Please see below

```

grep ath /etc/modprobe.d/*
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/ath9k.conf.save:options ath9k nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:# blacklist ath_pci


```

---

### Post by praseodym on 2011-10-05
This file can be safely removed:

```
sudo rm /etc/modprobe.d/ath9k.conf.save
sudo modprobe -v fsam7400 radio=1
sudo rfkill unblock all
```
Check:
```
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by metrics on 2011-10-05
I deleted the file and run the command as suggested.
the second lot is as per below 
```


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
   

``````
       
 rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


``````

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down



```

---

### Post by praseodym on 2011-10-05
There is no button, switch, etc.? Did you try Fn+F2?

---

### Post by metrics on 2011-10-06
I have tried fn+f8 which is the Wireless button but didn't work either.
Not other switch as far as i can see :(

---

### Post by praseodym on 2011-10-06
Is there the following module present?

```
modinfo toshiba_acpi
```
If yes, try to load it via:

```
sudo modprobe -v toshiba_acpi
sudo depmod -a
sudo rfkill unblock all
sudo service network-manager restart
```
Check:

```
iwconfig
dmesg | egrep 'tosh|radio|switch|kill'
sudo iwlist scan
rfkill list
```

---

### Post by metrics on 2011-10-07
> **praseodym said:**
> Is there the following module present?

```
modinfo toshiba_acpi
```If yes, try to load it via:

```
sudo modprobe -v toshiba_acpi
  
```
Hi Praseodym
For what i undestand the module is present however it cannot be loaded up. (do i need to have internet connected to load the module up)
 here are the msg

```
 modinfo toshiba_acpi
filename:       /lib/modules/2.6.38-11-generic-pae/kernel/drivers/platform/x86/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     2B96A55B68EF349279AE259
alias:          acpi*:TOS1900:*
alias:          acpi*:TOS6208:*
alias:          acpi*:TOS6200:*
depends:        sparse-keymap
vermagic:       2.6.38-11-generic-pae SMP mod_unload modversions 686 

``````

sudo modprobe -v toshiba_acpi

insmod /lib/modules/2.6.38-11-generic-pae/kernel/drivers/platform/x86/toshiba_acpi.ko 
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.38-11-generic-pae/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device

```

---

### Post by praseodym on 2011-10-07
Ok, its the "wrong" one. Try these modules one by one:

[http://wiki.ubuntuusers.de/Baustelle/rfkill#Herstellerspezifisches-Kernelmodul-ist-nicht-geladen](http://wiki.ubuntuusers.de/Baustelle/rfkill#Herstellerspezifisches-Kernelmodul-ist-nicht-geladen)

```
sudo modprobe -v modulename
sudo rfkill unblock all
```
and check after that with

```
rfkill list
iwconfig
lsmod | grep modulename
dmesg | grep modilename
```
If it doesnt work and the module is loaded unload it via

```
sudo modprobe -rf modulename
```
If it is not loaded try the next one.

---

### Post by metrics on 2011-10-07
I have tried all of them, the below didn't throw a fatal error, however it i could not unblock the wireless card. 

[B]fujitsu_laptop
[/B][B]ideapad_laptop
[/B]**msi_laptop**
[B]panasonic_laptop
[/B][B]sony_laptop

How do i  check a module is loaded? 

Iwconfig has never changed from the below. 
[/B]```
 iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     IEEE 802.11bgn  ESSID:off/any             Mode:Managed  Access Point: Not-Associated   Tx-Power=off              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:on
```

---

### Post by praseodym on 2011-10-07
Check also the "_wmi" modules. 

```
lsmod

```
checks all the loaded modules (left column)

---

### Post by metrics on 2011-10-08
I tried all the modules one by one, and all the others are simply not working. Only the  above listed modules can be loaded on my machine. 
This is lsmod list before loading any wireless module. I was wondering if any of the below loaded modules can conflicts with my wireless. 

```
lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          28209  2 
ath9k                 105891  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
i915                  451068  3 
mac80211              259567  1 ath9k
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13797  1 ath9k
ath9k_hw              311106  2 ath9k,ath9k_common
ath                    19147  2 ath9k,ath9k_hw
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              155552  3 ath9k,mac80211,ath
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 i915,drm_kms_helper
uvcvideo               66851  0 
psmouse                59039  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
video                  18951  1 i915
sparse_keymap          13666  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  46630  0 





```

---

### Post by praseodym on 2011-10-08
Just a quick reply (I am getting lost in this thread ;-) ):

Reboot twice, once with the key combination pressed, once with the combination pressed repeatedly during the complete boot time. Check also Fn+F2 with that

---

### Post by praseodym on 2011-10-08
You can also try Acer-Hotkeys for 32bit (not working on 64bit systems! Check with "uname -a"):

[http://forum.ubuntuusers.de/topic/acer-travelmate-291lci-funknetzwerk-nicht-akti/2/#post-2670605](http://forum.ubuntuusers.de/topic/acer-travelmate-291lci-funknetzwerk-nicht-akti/2/#post-2670605)

```
wget https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb
sudo dpkg -i acer*.deb
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential module-assistant debhelper
cd /usr/src
sudo tar -xjf acerhk.tar.bz2 
sudo mv /usr/src/modules/ /usr/src/acerhk-0.5.35/
gksudo gedit /usr/src/acerhk-0.5.35/dkms.conf
```
Insert the following:
```
PACKAGE_NAME=acerhk
PACKAGE_VERSION=0.5.35

DEST_MODULE_LOCATION=/extra
BUILT_MODULE_NAME=acerhk
BUILT_MODULE_LOCATION=acerhk/

MAKE="'make' -C acerhk/ all"
CLEAN="'make' -C acerhk/ clean"
AUTOINSTALL="yes"
```
save and close.

Test:
```
sudo dkms add -m acerhk -v 0.5.35 
```
If it works without error, compile and install:
```
sudo dkms build -m acerhk -v 0.5.35 
sudo dkms install -m acerhk -v 0.5.35 
```
Load the module:
```
sudo modprobe -v acerhk
sudo rfkill unblock all
```

---

### Post by Ramiro Franco on 2011-12-22
I solved this problem using this procedure (I have a Toshiba p755 with a AR9285)

"With the battery and AC adapter removed, close the Power switch for half-a-minute. 
Re-attach  those, press the Power button to turn the computer on, and then  immediately press the F2 key while the Toshiba logo is displayed. Press  F9 to restore the BIOS default settings, press F10, and then select Yes  (Exit Saving Changes). The computer will restart.
                                           "

[http://forums.toshiba.com/t5/Keyboards-Touchpads/Toshiba-Satellite-A665-S6050-Media-buttons-Keyboard-light-not/td-p/129321](http://forums.toshiba.com/t5/Keyboards-Touchpads/Toshiba-Satellite-A665-S6050-Media-buttons-Keyboard-light-not/td-p/129321)

good luck

---

### Post by res_au on 2012-06-02
Fixed the same issue with the X305 X300.

rfkill showed it as hard blocked. after doing the BIOS things, it works perfectly :-)

---

