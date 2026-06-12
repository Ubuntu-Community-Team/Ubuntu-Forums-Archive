---
title: "need help with connection sharing and networking.."
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by br0q on 2006-06-25
hi there. i'm not exactly new to linux,but i'm trying to get a network set up and i'm having no luck so far. my host machine is running mepis 3.43,connected to the cable modem through a d-link di-514 router. the machine i'm trying to share the connection with is running ubuntu 6.06 with a d-link dwl-520 adapter. i've tried everything i could find in the wiki and by searching the forums and nothing seems to work. can someone here help me get this up and running?

---

### Post by linuchsan on 2006-06-25
Can you give some more information, like the output from lspci, lsmod?

---

### Post by br0q on 2006-06-25
$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)



$ lsmod
Module                  Size  Used by
smbfs                  58872  2
binfmt_misc            11144  1
radeon                 97184  1
drm                    65812  2 radeon
video                  16260  0
thermal                13576  0
tc1100_wmi              6916  0
sony_acpi               5516  0
processor              23360  1 thermal
pcc_acpi               12416  0
hotkey                 11556  0
fan                     4868  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
ipt_limit               2432  2
ipt_state               2048  66
ipt_LOG                 6016  2
ipt_REJECT              5248  2
ip_conntrack_ftp        7280  0
ip_conntrack_irc        6640  0
ip_conntrack           47148  3 ipt_state,ip_conntrack_ftp,ip_conntrack_irc
nfnetlink               6296  1 ip_conntrack
ndiswrapper           156628  0
dm_mod                 52152  0
md_mod                 64084  0
af_packet              21000  2
yenta_socket           25356  0
rsrc_nonstatic         12288  1 yenta_socket
pcmcia                 36668  0
pcmcia_core            38672  3 yenta_socket,rsrc_nonstatic,pcmcia
joydev                  9152  0
snd_seq_dummy           3844  0
snd_seq_oss            29952  0
snd_seq_midi            8608  0
snd_seq_midi_event      6912  2 snd_seq_oss,snd_seq_midi
sworks_agp              8864  0
amd_k7_agp              8204  0
ali_agp                 6656  0
sis_agp                 8452  0
snd_seq                46480  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 32480  0
tsdev                   7360  0
usblp                  11904  0
ati_agp                 8332  0
snd_via82xx            26520  1
gameport               14728  1 snd_via82xx
snd_ac97_codec         83232  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
floppy                 55620  0
psmouse                32772  0
via_rhine              21764  0
i2c_viapro              8212  0
parport_pc             32708  1
lp                     10820  0
parport                32968  2 parport_pc,lp
snd_pcm_oss            46368  0
snd_mixer_oss          16896  1 snd_pcm_oss
pcspkr                  2052  0
rtc                    12468  0
serio_raw               6916  0
mii                     5376  1 via_rhine
i2c_core               19984  2 i2c_acpi_ec,i2c_viapro
nvidia_agp              7964  0
snd_pcm                79880  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              22660  2 snd_seq,snd_pcm
snd_page_alloc         10248  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            23328  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
uhci_hcd               29328  0
snd                    50276  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
via_agp                 9600  1
intel_agp              21276  0
via_ircc               23316  0
agpgart                31816  9 drm,sworks_agp,amd_k7_agp,ali_agp,sis_agp,ati_agp,nvidia_agp,via_agp,intel_agp
shpchp                 40384  0
pci_hotplug            26164  1 shpchp
soundcore               9568  1 snd
irda                  167996  1 via_ircc
crc_ccitt               2176  1 irda
evdev                   9088  1

---

