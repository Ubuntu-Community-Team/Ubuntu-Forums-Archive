---
title: "Broadcom bcm4311 installed but not recognized (??) in 8.10"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Unparallelogram on 2009-01-04
I've just finished a clean install of Ubuntu 8.10 and found that my wireless does not work. As far as I can tell, I have the relevant module installed and loaded. The wl module shows up in the restricted drivers dialog and in lsmod. However, my computer sometimes seems like it doesn't even realize I have the appropriate hardware that it should be using it for. I'm not sure if this is a module conflict or what, and am slightly afraid to poke around too much on my own.

Potentially relevant system info:

Dell Vostro 1000 laptop
w/ Broadcom BCM4311 chipset

This has worked in the past through ndiswrapper under Ubuntu, and wl under Fedora. I think I even got bcm43xx working once but I don't remember for sure. Not sure why it suddenly breaks in this version.

Currently the wireless light is off and the wireless hotkey does nothing.

(For the record, no I'm not running around logged in as root, just using sudo -i for poking with stuff.)

> root@unparallelogram:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
root@unparallelogram:~# 


> root@unparallelogram:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:af:96:28  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feaf:9628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4343090 (4.3 MB)  TX bytes:297889 (297.8 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

root@unparallelogram:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@unparallelogram:~# 


> root@unparallelogram:~# lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
rfkill_input           12672  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
arc4                    9984  2 
ecb                    10880  2 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
crypto_blkcipher       25476  1 ecb
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                45200  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
b43                   131356  0 
sdhci_pci              15360  0 
serio_raw              13444  0 
sdhci                  23940  1 sdhci_pci
dcdbas                 15008  0 
pcspkr                 10624  0 
soundcore              15328  1 snd
mmc_core               58268  1 sdhci
ricoh_mmc              11904  0 
k8temp                 12416  0 
evdev                  17696  11 
rfkill                 17176  2 rfkill_input,b43
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
i2c_piix4              16144  0 
mac80211              216820  1 b43
i2c_core               31892  1 i2c_piix4
cfg80211               32392  1 mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
wl                   1076372  0 
ieee80211_crypt        13572  1 wl
video                  25104  0 
output                 11008  1 video
battery                18436  0 
wmi                    14504  0 
ac                     12292  0 
button                 14224  0 
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
pata_acpi              12160  0 
sg                     39732  0 
b44                    35984  0 
mii                    13440  1 b44
pata_atiixp            12800  0 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
usbcore               148848  4 usbhid,ehci_hcd,ohci_hcd
ahci                   37132  3 
ssb                    40580  2 b43,b44
libata                177312  4 ata_generic,pata_acpi,pata_atiixp,ahci
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
root@unparallelogram:~# 


> root@unparallelogram:~# lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:96:28
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.100 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:60:e1:f3:d7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: c6:49:ea:dd:e4:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@unparallelogram:~# 


---

### Post by Ayuthia on 2009-01-04
Please try the following in the Terminal and see if it works:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```
If it works, just add the following:
```
echo wl|sudo tee -a /etc/modules
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```And that should allow it to work when the system restarts

---

### Post by Unparallelogram on 2009-01-04
> mpan@unparallelogram:~$ sudo /etc/network/interfaces restart
sudo: /etc/network/interfaces: command not found
mpan@unparallelogram:~$ 


However, it seems NetworkManager took over and restarted stuff for me and now my wireless works.

Thank you!

Should I still be running the other commands or not?

PS

It looks like the file exists but isn't executable nor does it seem to contain anything executable.

> mpan@unparallelogram:~$ cd /etc/network
mpan@unparallelogram:/etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d	if-up.d  interfaces
mpan@unparallelogram:/etc/network$ ls -la
total 28
drwxr-xr-x   6 root root 4096 2008-10-29 18:54 .
drwxr-xr-x 122 root root 4096 2009-01-04 17:21 ..
drwxr-xr-x   2 root root 4096 2008-10-29 19:06 if-down.d
drwxr-xr-x   2 root root 4096 2008-10-29 19:10 if-post-down.d
drwxr-xr-x   2 root root 4096 2008-10-29 19:10 if-pre-up.d
drwxr-xr-x   2 root root 4096 2008-10-29 19:11 if-up.d
-rw-r--r--   1 root root   32 2009-01-04 10:33 interfaces
mpan@unparallelogram:/etc/network$ sudo /etc/network/interfaces restart
sudo: /etc/network/interfaces: command not found
mpan@unparallelogram:/etc/network$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

mpan@unparallelogram:/etc/network$ 



---

### Post by Ayuthia on 2009-01-05
Sorry about the /etc/networking/interface command.  I meant to use /etc/init.d/networking instead.  However since Network Manager picked it up, it does not matter.  To make it work on reboots you should do the following:
```
echo wl|sudo tee -a /etc/modules
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

---

