---
title: "No sound with Ubuntu - beginner question"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by pipoo on 2007-10-16
hi everyone,

I am fairly new to ubuntu/ linux (as in 1 week lol), and so far Im loving Ubuntu, except for one thing... sound, (or lack there of).

I've done research and read threads and all the trouble shooting that you guys give are very helpful, but I just haven't managed to pinpoint the problem, im hoping a personalized troubleshooting guide with you guys will be enough 

when i type lsmod i get this (whether this helps or not)

```
Module                  Size  Used by
michael_mic             3584  4 
arc4                    2944  4 
ecb                     4480  4 
blkcipher               6784  1 ecb
ieee80211_crypt_tkip    12032  2 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   25472  2 
drm                    81044  3 i915
acpi_cpufreq           10056  1 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
dock                   10268  0 
asus_acpi              17308  0 
sbs                    15652  0 
battery                10756  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
button                  8720  0 
backlight               7040  1 asus_acpi
video                  16388  0 
ac                      6020  0 
container               5248  0 
ipv6                  268960  12 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
pcmcia                 39212  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ipw3945               118816  1 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211              34760  1 ipw3945
uvcvideo               42500  0 
sdhci                  18700  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
joydev                 10816  0 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              26140  1 
agpgart                35400  3 drm,intel_agp
mmc_core               26756  1 sdhci
af_packet              23816  8 
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
serio_raw               7940  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
iTCO_wdt               11812  0 :lolflag:
iTCO_vendor_support     4868  1 iTCO_wdt
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
ata_piix               15492  2 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
r8169                  32392  0 
ehci_hcd               34188  0 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
usbcore               134280  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

[[IMG]http://img521.imageshack.us/img521/5295/screenshotgj7.th.png[/IMG]](http://img521.imageshack.us/my.php?image=screenshotgj7.png)[                     [IMG]http://img526.imageshack.us/img526/7978/screenshotvolumecontrolum9.th.png[/IMG]](http://img526.imageshack.us/my.php?image=screenshotvolumecontrolum9.png)

I hope what i gave helps, and I appreciate all the help you guys can give

---

### Post by avik on 2007-10-16
[This guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto") did the trick for me.  I didn't need to do in Fiesty, though, as that version had sound working out of the box.  Maybe it'll help you.

---

### Post by pipoo on 2007-10-17
thanks avik I checked it out, only the first section really made sense to me lol and it didnt seem to work

I'm beating my head against the wall here lol,

I tried re-installing the driver and it worked as in the installation was successful (*smirks with pride*) but no sound... this is my card, Realtek ACL861
 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

thanks

---

### Post by 11touche on 2007-10-26
Did you check if you have the priviledges to use sound?
It happened once on my desktop.

System -> Administration -> Users and groups -> (choose your username) -> Click on properties -> User Priviledges -> And then be sure that "use audio devices" box is checked

Hope it can help you out

---

### Post by pipoo on 2007-10-26
hey thanks,

yea i have the privileges but I still cant hear anything, only in windows :confused:

---

### Post by Can+~ on 2007-10-26
My first question is.. why there is a "PCM-2" on your volume control panel? Is there a PCM (1) there? If there is, max it out.

---

### Post by pipoo on 2007-10-26
hey everyone, thanks Can+~, im not sure but I had maxed everything I could find,

anyway, I just updated to 7.10 Gutsy Gibbon and sound randomly works!!!

thanks to everyone who tried to help me out I really appreciate it

=D>

---

