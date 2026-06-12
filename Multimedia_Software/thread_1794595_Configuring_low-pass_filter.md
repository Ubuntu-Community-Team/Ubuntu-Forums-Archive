---
title: "Configuring low-pass filter"
date: 2011-07-01
forum: Multimedia Software
---

### Post by Geidrow on 2011-07-01
Good day all!
I could ask some details about setup speaker configuration (after reading article
"Low-pass filter for subwoofer channel (HOWTO) by Benjamin Eikel)

     1. There are 2 sound cards in my PC:
     cat /proc/asound/modules returns
     0 snd_hda_intel
     1 snd_emu10k1.
     4 satellites, a subwoofer
     
     2. Used Kubuntu 10.04.
     
     3.blop and cmt packeges was installed by Synaptic.
     4. /etc/asound.conf was created and then I paste to it follow text:
     pcm.upmix_20to51 {
     type plug
     slave.pcm lowpass_21to21
     slave.channels 3
     ttable {
     0.0 1 # left channel
     1.1 1 # right channel
     0.2 0.5 # mix left and right ...
     1.2 0.5 # ... channel for subwoofer
     }
     }
     
     pcm.lowpass_21to21 {
     type ladspa
     slave.pcm upmix_21to51
     path "/usr/lib/ladspa"
     channels 3
     plugins {
     0 {
     id 1098 # Identity (Audio) (1098/identity_audio)
     policy duplicate
     input.bindings.0 "Input";
     output.bindings.0 "Output";
     }
     1 {
     id 1672 # 4 Pole Low-Pass Filter with Resonance (FCRCIA)     (1672/lp4pole_fcrcia_oa)
     policy none
     input.bindings.2 "Input";
     output.bindings.2 "Output";
     input {
     controls [ 300 2 ]
     }
     }
     }
     }
     
     pcm.upmix_21to51 {
     type plug
     slave.pcm surround51
     slave.channels 5
     ttable {
     0.0 1 # front left
     1.1 1 # front right
     0.2 1 # rear left
     1.3 1 # rear right
     2.5 1 # subwoofer
     }
     hint {
     show on
     description "Upmix channel"
     }
     }
     
     
     
     A problem is: when I try to check sound in SystemSettings/Multimedia     a     message displayed : "The device Upmix channel does not work", and     sounds playing by snd_hda_intel. So this settings does not applyed     to     snd_emu10k1.
     
     Where is my mistake? I should use Creative SBLive (snd_emu10k1).
     How I can specify that Upmix channel would applyed only for     snd_emu10k1?
     
     Thank you in advance      -- 
Ronaldinho

---

