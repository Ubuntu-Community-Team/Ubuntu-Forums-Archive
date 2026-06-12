---
title: "No internet Access on Ubuntu 12.04"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by tr0m4n on 2013-03-15
Hello everybody,

I have switched from Fedora 17 to Ubuntu 12.04 on my Lenovo 'T' 500. Everything worked fine except for the WiFi. First it didn't even connect to my router then I got it somehow to work so that it connects but I couldn't load any Website. That was yesterday today the same thing again: didn't connect, after it connected somehow no Internet access. Now if plugged in an Ethernet Cable to my laptop and I had Internet acces! I dowloaded and installed all the updates, but nothing changed on my wireless problem. Can anyone say me what to do?

Thx, tr0m4n

---

### Post by apacketofsweets on 2013-03-15
It looks to me like the drivers for the wireless card for you particular computer are not embedded into the Linux kernel yet. If you try searching the web for Linux drivers for your particular model and wireless card then you might come across the solution there.

---

### Post by wildmanne39 on 2013-03-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by tr0m4n on 2013-04-08
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

Sorry for being off so long, had a stressfull time...
However, here's the Code:

```

*************** info trace ****************



**** uname -a ****


Linux roman-ThinkPad-T500 3.5.0-26-generic #42~precise1-Ubuntu SMP Mon Mar 11 22:19:42 UTC 2013 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Lenovo Device [17aa:20ee]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
    Kernel driver in use: iwlwifi


**** lsusb ****


Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 006 Device 002: ID 046d:c062 Logitech, Inc. LS1 Laser Mouse, corded
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


**** lsmod ****


Module                  Size  Used by
joydev                 17394  0 
snd_hda_codec_conexant    52560  1 
bnep                   17791  2 
parport_pc             32115  0 
rfcomm                 38104  0 
ppdev                  12850  0 
bluetooth             189585  10 bnep,rfcomm
binfmt_misc            17293  1 
coretemp               13362  0 
pcmcia                 39855  0 
arc4                   12474  2 
snd_hda_intel          32983  3 
snd_hda_codec         116477  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
kvm                   365556  0 
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
tpm_tis                18279  0 
thinkpad_acpi          73943  0 
nvram                  14030  1 thinkpad_acpi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
r592                   17809  0 
memstick               15886  1 r592
wmi                    18745  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17906  0 
sm_common              16773  1 r852
nand                   49703  2 r852,sm_common
nand_ids                8548  1 nand
mtd                    38671  2 sm_common,nand
nand_bch               13004  1 nand
bch                    21768  1 nand_bch
nand_ecc               13106  1 nand
yenta_socket           27465  0 
pcmcia_rsrc            18368  1 yenta_socket
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62675  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
iwlwifi               364622  0 
mac80211              475546  1 iwlwifi
i915                  474913  2 
psmouse                91022  0 
drm_kms_helper         47459  1 i915
soundcore              14636  1 snd
drm                   240232  3 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
microcode              18396  0 
serio_raw              13032  0 
mac_hid                13078  0 
cfg80211              181041  2 iwlwifi,mac80211
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lpc_ich                16993  0 
mei                    36404  0 
video                  19117  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
firewire_ohci          36110  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
ahci                   25621  2 
libahci                26166  1 ahci
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
e1000e                177679  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138




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
nameserver 127.0.0.1
search home


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


[   12.233297] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.233301] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   12.233373] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   12.233375] iwlwifi 0000:03:00.0: pci_resource_base = f8470000
[   12.233377] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[   12.233458] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[   12.306503] wmi: Mapper loaded
[   12.458600] iwlwifi 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   12.458808] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.458811] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.458813] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.458815] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   12.458817] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   12.458819] iwlwifi 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   12.458878] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   12.459255] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   12.479773] iwlwifi 0000:03:00.0: device EEPROM VER=0x11e, CALIB=0x4
[   12.479777] iwlwifi 0000:03:00.0: Device SKU: 0xF0
[   12.479780] iwlwifi 0000:03:00.0: Valid Tx ant: 0x2, Valid Rx ant: 0x3
[   12.479794] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.497037] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.654933] type=1400 audit(1365438181.353:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=827 comm="apparmor_parser"
[   12.655401] type=1400 audit(1365438181.353:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=827 comm="apparmor_parser"
[   13.181942] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.821915] type=1400 audit(1365438210.519:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2035 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************


```


I had a ethernet cable plugged to my computer, because I couldn't download the script, but wireless was on.
Hope that helps!

---

### Post by wildmanne39 on 2013-04-08
Hi, your wirless is turned off by the hardware switch and is hard blocked.
Please turn it on with the switch or it may be with FN key combination.

Then  do:
```
sudo rfkill unblock all
rfkill list all
```
is anything still blocked? if so post the out of those commands and this one:
```
dmesg wmi
lsmod wmi
```
Thanks

---

### Post by tr0m4n on 2013-04-08
If ran the first 2 codes and everything was unblocked but I can't connect to the internet with my WiFi.

Maybe I need to install an 'iwlwifi' driver?

---

### Post by wildmanne39 on 2013-04-08
No the driver is installed please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thanks

---

### Post by tr0m4n on 2013-04-08
OMG it worked!

Thank you very much, you helped me a lot!

---

### Post by wildmanne39 on 2013-04-08
Your welcome!
Enjoy!

---

### Post by lucasme on 2013-04-13
Hi, I'm having a similar problem...The system detects my wireless connection, but it only stay connected for about a minute, and then disconnects =/.

I downloaded your script as well Wild Man


```



*************** info trace ****************






**** uname -a ****




Linux lucas-System 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:20:06 UTC 2013 i686 i686 i686 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"




**** lspci ****




07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169




**** lsusb ****




Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 004: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 002 Device 003: ID 0461:4d42 Primax Electronics, Ltd 
Bus 002 Device 004: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller




**** iwconfig ****




wlan0     IEEE 802.11g  ESSID:"Mezalira"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






**** rfkill ****








**** lsmod ****




Module                  Size  Used by
iwlwifi               348525  0 
mac80211              461261  1 iwlwifi
cfg80211              175574  2 iwlwifi,mac80211
rfcomm                 37277  0 
bnep                   17708  2 
ndiswrapper           192684  0 
parport_pc             31969  0 
ppdev                  12818  0 
bluetooth             183270  10 rfcomm,bnep
binfmt_misc            17261  1 
snd_hda_codec_hdmi     31457  4 
coretemp               13169  0 
kvm                   357807  0 
aesni_intel            17939  0 
cryptd                 15615  1 aesni_intel
aes_i586               16996  1 aesni_intel
lpc_ich                16926  0 
psmouse                84878  0 
eeepc_wmi              12950  0 
asus_wmi               19321  1 eeepc_wmi
mei                    35797  0 
snd_hda_codec_realtek    63579  1 
sparse_keymap          13659  1 asus_wmi
mxm_wmi                12894  0 
microcode              18210  0 
serio_raw              13032  0 
snd_hda_intel          32516  5 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
joydev                 17162  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
video                  18895  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10236406  51 
snd                    62146  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13038  0 
wmi                    18591  2 asus_wmi,mxm_wmi
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
usb_storage            39346  0 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
r8169                  55977  0 
ahci                   25497  2 
libahci                25938  1 ahci




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: wlan0  [Mezalira] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Mezalira:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    WoottonHome:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




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
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1








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




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Mezalira"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00084D657A616C697261
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706555320010B1B






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home




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




[   14.001402] wmi: Mapper loaded
[   14.088241] asus_wmi: ASUS WMI generic driver loaded
[   14.095254] asus_wmi: Initialization: 0x0asus_wmi: BIOS WMI version: 0.9asus_wmi: SFUN value: 0x0<6>[   14.095457] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input13
[   15.119627] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.545632] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   16.087504] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmn43xx32, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   16.090120] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   16.090874] usbcore: registered new interface driver ndiswrapper
[   16.164686] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.164796] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.660987] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  256.571142] ndiswrapper: device wlan0 removed
[  259.316385] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  259.862364] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmn43xx32, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  259.864519] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  259.879633] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  259.879892] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  283.642076] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  711.950040] ndiswrapper: device wlan0 removed
[  714.439448] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  714.980955] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmn43xx32, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  714.982775] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  714.993473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  714.993724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  739.280768] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1226.786696] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 1226.786699] iwlwifi: Copyright(c) 2003-2012 Intel Corporation




**************** done ********************



```

---

