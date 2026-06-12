---
title: "ALC888 fails with PulseAudio, attempt2"
date: 2009-05-30
forum: Multimedia Software
---

### Post by soapBAR2 on 2009-05-30
I've posted this problem before, but the thread got hijacked and then died, so I'll try again. My ALC888-based soundcard does not allow multiple applications to access the sound device. I've had this problem before, but I fixed it by putting in some new lines [(LINK)]("http://amarok.kde.org/wiki/Setting_up_Dmix_for_ALSA") in /etc/asound.conf to have programs access sound via dmix. I'm sure I was using alsa back then, but I'm not entirely sure about what's happening behind the scenes of the new KDE/Ubuntu sound system (it's changed significantly, and linux multimedia is not my strongest suit ;)).

Whenever I start Amarok (amongst others), I get an error message from Phonon that "The audio playback device PulseAudio does not work. Falling back to HDA ATI SB (ALC888 Analog). From what I understand, my soundcard driver is somehow incompatible with PulseAudio, so it's therefore taken to directly accessing /dev/dsp (which of course locks the audio device for any other program until the first is killed). Does anyone know how to fix this?

I've tried
-adding new lines to /etc/asound.conf (and/or ~/.asoundrc) to have alsa access sound via dmix
-replacing PulseAudio with ESD
-(re)installing intel drivers

But to no avail.

SYSTEM INFORMATION:
Operating System: Kubuntu 9.04 Intrepid Ibex (x86_64)
Window Manager: KDE 4.2.2
Motherboard: Gigabyte GA-MA74GM-S2H [(LINK)]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2775")
Sound Card: Onboard Realtek ALC888 codec (?)
Sound Mixer: KMix 3.5
Audio Backend: Phonon Xine

```
$lspci
...
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
...

```

```
$lshw
.... 
*-multimedia
   description: Audio device
   product: SBx00 Azalia (Intel HDA)
   vendor: ATI Technologies Inc
   physical id: 14.2
   bus info: pci@0000:00:14.2
   version: 00
   width: 64 bits
   clock: 33MHz
   capabilities: bus_master cap_list
   configuration: driver=HDA Intel latency=32 module=snd_hda_intel
...

```

```

$lsmod
Module                  Size  Used by
...
snd_hda_intel         557364  5
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  16904  0
psmouse                64028  0
snd                    78792  19
snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,
snd_timer,snd_seq_device
...

```

---

### Post by KIAaze on 2009-09-29
I'm having similar problems. Did you manage to fix it by now?

SYSTEM INFORMATION:
Operating System: Kubuntu 9.04 Intrepid Ibex (x86_64)
Window Manager: KDE 4.2.2
Motherboard: Gigabyte GA-MA74GM-S2H (LINK)
Sound Card: ?
Sound Mixer: ?
Audio Backend: ?

```
$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```

```

$ lshw
        *-multimedia                                                                                                                                                                                       
             description: Audio device                                                                                                                                                                     
             product: SBx00 Azalia (Intel HDA)                                                                                                                                                             
             vendor: ATI Technologies Inc                                                                                                                                                                  
             physical id: 14.2                                                                                                                                                                             
             bus info: pci@0000:00:14.2                                                                                                                                                                    
             version: 00                                                                                                                                                                                   
             width: 64 bits                                                                                                                                                                                
             clock: 33MHz                                                                                                                                                                                  
             capabilities: pm bus_master cap_list                                                                                                                                                          
             configuration: driver=HDA Intel latency=32 module=snd_hda_intel                                           
```

```
$ lsmod | grep snd
snd_usb_audio         108832  2
snd_usb_lib            27392  1 snd_usb_audio
snd_hwdep              16776  1 snd_usb_audio
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_hda_intel         557364  6
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                99336  4 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_timer              34064  2 snd_seq,snd_pcm
snd                    78792  26 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
soundcore              16800  1 snd

```

Here's the notification I regularly get:

---

