---
title: "Help setting up wireless - here is all info &quot;Sticky&quot; guide asked for"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by wilhelk on 2009-04-12
**Machine Brand Model:**
Windows Vista PC 2007 - AMD processors 

**Wireless Brand, Model and Wireless Chipset:**
kyle@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

kyle@ubuntu:~$ lsusb
Bus 002 Device 004: ID 05ac:1292 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1532:0105 Razer USA, Ltd 
Bus 001 Device 004: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 003: ID 1532:0107 Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**3 ) check interface:**
kyle@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

kyle@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:86:ce:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23172 (23.1 KB)  TX bytes:23172 (23.1 KB)

[B]
4 ) Check for modules:[/B]
kyle@ubuntu:~$ lsmod
Module                  Size  Used by
wlan_scan_sta          20608  0 
ath_pci                99096  0 
wlan                  211952  2 wlan_scan_sta,ath_pci
ath_hal               198864  1 ath_pci
ipv6                  263972  10 
af_packet              25728  2 
rfkill_input           12672  0 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  0 
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
wmi                    14504  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
psmouse                45200  0 
dcdbas                 15008  0 
pcspkr                 10624  0 
serio_raw              13444  0 
b43                   131356  0 
joydev                 18368  0 
rfkill                 17176  2 rfkill_input,b43
k8temp                 12416  0 
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
led_class              12164  1 b43
evdev                  17696  8 
input_polldev          11912  1 b43
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
i2c_nforce2            14468  0 
i2c_core               31892  1 i2c_nforce2
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
sata_nv                30600  2 
pata_amd               18692  0 
ata_generic            12932  0 
libata                177312  4 pata_acpi,sata_nv,pata_amd,ata_generic
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
ehci_hcd               43276  0 
ohci_hcd               31888  0 
forcedeth              61328  0 
ssb                    40580  1 b43
dock                   16656  1 libata
usbcore               148848  5 usbhid,ehci_hcd,ohci_hcd
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  7 

[B]
5 ) Kernel boot messages[/B]
- If you need this let me know - it was HUGE!

**6 ) Network configuration**
- did not work for some reason
[B]
7 ) Scan for networks:[/B]
kyle@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


**8 ) Ubuntu Version: **
kyle@ubuntu:~$ lsb_release -d
Description:	Ubuntu 8.10

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
kyle@ubuntu:~$ uname -mr
2.6.27-7-generic i68

**10 ) Restarting the network:**
kyle@ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for kyle: 
 * Reconfiguring network interfaces...                                   [ OK ] 


Okay - that was fun - Don't know what that code means... but basically I setup the internet connection using "Add wireless" added WAP, SSID, Password, Etc - and it won't even try to connect to it. I can't seem to find the "Allow roaming" checkbox either. I use VISTA and it is a stantionary PC - I am wireless which works fine on windows... If needed, I can plug it in LAN wise - it would just be a hassle :P

Thanks,
Kyle

---

### Post by wilhelk on 2009-04-12
Also - I am also "Wired" through my internet (hooked up through the LAN) - its just the wireless that doesn't work properly I guess.

---

### Post by chili555 on 2009-04-12
Please check here: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

Especially read this:> Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.Network Manager will actively *prohibit* your wireless as long as the wire is plugged in. Please unplug the wire, restart networking and let us know the result.

---

### Post by wilhelk on 2009-04-12
Hey Chilli,
Thanks for responding - however, when I unplug it still doesn't pick up my wireless - I do know that if I am plugged in - it can't... but when I unplug my computer it is a fish dead in the water since my wireless is not working

---

### Post by iponeverything on 2009-04-12
Go to

System -> Administration -> Hardware Drivers

to see if there is driver that you can enable for your broadcom wireless card.

```
01:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

