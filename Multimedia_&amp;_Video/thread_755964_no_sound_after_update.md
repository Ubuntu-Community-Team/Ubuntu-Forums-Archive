---
title: "no sound after update"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by dexter.deepak on 2008-04-15
i updated my system yesterday and today my sound control gives the following message:
No volume control GStreamer plugins and/or devices found.

amarok as well as kaffeine give the same error :
audio device is busy
xine parameters :

vlc is playing the song but there is no sound output.
audacious is neither playing nor giving errors.

i did install some gtreamer* things from synaptic ..still no output.
before updating my system, it was all fine

dpak@dpak-server:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

dpak@dpak-server:~$ sudo lshw -C sound
[sudo] password for dpak:
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by dexter.deepak on 2008-04-16
from my xubuntu desktop, i issued the following commands :
dpak@dpak-server:~$ xfce4-mixer
alsa: Mixer attach default error: No such device
alsa: Mixer attach default error: No such device


please someone help...or i will have to choose between my favourite muzic and my favourate os.

---

### Post by Yellow Pasque on 2008-04-16
Try this:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by prshah on 2008-04-16
> **dexter.deepak said:**
> from my xubuntu desktop, i issued the following commands :
please someone help...or i will have to choose between my favourite muzic and my favourate os.

Can you please post the output of "lsmod"? ```
lsmod
```

---

### Post by dexter.deepak on 2008-04-16
dpak@dpak-server:~$ lsmod
Module                  Size  Used by
ppp_deflate             7040  0 
zlib_deflate           20632  1 ppp_deflate
bsd_comp                6912  0 
ppp_async              13056  1 
crc_ccitt               3072  1 ppp_async
ppp_generic            29332  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7552  1 ppp_generic
cdc_acm                17184  3 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26112  11 rfcomm
bluetooth              56804  4 rfcomm,l2cap
capability              5896  0 
vboxdrv                61872  0 
ppdev                  10244  0 
ipv6                  278916  22 
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
sbs                    19592  0 
button                  8976  0 
video                  17932  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14208  2 
fat                    54172  1 vfat
sbp2                   24584  0 
lp                     12452  0 
loop                   19076  0 
xpad                   10116  0 
parport_pc             37668  1 
parport                37448  3 ppdev,lp,parport_pc
shpchp                 34580  0 
psmouse                39952  0 
pcspkr                  4224  0 
pci_hotplug            32576  1 shpchp
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               8068  0 
intel_agp              25620  1 
agpgart                35144  1 intel_agp
evdev                  11136  4 
iptable_nat             8708  0 
nf_nat                 20012  1 iptable_nat
nf_conntrack_ipv4      19724  2 iptable_nat
nf_conntrack           65160  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  0 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  2 iptable_nat,ip_tables
ext3                  133640  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sd_mod                 30336  7 
sg                     36380  0 
sr_mod                 17700  0 
cdrom                  37408  1 sr_mod
usbhid                 29664  0 
hid                    28928  1 usbhid
ata_piix               17540  6 
pata_marvell            8064  0 
ohci1394               36784  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8580  0 
libata                125296  3 ata_piix,pata_marvell,ata_generic
scsi_mod              146828  5 sbp2,sd_mod,sg,sr_mod,libata
e1000                 126656  0 
uhci_hcd               26640  0 
ehci_hcd               36748  0 
usbcore               138760  6 cdc_acm,xpad,usbhid,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
commoncap               8320  1 capability
fuse                   47124  5

---

### Post by dexter.deepak on 2008-04-16
thanks ...the temujin stuff worked !!!

i am yet a noob to this community, and i dont know how to thank you people...can you please tell me how to thank you ??
(i know this sounds stupid but u'll have to do this !!)

---

### Post by prshah on 2008-04-16
> **dexter.deepak said:**
> dpak@dpak-server:~$ lsmod
Module                  Size  Used by


Unbelievably, you seem to have no module loaded for sound (hence the UNCLAIMED message, I guess).

So lets try this:
```

sudo modprobe snd_hda_intel
dmesg | tail -20
```

---

### Post by Yellow Pasque on 2008-04-16
> **dexter.deepak said:**
> thanks ...the temujin stuff worked !!!

i am yet a noob to this community, and i dont know how to thank you people...can you please tell me how to thank you ??
(i know this sounds stupid but u'll have to do this !!)
Awesome! You can hit the little ribbon star medallion next to the quote button on my post to officially thank me, but I don't really care about those. The real thanks is in helping people get their systems working and becoming less dependent on Windows.

---

