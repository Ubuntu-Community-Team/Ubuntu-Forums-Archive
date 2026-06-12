---
title: "M-Audio 24/96 - Sound issues."
date: 2008-05-05
forum: Multimedia Software
---

### Post by trey85stang on 2008-05-05
Im having a weird problem with a audiophile 24/96.  I cant seem to figure this out so Im posting for help.

The card works fine with jackd and with almost any app where I can manually select a sound device.  However,  I cant get any gnome related apps to use this card,  i get all kinds of error messages and nothing I try produces any results.

Here are a few of the error messages from gstreamer-properties, tests:

Plugin: Autodetect
"Autodetect: Internal data flow error."

Plugin: ALSA
ALSA - Advanced Linux Sound Architecture: Could not negotiate format

In the terminal,  here is a little more specific message

```

streaming task paused, reason not-linked (-1)]
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline8/audiotestsrc10:
Check your filtered caps, if any]

```

Now, Im pretty sure the filter caps the error message is referring to has nothing to do with the power supply on the computer. :D

Here is the error message from totem:
"Failed to connect stream: Invalid argument"

Anyone have ideas of what I can check?  Im thinking this is probably gstreamer issue and I am not sure what to do to make it work?

---

### Post by trey85stang on 2008-05-06
anyone?

---

### Post by trey85stang on 2008-05-08
```
trey@locke:~$ aplay
aplay: main:546: audio open error: Device or resource busy
trey@locke:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
trey@locke:~$ 


```

No matter what I do aplay shows device busy...  occasionally when it does not show device busy I get a loud static out of the speaker,  yet gstreamer still wont work?

---

### Post by trey85stang on 2008-05-08
I rebooted and it free'd up the device,  stil getting errors with gstreamer though...

if this helps

```

trey@locke:/dev/snd$ lsmod | grep snd
snd_ice1712            63860  1 
snd_ice17xx_ak4xxx      5120  1 snd_ice1712
snd_ak4xxx_adda         9472  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             10240  1 snd_ice1712
snd_ac97_codec        101284  1 snd_ice1712
snd_pcm_oss            42400  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78724  3 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
ac97_bus                3200  1 snd_ac97_codec
snd_i2c                 6528  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9984  1 snd_ice1712
snd_seq_dummy           4868  0 
snd_seq_oss            35968  0 
snd_seq_midi            9376  0 
snd_rawmidi            25632  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54992  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57636  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd
trey@locke:/dev/snd$ 

```

Also I notice this...

```

trey@locke:~$ alsaplayer
error on set_format SND_PCM_FORMAT_S16
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S32_LE
SUBFORMAT:  STD
SAMPLE_BITS: 32
FRAME_BITS: 320
CHANNELS: 10
RATE: [8000 96000]
PERIOD_TIME: (20 409500]
PERIOD_SIZE: [2 3276]
PERIOD_BYTES: [80 131040]
PERIODS: [1 1024]
BUFFER_TIME: (20 819125]
BUFFER_SIZE: [2 6553]
BUFFER_BYTES: [80 262120]
TICK_TIME: ALL
error on set_format SND_PCM_FORMAT_S16
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S32_LE
SUBFORMAT:  STD
SAMPLE_BITS: 32
FRAME_BITS: 320
CHANNELS: 10
RATE: [8000 96000]
PERIOD_TIME: (20 409500]
PERIOD_SIZE: [2 3276]
PERIOD_BYTES: [80 131040]
PERIODS: [1 1024]
BUFFER_TIME: (20 819125]
BUFFER_SIZE: [2 6553]
BUFFER_BYTES: [80 262120]
TICK_TIME: ALL
failed to configure output device...trying OSS
error on set_format SND_PCM_FORMAT_S16
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S32_LE
SUBFORMAT:  STD
SAMPLE_BITS: 32
FRAME_BITS: 320
CHANNELS: 10
RATE: [8000 96000]
PERIOD_TIME: (20 409500]
PERIOD_SIZE: [2 3276]
PERIOD_BYTES: [80 131040]
PERIODS: [1 1024]
BUFFER_TIME: (20 819125]
BUFFER_SIZE: [2 6553]
BUFFER_BYTES: [80 262120]
TICK_TIME: ALL
error on set_format SND_PCM_FORMAT_S16
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S32_LE
SUBFORMAT:  STD
SAMPLE_BITS: 32
FRAME_BITS: 320
CHANNELS: 10
RATE: [8000 96000]
PERIOD_TIME: (20 409500]
PERIOD_SIZE: [2 3276]
PERIOD_BYTES: [80 131040]
PERIODS: [1 1024]
BUFFER_TIME: (20 819125]
BUFFER_SIZE: [2 6553]
BUFFER_BYTES: [80 262120]
TICK_TIME: ALL
failed to configure output device...trying OSS
 trey@locke:~$ alsaplayer -d /dev/dsp
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
snd_pcm_open: No such file or directory (/dev/dsp)
Failed to initialize plugin!
Failed to register plugin: /usr/lib/alsaplayer/output/libalsa_out.so
Failed to load output plugin "alsa". Trying defaults.
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
snd_pcm_open: No such file or directory (/dev/dsp)
Failed to initialize plugin!
/usr/lib/alsaplayer/output/libalsa_out.so failed to load
jack: server not running?
/usr/lib/alsaplayer/output/libjack_out.so failed to load
NOTE: THIS IS THE NULL PLUGIN.      YOU WILL NOT HEAR SOUND!!

```

fwiw,  I had this card working under the previous version before the upgrade... :confused:

---

### Post by trey85stang on 2008-05-09
i guess this all might be related to some pulse audio app or something?  (wtf is wrong with just useing alsa?) I found some threads about removing pulseaudio and cleaning up asound.conf so I will give those a whirl.

---

### Post by johnabdl on 2008-05-12
I'm brand-new to Ubuntu--8.04--and can't any sound from Gnome apps either, on my Audiophile 2426.  I don't yet know anything to speak of about setting up soundcards in Linux.  

But I can't even see the Audophile.  When I 

   cat /proc/asound/modules

All that's returned is, 
 
   0 snd_intel8x0
   1 snd_ice1712

I don't see the Audiophile.

What next?  
I haven't find any drivers on the 'net yet.

---

### Post by trey85stang on 2008-05-13
> **johnabdl said:**
> I'm brand-new to Ubuntu--8.04--and can't any sound from Gnome apps either, on my Audiophile 2426.  I don't yet know anything to speak of about setting up soundcards in Linux.  

But I can't even see the Audophile.  When I 

   cat /proc/asound/modules

All that's returned is, 
 
   0 snd_intel8x0
   1 snd_ice1712

I don't see the Audiophile.

What next?  
I haven't find any drivers on the 'net yet.

snd-ice1712 is the audiophile,  aplay -l  shoudl yield a M2496 result.  If you're an ubuntu newb,  just check to make sure the card is not muted in volume control.

FWIW,  I reinstalled 8.04 as a fresh install and not an upgrade and everything then worked fine.  I figured it was best after changing 100 different files ine /etc trying to make it work and not remembering what all I had actually changed.

---

### Post by johnabdl on 2008-05-20
OK, I can now open Preferences > Sound and get the following results:

Sound Events
 Sound playback: Autodetect - testing window, but no sound
                 ICE1712 multi - testing window, loud beep unaffected 
                                 by volume control, or whether Mute is on  
                                 or off.  
                 ALSA - testing window, loud beep unaffected 
                        by volume control, or whether Mute is on  
                        or off.  

The volume control has no effect on the test beep, no matter which device is selected.

Any more tips would be greatly appreciated--thanks.

---

### Post by Yellow Pasque on 2008-05-20
The envy24 drivers are much better with OSS4
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

---

### Post by bobb0 on 2008-09-21
is this the accepted answer then?

i agree, the OSS driver is way nicer and easier to use for the m2496.

i was hoping to get it working with pulseaudio, but i've spent an entire day on this and i've gotten practically nowhere.  

i find it amusing that dpkg-reconfigure linux-audio-base didn't seem to help me in any way either.

---

### Post by Yellow Pasque on 2008-09-22
bobb0, I assume you built the latest OSS 4.1rc with mercurial and configured PulseAudio like so [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#Pulseaudio](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#Pulseaudio) ?

---

