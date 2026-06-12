---
title: "Audio Problem after Electric down"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by sEaL_Zealot on 2007-08-22
First, I'm sorry if I use poor English and post in wrong forum because I can't see where can I post this.

I'm newbie to use Ubuntu.
I installed Fiesty(7.04) and it works normal with my soundcard(VIT VT82XX).
But the problem is electric down while I use It.
After that My sound goes error.
It have High frequency sound comes up with normal sound every time.
How can I fix it?

---

### Post by DeusEx on 2007-08-22
Voltage peaks / dips can be very bad for hardware.

Are you using integrated speakers? If not, try to find out whether it's the soundcard that's outputting the HF noise or your speakers.
Also you could check whether it's software by doing a soundcheck in a different OS (liveCD, knoppix, windows?)

In my opinion though it sounds like soundcard components gone bad.

---

### Post by sEaL_Zealot on 2007-08-22
Thanks for reply,
I forgot to tell you that I check my soundcard after the problem in MS Windows (on same PC) and my sound work normally.
But When I restart to Ubuntu, the problem occur again(occur only on Ubuntu).

Should I reinstall soundcard driver?
and how?

---

### Post by sEaL_Zealot on 2007-08-23
Can someone tell me how to reinstall soundcard driver?

---

### Post by DeusEx on 2007-08-23
You're probably looking for this:
```

lsmod

```
and
```

modprobe

```

Maybe alsa is broken? you can reinstall it using synaptic package manager

---

### Post by sEaL_Zealot on 2007-08-23
Thank you again,
I'll try to reinstall ALSA driver first.
If it not work I'll try to use lsmod and modprobe as you introduce me.
In that step May I have your help?

------------------------------
OK,
I try to reinstall alsa by use synaptic and reinstall all installed that match the search by keyword ALSA.
Bad luck,
It's not solve the problem.
After that I try lsmod, I got this text :
------------------------------
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
ac                      6020  0 
video                  16388  0 
container               5248  0 
dock                   10268  0 
button                  8720  0 
backlight               7040  1 asus_acpi
af_packet              23816  0 
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
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
nvidia               4713780  22 
parport_pc             36388  1 
serio_raw               7940  0 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
i2c_viapro             10132  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_viapro
via_agp                11264  1 
pcspkr                  4224  0 
agpgart                35400  2 nvidia,via_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ipv6                  268960  10 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
sd_mod                 23428  3 
floppy                 59524  0 
sata_via               12548  2 
ehci_hcd               34188  0 
via82cxxx              10372  0 [permanent]
uhci_hcd               25360  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
ata_generic             9092  0 
libata                125720  2 sata_via,ata_generic
usbcore               134280  3 ehci_hcd,uhci_hcd
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
---------------------------------------------
and how can I do after this?

---

### Post by DeusEx on 2007-08-24
I don't use those commands very often, but they're for listing (lsmod) and managing (modprobe) modules.

see: [http://linux.about.com/library/cmd/blcmdl8_lsmod.htm](http://linux.about.com/library/cmd/blcmdl8_lsmod.htm)
and [http://linux.about.com/od/commands/l/blcmdl8_modprob.htm](http://linux.about.com/od/commands/l/blcmdl8_modprob.htm)

---

### Post by DeusEx on 2007-08-24
Apparantly your soundcard uses **snd_hda_intel** so you hava an Intel HDA card.

In some other topic I read that this is part of **linux-ubuntu-modules** (see synaptic)
Your driver file probably resides in **/lib/modules/2.6.xx-xx-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko**

You should be able to compile the hda intel drivers using the source from the Alsa website. I guess there's a howto on their website too, my knowledge is limited concerning (re)compiling alsa drivers...

Good luck!

---

### Post by sEaL_Zealot on 2007-08-24
Thank you for your continuous answer without feel annoyed me.
I got to recompile alsa driver now.

I will report the result soon.

-------------

I try > modprobe soundcore and > modprobe snd_hda_intel
and try to reinstall all installed in multimedia category on Synaptic.
after that I test the sound...
Good luck !!!
It work...

But only one time,
After I restart ubuntu, it appear again...
I give up for this...
I will reinstall Ubuntu again ...

PS. Thank you very much for your help, DeusEX.

---

### Post by DeusEx on 2007-08-24
No problem, I was bored at work anyway!

Back to your problem:
Could be that modprobe doesn't load it permanently. 
Check out this link: [https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

