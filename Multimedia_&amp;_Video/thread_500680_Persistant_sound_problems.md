---
title: "Persistant sound problems"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by bountonw on 2007-07-14
I am have not had any sound since installing Ubuntu over 1 month ago.  I have read through the comprehensive sound solutions guide [here.]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
I am not sure what exactly to do next.

I am using Ubuntu 7.04.  


Here is what I have so far.  
```

sound in alsamixer is unmuted
```
```

sudo lspci -vv
```


```
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: Elitegroup Computer Systems Unknown device 2171
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

```

```
aplay -l
```


```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lsmod | grep snd
```

```
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
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

```

```
lspnp -vv
```

```
lspnp: /proc/bus/pnp not available
```

And, yes, the speakers are plugged in and turned on.  They also work on other systems.

My children are about to commit mutiny.  Any help is appreciated!!

---

### Post by linuxwizard on 2007-07-14
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by bountonw on 2007-07-14
Thank you, for the suggested troubleshooting directions.  They are very similar to what I already linked to in my original post.

I guess what I am asking is for someone to help my untrained eye to see if what I have is ok. Is there a problem in what I have posted that I don't see?  I am a little afraid of  >  Getting the ALSA drivers from a *fresh* kernel

I have never done anything like that before.

Some advice would be helpful.

---

### Post by bountonw on 2007-07-15
I succeeded in "getting Alsa drivers  from a *fresh* kernel" and then re-installing my desktop via the command line as suggested from the trouble shooting advice. 

BTW I am using Edubuntu 7.04 on both of my children's computers and neither one has sound.  (I have Ubuntu 7.04 at the office.  I don't know if it has sound or not because I don't use sound on that computer.)

Would someone please tell me what to try next.  Based on my original post, I don't see anything wrong with my system, but I still can not hear sound in juicer or firefox (the two types of sound that i have tried.)

:confused:

---

### Post by bountonw on 2007-07-15
I did 
```
sudo modprobe snd-via82xx
```

Still no sound.

(I have tried both the front jack and the back jack each time I make a change and there is still no sound.)

I would really appreciate some knowledgeable advice.

Thanks.

---

### Post by bountonw on 2007-07-16
I know it is probably right in front of my face, but will someone please tell me whether there is anything wrong with my sound configurations as I have posted so far.  

And then what I should do next.  I have been trying to convince some friends to join Linux, but when they see me go over a month without sound, they are not very interested.  (Although Linux has a lot going for it even without sound.)

---

### Post by bountonw on 2007-07-16
I did 
```
lsmod
```

and got

lsmod

```
Module                  Size  Used by
ipv6                  268960  8 
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
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
battery                10756  0 
container               5248  0 
asus_acpi              17308  0 
dock                   10268  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
video                  16388  0 
button                  8720  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  4 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
i2c_viapro             10132  0 
pcspkr                  4224  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
via_agp                11264  1 
serio_raw               7940  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  1 via_agp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
sd_mod                 23428  3 
ata_generic             9092  0 
floppy                 59524  0 
ehci_hcd               34188  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
sata_via               12548  2 
libata                125720  2 ata_generic,sata_via
scsi_mod              142348  3 sg,sd_mod,libata
generic                 5124  0 [permanent]
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

```

---

### Post by bountonw on 2007-07-16
By typing 

```
uname -r
```

I see my kernal release is 

```
2.6.20-16-generic
```

I don't know if that is helpful or not.

I have posted everything I can think of.   (I see that as a NEWBIE I should have posted this thread in the newbie section.)

---

### Post by bountonw on 2007-07-16
The next thing on the troubleshooting guide is

> ALSA driver compilation

Do I need to do this?

Is anyone out there?  The only comment on this thread so far is to refer me to a dupicate of the troubleshooting guide that I already linked to in my original post.

I know that my problem is probably something really dumb and obvious, but I still don't see it and my children are giving me no end of hassle until I provide them with sound.

Question 1:  In my numerous posts in this thread are there any errors in my sound system?
Question 2:  What do I do next??????  I have tried many things (as is evident from my posts).  I have also tried to read and research in my limited time.  

Will someone please lend a hand.  The silence is deafening. (Pun intended).  

(I am beginning to wonder if converting to Linux was the right thing to do.  After solving the sound on my children's computers, I have to figure out how to get the USB working on my wife's computer.) (I thought I could afford the three computers with the understanding that at least most of  the software would be free.  I don't mind learning something new, but in the end, it needs to be functional.  So far, I am not experiencing that.)

---

### Post by fredj on 2007-07-16
Your sound chip the ALC861VD is supported in the 2.6.21 linux kernel but I don't think this is available
for Ubuntu yet. This is a recent sound chip so its not surprising that it has taken time for the Alsa people
to incorporate it into their drivers. Windows Vista users have also had to wait for suitable drivers.

---

### Post by bountonw on 2007-07-17
Fredj,

Thank you for pointing out the source of the problem.
I see that Ubuntu Gutsy Gibbon 7.10 will have the 2.6.22-6.13 kernel.

Is there a way for me to upgrade my kernel to 2.6.21 now on Ubuntu 7.04? or do I have to wait until October when Gutsy Gibbon comes out?

---

### Post by bountonw on 2007-07-17
I am trying to install the latest kernel.  Ran into problems and started a new thread [here.]("http://ubuntuforums.org/showthread.php?t=502956")

I will post back if the new kernel solves my sound problems or not.

---

### Post by bountonw on 2007-07-18
Updating the kernel solved my problem to 2.6.22 solved my problem.

I have sound!!

:guitar:

---

