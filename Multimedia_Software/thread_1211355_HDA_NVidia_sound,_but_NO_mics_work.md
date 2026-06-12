---
title: "HDA NVidia sound, but NO mics work"
date: 2009-07-12
forum: Multimedia Software
---

### Post by ambushsabre on 2009-07-12
So last night I was trying to get my fancy firewire mixer and mic set up, to no avail. I couldn't find any linux drivers for the thing, so I figured that was the problem, no drivers. So I went to the store and bought a cheap headset, with a mic that plugs right into the mic jack in the back of the computer. I can hear sound fine from these headphones. I am however having problems with recording, just like before. If it makes any difference, I want to use skype with my mic, but it doesn't work in any application. Heres a screenshot of my alsamixer and some other things:

[http://img8.imageshack.us/img8/1003/snapshot3h.png](http://img8.imageshack.us/img8/1003/snapshot3h.png)

Here's some other console code:
```

andrew@andrew-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

andrew@andrew-desktop:~$ lsmod
Module                  Size  Used by
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxdrv               131880  1 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  7 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfi_cmdset_0001        32768  1 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
jedec_probe            20352  0 
cfi_probe              11520  0 
gen_probe              11264  2 jedec_probe,cfi_probe
cfi_util               13696  2 cfi_cmdset_0001,cfi_probe
snd                    62628  22 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ck804xrom              12932  0 
mtd                    23048  3 cfi_cmdset_0001,ck804xrom
soundcore              15200  1 snd
chipreg                11012  3 jedec_probe,cfi_probe,ck804xrom
psmouse                61972  0 
nvidia               7233756  48 
dv1394                 25948  0 
i2c_nforce2            14980  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
map_funcs               9984  1 ck804xrom
serio_raw              13316  0 
pcspkr                 10496  0 
raw1394                32732  0 
agpgart                42696  1 nvidia
joydev                 18368  0 
usbhid                 42336  0 
forcedeth              61712  0 
ohci1394               38576  1 dv1394
ieee1394               94660  3 dv1394,raw1394,ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

andrew@andrew-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

```All of the tests in the sound config screen work, except for the recording one, which lets out a screech that makes me want to weep, and then die. If you have any info regarding this, please share. If I can VoIP working, I really don't need to go back to windows. Thanks.

---

### Post by igorzwx on 2009-07-12
This is really interesting.

On my old IBM notebook of 2003 with Ubuntu 9.04
it was actually impossible to use Skype and Ekiga.

Now they work well with OSS4.

On a power box with quadro core inside, it might be possible
to use Skype with Pulse. Or not?

---

