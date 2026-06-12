---
title: "sound disappeared"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by xterminalx on 2007-07-27
Sound has been working fine and dandy on this machine for moths. Tried to start a program under wine the other day (Great Battles of Hannibal, for trivia's sake), and as soon as the screen popped up, my sound quit. I exited out of the program, and the sound did not return. I restarted the computer, and the sound did not return. I'm relatively new to ubuntu (~3 months), and am not terribly sure what I'm looking for. The master volume control is set all the way up, and the volume control in banshee is set all the way up. Banshee is playing right now, and I can't hear anything. Have checked all connections on sound software, reseated and restarted, etc., no effect. From checking other threads on this problem, I ran a few diagnostics other have been asked to run: 

robert@goat:~$ lsmod
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
radeon                124576  2 
drm                    81044  3 radeon
cpufreq_ondemand        9228  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
button                  8720  0 
sbs                    15652  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
container               5248  0 
ac                      6020  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
video                  16388  0 
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  3 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_mpu401              9256  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54020  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
analog                 12832  0 
gameport               16520  1 analog
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
pcspkr                  4224  0 
i2c_nforce2             6784  0 
nvidia_agp              9500  1 
agpgart                35400  2 drm,nvidia_agp
i2c_core               22656  2 i2c_ec,i2c_nforce2
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
ata_generic             9092  0 
sata_nv                20868  0 
libata                125720  2 ata_generic,sata_nv
scsi_mod              142348  1 libata
generic                 5124  0 [permanent]
floppy                 59524  0 
amd74xx                15260  0 [permanent]
forcedeth              46728  0 
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
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

robert@goat:~$ lspci | grep -i audio
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

if anyone can tell me where to go from here, I'd greatly appreciate it. Thanks.

---

### Post by kyphi on 2007-07-28
Have you tried to enable sound via System (at the top left of your screen), then Preferences, then Sound, then place a tick into the 'enable sound' box'?  Also check at the bottom of that same screen which sound device has been enabled - if there are two or more, toggle them and see which one works best.

---

### Post by deadgobby on 2007-07-28
You can look at
Edit > Preferences > Preview tab and see if you have preview open for audio files. 
   If that does not work. Look into the ALSA and check your sound levels.

Gobby

---

### Post by xterminalx on 2007-07-28
> **deadgobby said:**
> If that does not work. Look into the ALSA and check your sound levels.

ALSA mixer was it. Genius, thanks!

---

