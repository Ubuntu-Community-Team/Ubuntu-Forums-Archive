---
title: "[SOLVED] SATA not recognized"
date: 2007-10-10
forum: Mythbuntu
---

### Post by govee on 2007-10-10
I am attempting to load Mythbuntu 7.10 beta and am having problems with my sata drive being recognized. I have an ASUS AV8-XE Mb with an 8.5 GB IDE and 500GB SATA. I have tried numerous variations of the hardware and or Bios (mode- IDE, SATA, AHCI). I can get the OS to load from the CD to the IDE but when I do the install the SATA is not available for partitioning. 

I tried it with only the SATA (IDE diconnected) and the LIVE CD fails to load. I get the /bin/sh failure. I tried the noapci with no luck. 

I also loaded the Gutsy beta and it does load and recognize the SATA, but I really want the MYthbuntu without all the extra baggage that comes with Gutsy.

Also I have an remote an IR sensor from an old sony vaio Media center PC and did not see it listed as one of the available remotes to use. Which should I select? I was thinking of one of the Windows MCE versions?

Thanks

---

### Post by tgm4883 on 2007-10-10
Did you check the md5sum of the iso and verify the cd?  Did you burn at a slow speed?  If all of that still checks out there is a different approach to installing that we could try.

---

### Post by govee on 2007-10-10
Yes I checked the md5sum. I also redownloaded the iso and reburned the image using slow speed. I can and did again last night got the install to work with the IDE connected, but my SATA is not recognized. I forgot to mention I used the GPARTED iso and it sees the SATA as well as the IDE. I tried 1.5 and 3.0 speeds. I also tried removing the quiet splash and adding noapci as well as VGA= ###, and Break=mount. I have searched a lot in the archieves to try and figure this one on my own. By the way I love the auto search feature in this forum, ie putting the title in a new post causes a retrieval of similar post. I have never seen that before an it is very useful.

---

### Post by superm1 on 2007-10-10
This is a bit odd that your sata wouldn't be recognized in the mythbuntu disks.  They were generated from the Gutsy archive a few days after the Gutsy beta.  

If you don't manage to sort things out, we will be doing a Release Candidate shortly (within a week), and you can give a shot then with the freshly upgraded kernel images.

---

### Post by dannyboy79 on 2007-10-10
please post your sata chipset info.

lspci

also, after you load up ubuntu onto the ide drive, then boot into ubuntu, you do have the sata drive connected correct? Does the sata drive show up in the bios? Which sata ports do you have it connected to? I ahve heard where some motherboards have 4 sata ports, 2 of them are built into the motherboard and a native ports, then I have heard that the other 2 are 3rd party sata ports and require different drivers. Just a thought you could try a different port?

Also, when I am in my system I ahve multiple sata drives, i can run the following command and it shows:
lsmod | grep sata
sata_via               12548  2
libata                125720  2 sata_via,ata_generic

so I have a via chipset sata controller. I at one time had to add sata_via within /etc/modules for it to load properly. but I think now libata has all the sata controllers drivers within it (correct me if I am wrong)

---

### Post by govee on 2007-10-10
VT8251 AHCI/SATA 4-Port Controller

I can load Ubuntu on the Sata just fine when it is plugged in without the ide, or I can load ubuntu on the ide with the sata plugged in and it is recognized by the OS. I can load Mythbuntu on the IDE with the sata plugged in, but the sata is not recognized. I can not load the mythbuntu on the sata when it is plugged in alone. I have it in Sata 1 and have tried 3. there are 4 total sata connectors on the MB. 1 and 3 are called master and 2 and 4 are slave. I thought sata did away with the master slave thing?

---

### Post by dannyboy79 on 2007-10-11
it does, the 2 ports are most likely on 1 controller and 2 ports are on another controller. Does your bios have a setting within it to treat sata as ide? when you load up ubuntu when only one drive (ide or sata not both) plugged in, what does this return

lsmod

and then what's that same command when the opposite drive is plugged in?

Also, does your bios see both drives? If so, then we can start trying to troublshoot better.

---

### Post by govee on 2007-10-11
Yes my bios has a setting to treat sata as ide (i tried both)
Below is the terminal response with the ide connected. I dont have anything currently loaded on th e sata so I cant get that info quickly. My bios does recognize both drives and so does Gparted if I run Gparted from the ISO. I ran Gparted from mythbuntu and it only finds the ide when both are connected.

andy@andy-mythbackend:~$ lsmod
Module                  Size  Used by
af_packet              24840  2 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ipv6                  274020  21 
video                  18060  0 
container               5504  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
lp                     12580  0 
wm8775                  7180  0 
cx25840                26640  0 
lirc_mceusb2           14980  0 
tuner                  63144  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  26 
psmouse                39952  0 
analog                 13344  0 
gameport               16776  1 analog
parport_pc             37412  1 
parport                37448  2 lp,parport_pc
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ivtv                  134928  0 
pcspkr                  4224  0 
serio_raw               8068  0 
soundcore               8800  1 snd
i2c_algo_bit            7428  1 ivtv
cx2341x                13316  1 ivtv
k8temp                  6656  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
tveeprom               16784  1 ivtv
videodev               29312  1 ivtv
v4l2_common            18432  6 wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  2 ivtv,videodev
lirc_mceusb            12128  0 
lirc_dev               15860  2 lirc_mceusb2,lirc_mceusb
i2c_viapro             10004  0 
i2c_core               26112  8 wm8775,cx25840,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom,i2c_viapro
amd64_agp              13700  1 
agpgart                35016  2 nvidia,amd64_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
usbhid                 29536  0 
hid                    28928  1 usbhid
reiserfs              248704  1 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18304  3 
via82cxxx              10372  0 [permanent]
ide_core              116548  3 ide_cd,ide_disk,via82cxxx
floppy                 60004  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
ehci_hcd               36108  0 
uhci_hcd               26640  0 
usbcore               138248  6 lirc_mceusb2,lirc_mceusb,usbhid,ehci_hcd,uhci_hcd
ata_generic             8452  0 
ahci                   23300  0 
libata                124528  2 ata_generic,ahci
scsi_mod              147084  1 libata
thermal                14344  0 
processor              31944  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40600  0 
commoncap               8320  1 apparmor
andy@andy-mythbackend:~$

---

### Post by propagandhi on 2007-10-11
I'm not sure if this will have any relevance at all, but I was having weird problems with a SATA DVD Burner and I also had different and unpredictable behaviours trying to boot from the cd and get it installed, however I did eventually get it installed, and then when booting from the installstion on the  SATA HDD it would sometimes boot fine when I only had the HDD plugged in.

There was a lot of other weird behaviour, including incredibly long boot times, but basically I found that if I added ***"IRQPOLL"*** to the kernel parameters at boot time I had no problems whatsoever.

For example, either at the grub menu hit ESC before it boots (you may only have a few seconds), then hit 'E' on the default kernel or the kernel you would like to boot so that you can edit it's parameters. Go to the kernel line, and add to the end where it will probably say 'ro quiet splash', just add the irqpoll setting,

so it would look like '**ro quiet splash irqpoll**'.

If you are already booted into your distro, just add it to the menu.lst file (/**boot/grub/menu.lst**) 

As I said, this may have no relevance to your particular situation at all, but you never know....

---

### Post by govee on 2007-10-11
Thanks forthe tip, but it did not help.

---

### Post by dannyboy79 on 2007-10-12
you know what I just thought of, you're saying that it's an eSATA drive? Do you have it plugged in before you even turn the machine on? I have an eSATA drive and unfortunately with the libata these drives are not hot pluggable like they should be. You didn't answer my question. Does the bios see the sata drive when you have them both plugged in?

I also see that your controller is using the ahci. Have you googled around for issues with this and what needs to be set within the bios. I know you said yuou tried some settings in the bios but maybe double check? I am running out of ideas. 

ata_generic 8452 0
ahci 23300 0
libata 124528 2 ata_generic,ahci

---

### Post by govee on 2007-10-12
The bios does see both drives. I decided I would flash to the newest bios as a possible solution. I have a copy of tiny xp that I loaded last night and will use the boards utilties program (windows based) to get past the fact I have no floppy. I saw a "how to" to create a CD to do the same work, I am just not yet that comfortable with Linux and the process was a bit over my head. I will get there one day! Interestingly enough windows does not see the sata drive either,, so I hope I am on the right path.

A note of interest to me was I ran gparted and I saw that the Mythbuntu OS is only taking up 1.5 GB. That is awsesome!

---

### Post by govee on 2007-10-13
i want to thank all that helped me through this issue. I updated the bios and upgraded to the RC. My sata is now recognized!!!! Now I need to get it all set up correctly.

---

