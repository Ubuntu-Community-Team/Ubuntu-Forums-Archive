---
title: "system hang on usage of administration\networking (network-admin)"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by hkais on 2006-01-26
Hello,

I have a wired problem with the network-admin (Administration\networking) under gnome. I often have a complete system halt if I try to reconfigure my network on my notebook (T42p). I cannot find anything in the syslog, except the last entry:

Jan 26 18:14:17 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan 26 18:14:17 localhost dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6484
Jan 26 18:14:17 localhost dhclient: killed old client process, removed PID file
Jan 26 18:14:17 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Jan 26 18:14:17 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Jan 26 18:14:17 localhost dhclient: All rights reserved.
Jan 26 18:14:17 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Jan 26 18:14:17 localhost dhclient:
Jan 26 18:14:17 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 18:14:17 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 18:14:17 localhost dhclient: Listening on LPF/eth1/<mac>
Jan 26 18:14:17 localhost dhclient: Sending on   LPF/eth1/<mac>
Jan 26 18:14:17 localhost dhclient: Sending on   Socket/fallback

Any ideas?

best regards,
Hans
here goes my configuration:

Hardware:
Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)
CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
Ethernet controller: Intel Corp. 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

Software:
Breezy 5.10

Modules:
vmnet                  37700  16
vmmon                 111980  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_centrino      7636  1
cpufreq_userspace       4316  1
cpufreq_stats           5252  0
freq_table              4388  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
pcmcia                 26568  4
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
ibm_acpi               17684  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  12
af_packet              21768  4
irtty_sir               8512  0
sir_dev                18444  1 irtty_sir
irda                  187612  2 irtty_sir,sir_dev
crc_ccitt               1984  1 irda
floppy                 59124  0
rtc                    12344  0
pcspkr                  3396  0
ipw2200               103880  0
firmware_class          9952  1 ipw2200
ieee80211              29380  1 ipw2200
ieee80211_crypt         5604  2 ipw2200,ieee80211
yenta_socket           25292  2
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           33248  1
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
tpm_atmel               5536  0
tpm_nsc                 6656  0
tpm                     9888  2 tpm_atmel,tpm_nsc
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
intel_agp              23164  1
dm_mod                 57692  1
tsdev                   7776  0
evdev                   9664  0
fglrx                 451552  7
agpgart                34792  2 intel_agp,fglrx
nvram                   8488  0
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  2 speedstep_centrino,thermal
fan                     4484  0
e1000                 101940  0
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  3 ehci_hcd,uhci_hcd
ide_cd                 41572  1
cdrom                  39616  1 ide_cd
ide_disk               18464  3
ide_generic             1376  0
piix                   10372  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,piix
unix                   26896  862
capability              4712  0
commoncap               6816  1 capability
vesafb                  7992  1
vgastate                9664  0
softcursor              2272  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
cfbcopyarea             4608  1 vesafb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

---

