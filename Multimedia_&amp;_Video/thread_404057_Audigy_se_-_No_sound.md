---
title: "Audigy se - No sound"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by Salo on 2007-04-07
I have an creative audigy se sound card that just wont work in ubuntu 6.10

I have been through 2 dozen help files and how to's for checking that all the channels are unmuted, certain options are disabled, this and that are working. But again I have no sound.

I have no idea how to install and configure alsa...which may be the savior Im looking for.

Output of lsmod:

```
Module                  Size  Used by
wlan_tkip              13824  2 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 548708  11 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  4 
nls_utf8                3200  2 
ntfs                  112116  2 
fuse                   43912  0 
lp                     12964  0 
tsdev                   9152  0 
usbhid                 45152  0 
8139cp                 24832  0 
8139too                29056  0 
wlan_scan_sta          15744  1 
psmouse                41352  0 
mii                     6912  2 8139cp,8139too
serio_raw               8452  0 
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207708  5 wlan_tkip,wlan_scan_sta,ath_pci,ath_rate_sample
evdev                  11392  4 
ath_hal               192976  3 ath_pci,ath_rate_sample
pcspkr                  4352  0 
analog                 12960  0 
gameport               17160  1 analog
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
intel_agp              26012  1 
agpgart                34888  2 fglrx,intel_agp
soundcore              11232  0 
floppy                 63044  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ata_piix               11780  0 
libata                 74892  1 ata_piix
scsi_mod              144648  1 libata
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Thanks.

edit: On my last reboot into ubuntu, the top right corner which normally contaisn my sound control panel has a red x through it. with the following errors:

Red x:
[http://img398.imageshack.us/img398/6827/screenshothf5.png](http://img398.imageshack.us/img398/6827/screenshothf5.png)

error:
[http://img359.imageshack.us/img359/2093/screenshot1bv2.png](http://img359.imageshack.us/img359/2093/screenshot1bv2.png)

---

### Post by deadgobby on 2007-04-07
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=sound&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=sound&titlesearch=Titles)
gobby

---

### Post by Salo on 2007-04-07
My problem isnt being illiterate, Ive checked through all of those helps many times. Again, Im thinking my issue is alsa not being installed or configured, and now that my sound card isnt even being detected none of that will help me.

Thanks anyway.

---

### Post by deadgobby on 2007-04-07
What do you get when you give this command in the terminal? Please post your results.

aplay --list-devices

Gobby

---

### Post by Salo on 2007-04-07
I get

```
aplay: device_list:222: no soundcards found...

```

---

### Post by deadgobby on 2007-04-07
It should of work out of the box. Plain and simple.  Have you disable the on board sound card in the BIOS?
 Here is a link and see if you tried this.

[http://doc.gwos.org/index.php/AudioCard/Alsa-doc/SB_Audigy_LS](http://doc.gwos.org/index.php/AudioCard/Alsa-doc/SB_Audigy_LS)

If not there may be a possible bug.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/46233](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/46233)

[http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&message.id=57232](http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&message.id=57232)

---

### Post by Salo on 2007-04-07
I get:

```
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/pci/ac97/snd-ac97-bus.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/core/snd-rawmidi.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.17-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko': No such file or directory

```

Im not ready to give in to it being a bug, is there anything else we can do?

---

### Post by deadgobby on 2007-04-08
Ok I am scratching my head here. 
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106)

OK or just run the Fiesty fawn live CD and see if that works. The new up date version may have needed support for the card. I am out of help for you. May be some one will know. I have a SB Live and it worked right out of the box. 
Gobby

---

### Post by Salo on 2007-04-08
What do I download so that I can follow those instructions?

And what is fawn?

---

### Post by Salo on 2007-04-08
Very Weird, I followed these instructions:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

After I rebooted after adding my sound card module to /etc/modules ubuntu froze at the loading screen. So I rebooted once more to get to recovery console and remove that value only to realize that recovery console froze as well.

So then, I do a hard shutoff and restart, then start up ubuntu. And to my amazement the login sound worked, so I start up a movie in vlc player and bam sound and everything. 

So I guess it works, I wont edit the title until the next reboot and Im sure it works.

Thanks for all your help. Appreciate it.

---

