---
title: "IEEE 1394 not responding"
date: 2009-04-14
forum: Multimedia Software
---

### Post by sphilli8 on 2009-04-14
I've got a Kubuntu desktop with Kino installed. I have previously been able capture video on it with firewire (IEEE 1394) but it recently stopped working. In the "IEEE1394" tab in Kino preferences I get the message "The IEEE 1394 Subsystem is not responding. The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394."

**NB: I'm running Kino as the superuser, so it's not a permissions issue.**

I tried reinstalling the "dvgrab" package, it didn't work.

I think /dev/raw1394 is supposed to show up when I plug the camera in but it doesn't. After looking around on these forums I tried a few things mentioned elsewhere that didn't work:

 - I tried "sudo modprobe raw1394 dv1394"
That made /dev/raw1394 exist but the camera still didn't show up in Kino.

 - Here is the output of "lsmod"
> hcec2@water:/dev$ lsmod
Module                  Size  Used by
video1394              19384  0
xt_limit                3584  8
xt_tcpudp               4096  28
ipt_LOG                 7296  8
ipt_MASQUERADE          4608  0
ipt_TOS                 3200  0
ipt_REJECT              5632  1
nf_conntrack_irc        7576  0
nf_conntrack_ftp       10144  0
xt_state                3328  6
af_packet              23812  2
binfmt_misc            12808  1
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0
ipv6                  267908  10
speedstep_lib           6532  0
cpufreq_userspace       5284  0
cpufreq_ondemand        9740  0
cpufreq_powersave       2688  0
cpufreq_stats           7104  0
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0
video                  19856  0
output                  4736  1 video
sbs                    15112  0
sbshc                   7680  1 sbs
container               5632  0
dock                   11280  0
battery                14212  0
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
ac                      6916  0
lp                     12324  0
snd_intel8x0           35356  2
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17920  1 snd_pcm_oss
parport_pc             36260  1
parport                37832  3 ppdev,lp,parport_pc
dcdbas                  9504  0
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
evdev                  13056  3
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
pcspkr                  4224  0
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
nvidia               4718832  22
i2c_core               24832  1 nvidia
button                  9232  0
intel_agp              25492  1
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
agpgart                34760  2 nvidia,intel_agp
iptable_nat             8324  0
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66752  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0
iptable_filter          3840  1
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  136840  3
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  6
pata_acpi               8320  0
ata_generic             8324  0
usbhid                 32128  0
hid                    38784  1 usbhid
floppy                 59588  0
ata_piix               19588  4
ohci1394               33584  1 video1394
e1000                 126016  0
libata                159600  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ieee1394               93752  2 video1394,ohci1394
ehci_hcd               37900  0
uhci_hcd               27024  0
usbcore               146412  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0
processor              36488  1 thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1


 - After that I did a "sudo modprobe video1394" and then a lsmod | grep 1394 (I don't even know what that means, was just following other threads in the forums). The output of that was:
> 
hcec2@water:/dev$ lsmod | grep 1394
video1394              19384  0
ohci1394               33584  1 video1394
ieee1394               93752  2 video1394,ohci1394


Hope you can help.

---

### Post by bumanie on 2009-04-14
[This]("http://ubuntufriends.wordpress.com/2008/06/25/kino-and-dv-1394-in-ubuntu-hardy/") might help.

---

### Post by sphilli8 on 2009-04-15
Hmmm...that page is just about overcoming permissions restrictions. As I wrote in the post above, I'm running Kino as the superuser, so it's not a permissions issue. Thanks anyway.

---

### Post by sphilli8 on 2009-04-16
Anyone?

---

### Post by inobe on 2009-04-17
i helped someone once before, make sure you have all the requirements.

[http://www.kinodv.org/article/static/3](http://www.kinodv.org/article/static/3)

the person i helped installed some of those requirements and got it working.

meaning you can install kino and be missing those components, compare those components in synaptic.

---

### Post by sphilli8 on 2009-04-19
Na, that didn't work either. It occurred to me that maybe my actual firewire card has been damaged somehow. But wouldn't that mean that no "IEEE1394" showed up when I executed "lsmod" and "lsmod | grep 1394" above?
s

---

### Post by inobe on 2009-04-19
it should have worked, but hardware can be unpredictable.


i initially thought an update or application change caused this, now it looks like hardware failure.

tell me about the device, is it a pci addon card ?

edit: include the model of your motherboard and i will check to see if it has headers for an optional 1394 connection, the adapters are very cheap if you have a header.

---

### Post by sphilli8 on 2009-04-22
Sorry for the delay, been away from the desktop. Yes, it is a PCI add-on card. I had a look at the motherboard but couldn't really see much identifying information. The computer is a Dell Optiplex GX270, with the original motherboard I presume (although I got it second hand, it came from an institution). Does that help?

I have had the firewire port working on this computer before, so it must be compatable. That's what makes me think the firewire card might just have been damaged.

thanks

---

