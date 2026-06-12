---
title: "Network Stalls..."
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by cdano on 2006-02-09
Symptom:

Install was fine from ISO image. However, after install, I've noticed that any large file transfer stalls after a few seconds. I first noticed this when I tried to run the update. It would start and then just get stuck and finally just report "Failed." I then tried to download a 40M file from another server in Firefox- it gets about 200K in, then fails. On a laptop on the same network in the same switch, no problems. A redhat install on another server in the same network, no problems. Ifconfig is reporting no errors, dropped, overruns, collisions, etc. All just receive and transmit packet counts.

Hardware:

Dell Dimension L800r with its built-in Intel ethernet chipset.
I've also tried inserting an old generic PCI ethernet card in it which works fine in another version of Linux and was able to configure it, but then I received the same result.
I've tried different switches, ethernet cables, etc.
I'm on broadband and I have no other problems.
On the same switch, I have a redhat install on the exact same type of machine with no problems.

So to sum up, I've tried both onboard and a seperate ethernet card, different cables, different switches, and have the same result.  I'm able to do casual browsing, but any streaming video/file downloads stall.

Anyone have any ideas?

More info..

Module                  Size  Used by
sg                     33696  0 
scsi_mod              124872  1 sg
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0 
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  6 
af_packet              20232  4 
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
snd_ens1371            22240  1 
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
hw_random               5268  0 
shpchp                 80612  0 
pci_hotplug            24628  1 shpchp
intel_agp              21276  1 
agpgart                32328  2 intel_agp
dm_mod                 50364  1 
tsdev                   7616  0 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  0 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
ne2k_pci               10464  0 
8390                    9088  1 ne2k_pci
e100                   32768  0 
mii                     5248  1 e100
uhci_hcd               28048  0 
usbcore               104188  2 uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  610 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


0000:00:00.0 Host bridge: Intel Corp. 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:01:01.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
0000:01:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
0000:01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)


eth0      Link encap:Ethernet  HWaddr 00:03:47:48:5A:73  
          inet6 addr: fe80::203:47ff:fe48:5a73/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:80:C8:C0:F9:93  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fec0:f993/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1877610 (1.7 MiB)  TX bytes:154723 (151.0 KiB)
          Interrupt:9 Base address:0xdf80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1039166 (1014.8 KiB)  TX bytes:1039166 (1014.8 KiB)

(I changed my actual eth1 address above due to paranoia)

---

### Post by cdano on 2006-02-21
FYI - I tried all kinds of things, disabling IPV6 among them, to no avail.  I am writing this from a fresh installation of DEBIAN on the same box.  I did a net install and am able to transfer large files with no stalling.  Therefore, there is some incompatibility with UBUNTU and this machine (Dell Dimsnion L800r).  Someone should take a look at it, I'd love to run UBUNTU but it just doesn't work on my hardware correctly.:neutral:

---

### Post by jamesr on 2006-02-21
To help identify the problem post the ifconfig from the debian install, because eth0 is not showing an address under inet4 whereas it seen under inet6. Eth1 being seen by both.
I am assuming that you had both NICs at this time.

How are you connecting to the internet via a router?

---

