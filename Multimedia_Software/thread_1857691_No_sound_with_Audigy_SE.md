---
title: "No sound with Audigy SE"
date: 2011-10-10
forum: Multimedia Software
---

### Post by phyll_ on 2011-10-10
Hi,
I have installed Ubuntu 10.04 last week. Everything is working out fine so far, except for the sound. I myself am rather new to Linux, but a more experienced friend could not help me either, so I am asking here.

-No sound is played at all. I also have Windows installed and it works fine there.

-Sound card is a Soundblaster Audigy SE.

-Speakers are connected to an output on the Sound card via 3,5mm connector

-cat /proc/asound/cards returns 
```
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xd000 irq 20

```(There were 2 more, an Intel HDA and some HDMI stuff from my ATI graphics card. We deactivated both, which didn't help.)

-When i try aplay to play some file, it plays with no error messages.

-alsamixer has everything turned on except for S/PDIF.

-lsmod returns 
```
nls_utf8               12493  1 
isofs                  39571  1 
vesafb                 13449  1 
snd_ca0106             39319  2 
snd_ac97_codec        105614  1 snd_ca0106
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_ca0106,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd                    55295  11 snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid_cherry             12547  0 
psmouse                59039  0 
fglrx                2434640  106 
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_ca0106,snd_pcm
serio_raw              12990  0 
x38_edac               12960  0 
edac_core              42881  2 x38_edac
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  2 hid_cherry,usbhid
firewire_ohci          31504  0 
floppy                 60032  0 
r8169                  46630  0 
ahci                   21591  3 
firewire_core          56138  1 firewire_ohci
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core
pata_jmicron           12651  0 

```

I have tried for 3 hours to fix the problem, maybe someone will see what I have missed. 
Thanks,

---

### Post by phyll_ on 2011-10-12
Update: 
I have meanwhile tried everything mentioned in various troublshooting guides like
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
Nothing had any effect. Should I just wait for the next update and hope it fixes my problem?

---

