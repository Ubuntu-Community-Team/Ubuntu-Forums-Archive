---
title: "Upgrade to 12.04... wireless not working..."
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by etfjr on 2013-03-12
I have a Sony VAIO (vgn AR825E).

I finally upgraded to 12.04 and my wireless is not working... (doesn't even acknowledge the wireless adapter is present)...

Wired networking works fine...

Any ideas on how to fix this?  I've looked everywhere I could on Google and even here on the Ubuntu forums and none of the solutions are helping...

Thanks,
Taylor

---

### Post by TK999 on 2013-03-12
Hey, are you using an internal or external adapter? If the former, run
```
lspci
```, if the latter, ```
lsusb
``` from a terminal (Ctrl+Alt+T) and post the result here.

---

### Post by etfjr on 2013-03-12
```
taylor@KA5NOM:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)        
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)       
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)       
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)      
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)                 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)                    
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)                       
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)                       
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)               
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)                 
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)                    
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)                   
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)                                                 
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)                                
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)                           
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)                
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)                                              
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GT] (rev a1)                                        
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)                   
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)                   
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller                                                                          
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller                                              
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

### Post by varunendra on 2013-03-12
> **TK999 said:**
> If the former, run
```
lspci
```
..make it -
```
lspci -nnk | grep -iA2 net
```
.. to let us see the exact id + driver in use (if any).

---

### Post by etfjr on 2013-03-12
```
taylor@KA5NOM:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
        Subsystem: Sony Corporation Device [104d:9016]
        Kernel driver in use: sky2
--
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
        Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
        Kernel driver in use: iwl4965
```

---

### Post by varunendra on 2013-03-12
> **etfjr said:**
> ```

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [**[COLOR="#800000"]8086:4229[/COLOR]**] (rev 61)
        Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
        Kernel driver in use: **[COLOR="#800000"]iwl4965[/COLOR]**
```

Please try -
```
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965 11n_disable=1
```
If it doesn't help, repeat the first command and make the second one -
```
sudo modprobe -v iwl4965 swcrypto=1
```

You can also use both parameters simultaneously -
```
sudo modprobe -v iwl4965 11n_disable=1 swcrypto=1
```

If none of these helps, please follow the 'Wireless Script' link in my signature, do as the linked posts says to do and post back the diagnostics report here.

**PS:**
While posting output codes, please use 'Code' tags, as it preserves formatting and makes the post more readable.
Follow the 'example' link in my signature to see how.

---

### Post by etfjr on 2013-03-12
when running the commands, it get this:
```

taylor@KA5NOM:~$ sudo modprobe -rfv iwl4965
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
rmmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/net/wireless/cfg80211.ko
taylor@KA5NOM:~$ sudo modprobe -v iwl4965 11n_disable=1
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
insmod /lib/modules/3.2.0-38-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko 11n_disable=1
taylor@KA5NOM:~$ sudo modprobe -rfv iwl4965
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
rmmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/net/wireless/cfg80211.ko
taylor@KA5NOM:~$ sudo modprobe -v iwl4965 swcrypto=1
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
insmod /lib/modules/3.2.0-38-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko swcrypto=1


```

here's the output of the wireless script
```


*************** info trace ****************



**** uname -a ****


Linux KA5NOM 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
	Subsystem: Sony Corporation Device [104d:9016]
	Kernel driver in use: sky2
--
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
	Kernel driver in use: iwl4965


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 002 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 005: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
iwl4965               117406  0 
iwl_legacy             71187  1 iwl4965
mac80211              436493  2 iwl4965,iwl_legacy
cfg80211              178877  3 iwl4965,iwl_legacy,mac80211
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252189  4 vboxpci,vboxnetadp,vboxnetflt
snd_hrtimer            12648  1 
sonypi                 19573  0 
dm_crypt               22528  0 
bnep                   17830  2 
parport_pc             32114  0 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm
ppdev                  12849  0 
usblp                  17885  0 
snd_hda_codec_realtek   174313  1 
snd_hda_codec_idt      60251  1 
arc4                   12473  2 
uvcvideo               67203  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
tifm_7xx1              12937  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  3 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
pcmcia                 39826  0 
tifm_core              15040  1 tifm_7xx1
v4l2_common            15793  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
videodev               86588  2 uvcvideo,v4l2_common
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  17 snd_hda_codec_realtek,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96718  0 
soundcore              14635  1 snd
mac_hid                13077  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sony_laptop            39681  0 
firewire_sbp2          18346  0 
serio_raw              13027  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_logitech_dj        18290  0 
usbhid                 41937  1 hid_logitech_dj
hid                    77428  2 hid_logitech_dj,usbhid
firewire_ohci          40180  0 
firewire_core          56940  2 firewire_sbp2,firewire_ohci
crc_itu_t              12627  1 firewire_core
nouveau               708578  2 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197641  4 nouveau,ttm,drm_kms_helper
sky2                   49545  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12893  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19115  1 nouveau


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.147
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.180.42.68
    DNS:             208.180.42.100




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true


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
address 127.0.0.1
netmask 255.0.0.0


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


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


**** dmesg ****


[    1.708786] wmi: Mapper loaded
[   16.675523] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   16.675527] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   16.675624] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.675667] iwl4965 0000:06:00.0: setting latency timer to 64
[   16.675727] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   16.718659] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   16.718704] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.718919] iwl4965 0000:06:00.0: irq 46 for MSI/MSI-X
[   17.311086] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[   18.547127] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   31.261734] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.911729] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[  226.610820] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[  227.862658] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[ 3368.748427] iwl4965 0000:06:00.0: PCI INT A disabled
[ 3386.626394] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[ 3386.626398] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[ 3386.626507] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3386.626551] iwl4965 0000:06:00.0: setting latency timer to 64
[ 3386.626625] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[ 3386.669477] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[ 3386.669504] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 3386.669726] iwl4965 0000:06:00.0: irq 46 for MSI/MSI-X
[ 3386.871763] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[ 3386.872917] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[ 3387.226302] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3401.384561] iwl4965 0000:06:00.0: PCI INT A disabled
[ 3416.940269] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[ 3416.940272] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[ 3416.940379] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3416.940451] iwl4965 0000:06:00.0: setting latency timer to 64
[ 3416.940509] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[ 3416.983452] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[ 3416.983495] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 3416.983661] iwl4965 0000:06:00.0: irq 46 for MSI/MSI-X
[ 3416.986965] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[ 3416.987404] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[ 3417.015481] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************

```



thanks for any help... i'm really lost in all this...
Taylor

---

### Post by varunendra on 2013-03-12
I didn't take a look at the report yet. Just want to confirm first -

Did you try all three variations in a row without giving it any time to get ready?

They were meant to be tried one at a time (**11n_disable=1** *then* **swcrypto=1**), give it a minute or two to get ready, try and see if it connects, if not, only then try the next.

Please try it that way if you didn't and post back if any of them could make a difference.

---

### Post by etfjr on 2013-03-12
Didn't do a thing...

---

### Post by varunendra on 2013-03-12
> **etfjr said:**
> Didn't do a thing...
The worst part is - either there is still no clue of what is causing this, or I am just unable to pick it. So I'm blindly trying whatever I know, and my knowledge too is very little in both scope and depth.

Anyway, before I go to sleep (trying hard, although may not), a few more things to try-
1st, another driver parameter -
```
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl-legacy bt_coex_active=Y
sudo modprobe -v iwl4965 11n_disable=1
```
Speaking of the *bt_coex...* parameter I suggestet above, do you have bluetooth in your laptop? Does it work? Did it ever use to work?

I'm asking because the rfkill output in the script didn't show any radio devices other than the wireless. So I suspect if we have some BIOS setting issue here.
If your lappy isn't UEFI enabled, I suggest you try resetting your BIOS to defaults to see if it helps.

One more thing - make sure your router uses WPA2 only encryption, not WPA/WPA2 mixed mode. I hope you must have already seen that recommendation at many places on the forums. Just double check it.

---

### Post by varunendra on 2013-03-12
Uh.. oh.. just noticed something too obvious -
> **etfjr said:**
> 
```
**** **NetworkManager.state** ****

[main]
NetworkingEnabled=true
**WirelessEnabled=[COLOR="#FF0000"]false[/COLOR]**
WWANEnabled=true
```


The highlighted part suggests to me that the wireless is not enabled in the nm drop down menu. Make sure "Enable Wireless" has a tick mark beside it.

---

### Post by etfjr on 2013-03-13
Here's what I got when i tried that...

I *think* my laptop has bluetooth, but I've NEVER used it, so I don't really know.


```

taylor@KA5NOM:~$ sudo modprobe -rfv iwl4965
[sudo] password for taylor: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
rmmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/iwl4965.ko
rmmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/iwlegacy.ko
rmmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/mac80211.ko
rmmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/cfg80211.ko
taylor@KA5NOM:~$ sudo modprobe -v iwl-legacy bt_coex_active=Y
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
insmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/cfg80211.ko 
insmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/mac80211.ko 
insmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko bt_coex_active=Y
FATAL: Error inserting iwl_legacy (/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko): Invalid argument
taylor@KA5NOM:~$ sudo modprobe -v iwl4965 11n_disable=1
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.backup, it will be ignored in a future release.
insmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/iwlegacy.ko 
insmod /lib/modules/3.2.0-38-generic/updates/cw-3.6/iwl4965.ko 11n_disable=1
taylor@KA5NOM:~$ 

```

---

### Post by etfjr on 2013-03-13
I can't find a tick box anywhere for this.  There's no networking icon in the system tray and when I go in to the Settings menu, it says I must click the Administrator button, but it's greyed out...

UGH...
Taylor

---

### Post by etfjr on 2013-03-13
> **varunendra said:**
> Uh.. oh.. just noticed something too obvious -


The highlighted part suggests to me that the wireless is not enabled in the nm drop down menu. Make sure "Enable Wireless" has a tick mark beside it.

OK... out of desperation, I did a direct edit of this file and changed the value to true and did a reboot... now all is working fine with the wireless connection (I'm wireless right now...)

There's still no (wireless) networking icon in the system tray, but that seems minor right now...
Taylor

---

### Post by varunendra on 2013-03-14
> **etfjr said:**
> OK... out of desperation, I did a direct edit of this file and changed the value to true and did a reboot... now all is working fine with the wireless connection (I'm wireless right now...)
Great!
Lesson to myself : Never ignore minor or the obvious!

By the way, aren't you the first user on the installation (admin)?

Sometimes in my laptop, the nm-applet menu becomes unresponsive (*[COLOR="#696969"]"..click me anywhere you like, I won't do a thing.."[/COLOR]* type), in that case, I simply kill it from System Monitor, then run it again with-

Alt+F2 > nm-applet

Although the proper way is -
```
sudo service network-manager restart
```
or
```
sudo service networking restart
```
..but these don't work for me, only killing > starting again does.

---

