---
title: "Broadcom Corporation BCM4313 not working on 11.04"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by marutiborker on 2011-08-25
I have checked all the posts written in this ubuntu forum. Tried out my luck with all those things not one worked :(  ( ndiswrapper, wl , bcm etc. etc. )

Also tried all the help posted by [chili55 ]("http://ubuntuforums.org/member.php?u=35909")and some other helpful users. Couldn't get it working at all :(

My laptop is new the wireless worked with broadcom STA drivers in 10.10 but on upgrading to 11.04 it stopped working.  

Here is my output for the following commands

```

 $ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b] 

``````

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: cc:af:78:77:64:85
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f1500000-f1503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:71:57:c3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.172 latency=0 link=yes multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff

``````

$ lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17387  0 
wl                   2568244  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
arc4                   12529  0 
mac80211              294370  0 
cfg80211              178528  1 mac80211
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
nvidia              10709116  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
i915                  515121  2 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72195  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 i915
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
acer_wmi               23809  0 
btusb                  18600  2 
soundcore              12680  1 snd
ideapad_laptop         13494  0 
sparse_keymap          13898  2 acer_wmi,ideapad_laptop
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw              13166  0 
drm                   227534  3 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0

``````

$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:71:57:c3  
          inet addr:192.168.1.172  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe71:57c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59360 errors:0 dropped:3 overruns:0 frame:0
          TX packets:54923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14845122 (14.8 MB)  TX bytes:4463011 (4.4 MB)
          Interrupt:41 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr cc:af:78:77:64:85  
          inet6 addr: fe80::ceaf:78ff:fe77:6485/64 Scope:Link
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
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


``````

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:245
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

``````

$ sudo cat /etc/modprobe.d/blacklist.conf 
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
blacklist brcm80211


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
blacklist ndiswrapper

```Presently it is showing that the wireless is disabled by hardware switch and its not allowing me to connect

```

$ sudo rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```My laptop is lenovo thinkpad Z570 just incase someone was wondering

---

### Post by marutiborker on 2011-08-25
Just in case someone was wondering for the whole lspci out put here it is :- [http://pastebin.com/ddi8t7Ea](http://pastebin.com/ddi8t7Ea)


and some more :- 

```
maruti@hotspace:~$ lsb_release -d
Description:    Ubuntu 11.04
maruti@hotspace:~$ uname -mr
2.6.38-11-generic x86_64
```

```

$ lsusb
Bus 002 Device 005: ID 0489:e00d Foxconn / Hon Hai 
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:58ea Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by praseodym on 2011-08-25
Hi,

take "ndiswrapper" out of the blacklist file and uninstall it completely, otherwise the STA driver makes problems:

```
sudo modprobe -rf ndiswrapper wl
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -v wl
sudo rfkill unblock all
sudo service network-manager restart
```
Check:
```
iwconfig
lsmod
rfkill list
dmesg | egrep 'wl|wmi|radio|switch|kill'
sudo iwlist scan
```

---

### Post by marutiborker on 2011-08-25
I removed ndiswrapper as you said restarted network too. Still shows it as disabled in the drop down. Anyways here is the list you asked for :- 

```
maruti@hotspace:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:245
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

maruti@hotspace:~$ rfkill list
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
7: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
maruti@hotspace:~$ dmesg | egrep 'wl|wmi|radio|switch|kill'
[    1.171614] wmi: Mapper loaded
[   11.778501] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.364757] Console: switching to colour frame buffer device 170x48
[   77.238978] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   77.238988] wl 0000:03:00.0: setting latency timer to 64
[   77.668756] wl 0000:03:00.0: PCI INT A disabled
[   77.669070] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   77.669086] wl 0000:03:00.0: setting latency timer to 64
[ 2927.677075] wl 0000:03:00.0: PCI INT A disabled
[ 3011.699998] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3011.700010] wl 0000:03:00.0: setting latency timer to 64
```

---

### Post by marutiborker on 2011-08-25
One more i think its able to scan but the network dropdown doesnt let me connect to any one :( 

[http://pastebin.com/Dujm0B3k](http://pastebin.com/Dujm0B3k)

---

### Post by marutiborker on 2011-08-25
> **marutiborker said:**
> One more i think its able to scan but the network dropdown doesnt let me connect to any one :( 

[http://pastebin.com/Dujm0B3k](http://pastebin.com/Dujm0B3k)

when i say doesnt let me connect to any one it doesnt even list it in the top network dropdown :(

Also now :- 

```

$  sudo rfkill list all
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
7: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by praseodym on 2011-08-25
Try to add a module parameter to "acer_wmi":

```
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
```
reboot, and
```
sudo rfkill unblock all
```
test it again. If its not working remove the file and blacklist acer_wmi.
```
sudo rm /etc/modprobe.d/acer_wmi.conf
echo "blacklist acewr_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot again.

---

### Post by marutiborker on 2011-08-25
> **praseodym said:**
> Try to add a module parameter to "acer_wmi":

```
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
```reboot, and
```
sudo rfkill unblock all
```test it again. If its not working remove the file and blacklist acer_wmi.
```
sudo rm /etc/modprobe.d/acer_wmi.conf
echo "blacklist acewr_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Reboot again.


I love you ! IT worked. I didnt even need to do unblock all etc. Thanks a lot :)

---

### Post by chili555 on 2011-08-25
"wireless=1" is not a recognized parameter of acer-wmi:```
modinfo acer-wmi
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/acer-wmi.ko
alias:          wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026
alias:          wmi:6AF4F258-B401-42fd-BE91-3D4AC2D7C0D3
alias:          wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB
license:        GPL
description:    Acer Laptop WMI Extras Driver
author:         Carlos Corbacho
srcversion:     C6DC276D3D41A4FAA06CFAE
depends:        sparse-keymap
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)[/COLOR]

```It does no good to load an unknown parameter.

---

### Post by praseodym on 2011-08-25
What was the solution? Parameter or blacklist?

---

### Post by marutiborker on 2011-08-25
> **praseodym said:**
> What was the solution? Parameter or blacklist?
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf



This did it for me. All I had to do was reboot

---

### Post by marutiborker on 2011-08-25
So if I would like to write the steps it would be :-

```

sudo modprobe -rf ndiswrapper wl 
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk 
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a 
sudo modprobe -v wl
sudo rfkill unblock all 
sudo service network-manager restart
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
reboot

```

---

