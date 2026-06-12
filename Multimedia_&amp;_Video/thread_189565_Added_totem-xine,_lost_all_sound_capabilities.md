---
title: "Added totem-xine, lost all sound capabilities"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by ktulu1115 on 2006-06-05
Here is my basic problem...  I added totem-xine and it screwed up all the sound functionality on my system.  The volume control applet is X'd out and says "No volume control GStreamer plugins and/or devices found."  System->Preferences->Sound lists no sound cards under "Default sound card".  I've reinstalled 3x to fix this problem - it seems adding/removing/changing any GStreamer packages causes this problem.  It worked fine up until I changed those packages, I have no idea what configuration files were modified in the process.  The only sound that works now is the drumbeat on the GDM logout or startup, that's it.

I did some searching online and heard removing my .asoundrc file might help, tried that but no luck.  Also, tried HOWTO here - [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063) - no luck either.

Some basic debugging info:
Chip: Athlon64 X2 3800+ (running Dapper i386 - 2.6.15-23-k7 #1 SMP PREEMPT)
Board: A8N-E, Realtek ALC850 onboard sound.
Module: snd_intel8x0 (i believe)

$ cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xd0003000, irq 225
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10

~$ aplay /dev/urandom
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
(sudo alsamixer works however)

$ lsmod
Module                  Size  Used by
snd_intel8x0m          18764  0
i810_audio             39444  0
ac97_codec             20684  1 i810_audio
nls_utf8                2560  0
nls_cp437               6208  0
vfat                   14976  0
fat                    56028  1 vfat
usb_storage            80000  0
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54244  4 rfcomm,l2cap
ppdev                  10116  0
powernow_k8            14560  1
cpufreq_userspace       6816  1
cpufreq_stats           6912  0
freq_table              5152  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5900  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
xfs                   653888  2
exportfs                7040  1 xfs
dm_mod                 63640  1
md_mod                 76244  0
lp                     12612  0
pcspkr                  2564  0
nvidia               4553140  16
agpgart                37072  1 nvidia
analog                 12960  0
snd_mpu401              7112  0
snd_mpu401_uart         8896  1 snd_mpu401
gameport               17032  1 analog
snd_rawmidi            27552  1 snd_mpu401_uart
snd_seq_device          9548  1 snd_rawmidi
snd_intel8x0           35740  0
snd_ac97_codec         98912  2 snd_intel8x0m,snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
psmouse                40196  0
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
serio_raw               8132  0
snd_pcm                96772  4 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  1 snd_pcm
snd                    60068  11 snd_intel8x0m,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11040  2 i810_audio,snd
i2c_nforce2             7360  0
i2c_core               23168  3 i2c_acpi_ec,nvidia,i2c_nforce2
snd_page_alloc         11592  3 snd_intel8x0m,snd_intel8x0,snd_pcm
ipv6                  287456  20
shpchp                 49376  0
pci_hotplug            30916  1 shpchp
af_packet              25224  2
tsdev                   8320  0
evdev                  10432  1
sg                     40288  0
usbhid                 41312  0
ext3                  148296  2
jbd                    65684  1 ext3
ide_generic             1792  0
ohci_hcd               22788  0
forcedeth              25860  0
ehci_hcd               33800  0
usbcore               137476  5 usb_storage,usbhid,ohci_hcd,ehci_hcd
ide_disk               19584  2
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
generic                 5444  0
sd_mod                 20864  6
amd74xx                15132  0 [permanent]
sata_nv                10180  8
libata                 84176  1 sata_nv
scsi_mod              145736  4 usb_storage,sg,sd_mod,libata
thermal                14088  0
processor              26696  2 powernow_k8,thermal
fan                     5124  0
fbcon                  44640  0
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit
capability              5256  0
commoncap               7616  1 capability

---

### Post by ktulu1115 on 2006-06-05
Just tried installing AMD64 version of Dapper...  same exact problem, only this time on the fresh install it didn't work at all.  I didn't format my /home partition, but everything else was wiped.

Any ideas?

---

### Post by XioNoX on 2006-06-05
I have exactly the same probleme with an MSI computer (nForce2) 
nd now, my laptop don't play the sound with gstreamer :/
but program like BMP or XMMS works

---

### Post by ktulu1115 on 2006-06-05
What output plugin do you use in XMMS?  At least that works for you, I can't get any of them to work for me.  I read on another thread ([http://ubuntuforums.org/showthread.php?p=1097560#post1097560](http://ubuntuforums.org/showthread.php?p=1097560#post1097560)) that someone had a similiar problem, they installed ALSA from source and it worked fine...  about to try that myself I think.

---

### Post by ktulu1115 on 2006-06-05
Well...  I tried compiling ALSA, but in the end I was just basically pulling my hair out.  There's no reason why the new verison should be needed - it worked perfectly on my i386 install before I messed with gstreamer.  And, sound does work because I hear that drumbeat whenever the GDM login screen appears.

Honestly, I would expect more from Ubuntu than this.  Does *anyone* have any suggestions???

---

### Post by ktulu1115 on 2006-06-05
Now this is interesting....    I normally do a weekly backup of /etc and I happen to have an old one from 2 weeks ago when I was running Dapper beta.  I backed up my current /etc directory, overwrote it with the backup I had from 5/28, rebooted, and *voila*....  sound works.

I'm assuming it's got to be some ALSA configuration file or something, I still find this rather odd though.

---

### Post by jtwJGuevara on 2006-06-05
ktulu:

I've run into the same problem after performing a Dapper upgrade and I have a Realtek onbound sound card as well.  Unfortunately, I didn't keep a backup of etc.  However, i'm not certain that it's an alsa problem.  I cannot find much of a trace of anything alsa related within my /etc directory.  In fact, I couldn't find anything sound or sound card related in /etc .  Would it be possible for you to compare the contents of your two /etc directories to determine what the real differences are?  I have a feeling that the problem that is plauging us is plauging several others as well.

Thanks.

---

### Post by ktulu1115 on 2006-06-05
[QUOTE=jtwJGuevara]ktulu:

Would it be possible for you to compare the contents of your two /etc directories to determine what the real differences are?  I have a feeling that the problem that is plauging us is plauging several others as well.

Thanks.[/QUOTE]

I was about to do that very same thing actually.  I'm just not sure what the best method is for comparing two directory trees.  diff doesn't seem to be the most efficient option.

---

### Post by ktulu1115 on 2006-06-05
Did a quick bit of research and this is what I came upwith...

```
(ktulu@eternal:pts/0)-(38/15 @ 148M)-(11:17 PM)
~$ cmptree /etc etc_original | sed '/.*does not exist.*/d'
/etc/acpi/powerbtn.sh different from etc_original/acpi/powerbtn.sh
/etc/adjtime different from etc_original/adjtime
/etc/aliases different from etc_original/aliases
/etc/apt/apt.conf different from etc_original/apt/apt.conf
/etc/apt/secring.gpg different from etc_original/apt/secring.gpg
/etc/apt/sources.list different from etc_original/apt/sources.list
/etc/apt/trustdb.gpg different from etc_original/apt/trustdb.gpg
/etc/at.deny different from etc_original/at.deny
/etc/brlapi.key different from etc_original/brlapi.key
/etc/crontab different from etc_original/crontab
/etc/environment different from etc_original/environment
/etc/fstab different from etc_original/fstab
/etc/gconf/gconf.xml.defaults/%gconf-tree.xml different from etc_original/gconf/gconf.xml.defaults/%gconf-tree.xml
/etc/group different from etc_original/group
/etc/group- different from etc_original/group-
/etc/gshadow different from etc_original/gshadow
/etc/gshadow- different from etc_original/gshadow-
/etc/gtk-2.0/gdk-pixbuf.loaders different from etc_original/gtk-2.0/gdk-pixbuf.loaders
/etc/gtk-2.0/gtk.immodules different from etc_original/gtk-2.0/gtk.immodules
/etc/hosts different from etc_original/hosts
/etc/iftab different from etc_original/iftab
/etc/init.d/alsa-utils different from etc_original/init.d/alsa-utils
/etc/ld.so.cache different from etc_original/ld.so.cache
/etc/lvm/.cache different from etc_original/lvm/.cache
/etc/mailcap different from etc_original/mailcap
/etc/modules different from etc_original/modules
/etc/mtab different from etc_original/mtab
/etc/network/interfaces different from etc_original/network/interfaces
/etc/passwd different from etc_original/passwd
/etc/passwd- different from etc_original/passwd-
/etc/popularity-contest.conf different from etc_original/popularity-contest.conf/etc/ppp/chap-secrets different from etc_original/ppp/chap-secrets
/etc/ppp/pap-secrets different from etc_original/ppp/pap-secrets
/etc/samba/smb.conf different from etc_original/samba/smb.conf
/etc/sgml/catalog different from etc_original/sgml/catalog
/etc/sgml/catalog.old different from etc_original/sgml/catalog.old
/etc/sgml/metacity.cat.old different from etc_original/sgml/metacity.cat.old
/etc/shadow different from etc_original/shadow
/etc/shadow- different from etc_original/shadow-
ls: /etc/ssl/private: Permission denied
/etc/sudoers different from etc_original/sudoers
/etc/X11/Xwrapper.config different from etc_original/X11/Xwrapper.config
```

Out of those, the ones I thought could be responsible are below:

```
(ktulu@eternal:pts/0)-(38/15 @ 148M)-(11:18 PM)
~$ diff /etc/aliases etc_original/aliases
3d2
< webmaster: root
(ktulu@eternal:pts/0)-(38/15 @ 148M)-(11:18 PM)
~$ diff /etc/init.d/alsa-utils etc_original/init.d/alsa-utils
226,227c226,228
<       # Snapper
<       if [ "`cat /proc/asound/card$1/id 2>/dev/null`" = "Snapper" ]; then
---
>       # Snapper/Tumbler   ## from Debian's alsa-utils alsa-utils_1.0.11-4
>       id=$(cat /proc/asound/card$1/id 2>/dev/null)
>       if [ "$id" = "Snapper" -o "$id" = "Tumbler" ]; then
(ktulu@eternal:pts/0)-(38/15 @ 148M)-(11:19 PM)
~$ diff /etc/modules etc_original/modules
6,16c6,8
<
< # Generated by sensors-detect on Sun May  7 11:25:09 2006
< # I2C adapter drivers
< # modprobe unknown adapter NVIDIA I2C Device
< # modprobe unknown adapter NVIDIA I2C Device
< # modprobe unknown adapter NVIDIA I2C Device
< i2c-nforce2
< i2c-isa
< # I2C chip drivers
< eeprom
< it87
---
> lp
> psmouse
> rtc

```

Looks to me, /etc/init.d/alsa-utils is the culprit.  /proc/asound/cards now reports only this:

```
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xd0003000, irq 225

```
Hopefully this will help.

---

### Post by ktulu1115 on 2006-06-07
Well...   I was wrong before about what the problem was.

This one threw me for a loop....   I basically spent all day installing and re-installing, trying to narrow down the cause of the problem.  Eventually I came up with the idea of creating a new user on the system for the install (still keeping my /home partition unformatted, just adding a new user).  And for whatever reason, when I logged in with that user the sound worked.

So then I figured, it might have something to do with a .gconf setting, spent a few hours trying to narrow it down....   nothing.  Eventually tried just replacing the home directory temporarily with the one from the new user....  still nothing.

After all was said and done, I finally narrowed it down to /etc/groups and /etc/shadow.  The username for my old user (from previous install) wasn't listed in the same groups as the new one.  Once I changed this, it worked!

Sigh....

---

