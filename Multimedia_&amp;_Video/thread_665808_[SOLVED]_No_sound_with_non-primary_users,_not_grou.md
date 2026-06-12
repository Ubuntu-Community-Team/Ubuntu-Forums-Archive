---
title: "[SOLVED] No sound with non-primary users, not groups issue"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by feminaexlux on 2008-01-12
I've got problems trying to get my other user "noxgl" to have sound on my Ubuntu Gutsy. As far as I can tell, it's not a groups problem, because I have this for "cat /etc/group | grep audio":

```
audio:x:29:divinya,noxgl,pulse
```

I'm not sure what's happening. "noxgl" is having problems with the sound, "divinya" works absolutely perfectly, and I installed the PulseAudio server on "divinya". "noxgl" I made because XGL conflicts with my tablet, but it doesn't have any sound, and just gives me this horrible system beep when there's supposed to be sound :(

lspci -v (audio):

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 022a
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

lsmod:

```
Module                  Size  Used by
xt_limit                3584  8 
xt_tcpudp               4224  7 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
af_packet              24840  4 
binfmt_misc            12936  1 
ipv6                  273892  16 
wacom                  17664  0 
ppdev                  10244  0 
fglrx                 656352  11 
powernow_k8            16960  1 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
video                  18060  0 
button                  8976  0 
sbs                    19592  0 
container               5504  0 
battery                11012  0 
dock                   10656  0 
ac                      6148  0 
ndiswrapper           185240  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  4 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  18828  0 
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mmc_core               28420  1 sdhci
i2c_piix4               9740  0 
soundcore               8800  1 snd
pcspkr                  4224  0 
i2c_core               26112  1 i2c_piix4
psmouse                39952  0 
k8temp                  6656  0 
serio_raw               8068  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sd_mod                 30336  4 
ata_generic             8452  0 
b44                    28300  0 
mii                     6528  1 b44
ehci_hcd               36492  0 
atiixp                  7056  0 [permanent]
ide_core              116804  2 ide_cd,atiixp
ahci                   23300  3 
libata                125168  2 ata_generic,ahci
scsi_mod              147084  3 sg,sd_mod,libata
ohci_hcd               22916  0 
usbcore               138632  5 wacom,ndiswrapper,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

If there's any insight to this problem, I'd really appreciate it!

Thanks in advance, femina ex lux

---

### Post by feminaexlux on 2008-01-17
Er, I figured it out, it WAS a permissions error, just not where I expected it. Just added the other users to the PulseAudio created groups, and it's fine...

---

