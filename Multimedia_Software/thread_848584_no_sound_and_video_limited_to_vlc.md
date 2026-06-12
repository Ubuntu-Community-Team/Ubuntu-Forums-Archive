---
title: "no sound and video limited to vlc"
date: 2008-07-03
forum: Multimedia Software
---

### Post by linuxnoob40 on 2008-07-03
i did a recent upgrade on my pc and after installing the new video card i have lost the ability to play any movies except under vlc, i also have no sound and i dont know where to turn next. 
would someone please be so kind as to steer me in the right direction

---

### Post by lukjad on 2008-07-03
Almost the same problem. I did not install a new vid card but I did upgrade to Hardy from Fiesty.

---

### Post by Technobabel on 2008-07-03
Do you have a Nvidia oder ATI card? Are you running the proprietary drivers? Do you have sound playing videos with vlc?

Cu
Babel

---

### Post by linuxnoob40 on 2008-07-03
brand new nvidia 9600 gt pci ex card. but the problems didn't start till i installed the video driver. if i recall i had video and sound before but i couldn't play a game.  now after installing the video driver i can play the game but have no sound, and movies limited to vlc. crazy isnt it?

---

### Post by Technobabel on 2008-07-03
hmm that's weird indeed...
open a terminal and type gstreamer-properties 
check under audio what is used there & change the plugin maybe that solves it already. Do the same for video...

---

### Post by linuxnoob40 on 2008-07-03
> gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(697): gst_alsasink_open (): /pipeline0/alsasink2:
Playback open error on device 'default': No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Autodetect': Failed to connect stream: Invalid argument [pulsesink.c(411): gst_pulsesink_prepare (): /pipeline1/autoaudiosink4/autoaudiosink4-actual-sink-pulse]

doesn't look good

---

### Post by Technobabel on 2008-07-03
hmm the skipping plug-ins are O.K. I do have them too. But the rest looks kinda bad :( I'll try to find something on it.

---

### Post by dodle on 2008-07-03
To get sound in VLC try this:

Go to your preferences then > Audio > Output Modules > ALSA

Click "Refresh list".  Try any new devices that appear.  

Hope that helps.

---

### Post by linuxnoob40 on 2008-07-03
its not just vlc that has no sound its the entire os that has no sound

---

### Post by Technobabel on 2008-07-04
Open a terminal and type
lsmod | grep snd*
and post what it says.
If you run gstreamer-properties does it open at all? If yes can you change the output for Audio?

Here is one other thing I found in the forum:
Here's how I fixed my problems.., run the following commands in a terminal.
asoundconf reset-default-card

If you still get default no such file...

Run asoundconf list and then use the cards name with
asoundconf set-default-card YOUR_CARD to set it to default.

Maybe that'll work.

---

### Post by linuxnoob40 on 2008-07-04
ok i would post what the output of lsmod | grep snd* but nothing happens i also got nothing on the output of asoundconf reset-default-card
i will post the output of lsmod although i have no idea what to look for 
Module                  Size  Used by
isofs                  34980  1 
binfmt_misc            11272  1 
ipv6                  255172  10 
af_packet              21636  2 
rfcomm                 39188  2 
l2cap                  23300  13 rfcomm
bluetooth              56964  4 rfcomm,l2cap
ppdev                   9348  0 
cpufreq_ondemand        8084  0 
cpufreq_conservative     7200  0 
cpufreq_powersave       1792  0 
cpufreq_userspace       4120  0 
cpufreq_stats           5124  0 
freq_table              4484  2 cpufreq_ondemand,cpufreq_stats
sbs                    14216  0 
sbshc                   6784  1 sbs
dock                   10124  0 
video                  18832  0 
output                  3712  1 video
container               4736  0 
battery                13316  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
aes_i586               32640  0 
dm_crypt               14340  0 
dm_mod                 60484  1 dm_crypt
ac                      6020  0 
sbp2                   22920  0 
parport_pc             35108  0 
lp                     11332  0 
parport                35912  3 ppdev,parport_pc,lp
nvidia               7102756  24 
agpgart                33328  1 nvidia
button                  8336  0 
i2c_nforce2             6656  0 
i2c_core               23696  2 nvidia,i2c_nforce2
shpchp                 33428  0 
pci_hotplug            29728  1 shpchp
evdev                  11776  3 
rtc                    13212  0 
pcspkr                  3072  0 
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sd_mod                 29584  3 
sg                     36256  0 
sr_mod                 16804  1 
cdrom                  36512  1 sr_mod
pata_marvell            7040  0 
pata_acpi               7424  0 
usbhid                 30720  0 
hid                    36480  1 usbhid
ata_generic             7428  0 
ohci1394               32688  0 
ieee1394               92216  2 sbp2,ohci1394
forcedeth              50060  0 
sata_nv                26504  2 
pata_amd               13316  1 
libata                159728  5 pata_marvell,pata_acpi,ata_generic,sata_nv,pata_amd
scsi_mod              151180  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               36748  0 
ohci_hcd               24196  0 
usbcore               143724  4 usbhid,ehci_hcd,ohci_hcd
thermal                15772  0 
processor              28080  1 thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  1

---

### Post by Technobabel on 2008-07-05
Ok if the lsmod | grep snd* prints nothing it means that the sound module is not found.
Does it show a sound by typing
asoundconf list
in a terminal? 
You can also check if alsa did find your card at all by typing
more /proc/asound/cards 
into the terminal
If nothing shows up you have to find out what kind of sound card is installed (on-board?) in your pc.

---

### Post by linuxnoob40 on 2008-07-05
i think it pretty much freaked out over the architecture change going from amd to intel as the problems just kept getting worse. anyhow i did a complete reinstall of the os and things seem to be normal now. thanx for all your effort

---

