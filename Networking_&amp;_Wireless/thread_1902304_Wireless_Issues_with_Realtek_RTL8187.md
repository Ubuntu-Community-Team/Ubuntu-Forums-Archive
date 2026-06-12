---
title: "Wireless Issues with Realtek RTL8187"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by ian_frost on 2011-12-30
Good Day Folks!

First of all my onboard wireless (Atheros IEEE Network Connection (802.11b/g)) works flawlessly. However I use my Realtek adapter for longer ranges. 
Both worked well under ubuntu 11.04. I have now upgraded to ubuntu 11.10 and only the internal cards works properly. 
Problem: I network manager shows wireless networks available and I can choose one and connect. When I choose a network; it shows good connection strength and the connection does not brake, however i am unable to browse any website. Ping only works on the local network. For eg I cannot ping google. 
I was folloing [this thread]("http://ubuntuforums.org/showthread.php?t=1896636&highlight=rtl8187+wireless") and many others but to no avail. 

Some of the primary info you may need. 
Currently running on Sony NR260E - Ubuntu 11.10

lsusb
```
hael@VGNNR260E:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 002 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

```lsmod
```
hael@VGNNR260E:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251973  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
r8187l                143412  0 
joydev                 17393  0 
rtl8187                56323  0 
eeprom_93cx6           12653  1 rtl8187
snd_hda_codec_realtek   254125  1 
pcmcia                 39822  0 
arc4                   12473  2 
tifm_7xx1              12937  0 
tifm_core              15040  1 tifm_7xx1
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_seq_midi_event     14475  1 snd_seq_midi
ath5k                 145100  0 
ath                    19387  1 ath5k
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73673  0 
mac80211              393459  2 rtl8187,ath5k
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            39681  0 
binfmt_misc            17292  1 
cfg80211              172392  4 rtl8187,ath5k,ath,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505159  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   21634  3 
libahci                25727  1 ahci
sky2                   49317  0 
```iwconfig
```
hael@VGNNR260E:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SHARAMA WI FI"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:15:2C:9F   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=19/70  Signal level=-91 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:62   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"SHARAMA WI FI"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:15:2C:9F   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23   Missed beacon:0

```As you can see I am connected on wlan1. But still no internet access

sudo iwlist wlan1 scan
```
hael: 
wlan1     Scan completed :
          Cell 01 - Address: 00:1A:2B:15:2C:9F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"SHARAMA WI FI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c830ed7fe8
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000D53484152414D41205749204649
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180238F4000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```iwlist chan
```
hael@VGNNR260E:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

```cat /etc/resolv.conf
```
hael@VGNNR260E:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain Home
search Home
nameserver 196.3.132.153
nameserver 196.3.132.154
michael@VGNNR260E:~$ 
```
hael@VGNNR260E:~$ sudo gedit /etc/modprobe.d/blacklist.conf
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
```route -n
```
hael@VGNNR260E:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```dmesg
```
hael@VGNNR260E:~$ dmesg | grep 8187
[    0.581874] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.818769] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHY2200B 0000 PQ: 0 ANSI: 5
[   18.998187] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.999280] ieee80211 phy1: hwaddr 00:c0:ca:51:8d:73, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   19.015411] rtl8187: Customer ID is 0xFF
[   19.016790] Registered led device: rtl8187-phy1::radio
[   19.017962] Registered led device: rtl8187-phy1::tx
[   19.019356] Registered led device: rtl8187-phy1::rx
[   19.019774] rtl8187: wireless switch is on
[   19.021298] usbcore: registered new interface driver rtl8187
[   19.063829] Linux kernel driver for RTL8187L based WLAN cards
[   19.063834] rtl8187L: Initializing module
[   19.063836] rtl8187L: Wireless extensions version 22
[   19.063839] rtl8187L: Initializing proc filesystem
[   19.063890] usbcore: registered new interface driver rtl8187L
[ 6712.575144] ieee80211 phy2: hwaddr 00:c0:ca:51:8d:73, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 6712.589723] rtl8187: Customer ID is 0xFF
[ 6712.589831] Registered led device: rtl8187-phy2::radio
[ 6712.589891] Registered led device: rtl8187-phy2::tx
[ 6712.589949] Registered led device: rtl8187-phy2::rx
[ 6712.590329] rtl8187: wireless switch is on
```I will provide any other details you may need.

---

### Post by ian_frost on 2012-01-03
I did some other testing and ruled out the possibility of the adapter being defective.

---

### Post by ian_frost on 2012-01-12
To date I have not made any further progress on my own. Anyone here having similar issues.

---

### Post by ian_frost on 2012-02-27
Amazing!

---

### Post by christophwelty on 2012-03-14
Were you able to find a solution?
I have the same problem with my cheap rtl8187 based dongle. On occasion it will connect to the internet and display a website for a few seconds before not working again.

Thanks for you post.

---

### Post by kurt18947 on 2012-03-14
Realtek has drivers for 8187l chipsets.  They're found here:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false)

about the center of the page.

Not  applicable to Ian's issue but for searchers, there are apparently a  few variants of realtek 8187.  The O.P. s device uses module  8187l (lower case L).  I have a USB adapter - TrendNet TEW-424UB v.3.x - which uses 8187b and has been  plug 'n' play since Ubuntu 9.x.  Just pointing out subtle differences  to anyone looking for a Linux compatible Wifi adapter.

---

