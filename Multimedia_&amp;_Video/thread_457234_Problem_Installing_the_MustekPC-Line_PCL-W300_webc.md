---
title: "Problem: Installing the Mustek/PC-Line PCL-W300 webcam"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by Jimbo2184 on 2007-05-28
Hi guys.

I've come unstuck when trying to install my PC Line/Mustek PCL-W300 webcamera in linux. Unfortunately, doing a google search did not turn up any help. In addition, I've searched these forums to no avail.

The kernel I am running is the stock Ubuntu Feisty 7.04 Kernel.
Linux james-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

I believe the webcam maybe based on the NW802 chipset. I've run:

sudo modprobe nw802

And linux returns:
**FATAL: Module nw802 not found.**

I've run 

sudo modprobe usbvideo

I tried to install the nw802 module, patch it for kernel 2.6 and then install but it fails to compile usbvideo.c and chokes with Make Error 1. The linux-source-2.6.20-15 package is installed, untarred and symlinked correctly.

The module installs correctly and is appears fine after running lsmod. In fact the lsmod output is produced for you below:

(apologies for its length).

Module                  Size  Used by
usbvideo               28164  0 
compat_ioctl32          2304  1 usbvideo
videodev               28160  1 usbvideo
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
cdc_acm                15904  0 
speedstep_lib           6148  0 
freq_table              5792  0 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vboxdrv                31620  0 
sonypi                 23196  0 
xt_limit                3584  6 
xt_tcpudp               4224  9 
iptable_mangle          3712  0 
ipt_LOG                 7680  8 
ipt_MASQUERADE          4608  0 
nf_nat                 19372  1 ipt_MASQUERADE
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11008  0 
nf_conntrack_ipv4      19468  7 
xt_state                3456  6 
nf_conntrack           62600  6 ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
nfnetlink               7704  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3968  1 
ip_tables              13796  2 iptable_mangle,iptable_filter
x_tables               16388  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
ppdev                  10116  0 
radeon                124576  3 
drm                    81044  4 radeon
binfmt_misc            12680  1 
ipv6                  268704  12 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
battery                10756  0 
container               5248  0 
sbs                    15652  0 
button                  8720  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sony_acpi               6412  0 
sbp2                   23812  0 
lp                     12452  0 
parport                36936  2 ppdev,lp
joydev                 10816  0 
pcmcia                 39212  0 
tifm_sd                12168  0 
mmc_core               26756  1 tifm_sd
snd_ali5451            24460  3 
snd_ac97_codec         98336  1 snd_ali5451
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
pcspkr                  4224  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  15 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                38920  0 
serio_raw               7940  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8672  1 snd
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tifm_7xx1              10240  0 
tifm_core               9856  2 tifm_sd,tifm_7xx1
ati_agp                10124  1 
agpgart                35400  2 drm,ati_agp
snd_page_alloc         10888  1 snd_pcm
i2c_ali1535             8324  0 
i2c_ali15x3             8964  0 
i2c_core               22784  3 i2c_ec,i2c_ali1535,i2c_ali15x3
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  8 
reiserfs              247680  2 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
usbhid                 26592  0 
hid                    27392  1 usbhid
alim15x3               13196  0 [permanent]
generic                 5124  0 [permanent]
8139cp                 25088  0 
8139too                27648  0 
mii                     6528  2 8139cp,8139too
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  6 usbvideo,cdc_acm,usbhid,ehci_hcd,ohci_hcd
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

The green camera LED illuminates briefly, then extingushes after connection to my PC. The kernel's DMESG information (tailed) is as follows:
[  246.804000] usb 1-1: USB disconnect, address 4
[  248.996000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[  249.200000] usb 1-1: configuration #1 chosen from 1 choice
[ 1043.300000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[ 1043.552000] usb 2-1: configuration #1 chosen from 2 choices
[ 1043.788000] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[ 1043.800000] usbcore: registered new interface driver cdc_acm
[ 1043.800000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 3586.120000] Linux video capture interface: v2.00
[ 3733.780000] usb 1-1: USB disconnect, address 5
[ 3737.672000] usb 1-1: new full speed USB device using ohci_hcd and address 6
[ 3737.876000] usb 1-1: configuration #1 chosen from 1 choice

(BTW: The USB Acm device is for my Motorola L6 mobile phone)

Any ideas? I'm fresh out of things to try right now, and some advice would be appreciated - otherwise its off to Windows XP to use this webcam - and I hate XP so right now thats not really an option. :(

---

