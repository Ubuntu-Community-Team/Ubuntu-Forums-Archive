---
title: "Aspire 3690 - WI Network problem."
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by VanderJoker on 2013-05-10
Well. I have instal ubutu on my Acer 3690, and now i cannot connect, please i need some help thank you for the atension.

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:19 memory:d0000000-d0003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:d0100000-d0101fff

I hope this can help.

---

### Post by wildmanne39 on 2013-05-10
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by VanderJoker on 2013-05-11
Hi there thank you for replying. i did all the thing that you mention but it doesnt work.

heres the code that appear.

E: Not possible to find packet broadcom-sta-common
E: Not possible to find packet broadcom-sta-source
fabio@fabio-Aspire-3690:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
fabio@fabio-Aspire-3690:~$ sudo cp Desktop/b43/* /lib/firmware/b43
cp: cannot stat `Desktop/b43/*': No such file or directory
fabio@fabio-Aspire-3690:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
fabio@fabio-Aspire-3690:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': Device or resource busy
fabio@fabio-Aspire-3690:~$ sudo modprobe b43

but in the meanwhile thanks for the help.

---

### Post by VanderJoker on 2013-05-11
fabio@fabio-Aspire-3690:~$ lsusb
Bus 001 Device 006: ID 13fe:4100 Kingston Technology Company Inc. 
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fabio@fabio-Aspire-3690:~$ sudo lshw -C nework
[sudo] password for fabio: 
fabio@fabio-Aspire-3690:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:19 memory:d0000000-d0003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:d0100000-d0101fff

---

### Post by wildmanne39 on 2013-05-11
Hi, did you copy and paste each command one line at a time for accuracy?
wl driver is there so the purge command should have found it.
Thanks

---

### Post by VanderJoker on 2013-05-11
Hi, yes i copyed and pasted each command for accuracy.
At first ctrl + alt + t then i copyed/pasted 

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

then i downloaded b43.zip to my desktop then i extract here

then 

ctrl + alt+ t

copy/ paste 
sudo mkdir /lib/firmware/b43
enter
copy/paste
sudo cp Desktop/b43/* /lib/firmware/b43
enter...
and so on

and the result are

E: Not possible to find packet broadcom-sta-common
E: Not possible to find packet broadcom-sta-source
fabio@fabio-Aspire-3690:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
fabio@fabio-Aspire-3690:~$ sudo cp Desktop/b43/* /lib/firmware/b43
cp: cannot stat `Desktop/b43/*': No such file or directory
fabio@fabio-Aspire-3690:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
fabio@fabio-Aspire-3690:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': Device or resource busy
fabio@fabio-Aspire-3690:~$ sudo modprobe b43

thanks for the help

---

### Post by wildmanne39 on 2013-05-11
Hi, please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo modprobe -rfv wl
sudo modprobe -rfv ssb
sudo modprobe -v b43
```
Thanks

---

### Post by VanderJoker on 2013-05-11
hi thanks for the help.

the result of the code are:

insmod /lib/modules/3.5.0-23-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/b43/b43.ko

on the top-rigth wi icon appeared VPN Connections
do i need to do something else?
thanks for the help

---

### Post by wildmanne39 on 2013-05-11
In that icon do you see a check by enable networking and one by wireless?
Do you see the network you want to connect too?
Thanks

---

### Post by VanderJoker on 2013-05-12
hi, the enable networking is checked but the wireless one does not appear.
So I cant see the network that i want to connect.
Thanks again

---

### Post by wildmanne39 on 2013-05-12
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by VanderJoker on 2013-05-12
hi, here you go.


*************** info trace ****************



**** uname -a ****


Linux fabio-Aspire-3690 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel modules: wl, ssb
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Kernel modules: b44


**** lsusb ****


Bus 001 Device 007: ID 13fe:4100 Kingston Technology Company Inc. 
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12618  1 
usb_storage            39720  1 
uas                    17745  0 
rfcomm                 38104  0 
bnep                   17791  2 
parport_pc             32115  0 
bluetooth             189585  10 rfcomm,bnep
ppdev                  12850  0 
snd_hda_codec_realtek    64876  1 
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
coretemp               13362  0 
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
acer_wmi               27975  0 
joydev                 17394  0 
snd_seq_midi           13133  0 
sparse_keymap          13659  1 acer_wmi
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
pcmcia                 39855  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
i915                  470823  3 
snd_timer              28932  2 snd_pcm,snd_seq
microcode              18396  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27465  0 
drm_kms_helper         47459  1 i915
psmouse                91022  0 
pcmcia_rsrc            18368  1 yenta_socket
serio_raw              13032  0 
drm                   240232  4 i915,drm_kms_helper
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18745  1 acer_wmi
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                16993  0 
soundcore              14636  1 snd
i2c_algo_bit           13317  1 i915
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
mac_hid                13078  0 
video                  19070  2 acer_wmi,i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid


**** nm-tool ****



NetworkManager Tool

State: disconnected



**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


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

# replaced by b43 and ssb.
blacklist bcm43xx

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
blacklist wl


**** dmesg ****


[   13.325160] wmi: Mapper loaded
[   14.135329] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.164194] acer_wmi: Function bitmap for Communication Device: 0x21
[   43.177753] type=1400 audit(1368378732.602:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1539 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************

thanks

---

### Post by VanderJoker on 2013-05-15
hello,
Is this what you wanted????? Or there isnt any solution for my problem.....
thanks

---

### Post by wildmanne39 on 2013-05-15
Hi, I am sorry I am very sick at the moment and have been unable to find an answer for issue.

---

### Post by VanderJoker on 2013-05-15
Thanks for the reply, get well soon!!!!

---

### Post by VanderJoker on 2013-05-23
hello there, i hope you are already better, so any news about my problem? Can you fix it?

---

