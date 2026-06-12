---
title: "[SOLVED] Realtek RTL8187SE - 8.10 - LG X110"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by helder815 on 2008-12-30
Need some help setting up wireless on netbook

Hardware:

```
Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

```

```
helder@X110-01:~$ lspci
<snip>
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
helder@X110-01:~$ lsusb
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 002: ID 5986:0203 Acer, Inc 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
helder@X110-01:~$ 

```

```
helder@X110-01:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:da:9c:a0  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:feda:9ca0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4036 errors:0 dropped:471217228 overruns:0 frame:0
          TX packets:3489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4018864 (4.0 MB)  TX bytes:595256 (595.2 KB)
          Interrupt:221 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

helder@X110-01:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

I didn't know what to look for in this next one so here is all of it, sorry

```
helder@X110-01:~$ lsmod | grep wlan
helder@X110-01:~$ lsmod | grep pan0*
helder@X110-01:~$ lsmod | grep wlan*
helder@X110-01:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
i915                   38144  2 
drm                    86056  3 i915
af_packet              25728  2 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
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
wmi                    14504  0 
uvcvideo               62728  0 
battery                18436  0 
evdev                  17696  11 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
ac                     12292  0 
video                  25104  0 
output                 11008  1 video
snd_seq_oss            38528  0 
serio_raw              13444  0 
snd_seq_midi           14336  0 
psmouse                45200  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
libusual               27156  1 usb_storage
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  4 usb_storage,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
r8169                  35972  0 
uhci_hcd               30736  0 
usbcore               148848  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

I did not do a dmesg. Again not sure what to look for and it's long.

```
helder@X110-01:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

```
helder@X110-01:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

helder@X110-01:~$ lsb_release -d
Description:	Ubuntu 8.10
helder@X110-01:~$ uname -mr
2.6.27-9-generic i686
helder@X110-01:~$ sudo /etc/init.d/networking restart
[sudo] password for helder: 
 * Reconfiguring network interfaces...                                                                                                         Ignoring unknown interface eth0=eth0.
                                                                                                                                        [ OK ]


```


Any help at all would be great. I have tried the deb package for the MSI wind ( same card) and ndiswrapper with LG's XP driver with no success.

I have started looking for a possible replacement card as well so suggestions are welcome.

Thanks to all in advance.

---

### Post by helder815 on 2008-12-30
I don't think the guide asks for this but here goes.

```
helder@X110-01:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:da:9c:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.194 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:12:97:80:40:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
helder@X110-01:~$ 

```

---

### Post by Del_ on 2008-12-30
It seems it has the same wireless as MSI Wind, and you will find directions for installing the drivers here:
[http://zoltron.blogspot.com/2008/12/my-new-lg-x110-ubuntu-810-installed.html](http://zoltron.blogspot.com/2008/12/my-new-lg-x110-ubuntu-810-installed.html)

---

### Post by helder815 on 2008-12-30
This worked. i followed the link to the French guide. I don't read French but cut and pasted all the commands into terminal and now have wireless. 

Thank you!

---

### Post by helder815 on 2009-01-04
Just thought I would give everyone an update. 

 The fix provided at [http://julienpecqueur.com/tutoriaux/install_driverwifi.html](http://julienpecqueur.com/tutoriaux/install_driverwifi.html) Does fix the driver issue and works well. Unfortunately there seems to be some connectivity issues. I have tried several different things but I am no expert and always seemed to end up with not network. At best, removing all security at the router side allowed me to connect to my home network. At worst, I lost both wired and wireless connectivity at home.

I have a copy of 8.04 running off a USB stick with instructions from PenDrive Linux and the drive fix mentioned above. It seems to work well and my guess is as long as i stay away from any updates it will continue to work.  

As for everyday use I have gone back to WindowsXP and wait to see what happens.

---

### Post by CPNowell on 2009-01-20
Just thought I would let everyone know that this worked perfectly for an Advent 4213 Netbook also... :D

Now to set about the built-in 3G module... (unless someone has already done it?)

Colin

---

