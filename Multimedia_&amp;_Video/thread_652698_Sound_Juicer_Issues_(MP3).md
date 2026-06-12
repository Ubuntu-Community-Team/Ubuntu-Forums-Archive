---
title: "Sound Juicer Issues (MP3)"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Belak on 2007-12-29
I've been trying to get lame encoding working in Sound Juicer for about a day now and it's starting to drive me crazy.

I've finally figured out that with the VBR files I want to rip (highest quality settings possible) I need a few packages, but I can't find them.

I want to add
```
! xingmux ! id3v2mux
``` to the pipeline but every time I do and I restart Juicer, the MP3 profile doesn't work any more.

I'm assuming that I need another package, because without that the pipeline kind of works.

Thanks for Your Help,
Belak

---

### Post by benson444 on 2007-12-29
I'd never heard of xingmux so I did a bit of searching and came across this:

[http://www.xhtml.net/breves/343-CD-Ripping-to-mp3-with-Ubuntu-Feisty](http://www.xhtml.net/breves/343-CD-Ripping-to-mp3-with-Ubuntu-Feisty)

Maybe installing the gstreamer0.10-plugins-bad, ugly and ugly-multiverse packages will get it working?

---

### Post by Belak on 2007-12-29
Nope.
It didn't work.

It has to be either the xingmux or the id3v2mux that's causing the problem because the profile will be displayed if I leave them out.
For what ever reason, when I add them to the pipeline and restart sound juicer, the profile isn't enabled even though I have it checked.

Thanks for the idea though.

---

### Post by Major_Kong on 2007-12-29
Do you have the good, the bad & the ugly packages installed ? 

Did you change the pipeline using gconf-editor ?


PS: You might encounter a vbr header bug later on. Just a heads up.

---

### Post by Belak on 2007-12-29
I have 
gstreamer-0.10-plugins-good
gstreamer-0.10-plugins-bad
gstreamer-0.10-plugins-ugly-multiverse

No, I didn't use the gconf... I changed it through sound juicer and it would display as long as I didn't have either xingmux or id3v2mux in it

Here's the pipeline I think I want: 
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! xingmux ! id3v2mux

Thanks,
Belak

---

### Post by benson444 on 2007-12-29
Have you installed id3v2?

---

### Post by Belak on 2007-12-29
Yeah.
It's installed.

Oh, yeah.
I tried 2 separate profiles with:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=0 ! xingmux
and
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=0 ! id3v2mux

Neither of those show up...

but when I do just
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=0

it shows up...

Any Idea why?

---

### Post by benson444 on 2007-12-29
Not really. Sorry.

Have you managed to rip any mp3s? Is this just with VBR? Can you play mp3s?

I've just tried those 2 and mp3 still shows up for me.

---

### Post by Belak on 2007-12-29
Yes, I can play mp3s...

I have a few different ripping issues, though...

There are a few pipeline switches that make the profiles non-selectable... a few of which are the VBR switches that I want to use...

I may just start ripping them in 320 bitrate, though that seems like overkill for a high quality CD backup.

Are there any other formats that would encode with that high a quality, without a massive size increase?

EDIT:
Why wouldn't this pipeline work, for example:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc -V 0 -b 256

---

### Post by Belak on 2007-12-29
Ok, I found this by running "gst-inspect-0.10 lame" in a terminal.
I guess there are different commands if you're running it from the command line than if you're running it in a pipeline.


```

Factory Details:
  Long name:    L.A.M.E. mp3 encoder
  Class:        Codec/Encoder/Audio
  Description:  High-quality free MP3 encoder
  Author(s):    Erik Walthinsen <omega@cse.ogi.edu>, Wim Taymans <wim@fluendo.com>
  Rank:         none (0)

Plugin Details:
  Name:                 lame
  Description:          Encode MP3s with LAME
  Filename:             /usr/lib/gstreamer-0.10/libgstlame.so
  Version:              0.10.6
  License:              LGPL
  Source module:        gst-plugins-ugly
  Binary package:       GStreamer Ugly Multiverse Plugins (Ubuntu)
  Origin URL:           https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly-multiverse0.10

GObject
 +----GstObject
       +----GstElement
             +----GstLame

Implemented Interfaces:
  GstTagSetter

Pad Templates:
  SRC template: 'src'
    Availability: Always
    Capabilities:
      audio/mpeg
            mpegversion: 1
                  layer: 3
                   rate: { 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000 }
               channels: [ 1, 2 ]

  SINK template: 'sink'
    Availability: Always
    Capabilities:
      audio/x-raw-int
             endianness: 1234
                 signed: true
                  width: 16
                  depth: 16
                   rate: { 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000 }
               channels: [ 1, 2 ]


Element Flags:
  no flags set

Element Implementation:
  Has change_state() function: gst_lame_change_state
  Has custom save_thyself() function: gst_element_save_thyself
  Has custom restore_thyself() function: gst_element_restore_thyself

Element has no clocking capabilities.
Element has no indexing capabilities.

Pads:
  SRC: 'src'
    Implementation:
    Pad Template: 'src'
  SINK: 'sink'
    Implementation:
      Has chainfunc(): gst_lame_chain
      Has custom eventfunc(): gst_lame_sink_event
    Pad Template: 'sink'

Element Properties:
  name                : The name of the object
                        flags: readable, writable
                        String. Default: null Current: "lame0"
  bitrate             : Bitrate in kbit/sec (8, 16, 24, 32, 40, 48, 56, 64, 80, 96, 112, 128, 160, 192, 224, 256 or 320)
                        flags: readable, writable
                        Integer. Range: 8 - 320 Default: 128 Current: 128
  compression-ratio   : let lame choose bitrate to achieve selected compression ratio
                        flags: readable, writable
                        Float. Range:               0 -             200 Default:               0 Current:               0
  quality             : Quality of algorithm used for encoding
                        flags: readable, writable
                        Enum "GstLameQuality" Current: 5, "5"
                           (0): 0                - 0 - Best
                           (1): 1                - 1
                           (2): 2                - 2
                           (3): 3                - 3
                           (4): 4                - 4
                           (5): 5                - 5 - Default
                           (6): 6                - 6
                           (7): 7                - 7
                           (8): 8                - 8
                           (9): 9                - 9 - Worst
  mode                : Encoding mode
                        flags: readable, writable
                        Enum "GstLameMode" Current: 1, "joint"
                           (0): stereo           - Stereo
                           (1): joint            - Joint Stereo
                           (2): dual             - Dual Channel
                           (3): mono             - Mono
                           (4): auto             - Auto
  force-ms            : Force ms_stereo on all frames
                        flags: readable, writable
                        Boolean. Default: true Current: false
  free-format         : Produce a free format bitstream
                        flags: readable, writable
                        Boolean. Default: true Current: false
  copyright           : Mark as copyright
                        flags: readable, writable
                        Boolean. Default: true Current: false
  original            : Mark as non-original
                        flags: readable, writable
                        Boolean. Default: true Current: true
  error-protection    : Adds 16 bit checksum to every frame
                        flags: readable, writable
                        Boolean. Default: true Current: false
  padding-type        : Padding type
                        flags: readable, writable
                        Enum "GstLamePadding" Current: 2, "adjust"
                           (0): never            - No Padding
                           (1): always           - Always Pad
                           (2): adjust           - Adjust Padding
  extension           : Extension
                        flags: readable, writable
                        Boolean. Default: true Current: false
  strict-iso          : Comply as much as possible to ISO MPEG spec
                        flags: readable, writable
                        Boolean. Default: true Current: false
  disable-reservoir   : Disable the bit reservoir
                        flags: readable, writable
                        Boolean. Default: true Current: false
  vbr                 : Specify bitrate mode
                        flags: readable, writable
                        Enum "GstLameVbrmode" Current: 0, "none"
                           (0): none             - No VBR (Constant Bitrate)
                           (2): old              - Lame's old VBR algorithm
                           (3): abr              - VBR Average Bitrate
                           (4): new              - Lame's new VBR algorithm
  vbr-mean-bitrate    : Specify mean VBR bitrate
                        flags: readable, writable
                        Integer. Range: 8 - 320 Default: 128 Current: 128
  vbr-min-bitrate     : Specify minimum VBR bitrate (8, 16, 24, 32, 40, 48, 56, 64, 80, 96, 112, 128, 160, 192, 224, 256 or 320)
                        flags: readable, writable
                        Integer. Range: 8 - 320 Default: 112 Current: 112
  vbr-max-bitrate     : Specify maximum VBR bitrate (8, 16, 24, 32, 40, 48, 56, 64, 80, 96, 112, 128, 160, 192, 224, 256 or 320)
                        flags: readable, writable
                        Integer. Range: 8 - 320 Default: 160 Current: 160
  vbr-hard-min        : Specify whether min VBR bitrate is a hard limit. Normally, it can be violated for silence
                        flags: readable, writable
                        Integer. Range: 0 - 1 Default: 0 Current: 0
  lowpass-freq        : frequency(kHz), lowpass filter cutoff above freq
                        flags: readable, writable
                        Integer. Range: 0 - 50000 Default: 0 Current: 0
  lowpass-width       : frequency(kHz) - default 15% of lowpass freq
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  highpass-freq       : frequency(kHz), highpass filter cutoff below freq
                        flags: readable, writable
                        Integer. Range: 0 - 50000 Default: 0 Current: 0
  highpass-width      : frequency(kHz) - default 15% of highpass freq
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  ath-only            : Ignore GPSYCHO completely, use ATH only
                        flags: readable, writable
                        Boolean. Default: true Current: false
  ath-short           : Ignore GPSYCHO for short blocks, use ATH only
                        flags: readable, writable
                        Boolean. Default: true Current: false
  no-ath              : turns ATH down to a flat noise floor
                        flags: readable, writable
                        Boolean. Default: true Current: false
  ath-lower           : lowers ATH by x dB
                        flags: readable, writable
                        Integer. Range: -2147483648 - 2147483647 Default: 0 Current: 3
  cwlimit             : Compute tonality up to freq (in kHz) default 8.8717
                        flags: readable, writable
                        Integer. Range: 0 - 50000 Default: 0 Current: 8
  allow-diff-short    : Allow diff short
                        flags: readable, writable
                        Boolean. Default: true Current: false
  no-short-blocks     : Do not use short blocks
                        flags: readable, writable
                        Boolean. Default: true Current: true
  emphasis            : Emphasis
                        flags: readable, writable
                        Boolean. Default: true Current: false
  vbr-quality         : VBR Quality
                        flags: readable, writable
                        Enum "GstLameQuality" Current: 5, "5"
                           (0): 0                - 0 - Best
                           (1): 1                - 1
                           (2): 2                - 2
                           (3): 3                - 3
                           (4): 4                - 4
                           (5): 5                - 5 - Default
                           (6): 6                - 6
                           (7): 7                - 7
                           (8): 8                - 8
                           (9): 9                - 9 - Worst
  xingheader          : Output Xing Header (BROKEN, use xingmux instead)
                        flags: readable, writable
                        Boolean. Default: false Current: false
  preset              : Lame Preset
                        flags: readable, writable
                        Enum "GstLamePreset" Current: 0, "none"
                           (0): none             - None
                           (1006): medium           - Medium
                           (1001): standard         - Standard
                           (1002): extreme          - Extreme
                           (1003): insane           - Insane
```



So, what I wanted should have been,

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=256

I stumbled upon this by accident, so I think I got lucky

---

### Post by Major_Kong on 2007-12-30
Try using gconf-editor to change the pipeline.

---

### Post by Belak on 2007-12-30
It's been mostly fixed... the audio will rip correctly now. I just can't get the songs to display the right length... at least in Rhythmbox.
mp3info displays the right info, though...

---

### Post by Major_Kong on 2008-01-01
> **Belak said:**
> It's been mostly fixed... the audio will rip correctly now. I just can't get the songs to display the right length... at least in Rhythmbox.
mp3info displays the right info, though...

You have to add xingmux to the pipeline. It rights the proper headers to the file.

---

### Post by emarco on 2008-01-02
Dear Linux experts: I am running Ubunto 7.10. I intend to use Sound-juicer to extrac my cd's in mp3 format. Altough I already have an mp3 sound profile included in soud-juicer, it does not shows up in the ouput format box. In fact, only 4 formats are available in the output format box, altough I have 6 sound profiles active. Can anybody help me to solve this issue?

---

### Post by Belak on 2008-01-02
I think I can help with this.

You have to install LAME from the package manager. I think that's liblame0, or something like that... maybe just search for liblame

Then add the gstreamer-0.10-plugins-ugly-multiverse package. I'd just search for gstreamer and make sure you had the main package, and most of the plugins, good, bad, and ugly.

After that, restart sound juicer and it should work.
If not, I forgot something...

Just a note: The MP3 pipeline uses a different format than just using lame in the terminal... you can get the information on how it works by running ```
gst-inspect lame
```
in a terminal

I just looked it up...
Here are the packages you need (some are in multiverse and possibly restricted repositories, so make sure those are enabled):
libgstreamer0.10-0
gstreamer0.10-tools
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-base
lame

Good Luck!
-Belak

---

### Post by Lobinho on 2008-01-29
Hello!

I'm having some problems ripping to mp3 with Sound Juicer and LAME.  The output format I created is not selectable in Sound Juicer but the profile is there and active.  Major_Kong mentioned changing the pipeline, but what is that and how would I go about doing that?

When running 'gst-inspect lame', I see that the values I want for VBR quality, etc, are not set the way I want them, but I don't really know what I'm looking at.  I'm a bit of a noob and appreciate any and all help.

Thanks!

---

### Post by Lobinho on 2008-01-29
Ok, using

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 ! id3v2mux

I think I'm getting the quality I want, but it reads 32kbps and 30:42 length, even though the song is only about 5 minutes.  So, I guess the id3v2mux is the culprit?  Why is the mp3 tagged incorrectly?

Thanks.

---

### Post by golovan on 2008-01-29
> **Lobinho said:**
> Hello!

I'm having some problems ripping to mp3 with Sound Juicer and LAME.  The output format I created is not selectable in Sound Juicer but the profile is there and active.  Major_Kong mentioned changing the pipeline, but what is that and how would I go about doing that?

When running 'gst-inspect lame', I see that the values I want for VBR quality, etc, are not set the way I want them, but I don't really know what I'm looking at.  I'm a bit of a noob and appreciate any and all help.

Thanks!

I had the same problem, but after I went to Add/Remove programs , searched for gstreamer in all available applications, and installed Ubuntu restricted extras plus all of the gstreamer packages, it suddenly appeared in the soundjuicer drop down:)

I used this guide [http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html) to get a good bitrate (320) havent tested with VBR yet.

---

### Post by Lobinho on 2008-02-01
Hmm, it seems I have all of those libraries, but I still can't see my profile in the drop-down menu - only when I hit 'edit profiles'.  Maybe I can't have more than one mp3 profile selectable at a time?  I deactivated the default 'CD Quality, MP3' but my mp3 still didn't show up.  Any thoughts?

Thanks.

---

### Post by Belak on 2008-02-18
> **Lobinho said:**
> Hmm, it seems I have all of those libraries, but I still can't see my profile in the drop-down menu - only when I hit 'edit profiles'.  Maybe I can't have more than one mp3 profile selectable at a time?  I deactivated the default 'CD Quality, MP3' but my mp3 still didn't show up.  Any thoughts?

Thanks.

What's the pipeline you're using?

---

### Post by Mike Dillon on 2008-02-20
Hello to the group - 

I am having the same problem as Belak, tried his solution, and it still doesn't work.

I paste in the pipeline, activate the profile, restart Juicer, and then I am not offered the selection of the mp3 profile.

Yes, I have installed LAME,

Am I missing something?

Thanks In Advance - MJD

---

### Post by Mike Dillon on 2008-02-20
Never mind, I found the solution at:

[http://ubuntuforums.org/showthread.php?t=581306&highlight=rip+mp3](http://ubuntuforums.org/showthread.php?t=581306&highlight=rip+mp3)

---

