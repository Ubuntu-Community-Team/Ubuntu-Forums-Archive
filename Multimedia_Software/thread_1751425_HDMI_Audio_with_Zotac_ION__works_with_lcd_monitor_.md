---
title: "HDMI Audio with Zotac ION  works with lcd monitor but not TV"
date: 2011-05-06
forum: Multimedia Software
---

### Post by mark.kendall on 2011-05-06
I've got at Zotac ION (ION-A or similar with MCP79/7A) and have a problem getting HDMI audio working through my TV.  It briefly worked a few years ago (Ubuntu 8 something I think) and now after upgrading to Natty I've gone through a bit of an effort to try and get it going again.

I've spent a LOT of time altering configuration files, un-muting devices, attempting different modprobe options seen in forums etc. To check if the TV might have developed a problem I recently plugged in a LCD monitor which has a stereo speaker out and attached speakers to it and without even rebooting the sound worked (using a aplay command like aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Left.wav)

I also borrowed a Windows7 laptop and plugged this into my TV and the sound worked so it seems it just the combination of my computer and TV that's causing the problem.

I have just recently seen the following posts and am wondering whether I may be suffering from the same problem which has not been fixed?

[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)


Here's some output that may be of interest
```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
ls /proc/asound/card0
codec#0  codec#3  id  pcm0c  pcm0p  pcm1p  pcm3p
```
I note that there are no eld* files here, should there be some?

```
uname -a
Linux lounge 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

/etc/asound.conf is currently empty.

extract from /etc/X11/xorg.conf
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "KTV LTW32DV6"
    HorizSync       31.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"

# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: 1360x768 +0+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "1360x768_60_0 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Does anyone have any advice on what I can try next to get the computer and TV to work together?

---

### Post by 10robinho on 2011-05-06
I had similar problem with my Zacate, and I solved it by forcing my drivers to use 1366x768 resolution. Somehow, 1360x768 didn't want to display at all.

Look at this tread:
[http://ubuntuforums.org/showthread.php?p=10774105#post10774105](http://ubuntuforums.org/showthread.php?p=10774105#post10774105)

I hope it helps!

---

### Post by BicyclerBoy on 2011-05-07
Did you see this post/thread..

[http://ubuntuforums.org/showpost.php?p=9732345&postcount=8](http://ubuntuforums.org/showpost.php?p=9732345&postcount=8)

I would think no ELD data is fatal..don't know what alsa does in that situation..

The nvidia hdmi audio document linked in the thread you have listed is the best info AFAIK.

Haven't found this brick wall yet !

---

### Post by mark.kendall on 2011-05-07
I was already using 1360x768 resolution and if I try forcing 1366x768 it switches to a much lower resolution.

---

### Post by mark.kendall on 2011-05-07
> **BicyclerBoy said:**
> Did you see this post/thread..

[http://ubuntuforums.org/showpost.php?p=9732345&postcount=8](http://ubuntuforums.org/showpost.php?p=9732345&postcount=8)

I would think no ELD data is fatal..don't know what alsa does in that situation..

The nvidia hdmi audio document linked in the thread you have listed is the best info AFAIK.

Haven't found this brick wall yet !

I had seen that thread but had missed the link to the nvidia hdmi audio document, which has unfortunately not solved the problem.  It has told me that when working with earlier IONs (as opposed to ION2s) ELD files are not created.

---

### Post by BicyclerBoy on 2011-05-07
My guess is the nvidia forums is the place to look for solution..

Are you the mark of LATM-AAC patches fame ?

---

### Post by mark.kendall on 2011-05-10
I've posted in the NVidia forum a few days ago but hadn't had any replies yet.

I'm not the same Mark Kendall as VDPAU, LATM etc

---

### Post by BicyclerBoy on 2011-05-10
As I understand it..
the ELD files are created by alsa/snd_hda_codec_nvhdmi module from EDID-like data from the video driver but they are not mandatory for operation.

[http://forum.xbmc.org/showthread.php?t=95599&page=2](http://forum.xbmc.org/showthread.php?t=95599&page=2)

Original post of nvidia info/doc.
[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)


I would try the latest alsa code base..& try the asound.conf in the XBMC post..

---

### Post by mark.kendall on 2011-05-12
> **BicyclerBoy said:**
> As I understand it..
the ELD files are created by alsa/snd_hda_codec_nvhdmi module from EDID-like data from the video driver but they are not mandatory for operation.

Yes, my understanding is that with the MCP79 hdmi audio is simply enabled for hdmi audio but this doesn't appear to be the case when it works on one screen but not another that is capable.

> 
[http://forum.xbmc.org/showthread.php?t=95599&page=2](http://forum.xbmc.org/showthread.php?t=95599&page=2)

I have seen a lot of related posts but believe that I need to get the audio working first with aplay or speaker-test before worrying about the asound.conf configuration.

> 
Original post of nvidia info/doc.
[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)


I would try the latest alsa code base..& try the asound.conf in the XBMC post..

Seen that post as well and will look at the latest alsa but I've been looking at "latest" nvidia and alsa for the past few years with varying degrees of successes and failures.

---

### Post by mark.kendall on 2011-05-16
Looks to me like Natty's 1.0.24 is the latest ALSA :(

---

### Post by mark.kendall on 2011-06-23
Someone with the same problem has solved this problem by reverting there bios version.  I've contacted Zotac and received older copies of bios's from them,  so far I've only had a chance to install the first one.  This fixed what I'm guessing is an over/underscanning problem with my DSUB vga output that caused a good portion of the left and right of the screen to be not visible but didn't change the hdmi audio.  I will report back again after trying other versions.

---

### Post by BicyclerBoy on 2011-06-23
Are you using a snd-hda-intel module option probe_mask ?
(/etc/modprobe.d/*.conf)

The earlier advice about the probe mask values was wrong.

If you are using mask
I would remove the effect of probe _mask by setting it to =-1
[sudo] update-initramfs -u

then post 
aplay -l

---

### Post by mark.kendall on 2011-06-23
I did try adding a probe_mask a couple of months ago and then after more research discovered that it didn't look like it applied to these series of boards (ionitx-a-... range).

aplay -l is the same as first reported.

---

### Post by BicyclerBoy on 2011-06-24
I agree. I think the probe mask just causes unnecessary confusion by changing the relationship between logical & physical codec#.

You've probably read this til your eyes are red...
Quote

"ELD and PD information is not available on these chipsets.

 In these chipsets, the multiple 2-channel converters are aggregated by the ALSA driver and exposed as a single 8-channel device. Some chipsets support 2, or 8 channels (MCP77). Other chipsets support 2, 6, or 8 channels (MCP79)."


What does this report ?
cat  /proc/asound/card0/codec#3
(what to do with this info is another question)

speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 2 -r 44100 -D hw:0,3
speaker-test -c 2 -r 48000 -F S32_LE -D hw0:3

Did you find suggestions this from opensuse forum ?
options snd-hda-intel bdl_pos_adj=64
linked to from
[https://bbs.archlinux.org/viewtopic.php?id=101103](https://bbs.archlinux.org/viewtopic.php?id=101103)

Do you have any errors in the kernel logs related to snd-hda-intel or snd-hda-codec-nvhdmi to suggest the above would have any benefit ?

Give this a spin..see what damage can be done..
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

---

### Post by mark.kendall on 2011-06-27
I had a chance on the weekend to try 4 different bioses.  None made a change to the hdmi audio output.

I also plugged in the LCD screen that I tried a little while ago and the HDMI audio worked straight away - I didn't think to look at the Xorg logs to see if they showed anything, from what's in the log directory at the moment I can't see any references to the replacement monitor but I wonder if that's because I didn't reboot/restart xorg. 

I have ended up reading lots of posts and nvidia FAQs etc on ELD information :-(

The speaker tests produced no sound (the last one needed the device correcting).
They all output something along the lines of
```

:~# speaker-test -c 2 -r 48000 -D hw:0,3

speaker-test 1.0.24.2

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 10.971214
 0 - Front Left
 1 - Front Right
^C

```

I've not seen any errors in the logs relating to snd so hadn't come across anything regarding bdl_pos_adj

Here's the output for codec#3
```

Codec: Nvidia MCP79/7A HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0007
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c

```

---

### Post by BicyclerBoy on 2011-06-27
What changes in the codec#3 between having the working LCD & non-working ?

Almost pointless to try because I have no idea what to do with the info.

Notice how the pin complexes & audio outputs are paired..0x04 & 0x05
I know should not really compare across the h/w types but..
My node 0x05 pin complex is enabled..& my HDMI audio is supported.

---

### Post by mark.kendall on 2011-07-02
I've just swapped the screens again and did a diff on the codec#3 information and there is no difference with either of the screens plugged in (including with a reboot)

I did a diff of the xorg logs as well and nothing stood out to me with these either.

---

### Post by mark.kendall on 2011-07-02
After noticing something in one of the log files about a missing pulse audio module.  I installed pulseaudio-module-x11 and after doing this I have HDMI sound through pulse audio but not directly through alsa (aplay -D ....)

---

### Post by BicyclerBoy on 2011-07-02
Do you get HDMI audio from media player or just the system sounds ?

Does that mean that you need a hardware device with software conversion ?
i.e. plughw: instead of hw:
& that speaker-test was trying to send data in an unsupported format/rate/channels

---

### Post by mark.kendall on 2011-07-03
I'm getting audio with both system sounds and media player (mythtv with audio set to Pulseaudio:default)

plughw is what I've predominantly tested with, I'll try a few more tests in the next few days - I'm limited with making changes/spending time/breaking it due to both little baby and WAF :-o

---

### Post by BicyclerBoy on 2011-07-15
Did you come across this in MythTV & XBMC forums..I think it relates to any ION box.
Looks to force rate resampling etc.

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][COLOR=#660066]### .asoundrc for Acer Revo 
[/COLOR] 
pcm.dmixer { 
   type dmix 
   ipc_key 1024 
   ipc_key_add_uid false 
   ipc_perm 0660 
   slave { 
      pcm "hw:0,3" 
      rate 48000 
      channels 2 
      format S32_LE 
      period_time 0 
      period_size 1024 
      buffer_time 0 
      buffer_size 4096 
   } 
} 
 
pcm.!default { 
   type plug 
   slave.pcm "dmixer" 
} [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by mark.kendall on 2011-07-15
Until a few minutes ago I hadn't had a chance to try any more tests.
I had seen settings similar to (if not the same) as those just posted.

I just worked out how to stop pulse respawning and get the pulse audio log (thanks to [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log))
```

echo autospawn = no >> ~/.pulse/client.conf
killall pulseaudio
LANG=C pulseaudio -vvvv > ~/pulseverbose.log 2>&1

```

After searching through the log for a while I discovered that Pulse Audio  appears to be using front:0 for audio, and hey presto hdmi audio works through ALSA if I use front:0 (instead of the expected hdmi:0 hw:0,3 or plughw:0,3)

---

