---
title: "sound plays fast"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by tmray on 2007-08-08
I just installed kubuntu feisty on my compaq with an AMD sempron processor and ATI Radeon video card and an ATI IXP SB400 AC'97 audio controller

The problem I'm having is when ever I play a song in a media player (any of them) ogg, or a cd or otherwise, it plays like someones holding down the fast forward button.

any ideas how to fix this?

---

### Post by variona on 2007-08-08
Probably your soundcard operates in a different samplingrate than your songs were sampled with.
Check out which module your soundcard uses 
lsmod | grep snd

variona

---

### Post by tmray on 2007-08-10
this is what came up

```
snd_atiixp             20620  35
snd_ac97_codec         98464  1 snd_atiixp
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_atiixp,snd_pcm

```

I tried changing the system sound settings to oss (as I see it all over this) but when I did that the players; amarok, kaffeine and VLC wouldn't even open. So I set it to auto. I tried setting it to ALSA but that also played fast.

Plus, if I play something like a youtube video everything is just fine. It's just when I try to play an audio file in any of the players on the computer that it plays like it's on fast forward.

---

### Post by variona on 2007-08-10
Output of
modinfo snd_atiixp
is:
filename:       /lib/modules/2.6.20-16-lowlatency/kernel/sound/pci/snd-atiixp.ko
license:        GPL
description:    ATI IXP AC97 controller
author:         Takashi Iwai <tiwai@suse.de>
srcversion:     34131DAFDDB377A323E2BD6
alias:          pci:v00001002d00004370sv*sd*bc*sc*i*
alias:          pci:v00001002d00004361sv*sd*bc*sc*i*
alias:          pci:v00001002d00004341sv*sd*bc*sc*i*
depends:        snd-ac97-codec,snd-pcm,snd-page-alloc,snd
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586 
parm:           index:Index value for ATI IXP controller. (int)
parm:           id:ID string for ATI IXP controller. (charp)
parm:           ac97_clock:AC'97 codec clock (default 48000Hz). (int)
parm:           ac97_quirk:AC'97 workaround for strange hardware. (charp)
parm:           spdif_aclink:S/PDIF over AC-link. (bool)
parm:           enable:bool


Maybe you try to load the module with another ac97_clock parameter (see: man modprobe) 
Not sure I never had such a problem, but maybe worth a try.
variona

---

### Post by tmray on 2007-08-11
Turns out it's xine that's causing the problem (I think)
when I played a song with xmms it was fine.

Any Idea how I can get amarok and other xine based players to play normally?

---

### Post by tmray on 2007-08-12
bump

---

