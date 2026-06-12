---
title: "Hauppauge NOVA-TD with Feisty"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by axen on 2007-07-16
Hi

I hope that someone can help me to get my tvcard working, the Tvcard is a Hauppauge WinTV NOVA-TD.
If i run lsusb -v in terminal, following info is shown about the usb stick,
2040:9580 Hauppauge

More info about the card can be found on this page,
[http://www.hauppauge.co.uk/pages/products/data_novatdstick.html](http://www.hauppauge.co.uk/pages/products/data_novatdstick.html)

BR
Henrik

---

### Post by Boyo on 2007-07-28
Any success with the Nova-TD yet running any version of Linux?

Many thanks

Martin

---

### Post by nzadLithium on 2007-07-28
can you do lsmod and put the output here?

I want to check whether this uses the bttv drivers. If it does then it means bttv must support usb devices too.
If it doesnt then you need to find a usb driver for you device.

---

### Post by Boyo on 2007-07-29
Hi

As requested here is the output of lsmod.... Hope it helps.

Many thanks

Martin

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
powernow_k8            16064  1 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
sbs                    15652  0 
video                  16388  0 
dock                   10268  0 
asus_acpi              17308  0 
ac                      6020  0 
container               5248  0 
backlight               7040  1 asus_acpi
i2c_ec                  6016  1 sbs
button                  8720  0 
battery                10756  0 
ipv6                  268960  20 
nls_utf8                3072  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               4713780  22 
soundcore               8672  1 snd
af_packet              23816  2 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
serio_raw               7940  0 
psmouse                38920  0 
pcspkr                  4224  0 
i2c_nforce2             6784  0 
agpgart                35400  1 nvidia
k8temp                  6656  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_nforce2
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  4 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
usb_storage            72256  0 
libusual               17936  1 usb_storage
sata_nv                20868  3 
libata                125720  2 ata_generic,sata_nv
scsi_mod              142348  5 sbp2,sg,sd_mod,usb_storage,libata
amd74xx                15260  0 [permanent]
ohci_hcd               22532  0 
forcedeth              46728  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  5 usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by nzadLithium on 2007-07-29
K I think your going to need a usb driver for it. I read about one a few days ago. When i get back from school i'll try and find it.

---

### Post by nzadLithium on 2007-07-30
I can't find any usb drivers.
It may go if you do this
modprobe bttv card=80

card=80 is setup for a WinTV PVR card.

then test it with a video camera or something.
chances are it won't though because bttv i think is meant to use only pci devices.

/usr/share/doc/kernel-doc-2.4.27/Documentation/video4linux/bttv/Cards.gz
contains a full list of what you can have card set to.

Hopefully this helps but i don't think it will work.

You really need to find a proper usb driver for it.

---

### Post by Boyo on 2007-07-31
Unfortunately this did not work.

I sent the card back to ebuyer.co.uk today stating that it was not as advertised as the specs had changed.  Hopefully they will give me a refund!

Thanks for your help

Martin

---

### Post by maluka on 2007-09-15
hi
i have the same card that i'm trying to get to install. any news on a fix to get it to work?

---

### Post by MrHippocampus on 2007-09-15
You could try updating to the latest linux-dvb modules, if you follow the instructions [here]("http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux") (there for the nova 500, but everything up to "Download the firmware" is just for downloading/compiling/installing the modules). After you've done that restart and then have a look at the output of dmesg to see if the device has been picked up.

---

### Post by waster on 2008-01-12
the chipset is supported in kernel 2.6.24, and therefore Hardy. I'm sure sticking a 2.6.24 kernel in your feisty/gutsy installation would be fine. Are kernels ever backported or is this always DIY?

I think you can download and compile the relevant kernel module for your own kernel, if you don't want to upgrade your whole kernel. You will also need firmware which is apparently freely available, but probably 'non-free.'

---

