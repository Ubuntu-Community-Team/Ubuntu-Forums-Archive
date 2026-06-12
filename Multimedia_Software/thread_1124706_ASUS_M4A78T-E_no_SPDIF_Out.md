---
title: "ASUS M4A78T-E no S/PDIF Out"
date: 2009-04-13
forum: Multimedia Software
---

### Post by gus_zernial on 2009-04-13
I have an ASUS M4A78T-E mobo running Kubuntu Jaunty 9.04 with a 
custom 2.6.28.9 kernel. I am getting sound out the Line Out/Speaker
Out jacks, but no sound through the Toslink S/PDIF Out jack.

This mobo has 8.1 channel HD Audio out using Via VT1708S chip,
plus HDMI out, which I think is by the integrated Radeon HD3300
mobo GPU (?). Questions:

1) Is the S/PDIF Out through the Via VT1708S??

2) Can I get sound out through the Line Out/Speaker Out jacks
*and* the S/PDIF Out simultaneously? (In my setup these go through
separate amplifiers/speakers in different rooms).

3) What do I have to do to enable S/PDIF Out?

Some (I hope) relevant command outputs below ...

Thanks!


$ aplay -L
default:CARD=SB
    HDA ATI SB, VT1708S Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

$ lspci -v

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Device 8357:1043                                
        Flags: bus master, slow devsel, latency 64, IRQ 16         
        Memory at fbbf4000 (64-bit, non-prefetchable) [size=16K]   
        Capabilities: <access denied>                              
        Kernel driver in use: HDA Intel                            
        Kernel modules: snd-hda-intel          

       
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ATI Technologies Inc RS780 Azalia controller
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fbdfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

$ lsmod | grep snd
snd_seq_dummy          11012  0
snd_seq_oss            38016  0
snd_hda_intel         433332  4
snd_seq_midi           14464  0
snd_rawmidi            29568  1 snd_seq_midi
snd_seq_midi_event     15360  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            46080  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq                57136  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_device         15244  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29320  2 snd_seq,snd_pcm
snd                    62500  17 snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              15456  1 snd
snd_page_alloc         17160  2 snd_hda_intel,snd_pcm

---

