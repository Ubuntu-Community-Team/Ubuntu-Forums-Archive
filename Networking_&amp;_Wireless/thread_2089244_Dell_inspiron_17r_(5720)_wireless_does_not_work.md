---
title: "Dell inspiron 17r (5720) wireless does not work"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by khaj_vah on 2012-11-28
Hello guys,

Just installed ubuntu 12.10 on my dell inspiron 17r but the wireless does not work. When i got this computer, it had ubuntu preinstalled and everything worked fine, (a year ago maybe, i changed everything since then). Now, the bluetooth works but the wifi doesn't.
Here is a link of windows driver (might help): [http://www.dell.com/support/drivers/us/en/19/DriverDetails/Product/inspiron-17r-5720?driverId=WTD28&fileid=2969488887I](http://www.dell.com/support/drivers/us/en/19/DriverDetails/Product/inspiron-17r-5720?driverId=WTD28&fileid=2969488887I) have tried to follow this link [http://forums.fedoraforum.org/showthread.php?p=1605451#post1605451](http://forums.fedoraforum.org/showthread.php?p=1605451#post1605451)  but after i did everything (some different things bc it is not fedora), my system crashed and i had to reinstall ubuntu.

Please help me guys,
Thanks in advance.

---

### Post by wildmanne39 on 2012-11-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by khaj_vah on 2012-11-28
First, sorry for lte reply.
Second, the script wasn't working so i ran all the commands manually and write in a file with same name.
check out..

```
Linux khajvah-Inspiron-5720 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

-->cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


-->lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0565]
    Kernel driver in use: r8169


-->lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:644b Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 

-->iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

-->rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


-->lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_idt      70209  1 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14438  1 dell_laptop
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
microcode              22803  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
uvcvideo               76749  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
btusb                  18334  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
bluetooth             209199  22 rfcomm,bnep,btusb
psmouse                95552  0 
serio_raw              13215  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                17061  0 
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i915                  520519  3 
nouveau               895609  0 
ttm                    83595  1 nouveau
mei                    40690  0 
mxm_wmi                12979  1 nouveau
drm_kms_helper         46784  2 nouveau,i915
drm                   275528  6 nouveau,i915,ttm,drm_kms_helper
i2c_algo_bit           13413  2 nouveau,i915
wmi                    19070  3 dell_wmi,nouveau,mxm_wmi
video                  19335  2 i915,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
r8169                  61650  0 

-->nm-tool
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        84:8F:69:D3:BE:D6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


-->cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


-->cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

-->cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

-->cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

-->[ -t 0 ] && sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

-->[ ! -t 0 ] && gksudo iwlist scan
NOTHING HERE

-->cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

-->cat /etc/modprobe.d/blacklist.conf
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


-->dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
[   15.327933] wmi: Mapper loaded




```

I hope this will help :)

---

### Post by wildmanne39 on 2012-11-28
Hi, here is the link in need.
[http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)
Thanks

---

### Post by khaj_vah on 2012-11-29
Thanks for help but I can not install the package. It says: "Building only for 3.5.0-17-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
"
so i cant modprobe the module ...

---

### Post by khaj_vah on 2012-11-29
Nevermind, I installed this: [http://packages.ubuntu.com/quantal/linux-headers-generic](http://packages.ubuntu.com/quantal/linux-headers-generic) package now everything works fine...\

THANK YOU VERY MUCH, YOU SAVED ME FROM WINDOWS :)

---

### Post by da_g_bomb on 2013-01-15
Solution worked for me, I now have wireless networks appearing in my network list, thanks

---

### Post by riezz on 2013-03-05
In my case after all this wifi is now enabled but i see no networks.

I'm using kubuntu 12.10.

---

