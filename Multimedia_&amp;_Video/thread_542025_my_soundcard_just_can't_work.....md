---
title: "my soundcard just can't work...."
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by hjbolide on 2007-09-03
feisty7.04 i've installed , but until now my laptop didn't show me its sound
    compaq presario b1925tu 
    

    lspci
    00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
    

    lshw
     *-multimedia
             description: Audio device
             product: SB450 HDA Audio
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: iomemory:c0500000-c0503fff irq:16
   

     lsmod | grep snd
snd_hda_intel         263576  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56324  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
  

    and i'm using 2.6.20-16-generic 
    could someone helps?i've been trying any solution,,,,,any solution about hda sb450 and realtek alc260,but just can't help
    [ATTACH]42489[/ATTACH]

---

### Post by linuxwizard on 2007-09-03
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

