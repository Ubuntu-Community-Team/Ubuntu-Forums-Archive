---
title: "terrible distortion/crackle when using flash through OSS"
date: 2010-03-04
forum: Multimedia Software
---

### Post by mikethehard on 2010-03-04
hey there,

i'm using a m-audio delta 44 card and if i play anything through vlc it sounds great. however my problem is using flash, any sound through flash sounds terrible. all distorted, glitchy and crackly and with lots of white noise mixed in for good measure.

i feel like i'm going round in circles now and i'm at the limits of my knowledge. i've tried all the packages i can think of for flash, reinstalling oss numerous times and a different browser but no luck

i'd be really grateful for any suggestions. i've been tearing my hair out all day..




    Selected mixer 0/M Audio Delta 44
    Known controls are:
    mon.out1/2 [<leftvol>:<rightvol>] (currently 108.0:108.0 dB)
    mon.out3/4 [<leftvol>:<rightvol>] (currently 114.0:114.0 dB)
    mon.in1/2 [<leftvol>:<rightvol>] (currently 122.0:122.0 dB)
    mon.in3/4 [<leftvol>:<rightvol>] (currently 122.0:122.0 dB)
    route.out1/2 <DMA|MONITOR|IN1/2|IN3/4> (currently MONITOR)
    route.out3/4 <DMA|IN1/2|IN3/4> (currently DMA)
    gain.out1/2 <+4DB|CONSUMER|-10DB> (currently CONSUMER)
    gain.out3/4 <+4DB|CONSUMER|-10DB> (currently CONSUMER)
    gain.in1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
    gain.in3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
    envy24.rate <8000|9600|11025|12000|16000|22050|24000|32000|44100|48000|88200|96000> (currently 48000)
    envy24.ratelock ON|OFF (currently ON)
    envy24.actrate <decimal value> (currently 48000) (Read-only)



    Version info: OSS 4.2 (b 2002/200911060735) (0x00040100) TRIAL
    Platform: Linux/i686 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (michael-desktop)

    Number of audio devices:   7
    Number of audio engines:   7
    Number of MIDI devices:      0
    Number of mixer devices:   1


    Device objects
    0: osscore0 OSS core services
    1: oss_envy240 M Audio Delta 44 interrupts=1223725 (1223725)
    2: oss_usb0 USB audio core services

    MIDI devices (/dev/midi*)

    Mixer devices
    0: M Audio Delta 44 (Mixer 0 of device object 1)
        Device file /dev/oss/oss_envy240/mix0, Legacy device /dev/mixer0
        Priority: 0
        Caps:
        Device handle: PCId6331412-0000:02:09.0-mx01
        Device priority: 0


    Audio devices
    M Audio Delta 44 out1/2           /dev/oss/oss_envy240/pcm0  (device index 0)
        Legacy device /dev/dsp0
        Caps: TRIGGER
        Modes: OUTPUT
          Out engine  1: 0/M Audio Delta 44 out1/2
                         Busy (OUT) by PID 5450 / firefox label 'firefox'
        Input formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Output formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au01
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: STEREO
        Supported number of channels (min - max): 1 - 10
        Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
        HW Type: Not indicated.
        Minimum latency: Not indicated

    M Audio Delta 44 out3/4           /dev/oss/oss_envy240/pcm1  (device index 1)
        Legacy device /dev/dsp1
        Caps: TRIGGER
        Modes: OUTPUT
          Out engine  1: 1/M Audio Delta 44 out3/4
                         Available for use
        Input formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Output formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au02
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: STEREO
        Supported number of channels (min - max): 1 - 8
        Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
        HW Type: Not indicated.
        Minimum latency: Not indicated

    M Audio Delta 44 in1/2            /dev/oss/oss_envy240/pcmin0  (device index 2)
        Legacy device /dev/dsp2
        Caps: TRIGGER
        Modes: INPUT 
          In engine   1: 2/M Audio Delta 44 in1/2
                         Available for use
        Input formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Output formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au03
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: STEREO
        Supported number of channels (min - max): 1 - 12
        Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
        HW Type: Not indicated.
        Minimum latency: Not indicated

    M Audio Delta 44 in3/4            /dev/oss/oss_envy240/pcmin1  (device index 3)
        Legacy device /dev/dsp3
        Caps: TRIGGER
        Modes: INPUT 
          In engine   1: 3/M Audio Delta 44 in3/4
                         Available for use
        Input formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Output formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au04
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: STEREO
        Supported number of channels (min - max): 1 - 10
        Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
        HW Type: Not indicated.
        Minimum latency: Not indicated

    M Audio Delta 44 input from mon. mixer   /dev/oss/oss_envy240/mon  (device index 4)
        Legacy device /dev/dsp4
        Caps: TRIGGER
        Modes: INPUT 
          In engine   1: 4/M Audio Delta 44 input from mon. mixer
                         Available for use
        Input formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Output formats (0x00009010):
          AFMT_S16_LE   - 16 bit signed little endian
          AFMT_S32_LE   - 32 bit signed little endian
          AFMT_S24_LE   - 24/32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au05
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: STEREO
        Supported number of channels (min - max): 1 - 2
        Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
        HW Type: Not indicated.
        Minimum latency: Not indicated

    M Audio Delta 44 (all outputs)    /dev/oss/oss_envy240/10ch_out  (device index 5)
        Legacy device /dev/dsp5
        Caps: TRIGGER MMAP
        Modes: OUTPUT
          Out engine  1: 5/M Audio Delta 44 (all outputs)
                         Available for use
        Input formats (0x00001000):
          AFMT_S32_LE   - 32 bit signed little endian
        Output formats (0x00001000):
          AFMT_S32_LE   - 32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au06
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: MULTICH
        Supported number of channels (min - max): 10 - 10
        Native sample rates (min - max): 8000 - 96000
        HW Type: Not indicated.
        Minimum latency: Not indicated

    M Audio Delta 44 (all inputs)     /dev/oss/oss_envy240/12ch_in  (device index 6)
        Legacy device /dev/dsp6
        Caps: TRIGGER MMAP
        Modes: INPUT 
          In engine   1: 6/M Audio Delta 44 (all inputs)
                         Available for use
        Input formats (0x00001000):
          AFMT_S32_LE   - 32 bit signed little endian
        Output formats (0x00001000):
          AFMT_S32_LE   - 32 bit signed little endian
        Device handle: PCId6331412-0000:02:09.0-au07
        Related mixer dev: 0
        Sample rate source: 0
        Preferred channel configuration: MULTICH
        Supported number of channels (min - max): 12 - 12
        Native sample rates (min - max): 8000 - 96000
        HW Type: Not indicated.
        Minimum latency: Not indicated


    Nodes
      /dev/dsp -> /dev/oss/oss_envy240/pcm0
      /dev/dsp_in -> /dev/oss/oss_envy240/pcmin0
      /dev/dsp_out -> /dev/oss/oss_envy240/pcm0
      /dev/dsp_multich -> /dev/oss/oss_envy240/pcm0

---

### Post by mikethehard on 2010-03-06
Solution courtesy of Cesium form the OSS forum.

> Try adding the following command the /usr/lib/oss/soundon.user file (before the "exit 0" line):

```

    vmixctl attach /dev/oss/oss_envy240/pcm0 /dev/oss/oss_envy240/pcmin0
``` 

Then do "chmod +x" to that file, and run it with "sudo /usr/lib/oss/soundon.user" (make sure nothing else is playing at the time). This will add software mixing to default sound output, which may help here. Note that OSS will run that file automatically when it's started if the exec bit is set, so you won't have to run it again every time.

---

### Post by rolandrock on 2010-04-25
I have Audiophile 2496 with same problem and can confirm this fixes it.

Thank you very much for sharing solution Mike.  This has been a thorn in my side for some time.

---

