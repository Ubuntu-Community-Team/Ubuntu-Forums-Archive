---
title: "Nova-T PCi: No video after upgrade"
date: 2008-05-10
forum: Multimedia Software
---

### Post by badgandalf on 2008-05-10
Hi,

Hope you can help me with this small problem. I used to run MytTV under Kubuntu 7.10 using a Hauppage Nova-T PCI card without problems. However, since upgrading, and trying everything I could figure out, I cannot get it to run. I get a blank screen when choosing 'Watch TV'. I also tried with Kaffeine, but it does not even give me the option to choose 'Watch TV' as it did with Gutsy...

Here's the result of lspci -v | grep -i audio:

[I]00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:09.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:09.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

[/I]Where, I believe, the card shows up correctly. Also I checked with lsmod, and here's the result:

[I]Module                  Size  Used by
binfmt_misc            12808  1
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
acpi_cpufreq           10796  0
cpufreq_stats           7104  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9740  2
cpufreq_userspace       5284  0
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
ipv6                  267780  14
cpufreq_conservative     8712  0
video                  19856  0
output                  4736  1 video
container               5632  0
dock                   11280  0
sbs                    15112  0
sbshc                   7680  1 sbs
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
af_packet              23812  2
ac                      6916  0
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
dvb_pll                13476  1
cx22702                 7172  1
cx88_dvb               14084  1
cx88_vp3054_i2c         3968  1 cx88_dvb
videobuf_dvb            7812  1 cx88_dvb
dvb_core               81404  1 videobuf_dvb
joydev                 13120  0
snd_hda_intel         344728  1
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
usb_storage            73664  0
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
libusual               19108  1 usb_storage
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
usbhid                 31872  0
hid                    38784  1 usbhid
nvidia               7825536  24
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cx8802                 19588  1 cx88_dvb
cx8800                 35848  0
cx88xx                 66088  3 cx88_dvb,cx8802,cx8800
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
ir_common              36100  1 cx88xx
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            7300  2 cx88_vp3054_i2c,cx88xx
soundcore               8800  1 snd
tveeprom               16656  1 cx88xx
compat_ioctl32          2304  1 cx8800
videodev               29440  2 cx8800,cx88xx
v4l1_compat            15492  1 videodev
button                  9232  0
acx                    98692  0
i2c_viapro              9876  0
via_agp                11136  1
agpgart                34760  2 nvidia,via_agp
v4l2_common            18304  3 cx8800,cx88xx,videodev
videobuf_dma_sg        14980  5 cx88_dvb,videobuf_dvb,cx8802,cx8800,cx88xx
videobuf_core          18820  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc               5896  3 cx8802,cx8800,cx88xx
evdev                  13056  7
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
i2c_core               24832  8 dvb_pll,cx22702,cx88_vp3054_i2c,nvidia,cx88xx,i2c_algo_bit,tveeprom,i2c_viapro
pcspkr                  4224  0
ext3                  136712  2
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sd_mod                 30720  8
pata_via               13316  1
pata_acpi               8320  0
sata_via               12420  5
via_rhine              26632  0
mii                     6400  1 via_rhine
ehci_hcd               37900  0
uhci_hcd               27024  0
ata_generic             8324  0
usbcore               146028  7 usb_storage,libusual,usbhid,acx,ehci_hcd,uhci_hcd
libata                159344  4 pata_via,pata_acpi,sata_via,ata_generic
scsi_mod              151436  6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
thermal                16796  0
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  7

[/I]I added the cx88_dvb to the /etc/ modules (as follows) just in case the problem might be there:

[I]fuse
lp
sbp2
cx88_dvb
[/I]
Then, I tried using the dvb_tools to figure out what the problem could be and here's what I get after a scan:

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/es-Madrid
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
[B]main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
[/B]
..and then i do not have a clue as to what might be happening. Anyone can help? Thanks in advance,

Ignacio

---

### Post by badgandalf on 2008-05-10
Partially solved !!

I did an lsof to figure out what kept the card busy..

lsof /dev/dvb/adapter0/frontend0
It turned out to be the mythtv-backend process all along.
 
A simple 
 sudo /etc/init.d/mythtv-backend stop cured the scanning problem
 
I'm restarting Mythtv-backend now to check if it works...

---

