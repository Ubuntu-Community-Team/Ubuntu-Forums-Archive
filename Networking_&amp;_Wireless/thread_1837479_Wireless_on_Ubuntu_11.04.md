---
title: "Wireless on Ubuntu 11.04"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by bineye on 2011-09-01
Hello, I spent a few hours trying numerous tutorials, running terminal commands, altering files, and am still bamboozled as to why my wireless won't work.
I just installed Ubuntu 11.04 on my Fujitsu Siemens Amilo Li 2727, after my installed version of Vista became badly corrupted after a nasty fall. The wireless manager was always run by pressing Fn and F1 together after Windows loaded, and this cannot be done on the new system. The tutorials I have found and tried to date have all been outdated, for slightly different versions of the FS laptops, or different (earlier) versions of Ubuntu, and as such some files are missing and not in this package.

I am completely new to Ubuntu and if its something simple like "install the missing acerhk file", could someone please tell me the shell command for doing this. My years of Windows usage has left me brain dead to this new technology, however I still feel like a kid at Christmas looking at my Ubuntu software. It appears to be better than Vista already, before Internet access (but what isn't, right?)

Any help would be appreciated. Thanks :)

---

### Post by nm_geo on 2011-09-01
Welcome to the forum.. 
Are you able to connect your Natty 11.04 with ethernet cable?
Have you updated and upgraded if ethernet cable connects? 

Open a terminal - Ctrl-Alt-T works in Natty usually

The following commands can be copied and pasted in terminal.. Then copy and paste the result in thread.

```
lspci -nn | grep 0280

```That should identify wireless card.

```
lsmod
```That will tell us drivers and modules that are loaded.

```
sudo lshw -C network
```That one tells more info on network,drivers and firmware. 

```
rfkill list all
```Hard wire switch that enable/disables Wifi 

There are many more those will get us going.

---

### Post by bineye on 2011-09-04
Hi thanks for your reply. I could not connect via cable, so I ran the reports.

lspci -nn
```
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 

```

lsmod
```
Module                  Size  Used by 
parport_pc             32111  0  
ppdev                  12849  0  
snd_hda_codec_realtek   255820  1  
joydev                 17322  0  
binfmt_misc            13213  1  
arc4                   12473  2  
snd_hda_intel          24140  2  
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel 
i915                  450944  3  
snd_hwdep              13274  1 snd_hda_codec 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0  
snd_rawmidi            25269  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
acer_wmi               23123  0  
sparse_keymap          13666  1 acer_wmi 
ath5k                 144412  0  
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
drm_kms_helper         40745  1 i915 
drm                   180037  4 i915,drm_kms_helper 
ath                    19141  1 ath5k 
mac80211              257001  1 ath5k 
snd_timer              28659  2 snd_pcm,snd_seq 
psmouse                73312  0  
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              156212  3 ath5k,ath,mac80211 
i2c_algo_bit           13184  1 i915 
serio_raw              12990  0  
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
video                  18951  1 i915 
soundcore              12600  1 snd 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
lp                     13349  0  
parport                36746  3 parport_pc,ppdev,lp 
hid_a4tech             12590  0  
usbhid                 41704  0  
hid                    77084  2 hid_a4tech,usbhid 
ahci                   21591  2  
libahci                25548  1 ahci 
r8169                  42534  0  

```

sudo lshw -C network
```
*-network                
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:1f:16:00:43:4b 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:42 ioport:2000(size=256) memory:f6000000-f6000fff memory:f0000000-f001ffff 
  *-network DISABLED 
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: wlan0 
       version: 04 
       serial: 00:16:44:e1:4b:f7 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg 
       resources: irq:18 memory:fa000000-fa00ffff 

```

rfkill list all
```

0: acer-wireless: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: no 

```

---

### Post by wildmanne39 on 2011-09-04
Hi, try this please if it works we will need to blacklist it to make it persistent.
```
sudo rmmod -f acer-wmi 
```
if it does not work post the results of these commands.
```
lspci -nn | grep -e 0280 -e 0200
```
```
nm-tool
```
```
sudo iwlist scan
```
```
dmesg | grep wlan0
```
```
dmesg | grep ath
```
```
lsmod | grep ath
```
Make sure you unplug your wired connection before you run the first command and do not restart your computer after you run it.
Thank you

---

### Post by bineye on 2011-09-04
Hi, thanks for the reply. Sorry I am a bit slow, but Linux is a brand new concept to me :(
Hoping to get started soon.
Here's the results I got:

lspci -nn | grep -e 0280 -e 0200
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01) 
08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 04) 

```

nm-tool
```
NetworkManager Tool 
 
State: disconnected 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            r8169 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1F:16:00:43:4B 
 
  Capabilities: 
    Carrier Detect:  yes 
    Speed:           10 Mb/s 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            ath5k 
  State:             unavailable 
  Default:           no 
  HW Address:        00:16:44:E1:4B:F7 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points  

```

sudo iwlist scan
```
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Network is down 

```

dmesg | grep wlan0
```
DID NOT RETURN ANY RESULTS.
```

dmesg | grep ath
```
[    0.962054] device-mapper: multipath: version 1.2.0 loaded 
[    0.962057] device-mapper: multipath round-robin: version 1.0.0 loaded 
[   13.044223] ath5k 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[   13.044240] ath5k 0000:08:00.0: setting latency timer to 64 
[   13.044297] ath5k 0000:08:00.0: registered as 'phy0' 
[   13.556337] ath: EEPROM regdomain: 0x30 
[   13.556341] ath: EEPROM indicates we should expect a direct regpair map 
[   13.556344] ath: Country alpha2 being used: AM 
[   13.556346] ath: Regpair used: 0x30 
[   13.652591] Registered led device: ath5k-phy0::rx 
[   13.652870] Registered led device: ath5k-phy0::tx 
[   13.652891] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```

lsmod | grep ath
```
ath5k                 144412  0  
ath                    19141  1 ath5k 
mac80211              257001  1 ath5k 
cfg80211              156212  3 ath5k,ath,mac80211 

```

---

### Post by wildmanne39 on 2011-09-04
Hi, did you run this command
```
sudo rmmod -f acer-wmi
```
before you ran the others?
and was your wired connection unplugged and you did not restart your computer right?
Thank you

---

### Post by bineye on 2011-09-04
I did run this first, and no I did not restart. Thanks.

EDIT: Yes, the ethernet cable was removed because I couldn't connect via it either, so I didn't see any need for it to be connected any further. :)

---

### Post by praseodym on 2011-09-04
Hello,

for [COLOR="Red"]F[/COLOR]ujitsu [COLOR="Red"]S[/COLOR]iemens [COLOR="Red"]Am[/COLOR]ilo you can load a special module for the radio kill switch:

```
sudo modprobe -v fsam7400 radio=1
sudo rfkill unblock all
sudo service network-manager restart
```

Check:

```
dmesg | egrep 'ath|radio|switch|firm'
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by bineye on 2011-09-04
Hi, thanks for the reply. This did not appear to solve the problem. I'll list what I got.

sudo modprobe -v fsam7400 radio=1
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release. 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save.1, it will be ignored in a future release. 
WARNING: /etc/modprobe.d/blacklist.conf.save line 57: ignoring bad line starting with '^X' 
insmod /lib/modules/2.6.38-8-generic/kernel/ubuntu/fsam7400/fsam7400.ko radio=1 

```

sudo service network-manager restart
```
network-manager start/running, process 4169
```

dmesg | egrep 'ath|radio|switch|firm'
```
[    0.962054] device-mapper: multipath: version 1.2.0 loaded 
[    0.962057] device-mapper: multipath round-robin: version 1.0.0 loaded 
[   13.044223] ath5k 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[   13.044240] ath5k 0000:08:00.0: setting latency timer to 64 
[   13.044297] ath5k 0000:08:00.0: registered as 'phy0' 
[   13.556337] ath: EEPROM regdomain: 0x30 
[   13.556341] ath: EEPROM indicates we should expect a direct regpair map 
[   13.556344] ath: Country alpha2 being used: AM 
[   13.556346] ath: Regpair used: 0x30 
[   13.652591] Registered led device: ath5k-phy0::rx 
[   13.652870] Registered led device: ath5k-phy0::tx 
[   13.652891] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70) 
[   14.100065] Console: switching to colour frame buffer device 160x50 
[ 4292.174257] fsam7400: SW RF kill switch for Fujitsu Siemens Amilo M 7400 / Maxdata 7000DX, v0.5.2 

```

rfkill list
```
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: yes 

```

iwconfig
```
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 

```

sudo iwlist scan
```
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Network is down 

```

---

### Post by wildmanne39 on 2011-09-04
Hi, it is hard blocked which means the switch is off try fn plus all the f keys and see if you can turn it on, if not look to see if there is a button or a switch on the lap top.

You can also try
```
rfkill unblock wifi
``` 
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
```
rfkill list All
```
Thank you

---

### Post by bineye on 2011-09-04
The FN + f produced nothing, still greyed out in the menu.
After the first two commands, I typed:
sudo ifconfig wlan0 up
```
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

rfkill list all
```
1: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: yes

```

Thanks.

---

### Post by wildmanne39 on 2011-09-04
Hi, restart your computer and run the commands in post 10 again, I am going to do some research while I wait.
Thank you

---

### Post by bineye on 2011-09-04
Ok I did that, and the phy0 still shows Hard blocked: yes

---

### Post by bineye on 2011-09-04
I was on the Fujitsu website and there is a BIOS for making the WiFi switch being on from boot. Only thing is, I never installed one of these either. Does anyone know how to do this? Thanks.

---

### Post by wildmanne39 on 2011-09-04
You can check your bios  when you start your computer watch the screen and it will tell what key to use to enter bios, it might say enter setup, then you check all settings in there.
Thank you

---

### Post by wildmanne39 on 2011-09-04
Hi, try this please if it works we will make it peristent and do not restart your computer after you run the command.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```
Thank you

---

### Post by bineye on 2011-09-04
I ran these commands and after "... wlan0 up" it says 
```
Operation not possible due to RF-kill
```

---

### Post by wildmanne39 on 2011-09-04
Hi, have a look here it may fix the problem of the hard block.

Start with post 10 and follow it to the end.
[http://ubuntuforums.org/showthread.php?t=1745317#10](http://ubuntuforums.org/showthread.php?t=1745317#10)
Thank you

---

### Post by nm_geo on 2011-09-04
> **wildmanne39 said:**
> Hi, have a look here it may fix the problem of the hard block.

Start with post 10 and follow it to th end.
[http://ubuntuforums.org/showthread.php?t=1745317#10](http://ubuntuforums.org/showthread.php?t=1745317#10)
Thank you

Good find wildmanne chili555 gave them a permanent fix in message 12

---

### Post by bineye on 2011-09-05
Hi.
So I tried this and it worked the first time. However I entered my network details, and it said Authentication Required, despite the fact I had the correct details in, then when I closed this, the network switch was blocking the wifi again and the procedure was no longer working from that post. The switch was blocked even when restarting again, and running the same commands.

Would starting with a fresh install of Ubuntu make any difference? In my earlier attempts to solve the problem, I may have altered some system files through instructions I got from Googling.

---

### Post by praseodym on 2011-09-05
Please show:

```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist.conf.save
cat /etc/modprobe.d/blacklist.conf.save.1
```

Maybe a BIOS reset works for you.

---

### Post by bineye on 2011-09-05
cat /etc/modprobe.d/blacklist.conf
```
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

```

cat /etc/modprobe.d/blacklist.conf.save
```
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
voyeur@voyeur-AMILO-Li-2727:~$ cat /etc/modprobe.d/blacklist.conf.save 
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
blacklist acer wmi 
^X 

```

cat /etc/modprobe.d/blacklist.conf.save.1
```
# This file listsse modules which we don't want to be loaded by 
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

```

---

### Post by praseodym on 2011-09-05
Remove those backuped files:

```
sudo rm /etc/modprobe.d/blacklist.conf.save
sudo rm /etc/modprobe.d/blacklist.conf.save.1
```
and blacklist acer_wmi inside of the "real" file:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
reboot to check.

---

### Post by bineye on 2011-09-05
Thanks for the reply. The "Enable Wireless" is still blocked by hardware switch though. Any further suggestions, or is a re-installation going to have to be done?

---

### Post by wildmanne39 on 2011-09-05
Hi, also you did the procedure in post 12 on that link I gave you by chili555 correct?
Thank you

---

### Post by bineye on 2011-09-05
Yes I did. I did this after the post 10 worked. After it failed to connect to the network, I rebooted, and as it was greyed out I removed it again and tried it without. Neither has worked. :/

---

### Post by wildmanne39 on 2011-09-05
Hi, it is strange that it came on then went back off maybe something else happened.

Please copy the contents of this command here:
```
cat /etc/rc.local
```
Thank you

---

### Post by praseodym on 2011-09-05
> **wildmanne39 said:**
> Hi, it is strange that it came on then went back off maybe something else happened.

Please copy the contents of this command here:
```
cat /etc/rc.local
```
Thank you

plus:

```
cat /etc/modules
```

please.

---

### Post by bineye on 2011-09-05
rc.local has just ```
exit 0
```
and modules ```
lp
``` in addition to the comments of course

---

### Post by wildmanne39 on 2011-09-05
Hi, that is what I was hoping for go to the link I gave you and in post 12 again do what chilli555 says and edit that file then save.
Thank you

---

### Post by bineye on 2011-09-05
Still the same :/

---

### Post by wildmanne39 on 2011-09-05
Hi praseodym, I did not notice at first but chili555 used sudo when he should have used gksu here
> sudo gedit /etc/rc.local
do you think it caused it to be owned by root and do you know how to check for that?
Thank you

---

### Post by bineye on 2011-09-05
Well if this is the case, would a fresh install be the best thing to do? It would not be a problem as the very first thing I did when I installed was to try and figure out the wifi problem, so I have no further files that I fear losing.

---

### Post by praseodym on 2011-09-05
If you use "sudo" instead of "gksu" or "gksudo" (both with GNOME, XFCE or LXDE) or "kdesudo" with KDE with [COLOR="Red"]graphical programs[/COLOR] (like editors, etc.), respectively, you change the owner rights to "root" instead of those of the "sudo"-user. This can make your system unstable.

---

### Post by wildmanne39 on 2011-09-05
Hi, it is most likely that the sudo command did not effect your system at all, it is only in a few cases that it does, and since other people in that link use that command and reported it worked I doubt that it caused problems.

However if you want to reinstall and start over you can I do not know that if it will help or not but I am out of ideas.

I am sorry about that.
Thank you

---

### Post by bineye on 2011-09-08
Yeah update on this. Probably a tip for anyone else that encounters this problem. 
So I gave up on Ubuntu and went and got Windows 7, and the same thing happened, WiFi was not connectable. After re-installing the drivers, still nothing, then I stumbled across the root of the problem, and probably why it was blocked for Ubuntu too.
When Ubuntu was installed, the system disabled the wifi right from the hardware, so if anyone has this problem, do this:
When the computer starts up (shows the Fujitsu Siemens screen), press F2. On the menu, in one of the tabs it will say "Wireless Device" or similar. Mine's was set to disabled, change to enabled and you should be good to go. 

Hope this help anyone who comes across this bizarre problem. Thanks to wildmanne39, praseodym and nm_geo for being so patient. Thanks guys!

---

### Post by wildmanne39 on 2011-09-08
Hi, I am very glad that you have it working and thank you for sharing your solution.

---

