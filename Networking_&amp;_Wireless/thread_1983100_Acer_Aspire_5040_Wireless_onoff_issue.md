---
title: "Acer Aspire 5040 Wireless on/off issue"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by JohnParr on 2012-05-19
I have an annoying issue with the wireless  adapter in my Acer Aspire 5040. This laptop has a button on the front  that lights up when the wireless adapter is powered on. It’s currently  set up to run 4 operating systems: 
 
            Windows XP: Wireless works perfectly but it has to run at  start-up a piece of Acer software (that sets the actions of several  special keys) for the wireless adapter to power on.  
 
            Lucid Puppy 5.2: Wireless works perfectly. Wireless adapter powers on every boot.  
 
            Ubuntu 11.04: Wireless adapter powers on sometimes if booted  from a shutdown state. If the adapter does not power on it is possible  to get it to power on by performing a shutdown and restart. If I do this  the adapter powers on during the shutdown process and remains on for  the restart. This is 100% repeatable and wireless works perfectly from  this point.  
 
            Ubuntu 12.04: The wireless adapter never powers on if booted  from a shutdown state. The shutdown and restart workaround that gets it  going under Ubuntu 11.04 does not work under Ubuntu 12.04. However it  does work if I shutdown one of the other operating systems and restart  Ubuntu 12.04.  
 
            Once the wireless adapter is powered on it always works fine  so I don’t think this is a networking driver issue. The intermittent  behaviour under Ubuntu 11.04 suggests to me it might be a timing issue  where something needs to happen before something else. Ubuntu 12.04  certainly boots much quicker than Ubuntu 11.04 but then I have only just  installed it.  
 
"rfkill list all" reports no blocks  in Ubuntu 12.04 and a hardware block which will not unblock in Ubuntu 11.04
 
            The Wireless adapter is an Atheros AR5005G and uses the ath5k driver and something called acer_wmi. 
 
           There must be a Linux solution because Puppy works fine. I would be very grateful for any suggestions.

---

### Post by wildmanne39 on 2012-05-27
Hi, please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot.
Thanks

---

### Post by JohnParr on 2012-05-29
Thanks for the suggestion."tee -a" is a neat command so I have learnt something there.

Blacklisting acer_wmi does not change anything for my Ubuntu 12.4 installation. If I blacklist acer_wmi in Puppy the wireless does not switch on. If I then modprobe acer_wmi the wireless springs to life and works fine again. I think that probably proves something normally done by acer_wmi is not working in Ubuntu 12.4.

One obvious difference between the two installations can be found at sys/devices/platform/acer_wmi where Puppy has an additional Folder "rfkill". I also get different results from "rfkill list all"

Puppy returns 

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Ubuntu 12.04 returns

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Ubuntu 11.04 returns

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-threeg: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I'm looking at a number of things on the net to solve this but would value any other suggestions. The acer_wmi module can be loaded with parameters that work with particular laptops

---

### Post by wildmanne39 on 2012-05-30
Hi, please do post 18 in this link.
[http://ubuntuforums.org/showthread.php?p=11792710#post11792710](http://ubuntuforums.org/showthread.php?p=11792710#post11792710)

Post the output of:
```
lsmod
```
Thanks

---

### Post by JohnParr on 2012-05-30
Thanks for your help.  The code you suggested does not have any noticeable effect.

lsmod produces the following on Ubuntu 12.04

Module                  Size  Used by
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
pcmcia                 39791  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
radeon                733693  3 
snd_seq_midi           13132  0 
ath5k                 145127  0 
snd_rawmidi            25424  1 snd_seq_midi
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72919  0 
cfg80211              178679  3 ath5k,ath,mac80211
serio_raw              13027  0 
k8temp                 12905  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   197692  5 radeon,ttm,drm_kms_helper
video                  19068  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 acer_wmi
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
mac_hid                13077  0 
shpchp                 32325  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
pata_atiixp            12999  4 


lsmod on Puppy produces:


Module                  Size  Used by
cpufreq_ondemand        5981  1 
powernow_k8             9212  0 
radeon                515838  2 
ttm                    31586  1 radeon
drm_kms_helper         17823  1 radeon
drm                   106327  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            3539  1 radeon
usbhid                 18009  0 
iptable_mangle          1189  0 
iptable_nat             2666  0 
nf_nat                 10083  1 iptable_nat
ipt_REJECT              1485  1 
nf_conntrack_ftp        4020  0 
nf_conntrack_irc        2359  0 
iptable_filter           958  1 
xt_state                 895  4 
nf_conntrack_ipv4       7063  7 iptable_nat,nf_nat
nf_conntrack           36999  6 iptable_nat,nf_nat,nf_conntrack_ftp,nf_conntrack_irc,xt_state,nf_conntrack_ipv4
nf_defrag_ipv4           755  1 nf_conntrack_ipv4
ip_tables               7321  3 iptable_mangle,iptable_nat,iptable_filter
snd_hda_codec_realtek   165209  1 
fan                     2478  0 
arc4                     962  2 
ecb                     1377  2 
snd_hda_intel          14978  0 
snd_hda_codec          38539  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            26845  0 
snd_mixer_oss           9963  1 snd_pcm_oss
snd_pcm                45385  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy            907  0 
snd_seq_oss            18888  0 
snd_seq_midi            3156  0 
snd_rawmidi            11924  1 snd_seq_midi
snd_seq_midi_event      3592  2 snd_seq_oss,snd_seq_midi
snd_seq                32379  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              11986  2 snd_pcm,snd_seq
snd_seq_device          3601  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    30859  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               3403  1 snd
snd_page_alloc          4645  2 snd_hda_intel,snd_pcm
ath5k                 105393  0 
mac80211               99898  1 ath5k
ath                     6106  1 ath5k
pcspkr                  1179  0 
yenta_socket           16079  1 
r8169                  25792  0 
rsrc_nonstatic          6693  1 yenta_socket
k8temp                  2315  0 
hwmon                    957  1 k8temp
serio_raw               2928  0 
cfg80211               90499  3 ath5k,mac80211,ath
mii                     2650  1 r8169
fbcon                  27736  0 
tileblit                1509  1 fbcon
font                    6916  1 fbcon
bitblit                 3514  1 fbcon
softcursor               805  1 bitblit
squashfs               15984  0 
aufs                  110466  0 
fuse                   42549  0 
acer_wmi               11359  0 
i2c_piix4               6788  0 
rfkill                  9968  2 cfg80211,acer_wmi
led_class               1733  2 ath5k,acer_wmi
i2c_core               11497  5 radeon,drm_kms_helper,drm,i2c_algo_bit,i2c_piix4
nls_iso8859_1           2937  0 
nls_cp437               4465  0 
ohci_hcd               16937  0 
ati_agp                 3910  0 
ssb                    29373  1 ohci_hcd
agpgart                18904  3 ttm,drm,ati_agp
shpchp                 21148  0 
pci_hotplug            18286  1 shpchp
wmi                     4337  1 acer_wmi
battery                 7164  0 
video                  14642  0 
output                  1120  1 video
thermal                 9263  0 
evdev                   5517  0 
button                  3522  0 
ac                      2143  0 
processor              24987  2 powernow_k8
ehci_hcd               25830  0 
usbcore                91279  4 usbhid,ohci_hcd,ehci_hcd

I guess its not as simple as using the modules in the puppy install in Ubuntu....

Puppy lists rfkill as a module. Might that be relevant?

---

### Post by wildmanne39 on 2012-05-30
Hi, rfkill does not show a block.

Please post the contents of:
```
gksudo gedit /etc/rc.local
```

Are you shutting down your other operating systems before you boot ubuntu? if not and you are hibernating them that might be the problem and also it is recommended not to do that. 

Please show:
```
dmesg | egrep 'ath|firm|radio|switch|wlan0|etork'
```
Thanks

---

### Post by JohnParr on 2012-05-31
Thanks again.

Contents of  rc.local:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod -r ath5k
rfkill unblock all
modprobe ath5k

exit 0

________________________________

I don't try to hibernate any of the other OS's. I have tried it on Ubuntu 11.04 but it does not work.
__________________________________

I can get wireless working on Ubuntu 12.04 by booting one of the others OS's, then doing a restart rather than power down followed by power up. The wireless switch on the front of the laptop stays lit throughout the restart > splash screen > grub menu process.
__________________________________

dmesg | egrep 'ath|firm|radio|switch|wlan0|etork'
[    0.004810] SMP alternatives: switching to UP code
[   20.762885] ath5k 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
[   20.762978] ath5k 0000:06:05.0: registered as 'phy0'
[   21.856542] ath: EEPROM regdomain: 0x63
[   21.856546] ath: EEPROM indicates we should expect a direct regpair map
[   21.856551] ath: Country alpha2 being used: 00
[   21.856554] ath: Regpair used: 0x63
[   21.894391] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   22.073436] Console: switching to colour frame buffer device 160x50
[   23.408763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.203561] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.144042] wlan0: authenticate with 00:12:0e:48:49:dd (try 1)
[   49.145549] wlan0: authenticated
[   49.157378] wlan0: associate with 00:12:0e:48:49:dd (try 1)
[   49.168109] wlan0: RX AssocResp from 00:12:0e:48:49:dd (capab=0x411 status=0 aid=4)
[   49.168126] wlan0: associated
[   49.175288] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.160070] wlan0: no IPv6 routers present

Thanks for your time and attention :)

---

### Post by wildmanne39 on 2012-05-31
Hi, are you running ubuntu 12.04 in virtual box by any chance? from what you said I am guessing no.
Thanks

---

### Post by JohnParr on 2012-06-01
No I am not running Ubuntu 12.04 in virtual box but I do have virtual box installed in Ubuntu 12.04. I use VBox to run an old game that needs Windows 98 of all things. It's a classic football manager game

Thanks

---

### Post by wildmanne39 on 2012-06-01
Hi, the information you posted looks good, did you run those commands while you could not connect to wireless in 12.04? that is when I need to see all the information that I ask for.

Please post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
rfkill list all
lsmod | grep ath
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork -e radio -e switch | tail -n75
```
Thanks

---

### Post by JohnParr on 2012-06-01
Ah, now thats a good point.... I've generally got things working to read and copy paste the commands. This time they were all run when the laptop was booted from cold and the wireless was not powered on.

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod | grep ath

ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211

sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork -e radio -e switch | tail -n75

Jun  1 21:17:48 John-Laptop NetworkManager[806]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  1 21:27:12 John-Laptop kernel: [    0.004810] SMP alternatives: switching to UP code
Jun  1 21:27:12 John-Laptop kernel: [   22.479381] ath5k 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
Jun  1 21:27:12 John-Laptop kernel: [   22.479466] ath5k 0000:06:05.0: registered as 'phy0'
Jun  1 21:27:12 John-Laptop kernel: [   23.331212] ath: EEPROM regdomain: 0x63
Jun  1 21:27:12 John-Laptop kernel: [   23.331216] ath: EEPROM indicates we should expect a direct regpair map
Jun  1 21:27:12 John-Laptop kernel: [   23.331222] ath: Country alpha2 being used: 00
Jun  1 21:27:12 John-Laptop kernel: [   23.331224] ath: Regpair used: 0x63
Jun  1 21:27:12 John-Laptop kernel: [   23.378855] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Jun  1 21:27:12 John-Laptop kernel: [   23.747051] Console: switching to colour frame buffer device 160x50
Jun  1 21:27:12 John-Laptop NetworkManager[797]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/net/wlan0, iface: wlan0)
Jun  1 21:27:12 John-Laptop NetworkManager[797]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  1 21:27:12 John-Laptop NetworkManager[797]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:07.0/net/eth0, iface: eth0)
Jun  1 21:27:12 John-Laptop NetworkManager[797]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:07.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  1 21:27:12 John-Laptop NetworkManager[797]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  1 21:27:12 John-Laptop NetworkManager[797]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): using nl80211 for WiFi device control
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): now managed
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): bringing up device.
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): preparing device.
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  1 21:27:12 John-Laptop dbus[743]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jun  1 21:27:12 John-Laptop kernel: [   25.492583] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  1 21:27:12 John-Laptop kernel: [   25.493423] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  1 21:27:12 John-Laptop dbus[743]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> wpa_supplicant started
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  1 21:27:12 John-Laptop NetworkManager[797]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  1 21:35:04 John-Laptop kernel: [    0.004808] SMP alternatives: switching to UP code
Jun  1 21:35:04 John-Laptop kernel: [   22.672743] ath5k 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
Jun  1 21:35:04 John-Laptop kernel: [   22.672828] ath5k 0000:06:05.0: registered as 'phy0'
Jun  1 21:35:04 John-Laptop kernel: [   23.567459] ath: EEPROM regdomain: 0x63
Jun  1 21:35:04 John-Laptop kernel: [   23.567462] ath: EEPROM indicates we should expect a direct regpair map
Jun  1 21:35:04 John-Laptop kernel: [   23.567467] ath: Country alpha2 being used: 00
Jun  1 21:35:04 John-Laptop kernel: [   23.567469] ath: Regpair used: 0x63
Jun  1 21:35:04 John-Laptop kernel: [   23.588383] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Jun  1 21:35:04 John-Laptop kernel: [   23.736943] Console: switching to colour frame buffer device 160x50
Jun  1 21:35:04 John-Laptop NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/net/wlan0, iface: wlan0)
Jun  1 21:35:04 John-Laptop NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  1 21:35:04 John-Laptop NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:07.0/net/eth0, iface: eth0)
Jun  1 21:35:04 John-Laptop NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:07.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  1 21:35:04 John-Laptop NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  1 21:35:04 John-Laptop NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): using nl80211 for WiFi device control
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): now managed
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): bringing up device.
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): preparing device.
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  1 21:35:04 John-Laptop kernel: [   24.817959] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  1 21:35:04 John-Laptop kernel: [   24.818851] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  1 21:35:04 John-Laptop dbus[757]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jun  1 21:35:04 John-Laptop dbus[757]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> wpa_supplicant started
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  1 21:35:04 John-Laptop NetworkManager[806]: <info> (wlan0): supplicant interface state: ready -> inactive

After running these commands I shutdown and restarted into puppy. The wireless switch lights up immediately puppy has finished loading kernel modules. I then shut down puppy and restarted Ubuntu 12.04 and as usual the wireless stays alive and connects fine. I then composed this post...

Thanks

---

### Post by wildmanne39 on 2012-06-01
Hi, see if this helps:
```
sudo su 
echo ath5k >> /etc/modules 
exit
```
Thanks

---

### Post by JohnParr on 2012-06-02
Hi, unfortunately that has not had any effect, with or without the extra lines you suggested in rc.local. I have checked the /etc/modules file and ath5k was appended.

About a year ago the problem was reversed. I was using Ubuntu 10.10 then and that turned the wireless on every time from original install. Lucid Puppy 5.2 on the other hand did not turn on the wireless if booted from cold. The solution was to instal a patch for puppy that if I recall correctly had a comment to the effect, "we forgot to include rfkill in 5.2". I will see if I can find the relevant link later but whilst it had the same symptoms the solution may well be different.

I am aware that the acer-wmi module can be started with some parameters including one "force series". This makes it work as it should for a particular model of laptop. I will try all the permutations of that.

Thanks again for all your suggestions

---

### Post by JohnParr on 2012-06-03
The link I referred to is [here ]("http://www.murga-linux.com/puppy/viewtopic.php?p=452093#452093")

It solved issues with similar symptoms for one version of Puppy Linux.

There is some news to report though. I checked what happens with a  Ubuntu 10.10 Live disk and found it works fine. Wireless is switched on  during the boot process. I checked what kernel was in play and have  added it to my Ubuntu 12.04 install (2.6.33.2). The result was that  wireless works from cold boot. However there are two quirks that I have  noticed so far:


[LIST=1]
[*]The laptop runs hot (I think it did this when I ran Ubuntu 10.10)
[*]The  launcher is default size, bigger than I like it and the option to  change the size does not appear in the "Appearance" system setting like  it does normally
[/LIST]
Next step is to look through the Kernel release notes since 2.6.33.2 and see if there is an optimal kernel to use...

I will also try the force_series parameter with acer-wmi. So far I have  found the following mentioned in posts and code some of which seem to  work with several laptop models


[LIST=1]
[*]290
[*]2020
[*]2490
[*]4000
[*]5020
[*]6805
[*]95400
[/LIST]
I will also try 5040 but I don't think there is any code that deals specifically with my laptop model.

---

### Post by wildmanne39 on 2012-06-03
Hi, I would not go backwards that far with a kernel, I would try going forward if need be.
Good Luck

---

### Post by JohnParr on 2012-06-05
Ok, so the force_series approach did not work but I do seem to have success with a newer kernel. There are a lot to choose from so for no special reason I went for 3.0.0 and so far its working fine. The laptop is running cool, the launcher is the size I want it and the wireless card powered on from cold.

The kernel is a mainline kernel from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-oneiric/")

I'll post the details of any thing else I find out on this but if it works reliably I've better things to spend time on.....

Big thanks to wildmanne39 for his suggestions

---

### Post by wildmanne39 on 2012-06-05
Hi, glad you got it working you did a great job.

In my opinion it is always better to go forward and not backwards unless absolutely necessary.
Enjoy

---

