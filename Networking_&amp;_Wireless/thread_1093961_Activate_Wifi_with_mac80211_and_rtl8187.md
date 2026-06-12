---
title: "Activate Wifi with mac80211 and rtl8187"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by reyman on 2009-03-12
Hello Community !
I'm a new french noob on ubuntu 8.10 intrepid and wifi chipset rtl8187

I have some question about wifi, and google don't help me really...

a) There are two families of drivers - ieee80211 and mac80211.  Aircrack-ng say in tutorial that "mac80211 is starting to replace ieee80211." 
Ok , so first question ... Driver of rtl8187 bu default in ubuntu intrepid is mac80211 or ieee80211 ? how can i desactivate the ieee80211 driver to switch in mac80211 ?  Why when i blacklist the driver in modprobe.d/blacklist my wifi is up after rebooting ? I don't understand where is the driver who launch wifi when i blacklist my driver wifi (sic bis) ? 

so, how can i desinstall wifi on ubuntu to restart at zero ?

b ) Last night (sic), i try to install the " **compat-wireless** on Ubuntu " with sudo apt-get install linux-backports-modules-intrepid ... I'm rebooting but no trace of interface "wmaster" >> mac absent and ieee80211 are in the place ... SIC..
how can i activate mac80211 ? and driver8187 need to be install when i install compass or not ? 

c)How can i compil kernel to desactivate ieee80211 ? 

Thanks a lot for reading and helping me ...
reyman :KS

---

### Post by reyman on 2009-03-12
[B]UP with more information on my problem !!
[/B]

1 ) Machine Brand and Model (PC/Laptop):
Code:
> 
PC C2DUO E6750 @3.2Ghz ; 4GoRam WIFI;  RTL8187

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci
> 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)


$ lsusb
> 
Bus 004 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter


3 ) check interface:
Code:

$ ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:6b:b8:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:7 erreurs:0 :0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:464 (464.0 B) Octets transmis:464 (464.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:19:f5:47  
          inet adr:192.168.1.2  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::215:afff:fe19:f547/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:941 erreurs:0 :923 overruns:0 frame:0
          TX packets:906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1055424 (1.0 MB) Octets transmis:199536 (199.5 KB)


$ iwconfig

> 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     802.11b/g linked  ESSID:"N9UF_TEL9COM"  
          Mode:Managed  Channel=6  Access Point: 00:16:CF:15:1F:46   
          Bit Rate=11 Mb/s   Tx-Power=8 dBm   
          Retry:on   Fragment thr:off
          Link Quality=81/100  Signal level=60 dBm  Noise level=19 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


4 ) Check for modules:
Code:

$ lsmod

> 
Module                  Size  Used by
ipv6                  263972  14 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
ieee80211_crypt_wep_rtl    11904  1 
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
lbm_cw_mac80211       215856  0 
lbm_cw_cfg80211        46744  1 lbm_cw_mac80211
eeprom_93cx6           10240  0 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
evdev                  17696  6 
r8187                  49796  0 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
ieee80211_rtl          62596  1 r8187
ieee80211_crypt_rtl    13316  2 ieee80211_crypt_wep_rtl,ieee80211_rtl
nvidia               6909268  40 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
i2c_core               31892  1 nvidia
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
button                 14224  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
agpgart                42184  2 nvidia,intel_agp
pci_hotplug            34976  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
pata_acpi              12160  0 
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_jmicron           11136  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
ata_generic            12932  0 
ahci                   37132  2 
sky2                   53380  0 
ehci_hcd               43788  0 
libata                178208  4 pata_acpi,pata_jmicron,ata_generic,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
usbcore               149360  5 r8187,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

[B]
Ps : NO MAC80211 here,why ?? :([/B]

5 ) Kernel boot messages
Code:

$ dmesg

> 
[   12.802325] rtl8187: Initializing module
[   12.802327] rtl8187: Wireless extensions version 22
[   12.802328] rtl8187: Initializing proc filesystem
[   12.802572] rtl8187: Enabling 14 channels.
[   12.802828] rtl8187: MAC chip version: 04
[   12.802829] rtl8187: Card type: CD
[   12.802951] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[   12.954200] rtl8187: Card MAC address is 00:15:af:19:f5:47
[   13.128954] rtl8187: RF Chip ID: 05
[   13.148703] rtl8187: Card reports RF frontend Realtek 8225
[   13.148706] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[   13.148707] rtl8187: WW:use it with care and at your own risk and
[   13.148708] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[   13.183308] rtl8187: This seems a new V2 radio
[   13.183449] rtl8187: PAPE from CONFIG2: 0
[   13.183637] rtl8187: Driver probe completed
[   13.183654] usbcore: registered new interface driver rtl8187
[   13.345598] Error: Driver 'rtl8187' is already registered, aborting...
[   13.345602] usbcore: error -17 registering interface 	driver rtl8187
[   22.833107] rtl8187: Card successfully reset
[   23.056108] rtl8187: RR:84 BRSR: 1ff
[   26.752080] rtl8187: Setting SW wep key
[   26.832072] rtl8187: Setting SW wep key
[   26.832219] rtl8187: Setting SW wep key
[   26.832295] rtl8187: Setting SW wep key
[   26.832386] rtl8187: Setting SW wep key
[   26.834938] GOT WX GET SCAN WX_SEM LOCKGOT WX GET SCAN WX_SEM LOCKGOT WX GET SCAN WX_SEM LOCK<6>rtl8187: Setting SW wep key
[   81.927954] rtl8187: Setting SW wep key
[   81.928278] rtl8187: Setting SW wep key
[ 1748.593441] rtl8187: Setting SW wep key
[ 1748.593475] rtl8187: Setting SW wep key
[ 1748.593491] rtl8187: Setting SW wep key
[ 1748.593506] rtl8187: Setting SW wep key
[ 1748.593520] rtl8187: Setting SW wep key
[ 1748.593535] rtl8187: Setting SW wep key
[ 1748.645034] rtl8187: RX process aborted due to explicit shutdown
[ 1751.768170] rtl8187: Card successfully reset
[ 1751.979358] rtl8187: wlan driver removed
[ 1753.554840] rtl8187: Enabling 14 channels.
[ 1753.555153] rtl8187: MAC chip version: 04
[ 1753.555155] rtl8187: Card type: AD
[ 1753.555278] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[ 1753.667779] rtl8187: Card MAC address is 00:15:af:19:f5:47
[ 1753.817779] rtl8187: RF Chip ID: 05
[ 1753.836529] rtl8187: Card reports RF frontend Realtek 8225
[ 1753.836530] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[ 1753.836532] rtl8187: WW:use it with care and at your own risk and
[ 1753.836533] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[ 1753.869759] rtl8187: This seems a new V2 radio
[ 1753.869905] rtl8187: PAPE from CONFIG2: 0
[ 1753.870390] rtl8187: Driver probe completed
[ 1761.166931] rtl8187: Card successfully reset
[ 1761.372674] rtl8187: RR:84 BRSR: 1ff
[ 1765.035825] rtl8187: Setting SW wep key
[ 1765.192050] rtl8187: Setting SW wep key
[ 1765.192066] rtl8187: Setting SW wep key
[ 1765.192078] rtl8187: Setting SW wep key
[ 1765.192089] rtl8187: Setting SW wep key
[ 1765.194062] GOT WX GET SCAN WX_SEM LOCKGOT WX GET SCAN WX_SEM LOCKGOT WX GET SCAN WX_SEM LOCK<6>rtl8187: Setting SW wep key
[ 1783.837184] rtl8187: Setting SW wep key
[ 1783.837595] rtl8187: Setting SW wep key



6 ) Network configuration
Code:
$ sudo lshw -C network

> 
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1b:fc:6b:b8:cb
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:9a:09:32:03:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:15:af:19:f5:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.2 multicast=yes wireless=802.11b/g linked



7 ) Scan for networks:
Code:

$ iwlist scan

> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:CF:15:1F:46
                    ESSID:"N9UF_TEL9COM"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 10ms ago


8 ) Ubuntu Version:
Code:

$ lsb_release -d
> Description:	Ubuntu 8.10

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr

> 2.6.27-11-generic i686

10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart
> 
 * Reconfiguring network interfaces...                                                                                   [ OK ] 


Thx a lot !:D

---

### Post by reyman on 2009-03-13
So, Nobody have an idea to help me to activate mac80211 ? :/

---

### Post by marcon00 on 2009-04-25
how did it go ?

---

### Post by Murdoc_of_puts on 2009-10-07
hello, wondering if you've had any luck lately, I'm having about the same problem.  If I come up with some thing I'll tell you.

---

### Post by t0mppa on 2009-10-07
I realize the original post is fairly old, but if you insist you have the same issue down to the smallest details, then here we go.

Thing is ieee80211 and mac80211 are different frameworks and a driver written for one will not work on the other. Think of it like trying to run a diesel engine with gasoline, not a good idea. So, you can't simply disable one framework and active the other. What you have to do is unload & blacklist (stops it from automatically getting loaded during boot up) your old driver and then install & load a new one.

The *lsmod* shows that you still have the r8187 loaded and that's using ieee80211, if you want to upgrade to mac80211, you'll have to unload it with **sudo modprobe -r r8187** and then blacklist it with **echo blacklist r8187 | sudo tee -a /etc/modprobe.d/blacklist.conf**.

As for installing rtl8187, looks like [here]("http://forum.aircrack-ng.org/index.php?topic=5755.0")'s a decent tutorial.

---

