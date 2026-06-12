---
title: "wireless Linksys WUSB54GC on Ubuntu 8.10"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by pb099 on 2009-02-05
Hi there,

I am new to Linux/Ubuntu, so I apologise if this is FAQ (but I have been looking around for several days now and could not find a solution, or at least one I could understand...)

I just cannot get the wireless to connect to the network, even though it looks like the hardware is recognised. It is also not an issue of the router, because I just manage to connect using a windows box sitting right to this one.

If anyone could think of telling me what to do, I am sending the information as required in ticket HOWTO post a Wireless issue

Thanks in advance

pbarros@PCBLinux:~$ lsusb |grep Linksys
Bus 005 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]

pbarros@PCBLinux:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:0f:15:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pbarros@PCBLinux:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=6 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


pbarros@PCBLinux:~$ sudo lsmod
Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  4 
binfmt_misc            16904  1 
i915                   38528  2 
drm                    86056  3 i915
sco                    18308  2 
bridge                 56980  0 
rfcomm                 44432  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
wmi                    14504  0 
sbs                    19464  0 
container              11520  0 
video                  25232  0 
output                 11008  1 video
sbshc                  13440  1 sbs
pci_slot               12680  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
arc4                    9984  2 
ecb                    10880  2 
snd_intel8x0           37532  3 
crypto_blkcipher       25476  1 ecb
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
dcdbas                 15008  0 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
rt73usb                30464  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
rfkill                 17176  1 rt2x00lib
snd_rawmidi            29824  1 snd_seq_midi
led_class              12164  1 rt2x00lib
serio_raw              13444  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
psmouse                45200  0 
mac80211              216820  2 rt2x00usb,rt2x00lib
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
cfg80211               32392  2 rt2x00lib,mac80211
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
evdev                  17696  6 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  2 
libata                178208  3 ata_generic,pata_acpi,ata_piix
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,uhci_hcd
tg3                   129924  0 
libphy                 27392  1 tg3
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

pbarros@PCBLinux:~$ lsmod | grep rt
rt73usb                30464  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  2 rt2x00usb,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
iTCO_vendor_support    11652  1 iTCO_wdt
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
agpgart                42184  3 drm,intel_agp
usbcore               149360  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,uhci_hcd


pbarros@PCBLinux:~$ sudo dmesg |grep rt7
[   15.941366] Registered led device: rt73usb-phy0:radio
[   15.941394] Registered led device: rt73usb-phy0:assoc
[   15.941417] Registered led device: rt73usb-phy0:quality
[   15.941861] usbcore: registered new interface driver rt73usb
[   27.699426] firmware: requesting rt73.bin

pbarros@PCBLinux:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:cb:fd:76
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.29a ip=168.202.99.126 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:7e:0f:15:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:29:90:10:03:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

pbarros@PCBLinux:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

pbarros@PCBLinux:~$ lsb_release -d
Description:	Ubuntu 8.10

pbarros@PCBLinux:~$ uname -mr
2.6.27-11-generic i686

pbarros@PCBLinux:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                         Ignoring unknown interface eth0=eth0.
                                                                                                        [ OK ]

---

### Post by jimbob on 2009-02-23
I don't know that much about it but from this post [http://ubuntuforums.org/showthread.php?t=1076411&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=1076411&highlight=wusb54gc) it looks like it should work "out of the box".

You don't have an ESSID defined, perhaps that is the problem.

---

### Post by speedwell68 on 2009-02-23
Ok, I bought one of these today, on the basis that it was supposed to work 'out of the box' in Linux.  I got the exact same problems detailed above.  It was connected using the extension lead supplied.  After much messing around I plugged the thing directly into a USB port and it instantly worked, go figure.  So if you are using the extension lead, try it without.

---

### Post by jimbob on 2009-02-23
Thanks, that's good information.  I'm planning on buying one myself within the month.

Which distro are you running?

Out of curiosity, what do they sell for over there?

---

### Post by speedwell68 on 2009-02-23
> **jimbob said:**
> Thanks, that's good information.  I'm planning on buying one myself within the month.

Which distro are you running?

Out of curiosity, what do they sell for over there?

Ubuntu 8.10.  Mine just cost me the princely sum of £25 GBP, which is about $36 USD.

---

### Post by MatthewMetzger on 2009-03-11
Mine didn't come with an extension. I plug it directly into the computer and it still does not work. Any suggestions or help on this would be great.

thanks

---

### Post by jimbob on 2009-03-11
It seems like you are out of luck for a while.  If you bought it new it probably has the newer RT3070 chip like mine.

See my tale of woe here: [http://ubuntuforums.org/showthread.php?t=1089893](http://ubuntuforums.org/showthread.php?t=1089893)

I have sent Ralink two emails so far begging for a module that would compile but as of now had no reply.

---

### Post by eeperson on 2009-03-12
If it is an rt73 chipset then you may need to install the package rt73-common from the repository.  This contains the drivers for that chipset and it is usually not installed by default.  

If you want to check what chipset you have, you can usually see by running the command:
```
lsusb
```

EDIT: This is intended more for MatthewMetzger as the OP appears to already have the driver installed.

---

### Post by eeperson on 2009-03-12
pb099 what kind of problems are you still having?  Is the the network manager just not showing you that you have a wireless connection?  It appears that your wireless adapter is installed and functioning.

---

### Post by ayyappa1 on 2009-04-06
Hi,
When someone googles with keywords: WUSB54GC Ubuntu 8.10 , this page pops up second. Hence i have added the link below for noobs like me to find the relative threads at ease.

Refer link below for installation:
[http://ubuntuforums.org/showthread.php?t=923387&page=4](http://ubuntuforums.org/showthread.php?t=923387&page=4)

Sorry to barge in to this thread.

---

### Post by eeperson on 2009-04-06
> **ayyappa1 said:**
> Hi,
When someone googles with keywords: WUSB54GC Ubuntu 8.10 , this page pops up second. Hence i have added the link below for noobs like me to find the relative threads at ease.

Refer link below for installation:
[http://ubuntuforums.org/showthread.php?t=923387&page=4](http://ubuntuforums.org/showthread.php?t=923387&page=4)

Sorry to barge in to this thread.

Is downloading a tarball of the driver is really necessary for 8.10 (although it probably is for previous versions)?  People on this forum have successfully used the repository driver.  I personally have used the repository driver for Debian Lenny (which is one kernel version behind Intrepid) without issue.

---

