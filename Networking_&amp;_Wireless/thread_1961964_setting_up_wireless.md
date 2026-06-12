---
title: "setting up wireless"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by bjgar on 2012-04-20
I'm trying to set up my wireless access and I'm having trouble with the bcm sta wireless card driver. I've uninstalled reinstalled everything, searched through countless forums, but I can't figure it out. Please someone help Me

---

### Post by Gone fishing on 2012-04-20
Have you plugged into a wired network to get internet then run ```
sudo apt-get update
``` and then opened the additional drivers application and run that?

---

### Post by sadaruwan12 on 2012-04-20
Please give us more info on your situation a small description is not helping us to understand your problem.

---

### Post by kc1di on 2012-04-20
> **bjgar said:**
> I'm trying to set up my wireless access and I'm having trouble with the bcm sta wireless card driver. I've uninstalled reinstalled everything, searched through countless forums, but I can't figure it out. Please someone help Me

We need a little more information to be able to help. can you go to a terminal and type the following command and post the output here

```
dmesg | grep iwl 
rfkill list 
```

then enter the following and post it also:

```
lspci
```

---

### Post by bjgar on 2012-04-20
No I have no connection, the wired didn't work either. It should all be up to date but I don't know what the app additional drivers is...
As for the outputs you asked for
```
 rfkill list
```  returns 
 ```
0: Dell-wifi: wireless LAN
soft blocked: no
Hard blocked: no
``` 
```
 dmesg | grep iwl
```  returns nothing at all
```
 root@ubuntu:/home/ben# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 0a)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

 
```

---

### Post by anewguy on 2012-04-20
I don't know if this still works or not with 11.10 or 12.04, but try the following in a terminal window and post back if your wireless starts working:

sudo rmmod ssb
sudo modprobe wl



Dave ;)

---

### Post by bkratz on 2012-04-20
> **anewguy said:**
> I don't know if this still works or not with 11.10 or 12.04, but try the following in a terminal window and post back if your wireless starts working:

sudo rmmod ssb
sudo modprobe wl



Dave ;)



Dave the op has a broadcom ethernet card also. Removing ssb temporarily like above, may fix the wireless but probably kill the wired.  Worth a temp try but be careful.

---

### Post by wildmanne39 on 2012-04-20
Hi, since you have no internet connection this should get you going but we may have to blacklist another driver.

Download the b43 zip file from a computer that has internet to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by Ascarletrequiem on 2012-04-20
> **wildmanne39 said:**
> Hi, since you have no internet connection this should get you going but we may have to blacklist another driver.

Download the b43 zip file from a computer that has internet to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Thanks

Thanks so much to you all. The above worked flawlessly!

---

### Post by wildmanne39 on 2012-04-20
Hi, your welcome!
Enjoy

---

### Post by kc1di on 2012-04-21
Glad you got it going :)
enjoy :) When you have a moment could you mark this thread as Solved.

---

### Post by bjgar on 2012-04-21
```
 root@ubuntu:/home/ben# sudo mkdir /lib/firmware/b43
root@ubuntu:/home/ben# sudo cp Desktop/b43/* /lib/firmware/b43
root@ubuntu:/home/ben# sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
root@ubuntu:/home/ben# sudo rmmod -f ssb
ERROR: Removing 'ssb': Resource temporarily unavailable
root@ubuntu:/home/ben# sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
 
```
 
So I tried these commands to no avail, any more insight it data on my system you need, very much appreciated

---

### Post by wildmanne39 on 2012-04-21
Hi, did you put the zip file on your ubuntu desktop?

Did you copy and paste all commands for accuracy?
Thanks

---

### Post by bjgar on 2012-04-21
No that was someone else I still need you I tried the command but it didn't have the desired effect, I'd there more data on my sys that would help?

```
 root@ubuntu:/home/ben# sudo mkdir /lib/firmware/b43
root@ubuntu:/home/ben# sudo cp Desktop/b43/* /lib/firmware/b43
root@ubuntu:/home/ben# sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
root@ubuntu:/home/ben# sudo rmmod -f ssb
ERROR: Removing 'ssb': Resource temporarily unavailable
root@ubuntu:/home/ben# sudo[CODE][] modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
 
```

---

### Post by bjgar on 2012-04-21
I can't copy paste cause I'm working off my phone now. ButI entered them accurately

---

### Post by wildmanne39 on 2012-04-21
Hi, did you put the file on your desktop and then extract it before you ran the commands?

I recommend rebooting and trying again.
Thanks

---

### Post by bjgar on 2012-04-21
Yeah I did exactly what you said, I will try again after work thanks so much for your help and patience

---

### Post by bjgar on 2012-04-22
Well I rebooted and tried again, don't think it worked
```
 root@ubuntu:/home/ben# sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
root@ubuntu:/home/ben# sudo cp Desktop/b43/* /lib/firmware/b43
root@ubuntu:/home/ben# sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
root@ubuntu:/home/ben# sudo rmmod ssb
ERROR: Module ssb is in use by b44
root@ubuntu:/home/ben# sudo nicotine b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
 
```

I don't know if these will help but here you go
 ```
 root@ubuntu:/home/ben# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/ben# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b3:5a:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1067584 (1.0 MB)  TX bytes:1067584 (1.0 MB)

root@ubuntu:/home/ben# 
 
```

---

### Post by wildmanne39 on 2012-04-22
Hi, please reboot then post the output of:
```
iwconfig
lsmod | grep b43
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by bjgar on 2012-04-22
```
 root@ubuntu:/home/ben# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/ben# lsmod | grep b43
b43                   163556  0 
mac80211              205434  1 b43
cfg80211              126528  2 b43,mac80211
led_class               2864  2 b43,sdhci
ssb                    38934  2 b43,b44
root@ubuntu:/home/ben# nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:15:C5:B3:5A:37

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


root@ubuntu:/home/ben# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning. 
``` 

 ```
 root@ubuntu:/home/ben# sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
Apr 22 12:29:01 ubuntu kernel: [80637.419988] b43-phy0: Broadcom 4321 WLAN found
 (core revision 11)
Apr 22 12:29:01 ubuntu kernel: [80637.464086] b43-phy0 ERROR: FOUND UNSUPPORTED PHY 
(Analog 5, Type 4, Revision 1)
Apr 22 12:29:01 ubuntu kernel: [80637.464133] b43: probe of ssb0:0 failed
 with error -95
 
```

---

### Post by wildmanne39 on 2012-04-22
Hi, looking at the output it looks like you most likely are not using a late enough version of the kernel to use this driver but I want to make sure before we switch back to the other driver.

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by bjgar on 2012-04-23
```
 root@ubuntu:/home/ben# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-40-generic #87-Ubuntu SMP Mon Mar 5 20:26:31 UTC 2012 i686 GNU/Linux
root@ubuntu:/home/ben# lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX 
[14e4:170c] (rev 02)
	Kernel driver in use: b44
	Kernel modules: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n 
[14e4:4328] (rev 01)
	Kernel driver in use: b43-pci-bridge

	Kernel modules: ssb
root@ubuntu:/home/ben# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/ben# rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
 
``` 
 ```
 root@ubuntu:/home/ben# lsmod
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
b43                   163556  0 
mac80211              205434  1 b43
cfg80211              126528  2 b43,mac80211
usb_storage            40033  0 
nls_utf8                1069  1 
isofs                  29250  1 
sha256_generic         11191  2 
aes_i586                7268  363 
aes_generic            26863  1 aes_i586
dm_crypt               11331  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_idt      52074  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_idt,snd_hda_intel
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
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
``` ```
 
ricoh_mmc               2923  0 
sdhci_pci               5470  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  15494  1 sdhci_pci
led_class               2864  2 b43,sdhci
dell_laptop             6888  0 
dcdbas                  5422  1 dell_laptop
lp                      7028  0 
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
b44                    25574  0 
i915                  289683  2 
drm_kms_helper         29329  1 i915
ohci1394               26950  0 
drm                   163779  3 i915,drm_kms_helper
ieee1394               81181  1 ohci1394
ssb                    38934  2 b43,b44
mii                     4381  1 b44
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
 
```

---

### Post by wildmanne39 on 2012-04-23
Hi, we need to change drivers, is your wired connection working now? if not make sure it is enabled in the bios because it will be a lot easier to install the driver with the wired working.

Please do:
```
sudo apt-get purge b43-fwcutter firmware-b43-installer
```
Here is a link if you need more help post back.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You need to install the sta driver also known as the wl driver if you do not get the wired connection working then follow the directions for installing the sta driver with no internet.
Thanks

---

### Post by bjgar on 2012-04-23
Still no wired connection but I input your code and followed the directions provided but it didn't seem to do anything, I couldn't figure out how to do it in terminal so I can't post the  output
```
 root@ubuntu:/home/ben# sudo apt-get purge b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer
 
```

---

### Post by wildmanne39 on 2012-04-23
Hi, try this command to get rid of the b43:
```
sudo apt-get purge b43-fwcutter
```
Where exactly are you stuck at installing the wl driver? Did you read the page carefully you do need to put the livecd in the drive but do not boot from it use it to install the driver.
Thanks

---

### Post by bjgar on 2012-04-23
Part two, I seem to have deleted the b43 and I have all the packages it says to install but under step2 it says to activate the sta driver but  it gives me the same error to look at the log file /var/log/jockey.log. Also the b43 driver is still listed under hardware drivers. Would the log file help

---

### Post by wildmanne39 on 2012-04-23
Hi, yes please post the file.
Thanks

---

### Post by bjgar on 2012-04-24
ive attached the file, sorry i was having some trouble posting it for a while it wouldnt let me

---

### Post by wildmanne39 on 2012-04-24
Hi, when you tried to install the wl driver did you have the live cd in the cd drive?

Did you open synaptic click on settings>repositories and put a check by install from cdrom then reload the package list?

Then type bcm in the search window of synaptic and click to install the packages with the ones that have the green square by them in the screenshot?
Thanks

---

### Post by bjgar on 2012-04-24
yes, yes, and yes. the b43 driver is gone now but its still giving the same error message for the sta. heres a screenshot of my package manager

---

### Post by wildmanne39 on 2012-04-24
Hi, now with your livecd in your cdrom go into synaptic and reinstall those 4 packages again then see if it will activate then reboot is it working now?
Thanks

---

### Post by bjgar on 2012-04-24
nope tried activating it rebooting then activating it, still the same message but it seemed to hit the error much quicker in its attempt to ¨download and install¨ heres the log:

---

### Post by wildmanne39 on 2012-04-24
Hi, please try:
```
sudo modprobe wl
```
Thanks

---

### Post by bjgar on 2012-04-24
root@ubuntu:/home/ben# sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
FATAL: Module wl not found.
FATAL: Error running install command for wl
root@ubuntu:/home/ben#

---

### Post by wildmanne39 on 2012-04-24
Hi, please post the output of:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```
```
lsmod
```
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by bjgar on 2012-04-24
```
root@ubuntu:/home/ben# sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
Apr 24 12:08:25 ubuntu dkms_autoinstaller: bcmwl (5.60.48.36+bdcom): Installing module on kernel 2.6.32-41-generic.
Apr 24 12:27:37 ubuntu NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)
Apr 24 12:55:11 ubuntu kernel: [ 1680.989656] usbcore: registered new interface driver rndis_wlan
Apr 24 16:21:29 ubuntu NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)
Apr 24 16:23:49 ubuntu kernel: [  167.522027] usbcore: registered new interface driver rndis_wlan
root@ubuntu:/home/ben# lsmod
Module                  Size  Used by
rndis_wlan             20617  0 
cfg80211              126528  1 rndis_wlan
rndis_host              5756  1 rndis_wlan
cdc_ether               3541  1 rndis_host
usbnet                 14943  3 rndis_wlan,rndis_host,cdc_ether
mii                     4381  1 usbnet
nls_utf8                1069  1 
isofs                  29250  1 
sha256_generic         11191  2 
aes_i586                7268  388 
aes_generic            26863  1 aes_i586
dm_crypt               11331  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52074  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
joydev                  8740  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
sdhci_pci               5470  0 
psmouse                63677  0 
dell_wmi                1793  0 
sdhci                  15494  1 sdhci_pci
dell_laptop             6888  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               3978  0 
led_class               2864  1 sdhci
snd_timer              19130  2 snd_pcm,snd_seq
lp                      7028  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                32635  2 ppdev,lp
dcdbas                  5422  1 dell_laptop
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
usb_storage            40033  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  290035  2 
drm_kms_helper         29329  1 i915
ohci1394               26950  0 
intel_agp              24375  2 i915
drm                   163779  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
ieee1394               81181  1 ohci1394
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
root@ubuntu:/home/ben# cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist wl
blacklist wl
blacklist wl

```

---

### Post by anewguy on 2012-04-25
I think you need to do the following for wildmanne39:

gksudo gedit /etc/modprobe.d/blacklist.conf

go to the end of the file and remove those 3 lines that say:

blacklist wl

save the file , exit the editor and reboot. This will hopefully effectively do what wildmanne39 was trying when he had you try the modprobe a couple of steps back.

Dave ;)

---

### Post by bjgar on 2012-04-25
ok i did that but it still gives the same error upon activation of the driver

---

### Post by alexsaysshoutitout on 2012-04-25
> **wildmanne39 said:**
> Hi, since you have no internet connection this should get you going but we may have to blacklist another driver.

Download the b43 zip file from a computer that has internet to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Thanks

i tryed what you sugested but this is all i got


alex@alex-MacBookPro:~$ sudo mkdir /lib/firmware/b43
alex@alex-MacBookPro:~$ sudo cp Desktop/b43/* /lib/firmware/b43
alex@alex-MacBookPro:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
alex@alex-MacBookPro:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
alex@alex-MacBookPro:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
alex@alex-MacBookPro:~$ sudo modprobe b43


any help ???

---

### Post by wildmanne39 on 2012-04-25
Hi, we also need to blacklist this driver:
```
echo "blacklist rndis_wlan" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
now do:
```
sudo modprobe wl
```
I do not think it will work but it is worth a try.

Is there anyway to take you computer and plug it in to an ethernet connection at a friends house?
Thanks

---

### Post by bjgar on 2012-04-25
well i have a wired internet connaction now so theres that. i dont know if that helps but heres the output of the last code: ```
root@ubuntu:/home/ben# echo "blacklist rndis_wlan" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rndis_wlan
root@ubuntu:/home/ben# sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
FATAL: Module wl not found.
FATAL: Error running install command for wl

```

---

### Post by wildmanne39 on 2012-04-25
Hi, please do:
```
sudo apt-get update
~$ sudo apt-get install --reinstall bcmwl-kernel-source
```
watch for errors, then unplug wired connection and reboot.
Thanks

---

### Post by alexsaysshoutitout on 2012-04-25
> **wildmanne39 said:**
> Hi, we also need to blacklist this driver:
```
echo "blacklist rndis_wlan" | sudo tee -a /etc/modprobe.d/blacklist.conf

```now do:
```
sudo modprobe wl
```I do not think it will work but it is worth a try.

Is there anyway to take you computer and plug it in to an ethernet connection at a friends house?
Thanks

i have it pluged into my router right now

---

### Post by wildmanne39 on 2012-04-25
Hi alexsaysshoutitout, I will be happy to help you if you need it but please start your own thread since you do not have the same device as the OP and you can post a link here.
Thanks

---

### Post by alexsaysshoutitout on 2012-04-25
im not entirely sure how to do that

---

### Post by codingman on 2012-04-25
I used to remember having that problem but i fixed it with something like sudo apt-get install firmware 

Hope this helps! 

Codingman

---

### Post by codingman on 2012-04-25
Oh, you can start a thread at the top of the page. There should be a button that says 'new thread'

---

### Post by bjgar on 2012-04-25
heres the output from those codes looks like its not recognizing my cdrom as a repository. ```
root@ubuntu:/home/ben# sudo apt-get update
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid Release.gpg
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid Release
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/main Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/main Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/restricted Packages
Err cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://archive.ubuntu.com lucid Release.gpg [189B]                       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US   
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com lucid-updates Release.gpg [198B]     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://archive.canonical.com/ lucid/partner Translation-en_US
Hit http://archive.canonical.com lucid Release                       
Get:3 http://archive.ubuntu.com lucid-security Release.gpg [198B]              
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com lucid Release [57.2kB]               
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://archive.canonical.com lucid/partner Sources                       
Hit http://ppa.launchpad.net lucid Release.gpg                               
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release             
Hit http://archive.canonical.com lucid/partner Packages                      
Hit http://ppa.launchpad.net lucid Release                                   
Get:5 http://archive.ubuntu.com lucid-updates Release [57.3kB]               
Hit http://ppa.launchpad.net lucid/main Packages                              
Get:6 http://archive.ubuntu.com lucid-security Release [57.3kB]
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:7 http://archive.ubuntu.com lucid/main Packages [1,386kB]
Get:8 http://archive.ubuntu.com lucid/restricted Packages [6,208B]             
Get:9 http://archive.ubuntu.com lucid/restricted Sources [3,775B]              
Get:10 http://archive.ubuntu.com lucid/main Sources [659kB]                    
Get:11 http://archive.ubuntu.com lucid/multiverse Sources [119kB]              
Get:12 http://archive.ubuntu.com lucid/universe Sources [3,165kB]              
Get:13 http://archive.ubuntu.com lucid/universe Packages [5,448kB]             
Get:14 http://archive.ubuntu.com lucid/multiverse Packages [180kB]             
Get:15 http://archive.ubuntu.com lucid-updates/main Packages [592kB]           
Get:16 http://archive.ubuntu.com lucid-updates/restricted Packages [4,617B]    
Get:17 http://archive.ubuntu.com lucid-updates/restricted Sources [2,194B]     
Get:18 http://archive.ubuntu.com lucid-updates/main Sources [220kB]            
Get:19 http://archive.ubuntu.com lucid-updates/multiverse Sources [5,063B]     
Get:20 http://archive.ubuntu.com lucid-updates/universe Sources [95.5kB]       
Get:21 http://archive.ubuntu.com lucid-updates/universe Packages [263kB]       
Get:22 http://archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]    
Get:23 http://archive.ubuntu.com lucid-security/main Packages [398kB]          
Get:24 http://archive.ubuntu.com lucid-security/restricted Packages [2,855B]   
Get:25 http://archive.ubuntu.com lucid-security/restricted Sources [1,259B]    
Get:26 http://archive.ubuntu.com lucid-security/main Sources [121kB]           
Get:27 http://archive.ubuntu.com lucid-security/multiverse Sources [1,766B]    
Get:28 http://archive.ubuntu.com lucid-security/universe Sources [36.4kB]      
Get:29 http://archive.ubuntu.com lucid-security/universe Packages [121kB]      
Get:30 http://archive.ubuntu.com lucid-security/multiverse Packages [4,558B]   
Fetched 13.0MB in 1min 52s (116kB/s)                                           
W: Failed to fetch cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/home/ben# ~$ sudo apt-get install --reinstall bcmwl-kernel-source
~$: command not found
root@ubuntu:/home/ben# sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libxine1-misc-plugins libxcb-xv0 libxine1-bin libxine1-ffmpeg
  libxcb-shape0 libxcb-shm0 libreadline5 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/895kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 225612 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-41-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-41-generic
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by wildmanne39 on 2012-04-25
Hi, since you have a wired connection now you can uncheck the cdrom in synaptic and the error message will go away.

Try these commands the unplug wired connection and reboot.
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Thanks

---

### Post by westie457 on 2012-04-25
Hi, it looks like you have booted off the LiveCD.

> [COLOR="Red"]root@ubuntu:/home/ben#[/COLOR] sudo apt-get update
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid Release.gpg
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid Release
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/main Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/main Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/restricted Packages
Err cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.3) lucid/restricted Packages
  [COLOR="red"][COLOR="red"]Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/COLOR][/COLOR]

Which is causing the error.

Try to install the driver this way.

1, Boot your machine normally then load the CD into the tray.

2, Click on Places and open anything listed there. If you see anything that looks like **700 MB Filesystem** choose that.

3, Navigate your way through pool > restricted > b > bcmwl and double-click on the .deb file it should then install with Software Centre.

4, Remove the CD and reboot.


You should now have wifi.

If you want to use wildmanne39's instructions make sure you use the first instruction here then use wildmanne39's earlier instructions to add the CD to the sources list

You are in very good hands, wildmanne39 is very good with wireless issues


EDIT: @wildmanne39 did not see your post as was writing mine

---

### Post by bjgar on 2012-04-25
nope still nothing i dont know what the problem is i have all the necessary drivers and packages but it gives the same error message.?? when i did the /pool/restricted/b/ idea it installed (although i think it already was)but under details it said:

---

### Post by anewguy on 2012-04-25
Do you have the build-essential package installed?  I know it's needed for most everything.  Currently I'm not in Ubuntu so I can't check to see if the kernel source is a different package - I suspect it is.

Dave ;)

---

### Post by bjgar on 2012-04-25
yes i do have that package

---

### Post by wildmanne39 on 2012-04-25
Hi, still getting an error for the kernel source not being installed.

Open synaptic type bcm click to remove completely the ones with the greens squares then reboot, open synaptic install the same packages as in the screenshot plus bcmwl-modaliases unplug wired connection and reboot.
Thanks

---

### Post by bjgar on 2012-04-26
Done, still no luck

---

### Post by wildmanne39 on 2012-04-26
Hi, what does this tell us:
```
dmesg | grep wl
```
Thanks

---

### Post by bjgar on 2012-04-26
it didnt do anything lol: 

```
root@ubuntu:/home/ben# dmesg | grep wl
root@ubuntu:/home/ben# 


```

---

### Post by wildmanne39 on 2012-04-26
Hi, post a screenshot of what is installed when you type bcm into synaptic please.
Thanks

---

### Post by bjgar on 2012-04-26
ok here ya go:

and thanks again for your continued help

---

### Post by wildmanne39 on 2012-04-26
Hi, do you still get the error when you try to activate it in restricted drivers?

Does this load the driver now:
```
sudo modprobe wl
```
Thanks

---

### Post by bjgar on 2012-04-26
yes i still get the same error message under sys-admin-hardware drivers
and no all that did was this:
```
root@ubuntu:/home/ben# sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
FATAL: Module wl not found.
FATAL: Error running install command for wl
root@ubuntu:/home/ben# 


```
is there a similar code to load it that has .config?

---

### Post by wildmanne39 on 2012-04-26
Hi that message is not a problem you can ignore it, I think we need to try to get the driver from another source let me see if I can find one.
Thanks

---

### Post by wildmanne39 on 2012-04-26
Hi, there is a bug in that driver for 10.04 I recommend that you upgrade to a newer version of ubuntu to get this card working preferably 12.04.
Thanks

---

### Post by bjgar on 2012-04-26
so i have to download another live cd with 12.04, how do i save my docs and media?

---

### Post by wildmanne39 on 2012-04-26
Hi, I recommend an external hard drive or a flash drive.
Thanks

---

### Post by bjgar on 2012-04-26
ok i will do that and report back

---

### Post by wildmanne39 on 2012-04-26
Hi, ok we may have to still make it work but in 12.04 it should be a lot easier.
Thanks

---

### Post by transistor on 2012-04-28
I wish to confirm Wildmanne39's post (#8 in the thread) for setting up Broadcom B43 driver. I got this to work with a Buffalo WLI-CB-G54A on an old Compaq Evo N610c. (The Evo built-in WiFi doesn't support WPA so it's probably not worth bothering with.)

Thank you.

---

### Post by bjgar on 2012-04-30
well i downloaded 12.04 and its running beautifully, the driver works great wireless is working. thank you so much for all your help i wish i could do more to show my appreciation. thanks again

---

### Post by wildmanne39 on 2012-05-02
Hi, I am glad to hear it is working.
Enjoy

---

### Post by BrooklynDave3 on 2013-02-03
> **Wild Man said:**
> Hi, since you have no internet connection this should get you going but we may have to blacklist another driver.

Download the b43 zip file from a computer that has internet to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

Hi,

I would like to try this but I cannot seem to get the file to actually save to anything and it never "shows in folder", any ideas?  Please, very new to ubuntu but very eager to learn.

David

---

### Post by Bucky Ball on 2013-02-03
@ BroolynDave3: Welcome to the forums. You will greatly improve your chances of help by posting a new thread in ***Networking & Wireless*** rather than burying yourself 70+ posts deep on a solved thread with a title which doesn't relate specifically to your issue and hasn't seen any action for eight months.

Include the output of these two commands:

```
sudo lshw -C network
iwconfig

```
... and as much info as you can think of.

Good luck.

***Thread Closed*** and moved to ***Networking & Wireless***

---

