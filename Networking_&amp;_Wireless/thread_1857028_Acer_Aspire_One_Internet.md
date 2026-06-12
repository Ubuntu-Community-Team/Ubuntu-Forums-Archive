---
title: "Acer Aspire One Internet"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by hijiz on 2011-10-09
Internet connections always where an issue in my computer but ever since i instaled 11.10 beta everything went quite smoothly. my acer has taken quite a beating in the past few months but this moening my little cousin triped on the charger and trashed my netbook to the ground. everything seemed fine but the internet dosnt work. does anyone know how to fix this?

---

### Post by retchid on 2011-10-09
sometimes mine does not recognise the ssd drive I turn it over and slap it (serious)works every time

1. give it a slap
2. reinstall
3. buy a usb wifi
4. plug it into the modem/router
5. bin it

(you sure you have not switched the wifi off)

---

### Post by wildmanne39 on 2011-10-09
Hi, please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
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

### Post by hijiz on 2011-10-09
cat /etc/lsb-release; uname -a
>  
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
Linux [EMAIL="emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] 3.0.0-12-generic #19-Ubuntu SMP Fri Sep 23 21:18:13 UTC 2011 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net
> 01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Subsystem: Foxconn International, Inc. Device [105b:e01b]
Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
Subsystem: Acer Incorporated [ALI] Device [1025:022f]
Kernel driver in use: atl1c


iwconfig
> lo no wireless extensions.
eth0 no wireless extensions.
eth2 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:199
Rx invalid nwid:0 invalid crypt:0 invalid misc:0
rfkill list all
0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no
1: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no

lsmod> Module Size Used by
nls_iso8859_1 12617 1 
nls_cp437 12751 1 
vfat 17308 1 
fat 55577 1 vfat
usb_storage 44173 1 
uas 17699 0 
bnep 17923 2 
rfcomm 38408 0 
bluetooth 148839 10 bnep,rfcomm
parport_pc 32114 0 
ppdev 12849 0 
joydev 17393 0 
snd_hda_codec_realtek 254125 1 
snd_hda_intel 24262 2 
snd_hda_codec 91754 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13276 1 snd_hda_codec
snd_pcm 80468 2 snd_hda_intel,snd_hda_codec
snd_seq_midi 13132 0 
snd_rawmidi 25241 1 snd_seq_midi
uvcvideo 67271 0 
videodev 85626 1 uvcvideo
snd_seq_midi_event 14475 1 snd_seq_midi
lib80211_crypt_tkip 17240 0 
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
snd_timer 28932 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse 73673 0 
wl 2646601 0 
serio_raw 12990 0 
snd 55902 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915 505108 3 
drm_kms_helper 32889 1 i915
drm 192226 4 i915,drm_kms_helper
lib80211 14570 2 lib80211_crypt_tkip,wl
soundcore 12600 1 snd
snd_page_alloc 14115 2 snd_hda_intel,snd_pcm
i2c_algo_bit 13199 1 i915
acer_wmi 23302 0 
sparse_keymap 13658 1 acer_wmi
binfmt_misc 17292 1 
video 18908 1 i915
wmi 18744 1 acer_wmi
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp
ahci 21634 2 
libahci 25727 1 ahci
atl1c 36638 0 



---

### Post by wildmanne39 on 2011-10-09
Hi, we are going to run a few commands please post the results here: but I also want to ask some questions.

1.Wireless was working in 11.10 beta before the fall?

Have you ran a disk check on your drive since the fall? it has a habit of causes bad sectors or file corruption.
```
nm-tool
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan0| tail -n25
```
Thank you

---

### Post by hijiz on 2011-10-09
11.10 wireless was working fine before the fall
no i havent run a disk check. the comands say
nm-tool
>  
NetworkManager Tool
State: disconnected
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: atl1c
State: unavailable
Default: no
HW Address: 00:26:22:13:CF:C3
Capabilities:
Carrier Detect: yes
Wired Properties
Carrier: off
- Device: eth2 -----------------------------------------------------------------
Type: 802.11 WiFi
Driver: wl
State: disconnected
Default: no
HW Address: 00:26:5E:6C:B3:5B
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points 
SpeedTouch3E1876:Infra, 00:14:7F:2D:CA:1F, Freq 2412 MHz, Rate 0 Mb/s, Strength 100

iwlist chan
>  
lo no frequency information.
eth0 no frequency information.
eth2 no frequency information.

sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan0| tail -n25
> re -e wlan0| tail -n25
Oct 9 11:32:24 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.450283] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 9 11:32:24 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.702461] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 9 11:32:24 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.702481] wl 0000:01:00.0: setting latency timer to 64
Oct 9 11:32:25 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.976623] ACPI Error: [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dswload2-316)
Oct 9 11:32:26 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] NetworkManager[572]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 9 11:32:26 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] NetworkManager[572]: <info> (eth2): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Oct 9 13:09:26 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] NetworkManager[496]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 9 13:09:26 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.700259] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 9 13:09:27 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.993315] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 9 13:09:27 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 13.993335] wl 0000:01:00.0: setting latency timer to 64
Oct 9 13:09:29 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] NetworkManager[496]: <info> (eth2): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Oct 9 13:09:29 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] NetworkManager[496]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth1/rfkill1) (driver wl)
Oct 9 15:21:19 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 3349.467556] wl 0000:01:00.0: PCI INT A disabled
Oct 9 15:21:19 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 3350.031794] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 9 15:21:19 emilio@Aspire-one[/EMAIL"]emilio@Aspire-one"]emilio@Aspire-one[/EMAIL] kernel: [ 3350.031806] wl 0000:01:00.0: setting latency timer to 64
sudo iwlist scan
>  lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
eth2 Scan completed :
Cell 01 - Address: 00:14:7F:2D:CA:1F
ESSID:"SpeedTouch3E1876"
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:5/5 Signal level:-30 dBm Noise level:-92 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s

---

### Post by wildmanne39 on 2011-10-09
Hi, I am sorry to respond so slowly, my computer crashed and it is only working on and off right now.

Please try this:
```
rfkill unblock all
```
if it does not come to life please post the results of these commands:
```
lsmod | grep wl
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by hijiz on 2011-10-09
lsmod | grep wl
>  
wl                   2646601  0 
lib80211               14570  2 lib80211_crypt_tkip,wl

 
sudo lshw -C network
>  
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:01:00.0"]pci@0000:01:00.0[/EMAIL]
       logical name: eth1
       version: 01
       serial: 00:26:5e:6c:b3:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: eth0
       version: c0
       serial: 00:26:22:13:cf:c3
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:55000000-5503ffff ioport:2000(size=128)

 
lspci -nnk | grep -iA2 net
 

> 01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
 Subsystem: Foxconn International, Inc. Device [105b:e01b]
 Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
 Subsystem: Acer Incorporated [ALI] Device [1025:022f]
 Kernel driver in use: atl1c
 
The command rfkill unblock all didnt help.

---

### Post by wildmanne39 on 2011-10-10
Hi, it looks like it should connect, but we are in new territory here with this card and the fact that it is 11.10 beta.

First I would change the channel from one to another number like 6 or 11.

Also I recommend running this command it may or may not help.
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

I am going off line for the night, I am still having computer issues so I am going to get some rest so I can tackle them and your issue tomorrow.
Thank you

---

### Post by hijiz on 2011-10-10
> **wildmanne39 said:**
> Hi, it looks like it should connect, but we are in new territory here with this card and the fact that it is 11.10 beta.

First I would change the channel from one to another number like 6 or 11.

Also I recommend running this command it may or may not help.
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

I am going off line for the night, I am still having computer issues so I am going to get some rest so I can tackle them and your issue tomorrow.
Thank you
Thanks but the command you posted didnt help.

---

### Post by praseodym on 2011-10-10
Hi,

blacklist the following module:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check:

```
cat /etc/udev/rules.d/70-persistent-net.rules
iwconfig
dmesg | egrep 'wl|eth1|eth2|wmi'
sudo iwlist scan
```
Any switches/key combinations?

---

### Post by hijiz on 2011-10-12
Thank you all i will try the command above if it fails ill reinstall ubuntu, wait for another command or asume its a hardware issue and change the wireless card. (please keep writing commands)

---

### Post by hijiz on 2011-10-13
thanks praseodym that fixed the problem.

---

### Post by wildmanne39 on 2011-10-13
Thank you praseodym.

---

