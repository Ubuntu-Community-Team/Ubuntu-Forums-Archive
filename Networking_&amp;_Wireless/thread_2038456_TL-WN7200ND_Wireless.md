---
title: "TL-WN7200ND Wireless"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by Yunito on 2012-08-06
Hey People, I have Ubuntu installed, but I have one problem, my USB  Inalambric Network Adapter TL-WN7200ND doesn't work in it. I need  drivers for this TP-LINK. Can you help-me? :D

**Ubuntu Version:** 11.10

Thanks!

---

### Post by wildmanne39 on 2012-08-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Yunito on 2012-08-06
Here is netinfo.txt:[PHP]
*************** info trace ****************



**** uname -a ****


Linux Bletka 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"


**** lspci ****


04:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6891]
    Kernel driver in use: rt2800pci
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:100f]
    Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 004: ID 3938:1006  


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


**** lsmod ****


Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_hda_intel          33390  3 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_hwdep              13668  1 snd_hda_codec
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
fglrx                2929009  103 
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              29991  2 snd_seq,snd_pcm
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
jmb38x_ms              17646  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_seq,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
memstick               16569  1 jmb38x_ms
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
binfmt_misc            17540  1 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  2 
libahci                26861  1 ahci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.39
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             80.58.61.250
    DNS:             80.58.61.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Generated by NetworkManager
domain Home
search Home
nameserver 80.58.61.250
nameserver 80.58.61.254


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

blacklist rt2800usb

blacklist rt2x00usb

blacklist rt2x00lib



**** dmesg ****


[    1.158139] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.181690] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.181692] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    2.574516] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.574542] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.574585] r8169 0000:06:00.0: setting latency timer to 64
[    2.574643] r8169 0000:06:00.0: irq 41 for MSI/MSI-X
[    2.575095] r8169 0000:06:00.0: eth0: RTL8168d/8111d at 0xffffc90000c7c000, <MAC address removed>, XID 081000c0 IRQ 41
[   13.248453] r8169 0000:06:00.0: eth0: link down
[   13.269843] wmi: Mapper loaded
[   13.312745] rt2800pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.312757] rt2800pci 0000:04:00.0: setting latency timer to 64
[   13.332706] Registered led device: rt2800pci-phy0::radio
[   13.332979] Registered led device: rt2800pci-phy0::assoc
[   13.333402] Registered led device: rt2800pci-phy0::quality
[   13.469716] type=1400 audit(1344287426.061:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=936 comm="apparmor_parser"
[   13.470146] type=1400 audit(1344287426.061:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=936 comm="apparmor_parser"
[   13.663128] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.935530] r8169 0000:06:00.0: eth0: link up


**************** done ********************[/PHP]

---

### Post by praseodym on 2012-08-06
Hi,

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: [COLOR="Red"]yes[/COLOR]
```
Button/switch/key/key combination? Just turn the card "on". Check also the BIOS settings.

---

### Post by Yunito on 2012-08-06
Adapter is ON, I see that because the light of TP-LINK is ON. But Linux say: The hardware is blocked.

---

### Post by wildmanne39 on 2012-08-06
Hi, first the internal card is probably interfering with the usb adapter plus let's see if it is still blocked post the output of:
```
rfkill list all
``` 
Thanks

---

### Post by Yunito on 2012-08-06
I don't want my internal network card because is old and don't work in my new connection (VDSL) I want my Network USB Adapter because, in windows works OK. Please Say what I have to do.

[PHP]yunito@Bletka:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/PHP]

---

### Post by wildmanne39 on 2012-08-06
Hi please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
then remove:
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```

add:
```
blacklist rt2800pci
```
save, close and reboot.
Make sure the hardware switch is on.
Thanks

---

### Post by Yunito on 2012-08-06
> **wildmanne39 said:**
> Hi please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```then remove:
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```add:
```
blacklist rt2800pci
```save, close and reboot.
Make sure the hardware switch is on.
Thanks

Thanks a lot!!! It works perfect!!!! You're the master!!! :D

---

### Post by wildmanne39 on 2012-08-06
Hi, great please use thread tools and mark the thread solved.
Enjoy

---

