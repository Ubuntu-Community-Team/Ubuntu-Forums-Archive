---
title: "unable to get Bigfoot Killer Wireless-n to work"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by Wascalwabbit on 2011-05-22
I just got my new sager p150hm and everything is great, but i can not get the wireless to work in ubuntu. i've been poking in the dark for a good 8 hours total and have made very little progress so far. 
As I said in the title the card is a bigfoot killer wirless-n which is based on an athos chip. so far i have tried to install the latest compat-wireless package per command line, which failed, so i installed it through apt, which worked, but didn't fix the problem. next i installed the linux-firmware package which didn't do anything either. here is some info on what's what

lspci:

```
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6720
01:00.1 Audio device: ATI Technologies Inc Device aa88
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
04:00.0 Network controller: Atheros Communications Inc. AR9300 Wireless LAN adaptor (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)

```

dmseg | grep ath

```
[    3.784115] device-mapper: multipath: version 1.1.1 loaded
[    3.784117] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.389306] ath9k 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.389336] ath9k 0000:04:00.0: setting latency timer to 64
[   16.395668] ath: EEPROM regdomain: 0x0
[   16.395669] ath: EEPROM indicates default country code should be used
[   16.395670] ath: doing EEPROM country->regdmn map search
[   16.395672] ath: country maps to regdmn code: 0x3a
[   16.395673] ath: Country alpha2 being used: US
[   16.395674] ath: Regpair used: 0x3a
[   16.497539] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.497874] Registered led device: ath9k-phy0::radio
[   16.497884] Registered led device: ath9k-phy0::assoc
[   16.497895] Registered led device: ath9k-phy0::tx
[   16.497905] Registered led device: ath9k-phy0::rx

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

```

and in case it is not apparent, i'm a linux noob, so please be gentle. 8-[

thanks for the help, 

dom

---

### Post by josephmills on 2011-05-23
hi there could we see ```
rfkill list all 
``` and ```
lsmod | grep ath  
``` thanks

---

### Post by Wascalwabbit on 2011-05-23
thanks for you reply

rfkill list all

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

lsmod | grep ath

```
ath9k                  89901  0 
mac80211              235093  1 ath9k
ath9k_common            4396  1 ath9k
ath9k_hw              291766  2 ath9k,ath9k_common
ath                     8053  2 ath9k,ath9k_hw
cfg80211              142616  3 ath9k,mac80211,ath
led_class               2633  2 ath9k,sdhci

```

---

### Post by josephmills on 2011-05-23
everything is looking good could we see ```
lsmod
``` and ```
iwlist scan
``` thanks

---

### Post by Wascalwabbit on 2011-05-23
lsmod

```
Module                  Size  Used by
ppp_deflate             3726  0 
zlib_deflate           19266  1 ppp_deflate
bsd_comp                4791  0 
ppp_async               6778  1 
crc_ccitt               1351  1 ppp_async
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
arc4                    1165  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
ath9k                  89901  0 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
mac80211              235093  1 ath9k
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
usbhid                 36882  0 
snd_timer              19067  2 snd_pcm,snd_seq
ath9k_common            4396  1 ath9k
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    67742  1 usbhid
ath9k_hw              291766  2 ath9k,ath9k_common
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     8053  2 ath9k,ath9k_hw
option                 13453  2 
soundcore                880  1 snd
psmouse                59033  0 
cfg80211              142616  3 ath9k,mac80211,ath
usb_wwan                9953  1 option
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
intel_agp              26566  0 
video                  18712  0 
usbserial              33357  7 option,usb_wwan
agpgart                32011  1 intel_agp
xhci_hcd               53471  0 
output                  1883  1 video
lp                      7342  0 
serio_raw               4022  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  1 
firewire_ohci          21234  0 
ahci                   19198  2 
sdhci_pci               6633  0 
libahci                21728  1 ahci
firewire_core          46643  1 firewire_ohci
sdhci                  15922  1 sdhci_pci
crc_itu_t               1383  1 firewire_core
led_class               2633  2 ath9k,sdhci
jme                    29882  0 
mii                     4425  1 jme

```

iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

ppp0      Interface doesn't support scanning.

```

---

### Post by josephmills on 2011-05-23
```
sudo /etc/init.d/networking restart
``` then post ```
iwlist scan 
``` and ```
cat /etc/apt/sources.list
```thanks

---

### Post by Wascalwabbit on 2011-05-23
iwlist scan (after sudo /etc/init.d/networking restart)

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

ppp0      Interface doesn't support scanning.

```

cat /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse

```

thanks so much for your help again

---

### Post by josephmills on 2011-05-23
> **Wascalwabbit said:**
> 
wlan0     Failed to read scan data :** Network is down**


 we have to get that network up try 
```
sudo ifup wlan
``` then a ```
iwlist scan
``` we will get this :D

Also click on the networkmanager icon and do you see enable wireless or is this greyed out?

---

### Post by Wascalwabbit on 2011-05-23
well sudo ifup wlan returned an error so i tried wlan0, but i got the same error, so there was no change when i input iwlist scan.

```
bugs@ubuntu:~$ sudo ifup wlan
Ignoring unknown interface wlan=wlan.
bugs@ubuntu:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

hehe, almost missed that last line there. enable wireless is not greyed out and it is checked

---

### Post by josephmills on 2011-05-23
could we see a ```
lspci -nn
``` thanks

---

### Post by Wascalwabbit on 2011-05-23
you got it

lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6720]
01:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa88]
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 05)
03:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 90)
03:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 90)
03:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2393] (rev 90)
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9300 Wireless LAN adaptor [168c:0030] (rev 01)
05:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380] (rev 30)

```

---

### Post by josephmills on 2011-05-23
please go to synaptic package manager then go to edit-->repositories  then make sure all are ticked see pic then close out of software sources and synaptic then open a terminal and do a ```
sudo apt-get update 
``` then ```
sudo apt-get upgrade
``` then reboot anything?

---

### Post by Wascalwabbit on 2011-05-23
well, that will have to wait a while since i don't have an ethernet connection available right now and i'm only getting 8kB/s on my wireless bradband. ](*,) I was hoping to get the wireless working so i can upgrade more easily. I'll hit up some friends tomorrow and try to get everything up to date. i'll post the results then. thanks again

p.s.: awesome square of fire btw, thx for that xD

---

### Post by Wascalwabbit on 2011-05-23
so i installed ubuntu 11.4 (i was on 10.10 before) and the wirless card worked right out of the box. I also tried kubuntu 11.4, but it didn't work there, and i had some issues with the video, so i scrapped that.

Thanks again for your help joseph

---

### Post by 3Balista on 2011-05-25
@Wascalwabbit:
Just for your information, I had the same problem with my Santech N67 (a different brand for the same laptop) with Lucid 64bit installed.
I resolved installing the latest Realtek driver.
You can find it [**here**]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782") (choose the **RTL8192CE-VA4** one).
Everthing works fine now.

---

