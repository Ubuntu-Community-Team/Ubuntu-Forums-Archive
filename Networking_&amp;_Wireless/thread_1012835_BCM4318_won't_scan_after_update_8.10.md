---
title: "BCM4318 won't scan after update 8.10"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by goathunter on 2008-12-16
Hello. I had wireless working fine on 8.04 after I downloaded the driver under system-admin-hardwaredrivers. I did a fresh install of 8.10 and now no wireless. It does not scan for networks using the network applet and when i connect to hidden network it just says 'the network cable has been disconnected. I have activated the restricted driver and the wireless light is on. I am using an acer aspire 3000 laptop with a broadcom 4318 wireless card. Kernal is 2.6.27-9-generic i686


> 00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


iwconfig shows this

> marcus@marcus-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> marcus@marcus-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:ce:2c:79:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




lsmod turned up this

> marcus@marcus-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
rfkill_input           12672  0 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
container              11520  0 
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
video                  25104  0 
output                 11008  1 video
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
wmi                    14504  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
serio_raw              13444  0 
psmouse                45200  0 
pcspkr                 10624  0 
b43                   131356  0 
k8temp                 12416  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  1 b43
evdev                  17696  10 
input_polldev          11912  1 b43
snd_intel8x0           37532  5 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  3 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                18436  0 
ac                     12292  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
amd64_agp              18396  2 
soundcore              15328  3 snd
i2c_sis96x             12420  0 
sis_agp                15232  1 
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
i2c_core               31892  1 i2c_sis96x
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 amd64_agp,sis_agp
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            81728  1 
libusual               27156  1 usb_storage
pata_sis               18436  2 
pata_acpi              12160  0 
ssb                    40580  1 b43
ohci_hcd               31888  0 
ehci_hcd               43276  0 
sis900                 27904  0 
libata                177312  3 ata_generic,pata_sis,pata_acpi
mii                    13440  1 sis900
usbcore               148848  6 usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 



dmesg gives this

> [   15.748570] b43-phy0: Broadcom 4318 WLAN found
[   15.794434] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   15.808037] intel8x0_measure_ac97_clock: measured 55398 usecs
[   15.808043] intel8x0: clocking to 48000
[   15.817573] phy0: Selected rate control algorithm 'pid'
[   16.037771] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   16.110917] ACPI: WMI: Mapper loaded
[   16.136506] acer-wmi: Acer Laptop ACPI-WMI Extras
[   16.136523] acer-wmi: No or unsupported WMI interface, unable to load


did network config
> marcus@marcus-laptop:~$ sudo lshw -C network
[sudo] password for marcus: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:2a:b0:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.11 latency=173 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:2c:79:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:a6:6b:04:7a:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


scan for networks.

> marcus@marcus-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.



tried restarting network

> marcus@marcus-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
marcus@marcus-laptop:~$ 




but with no luck.

I have been looking over this forum for days trying to see if I could get someone else's solution to work for me but to no avail. I even tried a live cd of kubuntu and it would not scan or connect there either. I just don't understand why it worked fine in 8.04 but in 8.10 it won't even connect even if i try to connect manually. Sometimes it just says network can not be found, other times it keeps asking me for my password and prompting me to click connect and then it says network not found.
Any help would be much appreciated as this is driving me bonkers.

thanks for your time

---

### Post by S_e_P_p on 2008-12-18
Hello,

This way worked for me after installation of all updates and activation of the restricted broadcom driver:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

and afterwards the activation through this:
echo 1 > /sys/devices/platform/acer-wmi/wireless


Greets,
SePp

---

### Post by tdawg2k7 on 2008-12-19
so how would I edit "echo 1 > /sys/devices/platform/acer-wmi/wireless" for my linksys wmp54gs which is also a BCM4318 card?

---

### Post by goathunter on 2008-12-21
> **S_e_P_p said:**
> Hello,

This way worked for me after installation of all updates and activation of the restricted broadcom driver:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

and afterwards the activation through this:
echo 1 > /sys/devices/platform/acer-wmi/wireless


Greets,
SePp


THANKYOU!!!

Been trying to get this to work for weeks and jsut copy/pasted 'sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh' into the terminal and it picked up all available networks instantly.

Thanks again
marcus

---

### Post by thorin81 on 2008-12-21
> **goathunter said:**
> THANKYOU!!!

Been trying to get this to work for weeks and jsut copy/pasted 'sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh' into the terminal and it picked up all available networks instantly.

Thanks again
marcus

I just tried the above solution, but it did not work for me... I am running an Acer 5000 with the Broadcom 4318. 

lspci gives:

nick@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

iwconfig gives:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I cannot seem to get it to run at all... I am relatively new to the Linux thing. Any help would be great!

---

### Post by thorin81 on 2008-12-21
dmesg also gives:

6103.444577] b43-phy1: Broadcom 4318 WLAN found
[ 6103.517319] phy1: Selected rate control algorithm 'pid'
[ 6107.630213] input: b43-phy1 as /devices/virtual/input/input9
[ 6107.712046] firmware: requesting b43/ucode5.fw
[ 6107.717900] firmware: requesting b43/pcm5.fw
[ 6107.725109] firmware: requesting b43/b0g0initvals5.fw
[ 6107.745786] firmware: requesting b43/b0g0bsinitvals5.fw
[ 6107.889698] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 6108.007692] Registered led device: b43-phy1::tx
[ 6108.008220] Registered led device: b43-phy1::rx
[ 6108.008642] Registered led device: b43-phy1::radio
[ 6108.044616] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6545.824166] b43-pci-bridge 0000:00:0b.0: PCI INT A disabled
[ 6567.838660] ieee80211_crypt: registered algorithm 'NULL'
[ 7025.576874] ieee80211_crypt: unregistered algorithm 'NULL'
[ 7037.035527] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7037.092118] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[ 7037.155678] b43-phy0: Broadcom 4318 WLAN found
[ 7037.222769] phy0: Selected rate control algorithm 'pid'
[ 7037.226013] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[ 7041.397943] input: b43-phy0 as /devices/virtual/input/input10
[ 7041.480054] firmware: requesting b43/ucode5.fw
[ 7041.485797] firmware: requesting b43/pcm5.fw
[ 7041.492852] firmware: requesting b43/b0g0initvals5.fw
[ 7041.511309] firmware: requesting b43/b0g0bsinitvals5.fw
[ 7041.656215] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7041.783403] Registered led device: b43-phy0::tx
[ 7041.783899] Registered led device: b43-phy0::rx
[ 7041.784360] Registered led device: b43-phy0::radio
[ 7041.820643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7042.408038] b43-phy0: Radio hardware status changed to DISABLED
[ 7042.464032] b43-phy0: Radio turned on by software
[ 7042.464048] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 7261.118968] ieee80211_crypt: registered algorithm 'NULL'
[ 7261.372323] ieee80211_crypt: registered algorithm 'TKIP'

Still not sure what to do next...

---

### Post by Ayuthia on 2008-12-21
> **thorin81 said:**
> dmesg also gives:

6103.444577] b43-phy1: Broadcom 4318 WLAN found
[ 6103.517319] phy1: Selected rate control algorithm 'pid'
[ 6107.630213] input: b43-phy1 as /devices/virtual/input/input9
[ 6107.712046] firmware: requesting b43/ucode5.fw
[ 6107.717900] firmware: requesting b43/pcm5.fw
[ 6107.725109] firmware: requesting b43/b0g0initvals5.fw
[ 6107.745786] firmware: requesting b43/b0g0bsinitvals5.fw
[ 6107.889698] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 6108.007692] Registered led device: b43-phy1::tx
[ 6108.008220] Registered led device: b43-phy1::rx
[ 6108.008642] Registered led device: b43-phy1::radio
[ 6108.044616] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6545.824166] b43-pci-bridge 0000:00:0b.0: PCI INT A disabled
[ 6567.838660] ieee80211_crypt: registered algorithm 'NULL'
[ 7025.576874] ieee80211_crypt: unregistered algorithm 'NULL'
[ 7037.035527] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7037.092118] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[ 7037.155678] b43-phy0: Broadcom 4318 WLAN found
[ 7037.222769] phy0: Selected rate control algorithm 'pid'
[ 7037.226013] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[ 7041.397943] input: b43-phy0 as /devices/virtual/input/input10
[ 7041.480054] firmware: requesting b43/ucode5.fw
[ 7041.485797] firmware: requesting b43/pcm5.fw
[ 7041.492852] firmware: requesting b43/b0g0initvals5.fw
[ 7041.511309] firmware: requesting b43/b0g0bsinitvals5.fw
[ 7041.656215] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7041.783403] Registered led device: b43-phy0::tx
[ 7041.783899] Registered led device: b43-phy0::rx
[ 7041.784360] Registered led device: b43-phy0::radio
[ 7041.820643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7042.408038] b43-phy0: Radio hardware status changed to DISABLED
[ 7042.464032] b43-phy0: Radio turned on by software
[ 7042.464048] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 7261.118968] ieee80211_crypt: registered algorithm 'NULL'
[ 7261.372323] ieee80211_crypt: registered algorithm 'TKIP'

Still not sure what to do next...

It doesn't look like your card is turned on.  Please check the switch or wireless button(if you have one).  Sometimes the card might be turned off in the BIOS.

---

### Post by thorin81 on 2008-12-21
> **Ayuthia said:**
> It doesn't look like your card is turned on.  Please check the switch or wireless button(if you have one).  Sometimes the card might be turned off in the BIOS.

checked both - the light for the switch is on (in fact it cannot be turned off...). there is no option to turn off the card in the BIOS. Is there a way for me to manually turn it on off - say, in the terminal?

---

### Post by goathunter on 2008-12-29
Hello. I had wireless working for a week, then it started randomly disconnecting and prompting me to reconnect.However it would not reconnect and I had to reboot to get it to do so. Now today it does the same thing, but now it won't connect at all after rebooting and it won't even scan for networks. I haven't changed anything so whats up?

I redid 'sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh' and it said file was not installed (even though I installed it in the first place to get the wireless to work.

> marcus@marcus-laptop:~$ echo 1 > /sys/devices/platform/acer-wmi/wireless
bash: /sys/devices/platform/acer-wmi/wireless: No such file or directory
marcus@marcus-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh--2008-12-30 00:38:39--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652866 (638K) [application/x-object]
Saving to: `wl_apsta-3.130.20.0.o'

100%[======================================>] 652,866     47.4K/s   in 13s     

2008-12-30 00:38:53 (47.4 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--2008-12-30 00:38:54--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 88.198.39.176
Connecting to mirror2.openwrt.org|88.198.39.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-tar]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[======================================>] 3,888,794   27.2K/s   in 2m 9s   

2008-12-30 00:41:06 (29.4 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/pcm4.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/ucode4.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/b0g0initvals4.fw
marcus@marcus-laptop:~$  echo 1 > /sys/devices/platform/acer-wmi/wireless
bash: /sys/devices/platform/acer-wmi/wireless: No such file or directory




I 'reinstalled' it anyway but still no wireless. ?!

Any ideas on how to fix this?

---

### Post by goathunter on 2008-12-30
bump

---

### Post by goathunter on 2008-12-31
bump

---

### Post by goathunter on 2009-01-01
Someone out there must have some idea?

---

### Post by goathunter on 2009-01-02
lshw -C network    gave me this:


> marcus@marcus-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:2a:b0:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.33 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:2c:79:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 7e:08:fb:e3:b1:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


From the looks of this the wireless card has been disabled?
If so how would i go about renabling it? Network Manager has the enable wireless box ticked so I would imagine there would be a commandline for this?

---

### Post by goathunter on 2009-01-04
bump

---

### Post by goathunter on 2009-01-05
Patience is a virtue?

---

### Post by lance bermudez on 2009-01-05
I do not know if this will be of any help to you but check out what i have done to get mine to work. the drivers that used are for windows xp the vista driver does not work.

[http://ubuntuforums.org/showthread.php?t=1029731](http://ubuntuforums.org/showthread.php?t=1029731)

---

### Post by goathunter on 2009-01-05
Cheers I'll have a look.

---

### Post by goathunter on 2009-01-08
Nah tried it and no luck. However out of curiosity I made 2 live usb sticks, one of linuxmint and one of fedora. I tried them both and no luck with wireless with them either. The strange thing is when I booted back into ubuntu wireless was scanning for networks, picking them up and connecting again. This work fine for a few hours until it wouldn't connect anymore. I rebooted and now its not scanning either. !?

WTF?!

---

### Post by knappen on 2009-01-08
Try OpenSuse.

Broadcom wireless works fine there. They have all the drivers in the Packman repository.

---

### Post by goathunter on 2009-01-08
Can that be run as a live system from a usb? Or do I need to install it to a partition on my hdd to run it?

---

### Post by jamin_melville on 2009-01-11
I've got the same problem, my wireless was working fine, then it stopped and only worked after a restart and now it doesn't work at all. I have some sort of broadcomm wireless card. lshw -C network doesn't show my wireless connection.. Any suggestions?

---

### Post by Ayuthia on 2009-01-11
> **goathunter said:**
> Can that be run as a live system from a usb? Or do I need to install it to a partition on my hdd to run it?

I think that it is a liveCD so it should be able to be used on a USB.  It has been a while since I have used it so I could be wrong.

By the way, are you able to scan for wireless sites, but just can't connect?  If so, can you post the results of:
```
sudo iwlist scan
```

---

### Post by Ayuthia on 2009-01-11
> **jamin_melville said:**
> I've got the same problem, my wireless was working fine, then it stopped and only worked after a restart and now it doesn't work at all. I have some sort of broadcomm wireless card. lshw -C network doesn't show my wireless connection.. Any suggestions?

Can you see if you can see your wireless card through:
```
lspci -nn
```

---

### Post by jamin_melville on 2009-01-11
Hey I did lspci -nn and it gave me:

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)                                                
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)                                        
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)                                        
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)                                        
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)                                        
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)                                                
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)                                        
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)                                        
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)                                         
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)                                         
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)                           
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)                                              
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

I don't recognize my wireless card in there...

---

### Post by Ayuthia on 2009-01-11
> **jamin_melville said:**
> Hey I did lspci -nn and it gave me:

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)                                                
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)                                        
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)                                        
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)                                        
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)                                        
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)                                                
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)                                        
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)                                        
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)                                         
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)                                         
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)                           
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)                                              
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

I don't recognize my wireless card in there...

I am not seeing it either.  Are you dual booting by any chance?  Also, is this an HP laptop?  If so do you have the model?

---

### Post by goathunter on 2009-01-11
hello
> marcus@marcus-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:2a:b0:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.11 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:2c:79:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 56:a6:5c:6b:55:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
marcus@marcus-laptop:~$ 



> marcus@marcus-laptop:~$ sudo iwlist scan
[sudo] password for marcus: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


> 00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)



Any ideas?

---

### Post by jamin_melville on 2009-01-11
Na I'm not dual booting and yea it is an HP, the model number is Presario V3019AU or just V3000. :)

---

### Post by goathunter on 2009-01-12
Just went to plug my laptop into my mates lcd tv before. Usually no probs. I plugged it in tonight and the vga signal cuts off after the login screen. But now wireless is working fine again. Maybe there is a connection here?

---

### Post by Ayuthia on 2009-01-12
> **goathunter said:**
> Just went to plug my laptop into my mates lcd tv before. Usually no probs. I plugged it in tonight and the vga signal cuts off after the login screen. But now wireless is working fine again. Maybe there is a connection here?

It could be possible that the graphics driver is conflicting with the wireless.  What kind of graphics card do you have?

---

### Post by Ayuthia on 2009-01-12
> **jamin_melville said:**
> Na I'm not dual booting and yea it is an HP, the model number is Presario V3019AU or just V3000. :)

You might want to check this out:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01087277](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01087277)

---

### Post by goathunter on 2009-01-12
> It could be possible that the graphics driver is conflicting with the wireless. What kind of graphics card do you have? 

its a generic one
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


---

### Post by Ayuthia on 2009-01-12
> **goathunter said:**
> its a generic one
I haven't heard of this card having problems with the Broadcom cards.  My only thoughts is that there is some interference in the air with the wireless card.

---

### Post by jamin_melville on 2009-01-12
> **Ayuthia said:**
> You might want to check this out:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01087277](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01087277)

That looks like the problem, I'll have to do a little more research into upgrading the BIOS through linux. Very helpful, thanks

---

### Post by acimmarusti on 2009-01-22
Hi there,

I got this card working fine in intrepid. I posted this thread with all the info.

Hope it works for ya

[http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318](http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318)

---

