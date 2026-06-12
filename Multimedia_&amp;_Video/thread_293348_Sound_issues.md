---
title: "Sound issues"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by NightWolf_Wicca on 2006-11-05
OK, I'm having some issues with my sound system here. I have a Logitech USB headset that I want to get running. Right now I can listen to music and stuff like that, but I'm not getting any system sounds. It was worse before, I wasn't getting any sound at all, but then I took out the PCI sound card, and now I can hear music if it's being played through amarok, kaffine or some other program similar to that; The problem is that I can't get any system sounds.

I figure it's something with the aRts sound server in KDE (yes, i removed gnome and pulled in KDE. I like it better, and it's faster). My best guess is that I need to manually override the device location, but I have no idea what to put. I've tried the only dsp location that I have in /dev, and that didn't work. I am clueless on this one. Any ideas floating around? At this point, anything would be helpful.

Thanks in advance,
NightWolf

---

### Post by NightWolf_Wicca on 2006-11-05
What? no body has any ideas?

---

### Post by DaveBorealis on 2006-11-05
As long as you want "any" ideas, let me throw out the obvious one.  Have you tried running alsamixer and playing with the setting?

Best regards,
Dave

---

### Post by NightWolf_Wicca on 2006-11-05
I have now. no luck

---

### Post by DaveBorealis on 2006-11-05
Here's another.  Note the kind of PCI sound card you have, re-insert it, and do a lsmod to see if the module matches the card.  You might have to google the card to see what the recommended module(s) is(are).

---

### Post by NightWolf_Wicca on 2006-11-05
well, what am i looking for? here's the lsmod output:

Module                  Size  Used by
ppp_deflate             7424  0
zlib_deflate           21912  1 ppp_deflate
bsd_comp                7552  0
ppp_async              13568  1
crc_ccitt               3200  1 ppp_async
ppp_generic            30612  7 ppp_deflate,bsd_comp,ppp_async
slhc                    8448  1 ppp_generic
ipv6                  272288  10
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
apm                    23280  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
lp                     12964  0
af_packet              24584  2
snd_usb_audio          80416  1
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
tsdev                   9152  0
snd_pcm                84612  2 snd_usb_audio,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd_page_alloc         11400  1 snd_pcm
snd_usb_lib            18816  1 snd_usb_audio
snd_rawmidi            27264  1 snd_usb_lib
snd_seq_device          9868  1 snd_rawmidi
snd_hwdep              10756  1 snd_usb_audio
snd                    58372  10 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
cdc_acm                16288  3
usbhid                 45152  0
psmouse                41352  0
soundcore              11232  1 snd
evdev                  11392  1
parport_pc             37796  1
parport                39496  2 lp,parport_pc
serio_raw               8452  0
pcspkr                  4352  0
i2c_amd756              7556  0
tulip                  54816  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
amd_k7_agp             10252  1
agpgart                34888  1 amd_k7_agp
i2c_core               23424  1 i2c_amd756
ext3                  142728  1
jbd                    62228  1 ext3
ohci_hcd               22532  0
usbcore               134912  6 snd_usb_audio,snd_usb_lib,cdc_acm,usbhid,ohci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  3
generic                 5764  0
amd74xx                15260  0 [permanent]
processor              31560  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

as a reminder, i'm trying to get a Logitech USB headset to play system sounds. the normal pci card worked just fine, i just don't have any speakers, headphones with a long enough cord, or money to buy either.

---

### Post by NightWolf_Wicca on 2006-11-07
sorry for the bump, but ***_[COLOR="Red"]BUMP[/COLOR]_***

---

