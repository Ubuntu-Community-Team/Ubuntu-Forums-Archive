---
title: "Ubuntu 11.04 wireless troubles"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by MannheimRocket on 2011-09-24
Hey everyone,
I have a nasty problem that I can't seem to solve. Ever since I installed Ubuntu 11.04, my wireless has stopped working properly. Whenever I log in, my wireless connects, but then immediately disconnects. Trying to reconnect fails. Any advice would be greatly appreciated at this point! :)

---

### Post by wildmanne39 on 2011-09-24
Hi, welcome to the forum! please run these commands in a terminal by hitting ctrl+alkt+t then copy and paste the commands into it, then post the results here:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Thanks for the reply! Here you are:
```
dakota@dakota-eMachines-E625:~$ sudo lshw -C network
[sudo] password for dakota: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2c:a3:d2:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.107 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:e5:47:ef
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.112 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0200000-f023ffff ioport:a000(size=128)
``````
dakota@dakota-eMachines-E625:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:23:5A:E5:47:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.112
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth1  [Auto dlink] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        00:24:2C:A3:D2:D9

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *dlink:          Infra, 00:22:B0:D4:20:E4, Freq 2412 MHz, Rate 0 Mb/s, Strength 100

  IPv4 Settings:
    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
``````
dakota@dakota-eMachines-E625:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e003]
    Kernel driver in use: wl
--
05:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0213]
    Kernel driver in use: atl1c
``````
dakota@dakota-eMachines-E625:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:207  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
``````
dakota@dakota-eMachines-E625:~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
dakota@dakota-eMachines-E625:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
radeon                900524  2 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ttm                    65184  1 radeon
snd_seq_midi           13132  0 
drm_kms_helper         40971  1 radeon
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
binfmt_misc            13213  1 
lib80211_crypt_tkip    17203  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm                   184164  4 radeon,ttm,drm_kms_helper
wl                   2642531  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 radeon
sp5100_tco             13456  0 
k8temp                 12872  0 
serio_raw              12990  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
video                  18951  0 
ati_agp                13202  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
pata_atiixp            12968  0 
atl1c                  36237  0 
libahci                25548  1 ahci

```

---

### Post by wildmanne39 on 2011-09-24
Hi, open synaptic and type bcm into the search window then uninstall everything there with a green square by it, then run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Disconnect your wired connection then restart your computer.
Thank you

---

### Post by MannheimRocket on 2011-09-24
No avail. After restarting, the wireless still connects briefly, and then immediately disconnects.

---

### Post by wildmanne39 on 2011-09-24
Hi, post the results of these commands please:
```
lsmod | grep b43
```
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by MannheimRocket on 2011-09-24
[LEFT]Nothing showed up for the first command. Second Command: 
```
dakota@dakota-eMachines-E625:~$ cat /etc/modprobe.d/blacklist.conf
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

```[/LEFT]

---

### Post by wildmanne39 on 2011-09-24
Hi, alright we will get the new driver working and go from there.

Please post the results of this command again, so I can see if the old driver is still loaded.
```
lsmod
```
Thank you

---

### Post by MannheimRocket on 2011-09-24
Hey there. Here it is:
```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
radeon                900524  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40971  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17203  0 
drm                   184164  4 radeon,ttm,drm_kms_helper
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
sp5100_tco             13456  0 
serio_raw              12990  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
video                  18951  0 
shpchp                 32345  0 
ati_agp                13202  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
pata_atiixp            12968  0 
ahci                   21591  2 
atl1c                  36237  0 
libahci                25548  1 ahci

```

---

### Post by wildmanne39 on 2011-09-24
Hi, open synaptic please and type in bcm then take screen shot of synaptic so I can see what you have installed for broadcom.

You can take a screenshot by hitting alt+print screen button, then upload the screenshot by clicking on the paper clip in the reply window.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Here you go:

---

### Post by wildmanne39 on 2011-09-24
Hi, also before you try the other driver you can make sure your routers encryption is set to just wpa2 and not mixed mode or wep.

Also the speed is on b,g,n and not just n, for your card in 11.04 people usually use the b43 it works better.

Also for your wireless to connect you need to unplug your wire connection.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Sorry, I don't quite understand. I'm fairly new to ubuntu, how do I check my router's encryption? And how do I check what the speed is?

---

### Post by wildmanne39 on 2011-09-24
Hi, this is how it works with a lot of routers so try this please:

Type 192.168.0.1 into your web browser and you have to have your wired connection plug into your router, then when the page open for your router settings click on your wireless and you will see security settings click and see what it is set on.

Then make sure mode is set to b,g,n or just b,g if you do not have the option of n.

Also while you are there look at the wireless power setting and make sure that it is at 100 percent.

Then if those do not correct the problem then you need to open synaptic uninstall the one under bcm that says bcmwl kernel source and restart your computer with the wired disconnected.
Thank you

---

### Post by MannheimRocket on 2011-09-24
I uninstalled bcmwl kernel source and rebooted without the wired connection, but the problem still persists.

---

### Post by wildmanne39 on 2011-09-24
Hi, did you get the other things mentioned in my previous post checked?

Please disconnect your wired connection then do this:
```
sudo modprobe b43
```
if it does not connect run these commands please:
```
dmesg | egrep 'b43|firm|eht1|wlan0'
```

---

### Post by MannheimRocket on 2011-09-24
I got nothing from the first command. Here's the second:
```
[    1.527502] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.527514] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   17.562503] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   17.869631] Registered led device: b43-phy0::tx
[   17.869665] Registered led device: b43-phy0::rx
[   17.869698] Registered led device: b43-phy0::radio
[   18.264080] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   23.816919] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.284830] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 1)
[   34.286988] wlan0: authenticated
[   34.287410] wlan0: associate with 00:22:b0:d4:20:e4 (try 1)
[   34.290411] wlan0: RX AssocResp from 00:22:b0:d4:20:e4 (capab=0x421 status=0 aid=4)
[   34.290418] wlan0: associated
[   34.291811] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.316115] ieee80211 phy0: wlan0: No probe response from AP 00:22:b0:d4:20:e4 after 500ms, disconnecting.
[   43.701368] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 1)
[   43.900041] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 2)
[   44.100040] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 3)
[   44.300038] wlan0: authentication with 00:22:b0:d4:20:e4 timed out
[  962.016095] Modules linked in: parport_pc ppdev arc4 snd_hda_codec_realtek snd_hda_intel radeon snd_hda_codec snd_hwdep b43 snd_pcm joydev binfmt_misc snd_seq_midi ttm snd_rawmidi drm_kms_helper mac80211 snd_seq_midi_event snd_seq snd_timer snd_seq_device drm snd cfg80211 psmouse sp5100_tco soundcore k8temp i2c_algo_bit serio_raw shpchp i2c_piix4 snd_page_alloc video ati_agp lp parport ahci pata_atiixp ssb libahci atl1c

```Now my wireless networks aren't even listed. 
Also, Wireless settings looked Ok.

---

### Post by wildmanne39 on 2011-09-24
Hi, I do not know why the old driver is still present.

Do this please: open synaptic and type bcm then uninstall everything there with a green square by it, then restart your computer then run the command in post 4 and watch for errors make sure it installs properly then unplug wired and restart.

What is your encryption set on? and what is speed set on? and is your wireless power at 100 percent or what happened when you checked your router settings?
Thank you

---

### Post by wildmanne39 on 2011-09-24
Hi, if you have not already done what I mentioned in my last post dont, give me a few minutes I am researching your issue.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Oh okay, thanks.

---

### Post by wildmanne39 on 2011-09-24
Hi,
Do this please: open synaptic and type bcm then uninstall everything there with a green square by it, then restart your computer.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then disconnect your wired connection. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Run these commands one at a time please.
Does it work now?
Thank you

---

### Post by MannheimRocket on 2011-09-24
It worked roughly 30 seconds. But like before, It quickly disconnected and I'm unable to reconnect.

---

### Post by wildmanne39 on 2011-09-24
Hi,okay I need to know what is your encryption set on? and what is speed set on? and is your wireless power at 100 percent or what happened when you checked your router settings?
```
lsmod
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
dmesg | egrep 'b43|firm|eht1|wlan0|wl'
```
```
sudo tail -n100 /var/log/syslog
```
Thank you

---

### Post by MannheimRocket on 2011-09-24
```
Module                  Size  Used by
b43                   296610  0 
ssb                    45942  1 b43
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
radeon                900524  2 
arc4                   12473  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 b43
drm_kms_helper         40971  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 radeon,ttm,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 b43,mac80211
psmouse                73312  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
sp5100_tco             13456  0 
serio_raw              12990  0 
k8temp                 12872  0 
video                  18951  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
ati_agp                13202  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
pata_atiixp            12968  0 
libahci                25548  1 ahci
atl1c                  36237  0 

``````
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

``````
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.412 GHz (Channel 1)


``````
[    1.564822] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.564835] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   18.054829] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   18.276805] Registered led device: b43-phy0::tx
[   18.276909] Registered led device: b43-phy0::rx
[   18.277005] Registered led device: b43-phy0::radio
[   18.435778] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   18.435784] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   18.435789] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  149.044634] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  149.044647] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  149.044656] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  186.202980] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[  196.905924] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  196.905953] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[  197.007091] b43-phy1: Broadcom 4312 WLAN found (core revision 15)
[  197.078876] Registered led device: b43-phy1::tx
[  197.079086] Registered led device: b43-phy1::rx
[  197.079218] Registered led device: b43-phy1::radio
[  197.440087] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  202.977332] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  205.637102] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 1)
[  205.639286] wlan0: authenticated
[  205.639730] wlan0: associate with 00:22:b0:d4:20:e4 (try 1)
[  205.645525] wlan0: RX AssocResp from 00:22:b0:d4:20:e4 (capab=0x421 status=0 aid=4)
[  205.645538] wlan0: associated
[  205.647446] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  236.316049] ieee80211 phy1: wlan0: No probe response from AP 00:22:b0:d4:20:e4 after 500ms, disconnecting.
[  237.028025] b43-phy1 ERROR: MAC suspend failed
[  238.441127] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 1)
[  238.640056] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 2)
[  238.840057] wlan0: authenticate with 00:22:b0:d4:20:e4 (try 3)
[  239.040031] wlan0: authentication with 00:22:b0:d4:20:e4 timed out
[  311.008100] Modules linked in: b43 ssb parport_pc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep radeon arc4 snd_pcm snd_seq_midi snd_rawmidi joydev ttm snd_seq_midi_event binfmt_misc snd_seq mac80211 drm_kms_helper snd_timer snd_seq_device drm snd cfg80211 psmouse i2c_algo_bit soundcore sp5100_tco serio_raw k8temp video i2c_piix4 snd_page_alloc shpchp ati_agp lp parport ahci pata_atiixp libahci atl1c [last unloaded: ssb]

``````
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (wlan0/wireless): connection 'Auto dlink' requires no security.  No secrets needed.
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Config: added 'ssid' value 'dlink'
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Config: added 'scan_ssid' value '1'
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Config: added 'key_mgmt' value 'NONE'
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 24 20:32:31 dakota-eMachines-E625 NetworkManager[499]: <info> Config: set interface ap_scan to 1
Sep 24 20:32:34 dakota-eMachines-E625 NetworkManager[499]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): carrier now ON (device state 2)
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Sep 24 20:33:24 dakota-eMachines-E625 kernel: [  305.325843] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) starting connection 'Auto eth0'
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> dhclient started with pid 1949
Sep 24 20:33:24 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 24 20:33:24 dakota-eMachines-E625 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep 24 20:33:24 dakota-eMachines-E625 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep 24 20:33:24 dakota-eMachines-E625 dhclient: All rights reserved.
Sep 24 20:33:24 dakota-eMachines-E625 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 24 20:33:24 dakota-eMachines-E625 dhclient: 
Sep 24 20:33:25 dakota-eMachines-E625 dhclient: Listening on LPF/eth0/00:23:5a:e5:47:ef
Sep 24 20:33:25 dakota-eMachines-E625 dhclient: Sending on   LPF/eth0/00:23:5a:e5:47:ef
Sep 24 20:33:25 dakota-eMachines-E625 dhclient: Sending on   Socket/fallback
Sep 24 20:33:25 dakota-eMachines-E625 dhclient: DHCPREQUEST of 192.168.0.112 on eth0 to 255.255.255.255 port 67
Sep 24 20:33:25 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 24 20:33:28 dakota-eMachines-E625 dhclient: DHCPREQUEST of 192.168.0.112 on eth0 to 255.255.255.255 port 67
Sep 24 20:33:30 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008048] ------------[ cut here ]------------
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008080] WARNING: at /build/buildd/linux-2.6.38/net/sched/sch_generic.c:256 dev_watchdog+0x213/0x220()
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008088] Hardware name: eMachines E625  
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008094] NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008100] Modules linked in: b43 ssb parport_pc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep radeon arc4 snd_pcm snd_seq_midi snd_rawmidi joydev ttm snd_seq_midi_event binfmt_misc snd_seq mac80211 drm_kms_helper snd_timer snd_seq_device drm snd cfg80211 psmouse i2c_algo_bit soundcore sp5100_tco serio_raw k8temp video i2c_piix4 snd_page_alloc shpchp ati_agp lp parport ahci pata_atiixp libahci atl1c [last unloaded: ssb]
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008201] Pid: 1507, comm: firefox-bin Not tainted 2.6.38-11-generic #51~pre201109230902-Ubuntu
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008208] Call Trace:
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008225]  [<c104f9b2>] ? warn_slowpath_common+0x72/0xa0
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008236]  [<c144a813>] ? dev_watchdog+0x213/0x220
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008246]  [<c144a813>] ? dev_watchdog+0x213/0x220
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008255]  [<c104fa83>] ? warn_slowpath_fmt+0x33/0x40
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008265]  [<c144a813>] ? dev_watchdog+0x213/0x220
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008275]  [<c1069371>] ? __queue_work+0xe1/0x360
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008296]  [<f808107f>] ? atl1c_clean_rx_irq.clone.41+0x1cf/0x2b0 [atl1c]
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008310]  [<c105c89b>] ? call_timer_fn+0x2b/0xe0
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008326]  [<c150a07d>] ? _raw_spin_lock+0xd/0x10
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008336]  [<c144a600>] ? dev_watchdog+0x0/0x220
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008345]  [<c105dbd9>] ? run_timer_softirq+0xe9/0x1e0
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008355]  [<c144a600>] ? dev_watchdog+0x0/0x220
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008364]  [<c10566c2>] ? __do_softirq+0x82/0x170
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008373]  [<c1056640>] ? __do_softirq+0x0/0x170
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008379]  <IRQ>  [<c105688d>] ? irq_exit+0x6d/0x80
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008394]  [<c151112b>] ? smp_apic_timer_interrupt+0x5b/0x8a
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008404]  [<c150a929>] ? apic_timer_interrupt+0x31/0x38
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.008412] ---[ end trace f7dec1dcfb2295a5 ]---
Sep 24 20:33:30 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): carrier now ON (device state 7)
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.033366] atl1c 0000:05:00.0: irq 42 for MSI/MSI-X
Sep 24 20:33:30 dakota-eMachines-E625 kernel: [  311.033471] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <warn> Activation (wlan0) failed for access point (dlink)
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <info> Marking connection 'Auto dlink' invalid.
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <warn> Activation (wlan0) failed.
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Sep 24 20:33:31 dakota-eMachines-E625 NetworkManager[499]: <info> (wlan0): deactivating device (reason: 0).
Sep 24 20:33:32 dakota-eMachines-E625 dhclient: DHCPREQUEST of 192.168.0.112 on eth0 to 255.255.255.255 port 67
Sep 24 20:33:32 dakota-eMachines-E625 dhclient: DHCPACK of 192.168.0.112 from 192.168.0.1
Sep 24 20:33:32 dakota-eMachines-E625 dhclient: bound to 192.168.0.112 -- renewal in 241630 seconds.
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info>   address 192.168.0.112
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info>   prefix 24 (255.255.255.0)
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info>   gateway 192.168.0.1
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info>   nameserver '192.168.0.1'
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info>   domain name 'eastlink.ca'
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Scheduling stage 5
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Done scheduling stage 5
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 24 20:33:32 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 24 20:33:32 dakota-eMachines-E625 avahi-daemon[490]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.112.
Sep 24 20:33:32 dakota-eMachines-E625 avahi-daemon[490]: New relevant interface eth0.IPv4 for mDNS.
Sep 24 20:33:32 dakota-eMachines-E625 avahi-daemon[490]: Registering new address record for 192.168.0.112 on eth0.IPv4.
Sep 24 20:33:33 dakota-eMachines-E625 NetworkManager[499]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep 24 20:33:33 dakota-eMachines-E625 NetworkManager[499]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep 24 20:33:33 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) successful, device activated.
Sep 24 20:33:33 dakota-eMachines-E625 NetworkManager[499]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 24 20:33:41 dakota-eMachines-E625 ntpdate[2002]: adjust time server 91.189.94.4 offset 0.000486 sec

```Encryption: WPA
Speed: High
Wireless power: Undetermined.
I'm not sure if this is correct, as it's not very specific, and it does not give me the option to change any of them.

---

### Post by wildmanne39 on 2011-09-24
Hi, it is having trouble with the encryption, what happened when you typed 192.168.0.1 into your web browser did it bring up a page for your router settings? if so you can click through that page and change your settings, I would set it to wpa2 AES. 

There should be like a drop down menu if you click on your encryption in the router set up page, do you understand about typing the 192.168.0.1 into your web browser if not I will explain.

You might want to deactivate watch dog until this is sorted out.

Also you can install wicd if you still can not stay connected after you set encryption to wpa2 only, it is in synaptic and after you install it you need to uninstall network manager but not before.

I would leave wicd as the last resort, also it is a good idea to disable watch dog and encryption for a few minutes and see if your connection issue go away and I think they will, but remember to disconnect you wired connection after you change your encryption and speed to b,g,n.
Thank you

---

### Post by MannheimRocket on 2011-09-24
When I type 192.168.0.1 into the address bar I get a page that says  "login to router". I click Login, there's a tab that says "wireless  settings". On that page, there are multiple wireless setup wizards.  Here's a screenshot. I'm not sure how to change my encryption. Also, could you explain to me what watchdog is, and how to disable it? Thanks so much for bearing with me :P

---

### Post by wildmanne39 on 2011-09-24
Hi, that is a little different then mine, but at the top of the page click on advance and tools and have a look around and see if you see encryption or wireless settings or it might say security settings, then set it to wpa2 AES only of that option is present and speed to g,b,n, or if you still do not see the settings you need you can run the setup wizard that it showed and you should be able to choose all those settings from there.

Never mind on the watch dog it is not what I thought it was, I thought it was like guard dog that is used to limit internet access, like parental controls but it is not so you we are ok there.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Okay, so there are no options to change encryption(security) or wireless settings, and there is nowhere to change to wpa2(I have searched EVERYWHERE,). I'm hesitant to run the setup wizard, as I don't want to screw up my router. Sorry if I'm being a pain, but do you have any other suggestions?

---

### Post by MannheimRocket on 2011-09-24
Nevermind my last post, I found how to switch over to wpa2 AES. however... my original problem still persists.

---

### Post by wildmanne39 on 2011-09-24
Hi, you can try what I mentioned in my previous post and install wicd, refer to the other post on what I said about it.

That is the only idea I have, but I will do some more research and see if I find anything but almost in every case changing the encryption is the answer that works.
Thank you

---

### Post by wildmanne39 on 2011-09-24
Hi, are you trying to connect with the wired connection unplugged?

If so set encryption to off and see if it connects if it does we will go from there.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Hi there. Just did what you said. Same thing is happening. It connects Immediately upon login and then immediately disconnects.

---

### Post by wildmanne39 on 2011-09-24
Please post the results if these commands:
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
cat /etc/network/interfaces
```
The reason we are running some of the commands again is because we have done ran then since we installed the b43 driver.
Thank you

---

### Post by MannheimRocket on 2011-09-24
Here are the outputs:
```
 *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:e5:47:ef
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.112 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0200000-f023ffff ioport:a000(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2c:a3:d2:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-11-generic firmware=478.104 ip=192.168.0.105 link=yes multicast=yes wireless=IEEE 802.11bg

``````
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dlink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:B0:D4:20:E4   
          Bit Rate=12 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:89   Missed beacon:0

``````
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

``````
auto lo
iface lo inet loopback

```

---

### Post by wildmanne39 on 2011-09-24
Hi, most of that looks good, let's look at the firmware, and you say it connects for a few seconds I would like to be able to see the output from this also
```
sudo iwlist scan
```
```
ls /lib/firmware/b43
```
but so far every time the scan is run it shows nothing.
Thank you

---

### Post by MannheimRocket on 2011-09-24
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:D4:20:E4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000040add6bc
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101B0000000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101B0000000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101

``````
ls: cannot open directory /lib/firmware/b43: Permission denied

```

---

### Post by wildmanne39 on 2011-09-24
Hi, with scan finally working, all of that looks good. Click on your internet icon in the top right corner of the screen and make sure your settings for your wireless under edit connections look like mine.

If they do you may want to check in your router settings and and see if your channel is set to auto, also I do not remember did you find the settings in the router and set the speed to b,g,n?
Thank you

---

### Post by MannheimRocket on 2011-09-24
Our settings are identical. And yes, I was able to set the speed to b,g,n.

---

### Post by wildmanne39 on 2011-09-24
Hi, that is good, and if you disconnect your wired connection you still can not stay connected with wireless?

Do you also have windows on this computer, so we will know if the card is going bad? 
Thank you

---

### Post by MannheimRocket on 2011-09-24
That's correct. And no, the only operating system on this computer is Ubuntu 11.04, which I upgraded from 10.10. Wireless worked perfectly in 10.10.

---

### Post by wildmanne39 on 2011-09-24
Hi, I am going to do some more research and see what I come up with, if you want give wicd a try and see if that works, just refer to the post where I told you how to install it.
Thank you

---

### Post by MannheimRocket on 2011-09-25
Okay, So I replaced wicd with network manager, but still the same issue.

---

### Post by wildmanne39 on 2011-09-25
Hi, try this please with the wired connection unplugged:
```
sudo ifconfig wlan0 down
sudo rmmod -f b43
sudo modprobe b43 11n_disable=1
sudo ifconfig wlan0 up
```
Run the codes one at a time and give the connection several seconds to come up.

If this helps we will have to make it permanent.
Thank you

---

### Post by MannheimRocket on 2011-09-25
There was no out put for the first two commands. The second two were as follows:
[B]
sudo modprobe b43 11n_disable=1[/B]
```
FATAL: Error inserting b43 (/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```**sudo ifconfig b43 up**
```
b43: ERROR while getting interface flags: No such device
```However, after running the commands, wireless would connect. But of course, It would then quickly disconnect.

---

### Post by wildmanne39 on 2011-09-25
Hi, that last set of commands did not work because of an error on my part mainly that parameter is not supported with this driver but that is ok, I am sorry about that but it caused no harm.

I am going to ask an expert for help.
Thank you.

---

### Post by chili555 on 2011-09-25
Could you please open Synaptic Package Manager and see if firmware-b43-**lpphy**-installer is installed? Please do so if not. > Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g **LP-PHY** [14e4:4315] (rev 01)Reboot with the ethernet cable detached and let us have a progress report along with:```
dmesg | grep b43
```

---

### Post by MannheimRocket on 2011-09-25
Hi there. firmware-b43-lpphy-installer is installed along with b43-fwcutter.

```
[    1.505677] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.505690] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   12.253256] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.541817] Registered led device: b43-phy0::tx
[   12.541935] Registered led device: b43-phy0::rx
[   12.542055] Registered led device: b43-phy0::radio
[   13.040081] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
```

---

### Post by chili555 on 2011-09-25
There is considerable doubt about this chipset. Some sources say that the STA driver (bcmwl-kernel-source) is correct. Others say b43, ssb and the lp-phy firmware is correct. Some Broadcom chipsets are definitely one or the other. 14e4:4315 is a mystery to me and the Wild Man. For now, let's work with what we have.

Please detach the ethernet cable and try to connect. When it bails out, please run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n25
sudo iwlist wlan0 scan
iwconfig
```Thanks.

---

### Post by MannheimRocket on 2011-09-25
Wireless failed to connect. here are the outputs:

```
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info>   address 192.168.0.105
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info>   prefix 24 (255.255.255.0)
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info>   gateway 192.168.0.1
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info>   nameserver '192.168.0.1'
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info>   domain name 'eastlink.ca'
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Scheduling stage 5
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Done scheduling stage 5
Sep 25 17:02:47 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <warn> Activation (wlan0) failed for access point (dlink)
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> Marking connection 'Auto dlink' invalid.
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <warn> Activation (wlan0) failed.
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): deactivating device (reason: 0).
Sep 25 17:03:07 dakota-eMachines-E625 NetworkManager[459]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1974

``````
wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:D4:20:E4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f2ff28fbd
                    Extra: Last beacon: 984ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101

``````
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by chili555 on 2011-09-25
> (wlan0): IP6 addrconf timed out or failed.This may be a clue. Please click the Network Manager icon and edit connections. Select wireless and edit Auto dlink. Set IPv6 to 'Ignore.' Save, close and try again.

---

### Post by wildmanne39 on 2011-09-25
Hi chili, that is what I thought last night also, so I attached a screenshot showing mine set to ignore and MannheimRocket said his was set just like mine, I guess we will no in a few minutes if it was or not.

---

### Post by MannheimRocket on 2011-09-25
Okay I set it back to ignore. wildmanne, I had it set to ignore lastnight, however I was screwing around earlier today, and must've forgot to set it back to ignore.#-o

---

### Post by wildmanne39 on 2011-09-25
Hi, did it help.
Thank you

---

### Post by MannheimRocket on 2011-09-25
Nope, I still have the problem.

---

### Post by chili555 on 2011-09-25
> <warn> Activation (wlan0) failed for access pointI am looking at this bug report that suggests the problem is wpa_supplicant. [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777)  I am especially interested in posts #27, #32 and following.

Let's try to rule in or rule out that theory. Can you please, just for a few moments, change your pouter's encryption to none and try to connect? Since this is insecure, change back immediately whether you connect or not.

What version of wpa_supplicant are you running?```
wpa_supplicant -v
```May we see:```
cat /usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service
```

---

### Post by MannheimRocket on 2011-09-25
Changing the encryption to none did not help. Here are the outputs you requested:
```
pa_supplicant v0.7.3
Copyright (c) 2003-2010, Jouni Malinen <j@w1.fi> and contributors
```
```
[D-BUS Service]
Name=fi.epitest.hostap.WPASupplicant
Exec=/sbin/wpa_supplicant -u -s
User=root

```

---

### Post by chili555 on 2011-09-25
> wpa_supplicant -u -sThere is a suggestion to remove -s in the bug report I linked:> just a little issue: with NetworkManager (I don't know with wicd) edit (root perms)

/usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service

and remove the "-s" option from the Exec line. Who knows what's the "-s" option of wpa_supplicant? Google doesn't help ...

newly thanks Nils, byeAnd:> Tried Nils' recipe to install 0.6.10 wpa_supplicant, and that broke nm completely until I removed the "-s"
from /usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service as suggested by spanna.

Now connects instantaneously afaict.It's hard to see what difference this might make; -s logs errors to syslog instead of standard output. However, let's try it:```
sudo gedit /usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service
```Change the file to remove -s. Save and close gedit. Reboot. Afterwards, let us see:```
sudo cat /var/log/syslog | grep -e etwork -e wpa | tail -n25
```

---

### Post by MannheimRocket on 2011-09-25
```
Sep 25 18:11:56 dakota-eMachines-E625 NetworkManager[467]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep 25 18:11:56 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 25 18:11:56 dakota-eMachines-E625 NetworkManager[467]: <info> dhclient started with pid 1634
Sep 25 18:11:56 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 25 18:11:56 dakota-eMachines-E625 NetworkManager[467]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   address 192.168.2.16
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   prefix 24 (255.255.255.0)
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   gateway 192.168.2.1
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   hostname 'dakota-eMachines-E625'
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   nameserver '192.168.2.1'
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   nameserver '192.168.2.1'
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info>   domain name 'no-domain-set.aliant'
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Scheduling stage 5
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Done scheduling stage 5
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 25 18:11:59 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 25 18:12:00 dakota-eMachines-E625 NetworkManager[467]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep 25 18:12:01 dakota-eMachines-E625 NetworkManager[467]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep 25 18:12:01 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) successful, device activated.
Sep 25 18:12:01 dakota-eMachines-E625 NetworkManager[467]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

```

---

### Post by wildmanne39 on 2011-09-25
Hi, just wanted to say I am still here, just have not found anything to contribute.

---

### Post by chili555 on 2011-09-25
> <info> Activation ([COLOR="Red"]eth0[/COLOR]) Stage 5 of 5 (IP Configure Commit) complete.Could we see wlan0, please? We know the ethernet connects. Please detach the cable and try again.

I will be away for most of the evening. See you both later.

---

### Post by wildmanne39 on 2011-09-25
Hi, thank you chili555 your help is greatly appreciated.

---

### Post by MannheimRocket on 2011-09-25
Hey guys,
So I've made the decision to revert back to Ubuntu 10.10. I'm having MULTIPLE issues with 11.04, and I don't have the time(Or patience!) to fix them. I want to thank you both for hanging in there and helping me out. You guys are truly awesome!:guitar:
Sorry for bailing out so suddenly! Again, thank you SO much for your efforts.

---

### Post by wildmanne39 on 2011-09-25
Hi, your welcome! we understand, I am sorry we did get it working it was not for a lack of effort though.
Thank you

---

