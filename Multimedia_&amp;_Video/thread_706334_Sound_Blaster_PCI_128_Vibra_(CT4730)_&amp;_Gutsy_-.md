---
title: "Sound Blaster PCI 128 Vibra (CT4730) &amp; Gutsy - No Sound"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by brucetan on 2008-02-24
Hello,

I just installed Ubuntu 7.10 but no sound.

My sound card is Sound Blaster PCI 128 Vibra (Model CT4730).

The following are the OS configuration related to the sound card:

> ~$ lspci
00:0b.0 Multimedia audio controller: Creative Labs Ectiva EV1938

> ~$ lshw
        *-multimedia
             description: Multimedia audio controller
             product: Ectiva EV1938
             vendor: Creative Labs
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ENS1371 latency=32 maxlatency=128 mingnt=12 module=snd_ens1371

> ~$ lsmod | grep snd
snd_ens1371             27680  1
gameport                  16776  1 snd_ens1371
snd_ac97_codec        100644  1 snd_ens1371
ac97_bus                  3200  1 snd_ac97_codec
snd_pcm_oss             44672  0
snd_mixer_oss           17664  1 snd_pcm_oss
snd_pcm                    80388  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy        4740  0
snd_seq_oss               33152  0
snd_seq_midi             9600  0
snd_rawmidi              25728  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event   8448  2 snd_seq_oss,snd_seq_midi
snd_seq                     53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer                  24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                            54660  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                 8800  1 snd
snd_page_alloc          11400  1 snd_pcm

> ~$ cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                              Ensoniq AudioPCI ENS1371 at 0xa000, irq 10


I suspect it is using the wrong driver.  I read from [http://www.pcdirectsource.com/Item.cfm?ID=458](http://www.pcdirectsource.com/Item.cfm?ID=458) that the chipset is "**EMU 10K1**"

Can someone confirm this and advise how to correct the above configuration?

Many thanks in advance.

Bruce

---

### Post by brucetan on 2008-02-28
Anyone? Please help!](*,)]

---

### Post by jebblue on 2008-02-28
As suggested in this thread: [http://ubuntuforums.org/archive/index.php/t-370214.html](http://ubuntuforums.org/archive/index.php/t-370214.html) make sure the onboard audio (if installed) is actually disabled in the BIOS.

---

### Post by brucetan on 2008-03-02
Thanks Jebblue.  There is no Audio function on Motherboard and the BIOS does not have entry for such function also.

Bruce

---

