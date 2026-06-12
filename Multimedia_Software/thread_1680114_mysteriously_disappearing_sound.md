---
title: "mysteriously disappearing sound"
date: 2011-02-02
forum: Multimedia Software
---

### Post by DatBugler on 2011-02-02
Hi,

My sound was working fine until yesterday, when it mysteriously went silent after I unplugged and replugged my headphone cable. None of my settings for Phonon, Pulse Audio, or ALSA appear to have changed, with the exception that while the "headphone" slider was formerly greyed out in ALSAMixer, it is now lit up. I have tried using a different cable, which I know works, and I have tried using all of the eighth inch ports on the computer with no luck.

I run Kubuntu 10.10 on this desktop system. All my packages are up to date. Here are some relevant specs:
```

~$ uname -rm
2.6.35-25-generic x86_64

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have the HDA NVidia devices disabled in PulseAudio, and I haven't so far succeeded in getting sound out of the Audiophile card, though MIDI in has been working with the Audiophile card both before and after my problem started. I doubt it's relevant, but for some reason when I set the Audiophile card as sound input in QJackCtl I get XRuns. Anyway, the sound output I mainly use is the HDA ATI SB, and that's the one that stopped working. I have it set to Analog Stereo Duplex in PulseAudio Volume Control, which worked fine until recently. It is the fallback interface, and is set to get the highest priority in Phonon. I use Xine as my Phonon backend.

When I play back audio, the levels show up in PulseAudio Volume Control, and nothing appears to be having trouble recognizing the appropriate sound interface. At a first glance I have the appropriate modules loaded, and my sound cards show up. Jack even starts up fine, it's just silent. I have tried setting the "Internal Audio" interface to both "Analog Headphones" and "Analog Output," but neither works. Output used to be the one that worked.

I'm utterly stumped, so any help would be most appreciated. I'm a professional musician, so you can understand why this might be a little important. :)

Here's the only thing I could find poking around that looked like a clue. The log covers about the time the problem started, from a bit before (if I remember correctly) to present.
```

~$ cat /var/log/user.log | grep alsa
Jan 31 02:27:22 Samiel pulseaudio[1914]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!                                                                                                                                
Jan 31 02:27:22 Samiel pulseaudio[1914]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.                                                                                                           
Jan 31 02:27:22 Samiel pulseaudio[1914]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.                                                                                                       
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 183920 bytes (1042 ms).                                                                                                                                    
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_ice1712'. Please report this issue to the ALSA developers.                                                                                                             
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: snd_pcm_dump():                                                                                                                                                                                                          
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Hooks PCM                                                                                                                                                                                                                
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Its setup is:                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   stream       : PLAYBACK                                                                                                                                                                                                
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   access       : MMAP_INTERLEAVED                                                                                                                                                                                        
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   format       : S16_LE                                                                                                                                                                                                  
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   subformat    : STD                                                                                                                                                                                                     
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   channels     : 2                                                                                                                                                                                                       
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   rate         : 44100                                                                                                                                                                                                   
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   exact rate   : 44100 (44100/1)                                                                                                                                                                                         
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   msbits       : 16                                                                                                                                                                                                      
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   buffer_size  : 6553                                                                                                                                                                                                    
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_size  : 3276                                                                                                                                                                                                    
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_time  : 74285                                                                                                                                                                                                   
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   tstamp_mode  : ENABLE                                                                                                                                                                                                  
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_step  : 1                                                                                                                                                                                                       
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   avail_min    : 4348                                                                                                                                                                                                    
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_event : 0                                                                                                                                                                                                       
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   start_threshold  : -1                                                                                                                                                                                                  
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   stop_threshold   : 7378022089539715072                                                                                                                                                                                 
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   silence_threshold: 0                                                                                                                                                                                                   
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   silence_size : 0                                                                                                                                                                                                       
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   boundary     : 7378022089539715072                                                                                                                                                                                     
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Slave: Route conversion PCM (sformat=S32_LE)                                                                                                                                                                             
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   Transformation table:                                                                                                                                                                                                  
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     0 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     1 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     2 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     3 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     4 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     5 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     6 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     7 <- none                                                                                                                                                                                                            
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     8 <- 0                                                                                                                                                                                                               
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:     9 <- 1                                                                                                                                                                                                               
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Its setup is:
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   stream       : PLAYBACK
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   format       : S16_LE
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   subformat    : STD
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   channels     : 2
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   rate         : 44100
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   msbits       : 16
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   buffer_size  : 6553
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_size  : 3276
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_time  : 74285
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   tstamp_mode  : ENABLE
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_step  : 1
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   avail_min    : 4348
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_event : 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   start_threshold  : -1
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   stop_threshold   : 7378022089539715072
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   silence_threshold: 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   silence_size : 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   boundary     : 7378022089539715072
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Slave: Hardware PCM card 1 'M Audio Audiophile 24/96' device 0 subdevice 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c: Its setup is:
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   stream       : PLAYBACK
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   format       : S32_LE
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   subformat    : STD
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   channels     : 10
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   rate         : 44100
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   msbits       : 24
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   buffer_size  : 6553
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_size  : 3276
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_time  : 74285
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   tstamp_mode  : ENABLE
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_step  : 1
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   avail_min    : 4348
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   period_event : 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   start_threshold  : -1
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   stop_threshold   : 7378022089539715072
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   silence_threshold: 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   silence_size : 0
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   boundary     : 7378022089539715072
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   appl_ptr     : 50492
Feb  1 01:06:47 Samiel pulseaudio[1914]: alsa-util.c:   hw_ptr       : 89919
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 164896 bytes (934 ms).
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_ice1712'. Please report this issue to the ALSA developers.
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: snd_pcm_dump():
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Hooks PCM
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Its setup is:
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   stream       : PLAYBACK
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   format       : S16_LE
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   subformat    : STD
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   channels     : 2
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   rate         : 44100
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   msbits       : 16
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   buffer_size  : 6553
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_size  : 3276
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_time  : 74285
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   tstamp_mode  : ENABLE
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_step  : 1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   avail_min    : 6112
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_event : 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   start_threshold  : -1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   stop_threshold   : 7378022089539715072
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   silence_threshold: 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   silence_size : 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   boundary     : 7378022089539715072
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Slave: Route conversion PCM (sformat=S32_LE)
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   Transformation table:
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     0 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     1 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     2 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     3 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     4 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     5 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     6 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     7 <- none
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     8 <- 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:     9 <- 1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Its setup is:
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   stream       : PLAYBACK
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   format       : S16_LE
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   subformat    : STD
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   channels     : 2
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   rate         : 44100
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   msbits       : 16
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   buffer_size  : 6553
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_size  : 3276
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_time  : 74285
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   tstamp_mode  : ENABLE
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_step  : 1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   avail_min    : 6112
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_event : 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   start_threshold  : -1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   stop_threshold   : 7378022089539715072
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   silence_threshold: 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   silence_size : 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   boundary     : 7378022089539715072
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Slave: Hardware PCM card 1 'M Audio Audiophile 24/96' device 0 subdevice 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c: Its setup is:
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   stream       : PLAYBACK
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   format       : S32_LE
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   subformat    : STD
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   channels     : 10
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   rate         : 44100
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   msbits       : 24
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   buffer_size  : 6553
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_size  : 3276
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_time  : 74285
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   tstamp_mode  : ENABLE
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_step  : 1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   avail_min    : 6112
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   period_event : 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   start_threshold  : -1
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   stop_threshold   : 7378022089539715072
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   silence_threshold: 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   silence_size : 0
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   boundary     : 7378022089539715072
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   appl_ptr     : 36227
Feb  1 01:25:31 Samiel pulseaudio[1829]: alsa-util.c:   hw_ptr       : 70898

```

Just in case it's useful, here's what my sound modules look like:
```

~$ lsmod | grep snd
snd_hda_codec_nvhdmi    15451  4 
snd_ice1712            66696  0 
snd_ice17xx_ak4xxx      3115  1 snd_ice1712
snd_ak4xxx_adda         9318  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7938  1 snd_ice1712
snd_hda_codec_via      62447  1 
snd_ac97_codec        125227  1 snd_ice1712
ac97_bus                1474  1 snd_ac97_codec
snd_i2c                 5574  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6849  1 snd_ice1712
snd_hda_intel          26115  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_seq_midi            5932  0 
snd_hwdep               6660  1 snd_hda_codec
snd_seq_midi_event      7291  1 snd_seq_midi
snd_rawmidi            22207  2 snd_mpu401_uart,snd_seq_midi
snd_pcm                89104  4 snd_ice1712,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_seq                57512  3 snd_seq_midi,snd_seq_midi_event
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              23850  2 snd_seq,snd_pcm
snd                    64181  20 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_hda_codec_via,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm

```

Once again, any help would be most appreciated.

---

### Post by DatBugler on 2011-02-03
Bump.

---

### Post by DatBugler on 2011-02-03
Just another data point:

I can run *aplay somefile.mp3* without getting any errors. So it looks like ALSA thinks nothing is wrong, but there is still no sound. I am totally stumped.

---

