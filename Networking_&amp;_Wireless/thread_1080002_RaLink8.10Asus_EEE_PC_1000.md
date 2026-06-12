---
title: "RaLink/8.10/Asus EEE PC 1000"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Merk2 on 2009-02-24
Hi again, my asus cannot connect to wireless internet while using ubuntu (it can connect via direct line, and it can connect while in xandros, but I want to use ubuntu)

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink Device 0781
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
```

lsusb:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink Device 0781
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 005: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 003: ID 0930:6545 Toshiba Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c51b Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:22:15:5b:82:30  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe5b:8230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25381 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:50953331 (50.9 MB)  TX bytes:2475539 (2.4 MB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14264 (14.2 KB)  TX bytes:14264 (14.2 KB)
```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

lsmod:

```
Module                  Size  Used by
ndiswrapper           196380  0 
ipv6                  263972  10 
af_packet              25728  2 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  2 
sco                    18308  2 
l2cap                  30464  16 bnep,rfcomm
ppdev                  15620  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq_dummy          10884  0 
btusb                  19736  3 
bluetooth              61924  11 bnep,rfcomm,sco,l2cap,btusb
snd_seq_oss            38528  0 
psmouse                45200  0 
snd_seq_midi           14336  0 
serio_raw              13444  0 
atl1e                  40212  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              33724  1 
pcspkr                 10624  0 
agpgart                42184  3 drm,intel_agp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
video                  25104  0 
output                 11008  1 video
ac                     12292  0 
evdev                  17696  12 
eeepc_laptop           16528  0 
button                 14224  0 
battery                18436  0 
squashfs               46600  1 
loop                   23180  4 
aufs                  169892  1 
exportfs               12544  1 aufs
usb_storage            81728  1 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
libusual               27156  1 usb_storage
ext3                  133256  2 
jbd                    55444  1 ext3
ext2                   72456  0 
mbcache                16004  2 ext3,ext2
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  1 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  4 usb_storage,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  9 ndiswrapper,uvcvideo,btusb,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
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

sudo lshw -c network:

```
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:5b:82:30
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.6 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:5a:3c:a2:00:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

uname -mr: 2.6.27-7-generic i686

networking restart:

```
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.
```

Other stuff:

I took down some numbers from lspci and lspci -n and I -think- my ralink card is 0781. Specifically, I recorded this output:

```
01:00.0 Network controller: RaLink Device 0781

01:00.0 0280: 1814:0781
```

I installed ndiswrapper and generally know how to use it, but there are a few major problems preventing me from using it:

1. I don't know which driver to get.
2. The RaLink site [http://www.ralinktech.com/ralink/Home/Support.html](http://www.ralinktech.com/ralink/Home/Support.html) has no indication of which one is right for me.
3. Even if I download one of them, I don't know what to do with it. I've never installed any drivers in ubuntu.
4. I'm pretty much a first time linux/ubuntu user so every guide I've found on installing drivers has been too specific and technical to be useful to me.

I'd really appreciate it if someone could help me determine what to do and maybe more importantly **how to do it**. Many thanks in advance!

---

### Post by tlois on 2009-02-25
A few ideas- I think if you search for my user name it should take you to a post in a wireless thread that got mine working on my eee box.  Found it:  [http://www.ubuntu-eee.com/wiki/index.php5?title=Getting_the_network_drivers_working_on_the_901](http://www.ubuntu-eee.com/wiki/index.php5?title=Getting_the_network_drivers_working_on_the_901)

That worked for me- I think it is the same driver.  Also, if you have access to a Linksys USB wireless dongle, that will work temporarily while you get the internal to work.

Another thing:  I found that when I downloaded/played with the live version of the beta Ubuntu (9--??) the wireless worked- tada- I didn't have to install anything, so look at that option too.  AND eeebuntu, which is what I am running on the eeebox worked immediately too.

Good luck.

---

### Post by ShakataGaNai on 2009-02-25
I can tell you for sure that the Wireless works in 9.04 out of the box.  I'm not sure what you need to do to get it working, but if there is any commands I can run to get you info you need, let me know.

---

### Post by Merk2 on 2009-02-26
Thanks everyone! I installed eeebuntu, and the wireless worked out of the box, which was a great relief. No need to mess around with ndiswrapper or any of that.

Though I've now run into a slightly different, much less critical problem. My asus has "40 GB" which is really an 8 GB SSD + a 32 GB SSD card that sticks into the side. I installed eeebuntu on the 8 GB part, but it doesn't seem to recognize that it can access another 32 GB. Do I need to also install eeebuntu on the 32 GB card, or is there an easier way for me to make it recognize the extra storage space?

---

### Post by tlois on 2009-02-26
You mean you have flash memory in the SD slot and it is not seeing it is there?  Hmmm.  I use it in both the eeebox and eee701 and the only problem I have is that it insists on having it on the desktop.  

Can you try some mount command in terminal?  I assume you have taken it out, put it back in.  Rebooted?

There is also an eeeubuntu forum that could be useful.

Take care.  Glad you got the wireless working!  Hooray, right??

---

