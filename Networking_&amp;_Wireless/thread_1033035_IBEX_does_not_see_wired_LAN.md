---
title: "IBEX does not see wired LAN"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by pgmer6809 on 2009-01-06
Hi.
Running live CD session on Asus Mobo desktop Athlone proc. Currently installed Gutsy. Checking to see if IBEX would work.
Cant get network to work at all.
Tried the fixes recommended in other threads. 
First tried defining a new connection, both static and DHCP using NetworkManager applet. 
No dice. 
Then removed NetworkManager applet, icon goes away in top bar. Also used cmd line to kill ```
/usr/sbin/nm-system-settings
``` process.
Edited the ```
/etc/resolv.conf
``` and ```
/etc/network/interfaces
``` files.
Tried both 
```
iface eth0 inet dhcp
``` and```
 iface eth0 inet static
``` no dice.
```
ifconfig eth0 up
``` 
does not give an error, but running```
 ifconfig eth0
``` does not show an IP and trying to ping, gives network unreacheable.
finally tried ```
ifconfig eth0 inet 192.168.2.40 netmask 255.255.255.0
```
and get an error:
```
SIOCSIFADDF no buffer space available
SIOCSIFNETMASK: cannot assign requested address
```
dmesg output shows that the 'link' eth0 is 'ready', running at 100 mbps etc.
Regardless of failure of ubuntu tools it should be possible in LINUX to manually configure a wired LAN connection. Is there any reliable documentation on how to do this? 
pgmer6809

---

### Post by pgmer6809 on 2009-01-06
Follow up.
On my HP pavillion DV1000 using same LIVE CD wireless works OK. Wired does not.
On my older generic P-III same LIVE CD wired networking works fine. Uses DHCP and runs with no issues.
 
Question:
Any chance that the liveCD tries to use config info already on the hard disk?

Question
Any chance that this problem is driver related? i.e depends on the model of LAN card/chipset you using?

pgmer6809

---

### Post by Jayock on 2009-01-07
Have the same issues with IBEX on my HP mini.  Wireless is great, but wired is not recognized.  Mine is this way on installed version, not sure about live CD, as the mini had no optical drive.

I actually didn't realize this until a couple of days ago, since I never used the wired connection, until I wanted to configure a managed switch, and couldn't.

I havn't looked into the problem much yet, but on mine the wired lan device wont even show up in lspci.  Tried lsusb too, just in case they spliced a USB nic in there, still no luck.  

Do you get a lan card showing up with lspci on yours?  I'm thinking that it may be a similar issue with your HP and mine.

---

### Post by Iowan on 2009-01-07
Have you tried manually disabling one interface, then manually enabling the other one?

---

### Post by pgmer6809 on 2009-01-08
Re Disabling one then enabling another.
1) on the Athlone there is only the wired LAN (which does NOT work).
On the P-III there is only the wired LAN which DOES work.
So I assume you mean on the HP Pavillion.
Answer Yes.
Tried booting with and without the wireless button turned on and off.
Booting without the wireless button completely hides it from Linux.
Even turning it on again once Linux is running does not make the wireless device visible.

Using Gutsy, If I leave the wireless on all the time, then plugging in and unplugging the LAN cable switches to/from wireless just fine. And the wired LAN works fine also.

Using IBEX live CD doing the same thing, also 'switches' from wireless to wired in the NETMANAGER applet, but of course no IP is ever assigned to the wired adapter so even though NETMANGER thinks the switchover is successful the network is down.
Unplugging the wired connection switches back to wireless and the network is up again.

The above is for background only. The real issue is why can we not get IBEX to work with a simple vanilla wired connection, not even with manual setup of all relevant files. 
pgmer6809

---

### Post by lswest on 2009-01-08
post the output of ```
lsmod
sudo lshw -C network
``` from the computer with issues while running the LiveCD and from your gutsy install.  (From the LiveCD you can save it to a text file on your hard drive)

Might be that there's a new driver that should work with your wired connection, but doesn't.

---

### Post by pgmer6809 on 2009-01-09
OK, per lswest request here is the relevant info for the Athlone/Asus Mobo, wired only LAN. Gutsy uses the skge driver for eth0
Under Gutsy:
greg@shadow:~$ ```
 cat gutsy.lshw
```
  sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 13
       serial: 00:0e:a6:a9:15:40
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.11 duplex=full firmware=N/A ip=192.168.2.40 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s

greg@shadow:~$```
 cat gutsy.lsmod
```
lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
fglrx                 656352  15 
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sbs                    19592  0 
container               5504  0 
video                  18060  0 
dock                   10656  0 
button                  8976  0 
ac                      6148  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sbp2                   24072  0 
lp                     12580  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
parport_pc             37412  1 
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
pcspkr                  4224  0 
snd_seq_dummy           4740  0 
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0 
xpad                    9988  0 
snd_seq_oss            33152  0 
snd_via82xx            29336  0 
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_midi            9600  0 
snd_via82xx_modem      16264  0 
snd_ac97_codec        100644  3 snd_emu10k1,snd_via82xx,snd_via82xx_modem
psmouse                39952  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
k8temp                  6656  0 
snd_rawmidi            25728  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
snd_pcm                80388  5 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
i2c_viapro             10004  0 
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               26112  1 i2c_viapro
snd_page_alloc         11400  4 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm
amd64_agp              13700  1 
agpgart                35016  2 fglrx,amd64_agp
emu10k1_gp              4736  0 
gameport               16776  3 snd_via82xx,emu10k1_gp
snd                    54660  18 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_seq_oss,snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ipv6                  273892  10 
joydev                 11328  0 
evdev                  11136  5 
ext3                  133896  4 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  8 
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138760  5 xpad,usbhid,ehci_hcd,uhci_hcd
ata_generic             8452  0 
sata_via               12548  0 
libata                125168  2 ata_generic,sata_via
scsi_mod              147084  2 sbp2,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
skge                   43152  0 
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

Under IBEX.
greg@shadow:/media/Memorex UFD/IBEX$ ```
cat ibex.lshw
```
  sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 13
       serial: 00:0e:a6:a9:15:40
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:37:a2:36:c7:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
greg@shadow:/media/Memorex UFD/IBEX$ ```
cat ibex.lsmod
```
lsmod
Module                  Size  Used by
usb_storage            81728  1 
libusual               27156  1 usb_storage
af_packet              25728  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
lp                     17156  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
ac                     12292  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
pcspkr                 10624  0 
psmouse                45200  0 
serio_raw              13444  0 
joydev                 18368  0 
evdev                  17696  9 
i2c_viapro             15764  0 
k8temp                 12416  0 
snd_via82xx            32536  2 
i2c_core               31892  1 i2c_viapro
snd_via82xx_modem      19464  0 
snd_mpu401_uart        15360  1 snd_via82xx
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  4 snd_emu10k1_synth
snd_ac97_codec        111652  3 snd_via82xx,snd_via82xx_modem,snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  5 snd_via82xx,snd_via82xx_modem,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  4 snd_via82xx,snd_via82xx_modem,snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  4 snd_mpu401_uart,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
button                 14224  0 
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
emu10k1_gp             10880  0 
snd                    63268  26 snd_via82xx,snd_via82xx_modem,snd_mpu401_uart,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gameport               19468  3 snd_via82xx,emu10k1_gp
amd64_agp              18184  1 
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 drm,amd64_agp
battery                18436  0 
squashfs               46600  1 
loop                   23180  2 
aufs                  169892  1 
exportfs               12544  1 aufs
isofs                  40100  1 
ext3                  133256  0 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
nls_iso8859_1          12032  1 
nls_cp437              13696  2 
vfat                   18816  1 
fat                    57376  1 vfat
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
pata_via               16132  2 
pata_acpi              12160  0 
ata_generic            12932  0 
sata_via               15492  0 
uhci_hcd               30736  0 
ehci_hcd               43276  0 
libata                177312  4 pata_via,pata_acpi,ata_generic,sata_via
usbcore               148848  6 usb_storage,libusual,usbhid,uhci_hcd,ehci_hcd
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci1394               37936  0 
skge                   48144  0 
ieee1394               96324  1 ohci1394
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

and just for completness here is some ifconfig output under ibex
note that the link is UP but no IP address assigned. Also not the lack of buffer space error.

greg@shadow:/media/Memorex UFD/IBEX$ ```
cat ibex.ifconfig
```
ifconfig eth0 inet 192.168.2.40  netmask 255.255.255.0
SIOCSIFADDR: No buffer space available
SIOCSIFNETMASK: Cannot assign requested address
ubuntu@ubuntu:~$```
 ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:a9:15:40  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6609 (6.6 KB)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27932 (27.9 KB)  TX bytes:27932 (27.9 KB)
greg

---

### Post by lswest on 2009-01-09
okay, try unloading (in Ibex) the skge driver with ```
sudo modprobe -r skge
``` and loading the forcedeth generic ethernet module with ```
sudo modprobe forcedeth
``` see if that helps.  If it does get it working, post back and we'll make it permanent for Ibex, or at least tell you how in case you install it.

---

### Post by pgmer6809 on 2009-01-10
> **lswest said:**
> okay, try unloading (in Ibex) the skge driver with ```
sudo modprobe -r skge
``` and loading the forcedeth generic ethernet module with ```
sudo modprobe forcedeth
``` see if that helps.  If it does get it working, post back and we'll make it permanent for Ibex, or at least tell you how in case you install it.

I did that.
What I end up with is no eth0 or other ethernet device at all.
forcedeth is loaded (confirmed with lsmod | grep forcedeth) and skge is not 
(confirmed with lsmod | grep skge) but ifconfig, and network restart show no device eth0. The only devices are lo and pan0.
I tried putting eth0 as static into /etc/network/interfaces and restarting network but I got an error.

I did a script cmd before doing all this so I have a record in a file if you want me to email it. It is prob too long to post here.
pgmer6809

---

### Post by lswest on 2009-01-10
The only thing that tells us is that forcedeth can't work on your device, which is fine, I wasn't sure it would.

Sadly, that also means I'm out of ideas...maybe someone else will have one?

---

### Post by pgmer6809 on 2009-01-10
> **lswest said:**
> The only thing that tells us is that forcedeth can't work on your device, which is fine, I wasn't sure it would.

Sadly, that also means I'm out of ideas...maybe someone else will have one?

Thanks for trying.
I am going to be away for a week, so this is my last post on this for awhile, maybe forever as it looks like IBEX is just not an option for me. (same as Hardy..... when WILL they get it right?)
Here is similar output from my old P-III machine.
It has a different ethernet device of course. The first part is running XUBUNTU (gutsy based version) the second part is running IBEX live CD.
***Both of these work.*** In the IBEX case the NetManager also works.
---------------------------------------------------------------------
**XBUNTU GUTSY on P-III wired LAN only.** 
root@irish:/tmp# ```
lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 00
       serial: 00:60:08:c8:01:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.101 latency=32 link=yes maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=100MB/s

```
lsmod
```
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sg                     36764  0 
sd_mod                 30336  2 
usb_storage            73152  1 
libusual               18448  1 usb_storage
binfmt_misc            12936  1 
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
container               5504  0 
button                  8976  0 
video                  18060  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
battery                11012  0 
ipv6                  273892  8 
lp                     12580  0 
snd_ens1371            27680  1 
gameport               16776  1 snd_ens1371
snd_ac97_codec        100644  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
psmouse                39952  0 
snd                    54660  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
i2c_viapro             10004  0 
i2c_core               26112  1 i2c_viapro
via_agp                11264  1 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  1 via_agp
af_packet              24840  2 
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
floppy                 60004  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
uhci_hcd               26640  0 
usbcore               138760  4 usb_storage,libusual,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:60:08:C8:01:02  
          inet addr:192.168.2.101  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fec8:102/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6082576 (5.8 MB)  TX bytes:457751 (447.0 KB)
          Interrupt:5 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12908 (12.6 KB)  TX bytes:12908 (12.6 KB)

```
 cat /etc/network/interfaces
``` 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**********************************************************
**IBEX LIVE CD on P-III wired LAN only.**
```
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:60:08:c8:01:02  

          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:55 errors:0 dropped:0 overruns:0 frame:0

          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:18112 (18.1 KB)  TX bytes:3271 (3.2 KB)

          Interrupt:5 Base address:0xd000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:216 errors:0 dropped:0 overruns:0 frame:0

          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)



```
ping 192.168.2.1
```

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=1.37 ms

64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.35 ms

^C

--- 192.168.2.1 ping statistics ---

2 packets transmitted, 2 received, 0% packet loss, time 1002ms

rtt min/avg/max/mdev = 1.352/1.361/1.371/0.038 ms

```
cat /etc/newtwork/interfaces 
```

auto lo

iface lo inet loopback


```
 lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 00
       serial: 00:60:08:c8:01:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.101 latency=32 link=yes maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:96:49:4a:3f:68
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
lsmod
```

Module                  Size  Used by

binfmt_misc            16904  1 

af_packet              25728  2 

bridge                 56980  0 

stp                    10628  1 bridge

bnep                   20480  2 

sco                    18308  2 

rfcomm                 44432  0 

l2cap                  30464  6 bnep,rfcomm

bluetooth              61924  6 bnep,sco,rfcomm,l2cap

ppdev                  15620  0 

lp                     17156  0 

speedstep_lib          12676  0 

cpufreq_userspace      11396  0 

cpufreq_stats          13188  0 

cpufreq_powersave       9856  0 

cpufreq_ondemand       14988  0 

freq_table             12672  2 cpufreq_stats,cpufreq_ondemand

cpufreq_conservative    14600  0 

wmi                    14504  0 

video                  25104  0 

output                 11008  1 video

sbs                    19464  0 

sbshc                  13440  1 sbs

pci_slot               12552  0 

container              11520  0 

ac                     12292  0 

iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables

snd_ens1371            30880  3 

gameport               19468  1 snd_ens1371

snd_ac97_codec        111652  1 snd_ens1371

ac97_bus                9856  1 snd_ac97_codec

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

snd_pcm                83204  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss

snd_seq_dummy          10884  0 

evdev                  17696  6 

parport_pc             39204  1 

parport                42604  3 ppdev,lp,parport_pc

snd_seq_oss            38528  0 

snd_seq_midi           14336  0 

psmouse                45200  0 

snd_rawmidi            29824  2 snd_ens1371,snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

serio_raw              13444  0 

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

button                 14224  0 

snd                    63268  16 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

i2c_viapro             15764  0 

pcspkr                 10624  0 

i2c_core               31892  1 i2c_viapro

soundcore              15328  1 snd

via_agp                16256  1 

snd_page_alloc         16136  1 snd_pcm

agpgart                42184  1 via_agp

shpchp                 37908  0 

pci_hotplug            35236  1 shpchp

battery                18436  0 

squashfs               46600  1 

loop                   23180  2 

aufs                  169892  1 

exportfs               12544  1 aufs

isofs                  40100  1 

ext3                  133256  0 

jbd                    55444  1 ext3

mbcache                16004  1 ext3

nls_iso8859_1          12032  1 

nls_cp437              13696  2 

vfat                   18816  1 

fat                    57376  1 vfat

sr_mod                 22212  1 

cdrom                  43168  1 sr_mod

sd_mod                 42264  4 

crc_t10dif              9984  1 sd_mod

usb_storage            81728  1 

libusual               27156  1 usb_storage

sg                     39732  0 

pata_via               16132  2 

pata_acpi              12160  0 

ata_generic            12932  0 

libata                177312  3 pata_via,pata_acpi,ata_generic

3c59x                  48936  0 

mii                    13440  1 3c59x

uhci_hcd               30736  0 

scsi_mod              155212  5 sr_mod,sd_mod,usb_storage,sg,libata

usbcore               148848  4 usb_storage,libusual,uhci_hcd

dock                   16656  1 libata

thermal                23708  0 

processor              42156  2 thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  3

---

### Post by pgmer6809 on 2009-01-10
> **lswest said:**
> The only thing that tells us is that forcedeth can't work on your device, which is fine, I wasn't sure it would.

Sadly, that also means I'm out of ideas...maybe someone else will have one?

PS to 'My last POST' where I give the output of a flawlessly working IBEX wired LAN. The fact that it works flawlessly with a very old 3Com ethernet card, but not with either of my more modern 'on mobo' ethernet interfaces is what makes me wonder if it is DRIVER related.
pgmer6809

---

