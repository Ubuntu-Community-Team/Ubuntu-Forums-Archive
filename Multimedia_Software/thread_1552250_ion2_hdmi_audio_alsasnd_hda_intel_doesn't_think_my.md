---
title: "ion2 hdmi audio alsa/snd_hda_intel doesn't think my tv is connected"
date: 2010-08-13
forum: Multimedia Software
---

### Post by tjones00 on 2010-08-13
[SIZE=3][B]****SEE THIS FIRST (unfortunately this information wasn't posted until after this thread was created) [http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

[SIZE=2]** See post #8 in this thread to enable HDMI audio with an Ion2 in Ubuntu 10.04.  (upgrade alsa to 1.0.23 via ubuntu backport) ubuntu wiki link [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

** See post #21 for an alternate solution by upgrading the kernel to 2.6.35 via ubuntu kernel backport. (do this if the alsa 1.0.23 backport doesn't work)

**Follow this thread (thanks to zAPPzAPP) for the final touches about setting up the dmix/hw and default sound [/SIZE]  [U][SIZE=2][http://ubuntuforums.org/showthread.php?t=1620926](http://ubuntuforums.org/showthread.php?t=1620926)[/SIZE]
[/U][/B][/SIZE]

Hello,

I have a nvidia ion2 and I can't get audio over hdmi to work. I think I've narrowed it down to the snd_hda_intel module and it's hdmi management but I can't be sure so I'm posting here.

To cover the basics.

I understand alsa 1.0.23 or a 2.6.35 kernel is required for the updated driver. I've also discovered the probemask info but to simplify things I just disabled the onboard sound leaving only the ion2.

I'm currently trying to use a backported maverick 2.6.35-14 kernel from the ppa on a 10.04 base with nvidia 256.44 drivers.

```
xbmc@xbmc-HTPC:~$ uname -r; cat /proc/asound/version
2.6.35-14-generic-pae
Advanced Linux Sound Architecture Driver Version 1.0.23.

``````
xbmc@xbmc-HTPC:~$ aplay -l; aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

``````
xbmc@xbmc-HTPC:~$ lsmod
Module                  Size  Used by
snd_hda_codec_nvhdmi    12879  1 
nvidia              10195166  40 
snd_hda_intel          22203  0 
snd_hda_codec          87392  2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47206  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  1 lp
psmouse                58969  0 
intel_agp              25589  0 
joydev                  8735  0 
agpgart                32075  2 nvidia,intel_agp
serio_raw               4022  0 
usbhid                 37234  0 
hid                    67742  1 usbhid
e100                   30676  0 
ahci                   19013  0 
libahci                20107  4 ahci
mii                     4425  1 e100

```lspci and lspci -nv
```
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
``````
02:00.0 0300: 10de:0a75 (rev a2)
    Subsystem: 17aa:3605
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at feb00000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nouveau, nvidiafb

02:00.1 0403: 10de:0be3 (rev a1)
    Subsystem: 17aa:3605
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```The results from aplay.

```
xbmc@xbmc-HTPC:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
xbmc@xbmc-HTPC:~$ aplay -D hdmi:NVidia /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:996: Channels count non available
xbmc@xbmc-HTPC:~$ aplay -D hdmi:CARD=NVidia /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:996: Channels count non available
```However even with plughw:0,3 there is still no sound coming out of my tv. The nvidia card is unmuted in alsamixer.


```
xbmc@xbmc-HTPC:/proc/asound/card0$ ls
codec#1  eld#1.0  id  pcm3p
xbmc@xbmc-HTPC:/proc/asound/card0$ cat codec#1
Codec: Nvidia GT21x HDMI
Address: 1
Function Id: 0x1
Vendor Id: 0x10de000b
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
xbmc@xbmc-HTPC:/proc/asound/card0$ cat eld#1.0
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0

```I think that monitor_present 0 means that snd_hda_intel has failed to detect that the tv is connected? I've tried physically toggling the connection with no luck. I also grabbed an edid.bin generated from win 7 registry (where the hdmi sound works) and used it in the xorg.conf with CustomEDID just incase the nvidia driver in linux wasn't grabbing it properly.

It's my assumption the graphics driver grabs the edid from the display and shares it with alsa who generates the eld#1.0

Leading me back to /proc/asound/card0/eld#1.0

I tried alsa force-reload that just cleared all the snd_hda_intel options. eg. empties out /proc/asound/card0 leaving no eld at all.

I also tried modprobe -r snd_hda_intel and reloading it. It was the same effect as restarting alsa.

So I was wondering if anybody knows how to force the hdmi connection and the eld information to be set in alsa/snd_hda_intel. I can't seem to find any information on this.

---

### Post by lidex on 2010-08-14
Wow, way too complicated for me. 
You've disabled on board sound and are trying to get audio from the hdmi port of your nVidia Corporation GT218 [GeForce 310M] controller, correct? And you've referenced this page also?
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

How is it aplay -l only shows one device (for hdmi)? I would expect something more like post #4 here:
[http://ubuntuforums.org/showthread.php?t=1534597](http://ubuntuforums.org/showthread.php?t=1534597)

---

### Post by tjones00 on 2010-08-14
Yes ([http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240))

is where I discovered the probemask info.

However if you simply disable the onboard sound you don't need to setup a /etc/modprobe.d/sound.conf for the gt2xx to use the proper codec. I did this just so I could troubleshoot what was wrong without having to worry about another card mucking things up.

The realtek codec is the one that lists 4 pcms eg 1,3 1,7 1,8 1,9 is the typical result if you do not use the probemask.

Upon using a generic probemask with onboard enabled eg. enable_msi=0 probe_mask=0xffff,0xfff2 it switches to the gt21xx codec and only the single 1,3 pcm.

Interestingly in win7 it uses the realtek driver and lists 4 pcms.'

I found some info on the 4 pcm definitions however it seems I didn't bookmark it. But 3 should be hdmi output 7, 8, 9 are just the different formats eg pcm vs ac3 vs dts. With the gt2xx codec all formats should be enabled and routed through 0,3 in my case.

**edit a post by someone who defined the 4 pmc outputs.
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg26691.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg26691.html)

7=pcm
8=ac3
9=dts

he was using alsa 1.0.22 and a gt220 with gt2xx codec so who knows my lack of pcms could be due to my card being incompatible with the gt2xx codec and therefore alsa won't setup multiple pcms. 


I found another post regarding someone with a mucked up eld.

[http://www.nvnews.net/vbulletin/showthread.php?t=153075](http://www.nvnews.net/vbulletin/showthread.php?t=153075)

It appears there is no resolution besides patching snd_hda_intel. And it appears the module in 2.6.35-14 kernel from ppa:kernel-ppa/ppa linux-lts-backport-maverick is not patched.

So even if i were to try using the realtek codec the hdmi output sense is broken for my card at least in snd_hda_intel.

I've scrapped the system for now but some possible fixes would be to patch snd_hda_intel either in the kernel or alsa 1.0.23.

Another possible fix would be enabling hdmi as default with a kernel boot paramater eg. video="HDMI Type A-1:1920x1080 <at> 60D" for a 1080p setup. Perhaps it's a kms issue with snd_hda_intel setting up assuming a vga/dvi connection.

If anybody reading this really really really wants to use hdmi for their audio you can try a hacked edid.bin removing all the audio data and splice the analog audio with the vga/dvi video into an hdmi adapter. Try a google on nvidia edid.bin. This is an old hack for nvidia hdmi audio troubles.

Oh snap that just made me realize I could try enabling onboard sound, strip the edid.bin audio data create a pcm duping the analog output from the onboard and try routing it through the hdmi. That might work since the hdmi sink in snd_hda_intel turns on sound when hdmi is sensed but with analog it's always on. Well it might not be always on but you could always plug something in it or hack the jack sense. Would that work? Darn I already trashed the system.

#edit the above might only work if you use the realtek codec that has the 1,3 1,7 1,8 1,9 pcm setup using 1,3 as the route path.

Anyway I'm dropping this since I've spent 2 weeks on it so far trying to hack around it I'll just wait until the pros get this figured out.

---

### Post by tjones00 on 2010-08-15
Out of curiousity and the pcm info I installed a new 10.04 2.6.32-24-generic and upgraded alsa to 1.0.23 via the upgrade script. Nvidia drivers 195.36 installed via apt-get install nvidia-current

before any probemasking

```
xbmc@xbmc-HTPC:/proc/asound/card1$ aplay -l; aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
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
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```all 4 channels are unmuted in alsamixer

now here's the odd part yet again. the gt218 is card1

```
xbmc@xbmc-HTPC:/proc/asound/card1$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfcef8000 irq 26
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfebfc000 irq 16
xbmc@xbmc-HTPC:/proc/asound/card1$ ls
codec#0  codec#1  codec#2  codec#3  eld#0.0  eld#1.0  eld#2.0  eld#3.0  id  oss_mixer  pcm3p  pcm7p  pcm8p  pcm9p
xbmc@xbmc-HTPC:/proc/asound/card1$ cat codec#*
Codec: Nvidia GT21x HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x10de000b
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GT21x HDMI
Address: 1
Function Id: 0x1
Vendor Id: 0x10de000b
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GT21x HDMI
Address: 2
Function Id: 0x1
Vendor Id: 0x10de000b
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=8
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GT21x HDMI
Address: 3
Function Id: 0x1
Vendor Id: 0x10de000b
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=9
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
xbmc@xbmc-HTPC:/proc/asound/card1$ cat eld*
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
```Even with the 4 pcm channels none of them have any eld information. As in my original post plughw does not report errors but no audio comes out of the TV. Whereas hw or the pcm report channel errors etc.

If I were to probemask the results are the same as in my original post with only 1,3 being the only pcm listed.

Time to try the analog hack I guess.

---

### Post by lidex on 2010-08-15
This is just way too complicated. Should be a much easier fix. Have you seen this thread:
[http://ubuntuforums.org/showthread.php?t=1532355](http://ubuntuforums.org/showthread.php?t=1532355)

---

### Post by tjones00 on 2010-08-15
Thank you for your interest in my issue lidex. This has really been mystifying me. I try to walk away and I just can't.

I wish I had an atom 330 ion1 system now lol. 

aplay -D hdmi:CARD=NVidia,DEV=0 ./SURROUNDTEST_011212.wav didn't produce any errors but no physical sound either.

To prevent myself from posting another wall of text I'll just leave some links regarding ion2 that I've gathered.

My system is a lenovo q150 D510 ion2.

[http://ossnotebook.blogspot.com/2010/07/ubuntu-1001-maverick-on-lenovo-q150.html](http://ossnotebook.blogspot.com/2010/07/ubuntu-1001-maverick-on-lenovo-q150.html)

I've tried adjusting the rate with no luck in 10.04 with upgraded kernel or alsa 1.0.23.

ion2 on zotac
[http://www.spinics.net/linux/fedora/alsa-user/msg09096.html](http://www.spinics.net/linux/fedora/alsa-user/msg09096.html)
[http://forums.gentoo.org/viewtopic-t-827888.html](http://forums.gentoo.org/viewtopic-t-827888.html)
I believe Petter is the user pgu on the gentoo post he has other posts in the alsa-user mail list.

Both of these results suggest they don't have any eld as well.

According to other gtxx posts I've read the probemask 1,3 setup is "proper" for nvidia hdmi not 1,3 1,7 1,8 1,9.

About eld From Takashi 2.6.34 kernel notes. Line 174

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/Procfile.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/Procfile.txt)

I'm going to see if I can install a 10.10 minimal with no desktop to eliminate any pulseaudio settings.

---

### Post by tjones00 on 2010-08-17
Well I finally got it working. I'm not exactly sure how.

After no success with my last 10.10 install I dropped back to 10.04 and used the backported alsa modules from ubuntu because I was sick of compiling. This is using the 185 drivers installed via.

```
sudo apt-get install nvidia-185-kernel-source nvidia-185-modaliases nvidia-glx-185 nvidia-settings libvdpau1 -y
```


```
xbmc@xbmc-HTPC:/proc/asound/card1$ uname -r
2.6.32-24-generic
xbmc@xbmc-HTPC:/proc/asound/card1$ apt-cache search linux-backports-modules-alsa-2.6.32-24
linux-backports-modules-alsa-2.6.32-24-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-24-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
```I installed the 2.6.32 backport then started playing around with the probemask /etc/modprobe.d/sound.conf and the nomodset and noplymouth boot parameters. 

```
xbmc@xbmc-HTPC:/proc/asound/card1$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).
```Eventually without a probemask 1,9 picked up an eld when I had nomodeset noplymouth enabled.

```
xbmc@xbmc-HTPC:/proc/asound/card1$ cat eld*
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
monitor_present        1
eld_valid        1
monitor_name        SAMSUNG
    
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x2d4c
product_id        0x313
port_id            0x10000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x1] FL/FR
sad_count        1
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0xe0] 44100 48000 88200
sad0_bits        [0xe0000] 16 20 24
```The last output is from eld#3.0 so device 1,9.

plughw:1,9 now works perfectly with no noise distortion and I didn't have to specify any rates. I haven't tried pcm alias's or hw: yet but who cares at this point. It works.

I've now removed nomodeset and noplymouth and it still picks up the eld. If I put the probemask back on (changing from 4 devices to 1) 1,3 no eld is present.

I can't be exactly sure when it picked up the eld if it was the first nomodeset or noplymouth since I was trying different probemasks. The important point is it acquired and retained the information.

I will reinstall 10.04 today with 256.44 nvidia drivers and see if I can replicate this result pinpointing what the key issue was.

---

### Post by tjones00 on 2010-08-17
[SIZE=3]***Update read this first: [http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

***Ubuntu wiki instructions regarding how to upgrade alsa modules [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)[/SIZE] 


Got it working again on a fresh install.

hw:1,9 works without distortion in most cases however plughw seems to handle the mixing properly.

eld was acquired upon installing the base system, nvidia drivers 256.44, and the ubuntu backport alsa 1.0.23

It appears nomodeset and noplymouth had nothing to do with it.

The difference was installing alsa 1.0.23 via the upgrade script using the alsa-project ftp vs the ubuntu backport.

Interestingly the patch that was suppose to correct hdmi sense was not officially applied for the kernel drivers until the beginning of august whereas the ubuntu 10.04 backport is timestamped for july 6th. Perhaps the ubuntu guys were a bit quicker on the fix?

My failures with the ubuntu 2.6.35 kernel from the ppa is probably due to me using the probemask and not checking the eld#3.0 for device 1,9 without the probemask.

[B]
Enabling your hardware:[/B]

To wrap things up:

With an ion2 try installing the ubuntu alsa 1.0.23 backport.

Update: Ubuntu wiki page on this subject: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

```

xbmc@xbmc-HTPC:~$ uname -r
2.6.32-24-generic
xbmc@xbmc-HTPC:~$ apt-cache search linux-backports-modules-alsa-2.6.32-24
linux-backports-modules-alsa-2.6.32-24-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-24-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots
```in my case

```
sudo apt-get install linux-backports-modules-alsa-2.6.32-24-generic alsa-utils
```Reboot. (sudo reboot) 

Then check to see that you're using alsa 1.0.23 backport.
cat /proc/asound/version

```
xbmc@xbmc-HTPC:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).
```Discover all devices listed. aplay -l

```
xbmc@xbmc-HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
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
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```Next check to see if you  have any eld info on a device. My ion2 is card1 in this case.

```
cd /proc/asound/card1
cat eld#0.0
cat eld#1.0
cat eld#2.0
cat eld#3.0
``` eld#0.0 corresonds to device 1,3, #1.0 to device 1,7 #2.0 to device 1,8 and #3.0 to device 1,9

A positive result for eld data will look something like this:

```
monitor_present        1
eld_valid        1
monitor_name        SAMSUNG

connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x2d4c
product_id        0x313
port_id            0x10000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x1] FL/FR
sad_count        1
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0xe0] 44100 48000 88200
sad0_bits        [0xe0000] 16 20 24
```A negative result will look like this:

```
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x0]
sad_count        0
```If you have no eld data for any device you're in the same boat that I was at the start of this thread :| 

If you have eld data for a device first unmute the device in alsamixer then test the device.

alsamixer

Select a device/channel and press m to unmute the devices/channels .MM denotes muted 00 is unmuted.

Test the audio with aplay *,* denotes whatever device you're testing eg 1,9 = plughw:1,9. hdmi:NVidia is a pcm alias used by the system

aplay -Dplughw:*,* /path/to/file.wav
aplay -Dhw:*,* /path/to/file.wav
aplay -Dhdmi:NVidia /path/to/file.wav

/usr/share/sounds/alsa/ has some .wav files you can test

At this point you've determined that your hardware works. Now you must configure alsa/pulseaudio.




**Update**: **setting the alsa snd-hda-intel probemask for your device.** 

A lot of people tend to be confused by the information in this post. I've attempted to make a less confusing howto using the probemask method [http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

You might be able to ignore the Configuring Alsa pcm alias section below by assigning a probemask to the device responsible for hdmi audio.

> An alternative is to use the "probe_mask" ALSA module parameter as described on this page:

[http://wiki.xbmc.org/?title=HOW-TO_s...20%2C_or_GT240]("http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240")

However, please note that the actual values for probe_mask on that page  don't make sense; the correct values you should try are 0x101, 0x102,  0x104, 0x108. You can determine which you need by plugging in your HDMI  monitor, starting X, then viewing /proc/asound/card*/eld*. Whichever eld  file has your monitor's information in it will tell you which  probe_mask to use; eld#0.0 -> 0x101, eld#1.0 -> 0x102, eld#2.0  -> 0x104, eld#3.0 -> 0x108. If you use multiple HDMI monitors and  want audio on both, logical/bitwise OR the probe_mask values together.  Note that the required probe_mask will change if you move monitors to  different connectors on your graphics board.eg. If 1,9 is my device to set a probemask for alsa hw:1,9 I'd do the following.
```

sudo gedit /etc/modprobe.d/sound.conf
```add

options snd-hda-intel probe_mask=0x108

save the file and reboot. 

This should tell alsa (snd-hda-intel module) that the hdmi output on my ion2 is 1,9 (NVidia,9) instead of 1,3(NVidia,3 default). I haven't tried this myself. I believe these masks should use the NVidia id (symlink) since it would make the most sense vs a discrete 0,1,2,3 definition.

hw:NVidia,3 = 0x101
hw:NVidia,7 = 0x102
hw:NVidia,8 = 0x104
hw:NVidia,9 = 0x108

To test the new probemask try aplay -D hdmi:NVidia /path/to/wav.file

If that doesn't work for alsa undo the modification and continue onto  Configuring Alsa.

If you hear sound do the following:

```
sudo gedit /etc/pulse/default.pa
```change

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
```to 

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hdmi:NVidia

```Save the file and reboot. If you still don't get audio at your desktop by this point make sure you've cleared all local user settings for pulseaudio so it will use the configuration from default.pa

To remove local pulseaudio settings (thx to lidex) Within a terminal in your desktop type:

```
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie  
```After removing the files logout/login or reboot.

[B]

Configuring Alsa:[/B] 

Information as to setting up a proper pcm alias for a device can be found

[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

You may set these options in the /etc/asound.conf file to be default for the entire system. .asoundrc is per user but the format is the same.

[B]Update: See this thread for more about setting up default audio with dmix/hw.
[http://ubuntuforums.org/showthread.php?t=1620926]("http://ubuntuforums.org/showthread.php?t=1620926&highlight=hdmi+audio")[/B]

Please see post #3 in the thread linked above.

eg. I want to create a new hdmi alias for hw:1,9, rate=48000, format=S16_LE and set it as default.
> 
```
pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:1,9" # Always use pure hw. dmix will reformat/resample audio.
    period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
    buffer_size 4096
    rate 48000 # HDMI, I'll assume 48kHz
    format S16_LE # Should be default for pretty much any soundcard.
  }
  bindings {
    0 0
    1 1
  }
}

pcm.!default {
  type plug
  slave.pcm dmixer
}
```Depending on your eld and codec information (codec is found in the same directory as eld) you may chose to set variables such as rates, format, channel # etc. 

[B]
Changing default device to NVidia:*[/B]

**note if you just want to set default sound to NVidia,9 (hw:1,9) thanks to [http://ossnotebook.blogspot.com/](http://ossnotebook.blogspot.com/)

> In case you want to make a permanent change for the hdmi sound as the deafult card you can update /usr/share/alsa/alsa.conf and change these lines:

defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0

to this:

defaults.ctl.card NVidia
defaults.pcm.card Nvidia
defaults.pcm.device 9The above should correctly setup the system to use NVidia,9 (hw:1,9). I'm not sure if this corrects the faulty hdmi:NVidia alias though. ie. would hdmi:NVidia automatically use device 9. If I find more information on this I'll update this post.
[B]


Configuring Pulseaudio:[/B]

In Ubuntu there are basically two sound layers alsa is the base then in a standard desktop environment pulseaudio sits ontop of alsa. Once you've established that your sound works in alsa with aplay -D or discovery of eld information but you are not getting sound at your desktop the issue is most likely pulseaudio.

At this point you know what the proper device call is for your hdmi. So in a terminal within your desktop type:

```
pactl list | less
```[http://linux.die.net/man/1/pactl](http://linux.die.net/man/1/pactl)

This will display the pulseaudio sinks to alsa for sound. If there is no hdmi sink or the sink is misconfigured eg 1,3 instead of 1,9 do the following.

Edit 

/etc/pulse/default.pa

find the "module-alsa-sink" section and add (eg. for hw1,9)

```
load-module module-alsa-sink device=hw:1,9
```at the end of the section using your device definition of course.

Ok I'm done here good luck with those ion2's guys!

---

### Post by lidex on 2010-08-17
Thanks for posting your solution. Good work!

---

### Post by cncook001 on 2010-08-18
Thanks for these posts.  I now have my Zotac Zbox HD-ID11 (ion2) working.

Well, using the HDMI port translates to plughw:1,7.  I tried using the DVI port but sound is not working yet (not really needed though).

Using linux-backports-modules-alsa-2.6.32-24-generic
Nvidia Driver: 195.36.24

I was running kernel 2.6.32-22, but alsa backports must be 2.6.32-24, so upgraded to newer kernel and then the list of NVIDIA hdmi devices showed up.
 
```


user@HD-ID11$  uname -r
2.6.32-24-generic

user@HD-ID11$  aplay -l;aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
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
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

```

---

### Post by dvm1982 on 2010-08-19
Thanks!! It was really useful. But I have an strange problem now. Sound works perfect in both Ubuntu and XBMC. But if I try running xbmc-standalone there's no sound at all. No one have tried? It only happens starting XBMC session from the beginning. If you close Gnome session and start XBMC session, the sound works.

---

### Post by lidex on 2010-08-19
> **dvm1982 said:**
> Thanks!! It was really useful. But I have an strange problem now. Sound works perfect in both Ubuntu and XBMC. But if I try running xbmc-standalone there's no sound at all. No one have tried? It only happens starting XBMC session from the beginning. If you close Gnome session and start XBMC session, the sound works.

Scroll down to 'Part 3' here:
[http://forum.xbmc.org/showthread.php?t=59877](http://forum.xbmc.org/showthread.php?t=59877)

Hmm, or maybe it's the alsa setup. Start from the top.

---

### Post by tjones00 on 2010-08-19
I'm running xbmc stand-alone from the xbmc svn ppa right now. It's rather unstable for me atm so I haven't done a lot of testing yet I'm waiting for the offical ppa to be back online. I do have audio though using plughw:1,9 for custom output and passthrough without setting up a /etc/asound.conf

Ensure the user that xbmc stand-alone is running under is part of the audio group. I think xbmc stand alone requires you to create the user xbmc and add them to the necessary groups. My default user is xbmc so I don't have to mess with this stuff.

Xbmc should set this up automagically if not. List all users.

```
cat /etc/passwd | cut -d":" -f1
``` or simply cat /etc/passwd

If xbmc doesn't exist add them.

```
sudo adduser xbmc --gecos XBMC
```If they do exist check the groups for xbmc

```
groups xbmc
```To add the necessary groups

```
sudo usermod -a -G audio,video,netdev,fuse,cdrom,plugdev xbmc
```only using --group as described in the links below or -G will strip any current groups and replace them with those defined above -a -G will add groups alongside any preexisting ones.

[http://wiki.xbmc.org/?title=XBMCbuntu](http://wiki.xbmc.org/?title=XBMCbuntu)

[http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501](http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501)

---

### Post by dvm1982 on 2010-08-20
Finally it worked but I really don't know how, because I changed so many things in so many places :S. I added my user to the groups you said and used custom output plughw:1,7. But the sounds for the menus are lost! However, I can hear music and movies so it's enough for me :D

---

### Post by tjones00 on 2010-08-20
The lost menu noises using sound over hdmi is a xbmc issue if you dig around their forums/tutorials there is a fix.

Personally I find the ticking annoying so I actually prefer that it's broken.

I've now installed xbmc from the team-xbmc ppa and I'm not crashing anymore I played about 4hrs of mkv files last night.  Using nvidia 256.44 drivers with vdpau enabled.

I'll try to keep any xmbc tweaking on the Lenovo Q150 thread at the xbmc forums.

---

### Post by lidex on 2010-08-20
> **tjones00 said:**
> The lost menu noises using sound over hdmi is a xbmc issue if you dig around their forums/tutorials there is a fix.

Personally I find the ticking annoying so I actually prefer that it's broken.

I've now installed xbmc from the team-xbmc ppa and I'm not crashing anymore I played about 4hrs of mkv files last night.  Using nvidia 256.44 drivers with vdpau enabled.

I'll try to keep any xmbc tweaking on the Lenovo Q150 thread at the xbmc forums.

Wow. I just want to thank *tjones00* for his efforts here. Good job! If you would please mark the thread solved using 'Thread Tools' up top so others will know there is a solution here ;)

---

### Post by tjones00 on 2010-08-20
lol thx lidex I was trying to figure out how to do that last night.

I'm not much of a forum user. I'll watch this post for a couple more days in case questions come up then it's back to the interwebs with me.

I still have to solve fixing the hdmi alias in alsa.conf that should just entail finding the alias definition and switching whats probably 3 to 9 then putting the probemask back on to list only 1 device instead of 4. Then everything should be "proper".

For now I've moved onto upgrading xbmc codec issues since the wife is wants her m2ts blueray files.

---

### Post by ssarkar on 2010-08-26
I just got the Jetway Mini-TOP HBJC600C99-52W-BW, long name, and it has an ION2. I am running into this same problem where the audio drivers don't detect the nvidia hdmi output.  However, when I install the audio drivers via the instructions, when I go to reboot, ubuntu just stops at the splash screen and doesn't get any further.  How can I figure out what's going wrong with this upgrade?  Thanks.

---

### Post by tjones00 on 2010-08-26
Hi and yay a Jetway!

Hmmm I never encountered anything like this when upgrading alsa.

From the description you've posted I'm more inclined to think it's a graphics driver error.

If you can get to a terminal during the hangup (ctrl+alt+f2) use dmesg to check your kernel boot log.

First try replacing the kernel boot paramater "quiet splash" with "noplymouth" at the grub menu this will give a verbose output of the boot process instead of the splash.

If it still hangs up and the verbose output or dmesg didn't give you any clues try adding nomodeset. "nomodeset noplymouth"

If that works your Nvidia driver install might have gotten messed up. To me this sounds like you installed the 256.44 NVIDIA*.run file from the Nvidia website and didn't blacklist nouveau etc. before compiling.

If you still can't figure out whats happening boot in recovery mode and check the logs in /var/log and look at one of the old dmesg.* logs from when your system got stuck.

---

### Post by DrMPS on 2010-08-28
I also have just got the very same Jetway Mini-TOP.  I have exactly the same problem--the audio drivers do not detect the nvidia HDMI out [fyi, the box also has a toslink optical out, which the system DOES recognize, but I have not tested its functionality yet as my amp w/optical in is in storage].

When I install the audio drivers via the instructions here (or anyone else's instructions I've found on the web), I have the same problem--ubuntu stops at the splash screen; it is not possible to get to a terminal at the hangup.  VERY frustrating.  I've done it several times now in the last 2 days with fresh installs of ubuntu 10.04, using the default NVIDIA drivers (mmm, v192.something?) provided via ubuntu, and using the new 256.44 NVIDIA drivers downloaded directly from the NVIDIA website, and I believe I blacklisted nouveau--the 256.44 driver package said it would do it.  I will try *again* to make sure that the nouveau is blacklisted from a clean install, but it'll be the 3rd time tonight I reinstall ubuntu, recompile/reinstall the new alsa, etc, kind of time consuming and my patience is wearing thin for this evening.

On boot the noplymouth response hangs at, hmm, 
[B]* Speech-dispatcher configured for user sessions
* Starting Common Unix Printing System:cupsd[/B]


and then gives me some garbage about the CPU#0 not responding for 61sec over and over again.

When I access the 'Recovery Menu', the system stalls after about 15 seconds, so if I don't make a selection quickly it gives me an error like it is doing on the TV right now:
[  79.457005] BUG: soft lockup - CPU#2 stuck for 61s! [modprobe:467]
This is the same error message visible when I change 'quiet splash' to 'noplymouth'.

I don't *think* there's any hardware failure, it's all brand new and clean installs of ubuntu work just fine (of course, the clean install does not do HDMI audio out, which is the problem).

The problem is compounded by the fact that my idiot samsung 7000 series LCD apparently ONLY takes HDMI video + HDMI audio--you can't source HDMI video to input 1 and pair that with audio input 1, that is reserved for DVI input only...yeah I know, get an amp to combine the toslink and HDMI signals or run it DVI+stereo but I'd prefer to do neither of those things for this particular setup.

I really hope someone can figure out this particular issue, because the Jetway Mini-TOP really is a nice little package (if the stupid HDMI audio can be resolved).

---

### Post by tjones00 on 2010-08-28
I can't remember how many times I had to re-install trying to figure out my alsa 1.0.23 backport solution. I feel your pain.

Hangups during the recovery option is kind of troubling. If you can try using a live CD and take a look at the system logs. Especially the dmesg in /var/log.

Ok to recap. It sounds like you have a standard ubuntu full desktop install and are using the Ubuntu repository for nvidia drivers.

A couple of questions.
1) is it a 32b or 64b install?
2) did you upgrade the kernel to 2.6.32-24 before upgrading alsa via the backport? 
3) you have a bootable o/s before the alsa upgrade and it is explicitly the alsa upgrade that messes everything up? (you didn't upgrade graphics drivers at the same time etc)

Just off the top of my head I think the Jetway has an intel atom D525 (1.8ghz) cpu correct? For the zotac and lenovo mentioned in this thread both have the D510 (1.6ghz) cpu. I'm not sure if the D525 is an over-clocked D510.

All of my installs have been of the 32b variety either generic or generic-pae(server) and I haven't encountered any cpu errors.

I'd try three things:


1) Test the cpu

Do a fresh 32b install use the ubuntu repo nvidia drivers and try getting MPrime up and running to test the cpu before touching the alsa upgrade or whatever the specific step is that messes up your system.

[http://en.wikipedia.org/wiki/Prime95](http://en.wikipedia.org/wiki/Prime95)

MPrime is the linux equivalent of prime95 which you may already know of. You can use this to run stability tests on your cpu. You can also try prime95 if you have an available win o/s to install and compare it to the linux results. If the D525 is an over-clocked D510 some stability tweaking may be required.


2) Try using a Ubuntu 2.6.35 kernel backport

You need either alsa 1.0.23 or a 2.6.35 kernel to see the ion2 soundcard. Try upgrading via a ubuntu kernel backport to 2.6.35.

**you will probably have to reinstall nvidia after doing this if you already installed the drivers

[https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-meta-lts-backport-maverick
```I never got this to work since it wasn't patched at the time or I had some funky probemask on but it might work now. This is easier than compiling alsa from the kernel ftp. Last build is dated 8/25.


3) Try compiling alsa 1.0.23 from source using the linux kernel ftp alsa packages. Or compile a custom kernel from there.

Anything dated Aug01/10 or later should have the required hdmi sense patch and upgraded snd_hda_intel.

[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/)

The alsa upgrade script uses the alsa project ftp instead of this one for the source and apparently it isn't patched for snd_hda_intel hdmi sense.

Just a warning. When I tried compiling from those packages it was giving me make errors saying it couldn't find the linux headers even though I had the ubuntu 2.6.32-24 ones installed so it may require you to upgrade your kernel to 2.6.35 from this source as well. If you upgrade your kernel to 2.6.35 from this source technically you shouldn't need to upgrade alsa.

---

### Post by DrMPS on 2010-08-29
Thanks for the response!  So, 32bit install. I *had* been running with 2.6.32-24-generic-pae prior to upgrading alsa via the backport, or via compiling my own from the ftp sites, etc (i tried several guides).  Yes, the OS was 100% bootable and running before the alsa upgrade and the alsa upgrade ONLY.  This occured on a clean install of ubuntu 10.04.

This afternoon I finally tried installing win vista on the machine, and (after loading the drivers off the install disc included with the barebones pc) the HDMI video and audio worked right out of the gate.  Did not test the 5.1 of it as I don't have an hdmi-compatible amp lying around (but I'll have one soon).  So I can guarantee the hardware works.

HOWEVER----MAJOR BREAKTHROUGH TONIGHT!!  Got home tonight, tried out your suggestions.  CPU, fine, RAM, fine, upgraded to kernel 2.6.35-18-generic in command line.  Restarted, and bam!  aplay -l all of the sudden shows my HDMI audio channels! (Also I am now, apparently, upgraded to alsa 1.0.23 by virtue of having upgraded the kernel.  At least, cat /proc/asound/version says 1.0.23 now.)

However....getting those HDMI channels to do anything is taking some effort.  I can get the channels to play back sample .wav files through the TV speakers, but that's about it.
This works:

aplay -Dplughw:0,7 /usr/share/sounds/alsa/Front_Center.wav

likewise 0,3 and 0,8 and 0,9 all of which are listed under aplay -l

This does NOT work:
aplay -Dhw:0,3 /usr/share/sounds/alsa/Front_Center.wav
(likewise 0,7 0,8 0,9 don't work either) 
Trying the aplay -Dhw:0,x command returns the message:
aplay: set_params:996: Channels count non available.

This also does NOT work:
aplay -Dhdmi:NVidia /usr/share/sounds/alsa/Front_Center.wav
It generates several lines of unhappy response, but the most important seems to be "Unable to find definition 'cards.HDA-Intel.pcm.hdmi.9:CARD=NVidia,AES0=4,AES1=130,AES2=0,AES3=2" 
and "Unknown PCM hdmi:NVidia".

I followed your lead in the thread to make my own .asoundrc file and stuck a copy in /home and in /home/username and also made a asound.conf in /etc that was *supposed* to work, but does not.  I can't seem to get the HDMI device(s) to show up in the list when I do aplay -L, no matter which of the 4 of them I map in .asoundrc

Incidentally my .asoundrc file contains:
pcm.hdmi07 {
    type hw
    card 0
    device 7
}
Is this correct?  It does nothing on my system.
The NVIDIA hdmi IS card 0, card 1 is the onboard "USB PnP Sound Device", which is a combo 1/8" minijack + TOSLINK optical jack---the minijack certainly works, the optical I'll know whenever I find my amp with an optical in.

Incidentally aplay -l generates:
card 0: NVidia [HDA Nvidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
   Subdevices: 1/1
   Subdevice#0: subdevice #0
(and the same where 3 is replaced by 7, 8, 9.)
card 1: default [USB PnP Sound Device {, device 0: USB Audio [USB Audio]
   Subdevices: 1/1
   Subdevice #0: subdevice #0

I'm transcribing not copy/pasting because THIS machine has about 20 firefox tabs/windows open and is being used to help understand what is going wrong with the Jetway MiniTOP ubuntu 10.04 system.

Thanks so much for your input, it would have taken me awhile to think of upgrading the kernel.  Any further ideas on how to get the stupid HDMI to appear in aplay -L?

---

### Post by tjones00 on 2010-08-29
did aplay -Dhdmi07 work?

Remove the .asoundrc that's a finishing touch once you've established which device to use while having 4 devices listed.

edit** sorry I didn't see where you mentioned all 4 devices are listed under aplay -l still remove the .asoundrc for now

whats the output from 

```
cat /proc/asound/card0/eld*
```

edit** again gd I was out of it with my original response I blame lack of coffee still give me the eld info though.

so plughw:0,7 works, hw:0,7 doesn't work hdmi:NVidia doesn't work (it shouldn't at this point anyway)

hw:0,7 is troubling but we can't do anything about that until we see the eld information. plughw adjusts the format and hw is just raw output.


As to why hdmi:NVidia doesn't work it's probably set to 0,3 in the alsa.conf. Thats the reason for making hdmi** pcm alias and using that instead eg with the one you made aplay -Dhdmi07 /path/to/wav.file.

If you want to correct that (I never bothered with it since I just needed plughw:*,* to work) try checking the alsa.conf at /usr/share/alsa/alsa.conf find where hdmi:NVidia gets it's definition to use device 3 and replace it with 7. You could also replace any hw definition for hdmi:NVidia with plughw.

I believe hdmi:NVidia is just fancy talk for hw:0,3 in your case so even if you change it to 7 it still might not work since hw:0,7 is giving you issues.

You can refer to [http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc) to setup a proper plughw pcm alias if you wish. Also check [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

I think 

pcm.hdmi07 {
type plughw
card 0
device 7
}

might work test it via aplay -Dhdmi07 /path/to/wav.file

---

### Post by DrMPS on 2010-08-29
The audio now works!  After removing the .asoundrc, I made an asound.conf in /etc that duplicates what the .asoundrc had.  Now all of the sudden I get sounds.  Media playback in Movie Player and VLC both sound tinny...not sure why, the speakers on the TV certainly work correctly.  

hw0,7 and hdmi:NVidia don't work still at the command line.

The system still lists (in system-->preferences-->sound), under hardware, "High Definition Audio Controller" as "Analog Stereo Output", that can't be right.

Here's the eld info response:

monitor_present                  0
eld_valid                             0
monitor_name
connection_type                  HDMI
eld_version                         [0x0] reserved
edid_version                       [0x0] no CEA EDID Timing Extension block present
manufacture_id                   0x0
product_id                          0x0
port_id                               0x0
support_hdcp                      0
support_ai                          0
audio_sync_delay                0
speakers                            [0x0]
sad_count                           0
monitor_present                  1
eld_valid                            1
monitor_name                    SAMSUNG

connection_type                 HDMI
eld_version                        [0x2] CEA-861D or below
edid_version                      [0x3] CEA-861-B, C or D
manufacture_id                  0x2d4c
product_id                         0x6ac
port_id                              0x20000
support_hdcp                     0
support_ai                         0
audio_sync_delay               0
speakers                           [0x1] FL/FR
sad_count                         1
sad0_coding_type              [0x1] LPCM
sad0_channels                   2
sad0_rates                        [0xe0] 44100 48000 88200
sad0_bits                          [0xe0000] 16 20 24
monitor_present                 0
eld_valid                           0
monitor_name
connection _type                 HDMI
eld_version                         [0x0] reserved
edid_version                      [0x0] no CEA EDID Timing Extension block present
manufacture_id                  0x0
product_id                         0x0
port_id                              0x0
support_hdcp                     0
support_ai                         0
audio_sync_delay               0
speakers                           [0x0]
sad_count                          0
monitor_present                0
eld_valid                           0
monitor_name
connection_type                HDMI
eld_version                       [0x0] reserved
edid_version                     [0x0] no CEA EDID Timing Extension block present
manufacture_id                 0x0
product_id                        0x0
port_id                              0x0
support_hdcp                    0
support_ai                        0
audio_sync_delay             0
speakers                          [0x0]
sad_count                        0

the response to aplay -L still doesn't show anything new.

---

### Post by tjones00 on 2010-08-30
Hmmm probably have to edit the alsa.conf to see it in aplay -L I guess.

The odd audio in VLC is probably the driver/codec using a messed up rate by default.

Anyway woot!.

Ok if you do anymore pcm alias editing you now know the audio capabilities of your display from that eld information so you can set standards like rate 48000, 2 channels S16_LE etc.

```

speakers                           [0x1] FL/FR
sad_count                         1
sad0_coding_type              [0x1] LPCM
sad0_channels                   2
sad0_rates                        [0xe0] 44100 48000 88200
sad0_bits                          [0xe0000] 16 20 24
```

The capablities of your codec are found at cat /proc/asound/card0/codec#1.0 for device 7

---

### Post by ssarkar on 2010-08-30
Well this has definitely been an interesting challenge.  I'm making some progress, but still not super successful.  I've managed to upgrade my alsa driver to the 1.0.23 version.

When I look at my eld#1.0 file, it brings up the information I expect

```

monitor_present        1
eld_valid        1
monitor_name        DENON-AVAMP

connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0xee11
product_id        0x1f
port_id            0x20000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x5f] FL/FR LFE FC RL/RR RC RLC/RRC
sad_count        7
sad0_coding_type    [0x1] LPCM
sad0_channels        8
sad0_rates        [0x1ee0] 44100 48000 88200 176400 192000 384000
sad0_bits        [0xe0000] 16 20 24
sad1_coding_type    [0x7] DTS
sad1_channels        6
sad1_rates        [0x6c0] 48000 88200 176400 192000
sad1_max_bitrate    1536000
sad2_coding_type    [0x2] AC-3
sad2_channels        6
sad2_rates        [0xe0] 44100 48000 88200
sad2_max_bitrate    640000
sad3_coding_type    [0xb] DTS-HD
sad3_channels        8
sad3_rates        [0x1ec0] 48000 88200 176400 192000 384000
sad4_coding_type    [0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad4_channels        8
sad4_rates        [0xc0] 48000 88200
sad5_coding_type    [0xc] MLP (Dolby TrueHD)
sad5_channels        6
sad5_rates        [0x1ec0] 48000 88200 176400 192000 384000
sad6_coding_type    [0xc] MLP (Dolby TrueHD)
sad6_channels        8
sad6_rates        [0x6c0] 48000 88200 176400 192000

```And when I run this command, I get sound coming out of my speakers via HDMI
aplay -Dplughw:0,7 /usr/share/sounds/alsa/Front_Center.wav

but -Dhw doesn't work, just like DrMPS when he was trying to set up his jetway

However, when I make an asound.conf file in my /etc directory, some strange things happen.  When I put this as my entire asound.conf file

pcm.hdmi07 {
type plughw
card 0
device 7
}


then run 
aplay -Dhdmi07 /usr/share/sounds/alsa/Front_Center.wav

I get this error
ALSA lib pcm.c:2171:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_plughw.so


I find this kind of strange because when I do the -Dplughw command the sound plays fine, but not when I do the .conf file alias, it does not play.  But when I checked, the library wasn't in that location

So I'm not quite sure what is going on.  Any help would be appreciated.  Thanks.

---

### Post by tjones00 on 2010-08-30
So plughw:0,7 works for you.

I'd think that means plughw doesn't work properly for "type" in your setup. I was just grasping at straws when suggesting to use it as type.

Try type plug instead of plughw and see if that grabs some defaults. plug appears to be an official type.

If plug doesn't work you'll probably have to setup a full dmix/asym or full hw/slave setup

[FONT=monospace]see [http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc) Plugins Section


You could also try sending all audio through dmix (adjust format) then to 0,7 with the following.

[https://bbs.archlinux.org/viewtopic.php?pid=789152](https://bbs.archlinux.org/viewtopic.php?pid=789152) Themaister's post.


[/FONT]

---

### Post by ssarkar on 2010-08-30
Ok, I think I'm starting to see what my problem is.  After a bunch of mucking around in my asound.conf file in /etc, now when I type 

*aplay <wav file>*

the file plays fine, so my alsa default settings are ok.

I went a step further and used mplayer to play some other types of media.  When I run this command

[I]mplayer -ao also:device=plughw=0.7 <mp3 or video file>
[/I]
it plays ok.  But when I remove the -ao option and do this

*mplayer <mp3 or video file>*

nothing happens.  The main difference I'm seeing is that when mplayer runs it says 
*A0: [pulse] 44100Hz *

but when I put the -ao command line option I get
*A0: [alsa] 44100Hz*

So it seems as though it's using pulseaudio instead of alsa by default for everything.  I think that's why I can hear things through aplay, but media player or vlc are trying to use pulse by default and that doesn't seem to work.

Does this mean that I need to deactivate pulseaudio?  Or should pulse work through the alsa config that I currently have set up?

Thanks.

---

### Post by ssarkar on 2010-08-30
So I put in plughw:0,7 as a custom audio device inside xbmc, and audio now works in there.  I don't have audio in anything else like vlc because they seem to default to pulse.  But since I'm primarily planning on running xbmc, this isn't the end of the world.  Still curious about what needs to be done to get it all working though.

---

### Post by lidex on 2010-08-30
> **ssarkar said:**
> So I put in plughw:0,7 as a custom audio device inside xbmc, and audio now works in there.  I don't have audio in anything else like vlc because they seem to default to pulse.  But since I'm primarily planning on running xbmc, this isn't the end of the world.  Still curious about what needs to be done to get it all working though.

It may help to change the audio output to alsa in vlc preferences. (Also mplayer, xine). This is a decent reference:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)

---

### Post by leespa on 2010-09-01
Hi Guys,

I am trying to get a GT 240 + atom330 + ALSA 1.0.23 + Nvidia 256.53 setup going. 

I have aplay showing correct plugs but get NO SOUND or errors. I will follow some of the leads here relating to the eld* issue since I never checked that.

As I understand it the GT 2xx + atom 330 *should* work similiar to your ION2's since the system sees that as a discrete GPU as well; correct?

My ubuntu thread is here with all the gory details:

[http://ubuntuforums.org/showthread.php?t=1565479&highlight=gt+240](http://ubuntuforums.org/showthread.php?t=1565479&highlight=gt+240)

---

### Post by leespa on 2010-09-02
Hi All,

So I tried the **linux-backports-modules-alsa-2.6.32-24** on my rig and my **eld** are all still EMPTY.

**Atom330 + GT 240 + NVIDIA 256.53 + ALSA 1.0.23 backports**

```

xbmc@xbmc:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

xbmc@xbmc:~$ uname -r
2.6.32-24-generic

xbmc@xbmc:~$ nvidia-settings -v
nvidia-settings:  version 256.53  

xbmc@xbmc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708BCE Analog [VT1708BCE Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708BCE Digital [VT1708BCE Digital]
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

xbmc@xbmc:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, VT1708BCE Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, VT1708BCE Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

xbmc@xbmc:~$ cat /proc/asound/card1/eld#*
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0


```

I'm fresh out of ideas. Try old rev of NVIDIA drivers?!

---

### Post by tjones00 on 2010-09-03
Hello leespa

I checked your post. That does seem very odd for a gt240 and you've referred to the xbmc wiki about the gt240.

With your solution that x must be running makes me think it might be a pulseaudio or groups issue for the user xbmc is running under or the user you did your command line tests with.

It still doesn't explain the missing eld information on any device which is very odd.

I assume you're probably following this guide.

[http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501](http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501)

for a 330 system.

You could try upgrading the kernel to 2.6.35 via ubuntu backport like the Jetway guys had to do. See post #21 on this thread about upgrading the kernel via ubuntu backport.

---

### Post by leespa on 2010-09-03
Hi tjones00.

Thanks for the reply. I have been following this guide: [http://forum.xbmc.org/showthread.php?t=74778&highlight=xci](http://forum.xbmc.org/showthread.php?t=74778&highlight=xci) 

I have checked and my xbmc user is part of group audio; also AFAIK I never installed pulseaudio through the minimal ubuntu 10.04 process.

I can continue with the testing via ssh from the other room. I just need to install xbmc-live or run xinit xbmc before I try it out.

Another interesting thing I found last night: if I load xinit xbmc and then drop back to another shell via CTL+ALT+F2 for instance the aplay tests don't work from that shell...meaning I have to keep xbmc running and do the tests from another PC.

I am going to go back to the 256.53 drivers; will report back once all that is pushed through.

---

### Post by tedder on 2010-09-28
BTW, what got HDMI working on my Jetway Mini-top was to install the 2.6.35 kernel. It isn't available on backports yet, but I was able to install easily from the debs.

[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)

---

### Post by cyle1116 on 2010-09-29
> **tedder said:**
> BTW, what got HDMI working on my Jetway Mini-top was to install the 2.6.35 kernel. It isn't available on backports yet, but I was able to install easily from the debs.

[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)

Hi Tedder,

I have the same Jetway box and upgraded the kernel, but I still have no sound through the HDMI, did you have to update anything else?

Thanks

---

### Post by tedder on 2010-09-30
> **cyle1116 said:**
> I have the same Jetway box and upgraded the kernel, but I still have no sound through the HDMI, did you have to update anything else?

Hey- that was all I had to update. But post the results of the following commands and I'll see if I can help.
uname -a
aplay -l
aplay -L

---

### Post by cyle1116 on 2010-10-05
Here is uname -a:

Linux XBMC 2.6.35-020635-generic #020635 SMP Mon Aug 2 09:08:21 UTC 2010 x86_64 GNU/Linux


Here is aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB PnP Sound Device          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here is aplay -L:

pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
front:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    IEC958 (S/PDIF) Digital Audio Output

Thanks for all your help.

-Cyle

---

### Post by lidex on 2010-10-05
> **cyle1116 said:**
> Here is uname -a:

Linux XBMC 2.6.35-020635-generic #020635 SMP Mon Aug 2 09:08:21 UTC 2010 x86_64 GNU/Linux


Here is aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB PnP Sound Device          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here is aplay -L:

pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
front:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    USB PnP Sound Device          , USB Audio
    IEC958 (S/PDIF) Digital Audio Output

Thanks for all your help.

-Cyle

Not sure what you're trying to pass audio through, but your usb device is the default soundcard. Is that what you want?

---

### Post by cyle1116 on 2010-10-11
No that is not what I want. How do you change it?

---

### Post by carchaias on 2010-11-03
Hi, thanks for that threat. I searched the web for days to activate the HDMI output on my ASUS AT5IONT ION2 Board. Im using Mythbuntu 10.10 and finally I learned that it was all there. HD-output just had to be aktivated in MythTV Frontend by chosing plughw1,3 as the device. 1,7 / 1,8 / 1,9 does also, unfortunatly HDMI what I tried does not and plughw1,x wasn't in the list. Good idea just typing it in. What ist the difference between these four?
Another question : This Board has two Audio-cards. One (Intel) for Analog and SPDIF output and the ION for HDMI. How to configure, all output to both cards? Can that be done in the asound.conf file. So sound should come from the TV if the TV is runnning, and sound should come  from my "historic" analog Stereo-Amp if the Amp is powered on. Just now I am only toggling between the two cards by changing the device in Myth's Frontend.

---

### Post by Leviathor on 2010-11-10
> **tjones00 said:**
> [Post Number 8]("http://ww.ubuntuforums.org/showpost.php?p=9732345&postcount=8")

I was able to get my discrete ION2 graphics working in 10.10 using this outline.  Thanks!

---

### Post by greven79 on 2010-11-14
I have similar issues with my Asus EB 1501P that I bought for running XBMC.

I've been trying for 2 days to get sound from it but I'm stuck.

I'm a Linux noob so bare with me.

I feel that I'm close now since installing alsa 1.0.23.

aplay -l gives me:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
and aplay -L:

> null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
I would really appreciate some help, feels like I'm banging my head against the wall now. (probably a time to take a break.)

---

### Post by angry_norwegian on 2010-11-15
I tried everything here, without success. I have an Asus AT5IONT-I mobo.

Turns out I had to follow [this procedure]("http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240").

*sigh* But now my mouse cursor won't hide in gnome-mplayer. Back to whacking moles! :D

---

### Post by uncouth on 2010-11-20
Followed this thread with great interest to get my own Q150 working with the new XBMC Dharma (RC1) - and it almost does. The menu sound effects work after following the guide here, however once I stream audio or video I get the dreaded "Failed to initialize audio device" error... 
 
So close... yet so far.

---

### Post by speed32219 on 2010-11-22
> **carchaias said:**
> Another question : This Board has two Audio-cards. One (Intel) for Analog and SPDIF output and the ION for HDMI. How to configure, all output to both cards? Can that be done in the asound.conf file. So sound should come from the TV if the TV is runnning, and sound should come  from my "historic" analog Stereo-Amp if the Amp is powered on. Just now I am only toggling between the two cards by changing the device in Myth's Frontend.

Any headway on this?  I have the HDMI output working fine, but I can not get the headphone or SPIDF working.  I am sure it is probably the asounrc or asound.conf settings.  Anyone have a woking asoundrc or asound.conf file they would like to share?

Also, when I first installed following post #8 using the backports to install Alsa 1.0.23 I finally got aplay to post.  When I went into set alsamixer it had four SPIDF entries, after reboot it now only has one.  (HDMI is working so it must be the one) 

Here is the output of aplay -l:
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: default [USB PnP Sound Device          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now I want to get the stereo headphone/Microphone working as well as spidf optical. Any recommendations?

HW:
Jetway Mini-TOP HBJC600C99-52W-BW - New Ion 2 ###GEforce 218
Intel Atom 525 dual core 1.8Ghz 
1 GB Notebook (200 pin) PC-6400 Rendition RAM (Cruical)
WD Scorpio Blue 250GB 2.5" drive

Solved:  IT was a matter of setting my output devies in the App.  I set my Audio and passthrough to USB Pnp Sound iec958.  Eveything is working great.

---

### Post by tjones00 on 2010-12-02
> **uncouth said:**
> Followed this thread with great interest to get my own Q150 working with the new XBMC Dharma (RC1) - and it almost does. The menu sound effects work after following the guide here, however once I stream audio or video I get the dreaded "Failed to initialize audio device" error... 
 
So close... yet so far.

I believe this is an xbmc hdmi audio issue it can be fixed by editing some of the xbmc config files check their wiki for more information.


As to the combining digital + analog cards. Yes you can have both active at once by creating a custom dmixer pcm alias for alsa. Pretty much duping all channels on both devices and dumping them into one alias. Check the alsa wiki for more infomation. The archlinux  wiki tends to have good alsa information as well. I think there are some how to posts in the xbmc forum about creating a combined card

I stopped visiting these forums/topic since ubuntu 10.10 was around the corner and I assumed with the updated snd_hda_intel this would soon become a non-issue. 

If you've posted on this thread and haven't resolved your issue send me a private message I'll then read your post and attempt to point you in the right direction.

[B]Update thanks to zAPPzAPP

Setting up a dmix/hw and default sound.
[http://ubuntuforums.org/showthread.php?t=1620926]("http://ubuntuforums.org/showthread.php?t=1620926&highlight=hdmi+audio")[/B]

---

### Post by Jags_FL on 2011-01-04
@ tjones00

thanks a million for your efforts. ok after reading your posts, I've got this far:

installed Alsa 1.0.23 from ubuntu backports:

```
jags@mint /proc/asound/card0 $ uname -r
2.6.35-22-generic

apt-cache search linux-backports-modules-alsa-2.6.35.22

jags@mint /proc/asound/card0 $ apt-cache search linux-backports-modules-alsa-2.6.35.22
linux-backports-modules-alsa-2.6.35-22-generic - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
linux-backports-modules-alsa-2.6.35-22-server - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
```

```
sudo apt-get install linux-backports-modules-alsa-2.6.35-22-generic alsa-utils
```

Reboot.

to discover all devices aplay -l

```
jags@mint /proc/asound/card0 $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and now I'm also getting following for cat eld*

```
jags@mint /proc/asound/card0 $ cat eld*
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		1
eld_valid		1
monitor_name		SAMSUNG
    
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x2d4c
product_id		0x667
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x1] FL/FR
sad_count		1
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0xe0] 44100 48000 88200
sad0_bits		[0xe0000] 16 20 24
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
```

so now I need to "set up a proper pcm alias for a device(HDMI?) / create/edit /usr/share/alsa/alsa.conf ? do I enter following as you've suggested in [here]("http://ubuntuforums.org/showpost.php?p=9779896&postcount=23") or something else?

```
pcm.hdmi07 {
type plughw
card 0
device 7
}
```

Many thanks in advance!

PC: Dell Vostro 430, Core i5-760, Nvidia G310
OS: Linux Mint 10 Julia 64bit
Nvidia Driver: 260.19.06
Nvidia X server display configuration: TwinView (clones)
Monitors: (1) Dell 1080p 23" (2) Samsung 1080p LCD HDTV

---

### Post by tjones00 on 2011-01-04
Na plughw won't work for setting up a pcm. I never needed to go beyond plughw in xbmc so I never setup an alias myself. 

Check the zAPPzAPP thread for setting up a proper pcm (dmix/hw) alias it should resolve the final touches.

[http://ubuntuforums.org/showthread.php?t=1620926](http://ubuntuforums.org/showthread.php?t=1620926)

I still haven't seen anybody mess with pulseaudio tweaking so hopefully that isn't required. If it is you'll want to look up hdmi sink for pulseaudio.

---

### Post by Jags_FL on 2011-01-06
> **tjones00 said:**
> Na plughw won't work for setting up a pcm. I never needed to go beyond plughw in xbmc so I never setup an alias myself. 

Check the zAPPzAPP thread for setting up a proper pcm (dmix/hw) alias it should resolve the final touches.

[http://ubuntuforums.org/showthread.php?t=1620926](http://ubuntuforums.org/showthread.php?t=1620926)


Thanks a million for this thread... =D> 

I've just [summed it up in here]("http://ubuntuforums.org/showpost.php?p=10322429&postcount=14") how I made the HDMI audio work through Nvidia G310 with your and [zAPPzAPP's]("http://ubuntuforums.org/showpost.php?p=10121401&postcount=3") help.

---

### Post by achkap on 2011-01-15
> **tjones00 said:**
> [SIZE=3]

**Update**: **setting the alsa snd-hda-intel probemask for your device.** 

[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

You might be able to ignore the pcm alias section below by assigning a probemask to the device responsible for hdmi audio.

eg. If 1,9 is my device to set a probemask for alsa hw:1,9 I'd do the following.
```

sudo gedit /etc/modprobe.d/sound.conf
```add

options snd-hda-intel probe_mask=0x108

save the file and reboot. 

This should tell alsa (snd-hda-intel module) that the hdmi output on my ion2 is 1,9 (NVidia,9) instead of 1,3(NVidia,3 default). I haven't tried this myself. I believe these masks should use the NVidia id (symlink) since it would make the most sense vs a discrete 0,1,2,3 definition.

hw:NVidia,3 = 0x101
hw:NVidia,7 = 0x102
hw:NVidia,8 = 0x104
hw:NVidia,9 = 0x108

To test the new probemask try aplay -D hdmi:NVidia /path/to/wav.file

If that doesn't work for alsa undo the modification and continue onto Configuring Alsa, if it does work go down to Configuring Pulseaudio at the end of this post.



this did the thing that i have been trying for nearly one month... thank you very very much.
but now i don t have sound on my desktop.
i know that i can delete it from sound.conf file, reboot, and have sound from desktop. but not from tv. isn t there a simplier way to have both? i mean without rebooting.

i tried to configure pulse but it didn t work.

but again, thank you very much because i was so tired looking for a solution

---

### Post by tjones00 on 2011-01-15
Oh cool I've been waiting for someone to try this out and confirm if it works since I only use plughw with xbmc stand alone.

So lets clear this up. From your other post your hdmi device is hw:1,7

You used the following probe_mask in /etc/modprobe.d/sound.conf

options snd-hda-intel probe_mask=0x102

Now you have audio over your hdmi connection without making any other modifications? eg. asound.conf default.pa


Now onto your issue.

With your system you have 2 hdmi displays? What do you mean you get sound on the tv vs sound on the desktop? Can you elaborate more please I don't think I fully understand. Give me a complete physical description of the setup and issue.


Edit:
I think I know what you mean now. The talk about TV vs desktop confused me. Try:

```
load-module module-alsa-sink device=hdmi:NVidia
```

in the default.pa file

---

### Post by zaphod777 on 2011-02-08
Hey guys I have ion2 little set top box and have the audio and video all working great over HDMI but when I play a mkv the audio doesn't play and I see this in my logs. BTW I am using XBMC on ubuntu 10.10 server. Should I just rip out pulseaudio? I don't care as long as audio works for videos and music.


22:31:15 T:1446124400 M:1768480768  NOTICE: Creating audio device with codec id: 86017, channels: 2, sample rate: 48000, no pass-through
22:31:15 T:1456614256 M:1768669184  NOTICE:  fps: 23.976025, pwidth: 624, pheight: 352, dwidth: 624, dheight: 352
22:31:15 T:1456614256 M:1769484288 WARNING: CRenderManager::Configure - timeout waiting for previous frame
22:31:15 T:1456614256 M:1769484288  NOTICE: Display resolution DESKTOP : 1920x1080 @ 60.00 - Full Screen (12)
22:31:15 T:1446124400 M:1769357312   ERROR: PulseAudio: Waited for the Context but it failed
22:31:15 T:1446124400 M:1769357312   ERROR: PulseAudio: Failed to create context

---

### Post by tjones00 on 2011-02-08
If you are only using the computer for xbmc just purge pulse there is no need for it especially when only using one application.

As to your specific issue. .mkv files will typically have 5.1 audio or 7.1 audio. What log is that? regardless

22:31:15 T:1446124400 M:1768480768 NOTICE: Creating audio device with codec id: 86017, channels: 2, sample rate: 48000, no pass-through

Suggests to me that the 5.1 or 7.1 audio isn't being downmixed to stereo(2 channels). Usually the recieving hardware(tv/amp) should prefer a raw output and handle all the downmixing itself.

Assigning a passthrough/downmix device with plughw in xmbc/pulseaudio should correct this(eg. downmix 5+ channels to 2). Remove any asound.conf or .asoundrc files and try tapping into plughw for downmixing.

To quote:[http://www.suse.de/~mana/alsa090_howto.html](http://www.suse.de/~mana/alsa090_howto.html)

> The most important ALSA interfaces to the PCM devices are the "plughw" and the "hw" interface. If you use the "plughw" interface, you need not care much about the sound hardware. If your soundcard does not support the sample rate or sample format you specify, your data will be automatically converted. This also applies to the access type and the number of channels. With the "hw" interface, you have to check whether your hardware supports the configuration you would like to use.


**plughw downmix for pulseaudio:**
If you continue to use pulseaudio purge the alsa and pulse local settings and use plughw for the hdmi sink in default.pa instead of hw or whatever you're using. This should automatically downmix any 5.1/7.1 audio when selecting the device in pulseaudio. Refer to post 1 and 3 in this thread for clarification on this issue. [http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

eg. load-module module-alsa-sink device=plughw:1,9

**xbmc alsa plughw passthrough**
If you purge pulseaudio from the system just call upon alsa plughw:#,# for passthrough and audio device in xbmc and of course remove any asound.conf or .asoundrc

eg. plughw:1,9

---

### Post by zaphod777 on 2011-02-09
> **tjones00 said:**
> If you are only using the computer for xbmc just purge pulse there is no need for it especially when only using one application.

As to your specific issue. .mkv files will typically have 5.1 audio or 7.1 audio. What log is that? regardless

22:31:15 T:1446124400 M:1768480768 NOTICE: Creating audio device with codec id: 86017, channels: 2, sample rate: 48000, no pass-through

Suggests to me that the 5.1 or 7.1 audio isn't being downmixed to stereo(2 channels). Usually the recieving hardware(tv/amp) should prefer a raw output and handle all the downmixing itself.

Assigning a passthrough/downmix device with plughw in xmbc/pulseaudio should correct this(eg. downmix 5+ channels to 2). Remove any asound.conf or .asoundrc files and try tapping into plughw for downmixing.

To quote:[http://www.suse.de/~mana/alsa090_howto.html](http://www.suse.de/~mana/alsa090_howto.html)




**plughw downmix for pulseaudio:**
If you continue to use pulseaudio purge the alsa and pulse local settings and use plughw for the hdmi sink in default.pa instead of hw or whatever you're using. This should automatically downmix any 5.1/7.1 audio when selecting the device in pulseaudio. Refer to post 1 and 3 in this thread for clarification on this issue. [http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

eg. load-module module-alsa-sink device=plughw:1,9

**xbmc alsa plughw passthrough**
If you purge pulseaudio from the system just call upon alsa plughw:#,# for passthrough and audio device in xbmc and of course remove any asound.conf or .asoundrc

eg. plughw:1,9

Actually I went to remove pulseaudio but it was not even installed!! ;) 

So I installed pulseaudio and then set the output devices to the nvidiaHDMI instead of of the manual hardware configuration. Now it all works great!

---

### Post by phoenix1/4 on 2011-04-12
THANK YOU!

Somehow after stumbling through this post I managed to get it working! many thanks.

---

### Post by davst825 on 2011-09-20
I've followed this guide.. the experience has been kinda frustrating.. I'm up to the point where I tried playing sound via aplay -Dplughw:1,7 and I got sound there, then I tried to do both the proposed 
options snd-hda-intel probe_mask=0x102
did not work, also I did the ALSA configure without result.

So i backed out if the last few steps to where i got sound from the plughw, suddenly things worked.. wtf? but with the shitty audio from pulse as you described.i installed mplayer to try playing via pulse and via alsa. This made all audio work clearly! great.

2 hours later audio has stopped working... kinda. now i Only have clear audio from flash player (youtube videos) rest of the system is the shitty scratchy pulse audio and also I can't get audio in XBMC.. I'm ******* lost.

going to try to remove pulse audio but I need audio from flash player as well.

oh btw.. even though flash audio is working great.. now when i aplay -Dplughw:1,7 all i get is ******* noise

Update: I added a custom plughw:1,7 to XBMC audio and now at least that is working

Current status:

XBMC: Audio via custom plughw:1,7
Desktop: No audio from ubuntu
Mp3s played: via -ao alsa in mplayer work
Flash: Audio works great... 

This is a nightmare but I'vbe reached a semi acceptable point

---

