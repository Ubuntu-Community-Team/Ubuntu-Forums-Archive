---
title: "Soundproblems ZOTAC-HDMI SOUNDBLASTER"
date: 2011-01-07
forum: Multimedia Software
---

### Post by ialvik on 2011-01-07
Hi..

I have some problems installing drivers, if possible, so i can pair my soundblaster and HDMI card. 

I ****ed up with some oss settings and have a bit of a problem getting back to my ALSA settings.

>  02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 2117
    Flags: fast devsel, IRQ 5
    Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

0a:09.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs SB0570 [SB Audigy SE]
    Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 21
    I/O ports at 5000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: oss_audigyls
 

so this is the situation right now... please help someone :) I'm bit of a newbie... :/

Is this Zotac-HDMI card also a soundcard or is it just possible to "pair" it with my other soundcard?

---

### Post by lidex on 2011-01-07
Need to know a little more. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by ialvik on 2011-01-07
Here comes the info. Thank you for helping!!

>  
iver@S51:~$ sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-01-07 13:42:44--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-01-07 13:42:44--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [ <=>                                   ] 27,025      --.-K/s   in 0.1s    

2011-01-07 13:42:44 (238 KB/s) - `alsa-info.sh' saved [27025]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.WF6LxO3er6/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=17b44b8fd144d757186e913d253ee97c5c48cac5](http://www.alsa-project.org/db/?f=17b44b8fd144d757186e913d253ee97c5c48cac5)

Please inform the person helping you.



-Iver

---

### Post by lidex on 2011-01-07
You'll need to uninstall any packages starting with 'oss-'
Do a search in synaptic. Then re-install alsa:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by ialvik on 2011-01-07
Hi again..

I think i worked for the sound problems  but made some problems for my Graphic settings.

When i try to start up now I get " Ubuntu is running i low graphicsmode, your screen graphics card, and input device setting could not be detected correctly. You will need to configure these your self"

When i try to boot up i low-graphics mode ubuntu never comes past the start up screen. So the only option I got here now is to go in terminal. 

Anyone know what to do? 

-Iver

---

### Post by lidex on 2011-01-09
Is this an nvidia gpu? In the terminal input this command then reboot:
```
sudo nvidia-xconfig
```

---

### Post by ialvik on 2011-01-09
Hi.

Just reinstalled whole Ubuntu. But I keep that in min until next time :)

But thank you for helping.

Do you know anyway there would be possible to run the sound through the HDMI cabel here?

Pairing the Sound Blaster card and the graphics card or something?

---

### Post by tjones00 on 2011-01-09
From what you've posted it looks like you have a Nvidia graphics card produced by Zotac and yes it has a built in soundcard for hdmi. 

So you could run the hdmi cable from the card to a tv(or a display with built in speakers, or amp) and get both digital sound and picture.

Setting up hdmi with nvidia appears to be a pain for most people try a simple search of this forum and you'll see. 

Read a couple of the solved posts and decide if you're up for the task ;)

There are walkthroughs for most video cards somewhere in this forum.

---

### Post by ialvik on 2011-01-09
Ok, thank you guys... I'll be reading for a few hours then :D

---

### Post by efflandt on 2011-01-09
What shows for **dmesg | grep -i hda** (-i as in case insensitive) and **aplay -l** (small L)?

Assuming that looks good, NVidia appears to be card 2, so you need to figure which device on that works.  Run **alsamixer** in a terminal, F6 select the **HDA NVidia** device and unmute all the S/PDIF devices (press m to unmute any that are MM so they become 00).  Then making sure that the volume is not too low on your HDTV or whatever HDMI try the following:

```
aplay -D plughw:2,3 /usr/share/sounds/alsa/Front_Center.wav
```Or try 2,7 2,8 2,9 until you hear HDMI sound for one of them.  Add a line to /etc/pulse/default.pa after the alsa-sink line for whichever one works.

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:2,3**
```Then selecting **HDA NVidia** (without HDMI) as **Output** in **Sound Preferences** should output sound to HDMI.  If you play something in Rythmbox you should be able to switch Sound Preferences between your Soundblaster and HDA NVidia on the fly.  But I am not sure how to configure pulse or alsa to use both at the same time or surround sound (I have only done stereo).

---

### Post by ialvik on 2011-01-09
Hi

Here comes the numbers :)

> 

[B]root@S51:/etc# dmesg | grep -i hda

[   10.544082] HDA Intel 0000:02:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.544090] hda_intel: Disable MSI for Nvidia chipset
[   10.544133] HDA Intel 0000:02:00.1: setting latency timer to 64
[   30.720068] Modules linked in: nvidia(P) snd_hda_codec_nvhdmi snd_ca0106 snd_ac97_codec snd_hda_intel snd_usb_audio snd_usbmidi_lib ac97_bus snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device intel_agp joydev agpgart snd snd_page_alloc psmouse usbhid serio_raw ppdev lp parport_pc soundcore parport hid usb_storage floppy tg3
[   30.720159]  [<f837f66d>] snd_print_pcm_bits+0x5d/0x80 [snd_hda_codec]
[   30.720169]  [<f83888a7>] hdmi_show_short_audio_desc+0xf7/0x100 [snd_hda_codec]
[   30.720184]  [<f838890f>] snd_hdmi_show_eld+0x5f/0xa0 [snd_hda_codec]
[   30.720193]  [<f8388cb0>] ? snd_hdmi_get_eld+0xd0/0x100 [snd_hda_codec]
[   30.720199]  [<f8e9b64e>] hdmi_present_sense+0x5e/0x70 [snd_hda_codec_nvhdmi]
[   30.720205]  [<f8e9b74d>] hdmi_intrinsic_event+0xed/0x100 [snd_hda_codec_nvhdmi]
[   30.720210]  [<f8e9b7a6>] hdmi_unsol_event+0x46/0x80 [snd_hda_codec_nvhdmi]
[   30.720223]  [<f837f106>] process_unsol_events+0x56/0x70 [snd_hda_codec]
[   30.720237]  [<f837f0b0>] ? process_unsol_events+0x0/0x70 [snd_hda_codec]
[   44.860443] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[/B]


> 

root@S51:/etc# aplay -l

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
card 1: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




When i write: 
>  
aplay -D plughw:2,3 /usr/share/sounds/alsa/Front_Center.wav 

I get the output but no sound.

> 
root@S51:/etc# aplay -D plughw:2,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono


When I try the other commands i get 

> 
root@S51:/etc# aplay -D plughw:2,7 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:654: audio open error: No such file or directory


Thanks for trying to help, greatly appreciated!

-Iver

---

### Post by lidex on 2011-01-09
> When i write:
Quote:
aplay -D plughw:2,3 /usr/share/sounds/alsa/Front_Center.wav
I get the output but no sound.
Your hdmi is the first device, instead of 2,3 try these one-by-one:
```
0,3
0,7
0,8
0,9
```
Why are you root?

---

### Post by ialvik on 2011-01-09
Still quiet... but I get a response from all of them.. 

> 

root@S51:/etc# aplay -D plughw:2,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

root@S51:/etc# aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

root@S51:/etc# aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

root@S51:/etc# aplay -D plughw:0,8 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

root@S51:/etc# aplay -D plughw:0,9 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono



Since I reinstalled Ubuntu, and all my other stuff, I set myself as root so I didn't have to write sudo all the time.. bit lazy i guess :)

---

### Post by lidex on 2011-01-09
Make sure your hdmi device is hooked up and turned on then reboot your comp.Then use alsamixer to make sure your s/pdif or IEC958 outs are not muted.

---

### Post by ialvik on 2011-01-10
I'm starting to wonder if this has a soundcard at all. Can't make any changes on it in Alsamixer.

Its a Zotac GT218-ION it says high definition on the box. but??  

But is there no way to connect the Sound Blaster card to the HDMI. Like pairing the cards or something?

But thanks for all the help guys! I learned a lot at least :KS

- Iver

---

### Post by tjones00 on 2011-01-10
In alsa mixer the card will have no volume control it's either on or off (muted/unmuted) the receiving end is responsible for volume. This is how digital audio streams typically work.

Ah the gt218 310m ion (ion2) with discrete 512mb of ram.

This will involve a bit more work and yes there is a sound card built in you shouldn't need the soundblaster card at all. I know of no way to combine hdmi signals.

The gt218 is audio card 0 in your setup, for a zotac gt218 the hdmi audio device is most likely to be 7 so device 0,7. But you must confirm this yourself.

Many people have setup this card. It will involve learning a bit about how hdmi and audio in general is configured in ubuntu and it will involve custom modifications.

From what you've posted it appears you already have alsa 1.0.23 installed but it won't hurt to update it if there is an update for your kernel.

Start with post #8 in this thread.
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

Try to understand what each step is actually doing. Many people do not try to understand the process and just jump right  in copy and paste everything then complain when it doesn't work. 

Examples of people setting up what I think is your card.
[http://ubuntuforums.org/showthread.php?t=1659373](http://ubuntuforums.org/showthread.php?t=1659373)
[http://ubuntuforums.org/showthread.php?t=1620926](http://ubuntuforums.org/showthread.php?t=1620926)
[http://ubuntuforums.org/showthread.php?t=1651152](http://ubuntuforums.org/showthread.php?t=1651152)  <--this post involves oss and a custom kernel

---

### Post by ialvik on 2011-01-10
Thanks for taking interest :)

Been trying for a while now but still no sound. 


> 
iver@S51:~$ apt-cache search linux-backports-modules-alsa-2.6.35-24
linux-backports-modules-alsa-2.6.35-24-generic - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
linux-backports-modules-alsa-2.6.35-24-generic-pae - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
> 
iver@S51:~$ aplay -l
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
> 
iver@S51:/proc/asound/card0$ ls
codec#0  codec#2  eld#0.0  eld#2.0  id     pcm7p  pcm9p
codec#1  codec#3  eld#1.0  eld#3.0  pcm3p  pcm8p

Still can't get this one to change... would like to se som 1's and not only 0...

> 
iver@S51:/proc/asound/card0$ cat eld#0.0
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
iver@S51:/proc/asound/card0$ cat eld#1.0
monitor_present        1
eld_valid        1
monitor_name        SAMSUNG
    
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x2d4c
product_id        0x669
port_id            0x20000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x5f] FL/FR LFE FC RL/RR RC RLC/RRC
sad_count        8
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0x1ee0] 44100 48000 88200 176400 192000 384000
sad0_bits        [0xe0000] 16 20 24
sad1_coding_type    [0x1] LPCM
sad1_channels        8
sad1_rates        [0x1ee0] 44100 48000 88200 176400 192000 384000
sad1_bits        [0xe0000] 16 20 24
sad2_coding_type    [0x2] AC-3
sad2_channels        6
sad2_rates        [0xe0] 44100 48000 88200
sad2_max_bitrate    640000
sad3_coding_type    [0x7] DTS
sad3_channels        7
sad3_rates        [0x6e0] 44100 48000 88200 176400 192000
sad3_max_bitrate    1536000
sad4_coding_type    [0x9] DSD (One Bit Audio)
sad4_channels        6
sad4_rates        [0x40] 48000
sad5_coding_type    [0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad5_channels        8
sad5_rates        [0xc0] 48000 88200
sad6_coding_type    [0xc] MLP (Dolby TrueHD)
sad6_channels        8
sad6_rates        [0x1480] 88200 192000
sad7_coding_type    [0xb] DTS-HD
sad7_channels        8
sad7_rates        [0x1480] 88200 192000



Anyone have a clue whats wrong here? I can unmute them all in alsamixer now.

---

### Post by tjones00 on 2011-01-11
Nothing is wrong you've established that your hdmi connection has been recognized by the nvidia card on device 7. /proc/asound/card0/eld#1.0 corresponds to device 0,7.

The massive eld output is due to the complex setup on your tv. It appears to support 8 channels and has a whole lot of speakers.

The device you want to test now for audio is 0,7. Open alsamixer and make sure device 7 is not muted then attempt to play audio through it with aplay -D hw:0,7 /path/to/wav.file

/usr/share/sounds/alsa/ should have some wav files you can test

for example 

aplay -D hw:0,7 /usr/share/sounds/alsa/Front_Center.wav

aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav

If you hear any audio move onto the Configuring Alsa and Configuring Pulseaudio sections of that thread for the final touches.

---

### Post by ialvik on 2011-01-11
Hi.

Still no sound there, but in Alsamixer I only see 4 channels, S/PDIF, S/PDIF1, S/PDIF2,SPDIF3

> 
iver@S51:~$ aplay -D hw:0,7 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1059: Channels count non available
iver@S51:~$ aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono


---

### Post by tjones00 on 2011-01-11
S/PIDF1 is most likely responsible for 0,7 but just unmute everything for good measure. Remember MM denotes muted 00 is unmuted. f6 toggles between cards.

Do the alsa asound.conf and pulseaudio default.pa edits as in the original thread remember though your device is 0,7 when doing the edits. The examples use device 1,9.

It seems something weird is going on with pulseaudio in 10.10  didn't seem to have this issue with 10.04.

Edit: another person with the same card as you just got theirs working. You might want to refer to the last couple pages of the thread.
[http://ubuntuforums.org/showthread.php?p=10346336#post10346336](http://ubuntuforums.org/showthread.php?p=10346336#post10346336)

---

### Post by efflandt on 2011-01-12
This is an example of alsamixer when you use F6 to switch it to HDA NVidia.  Although, in this case the first one is unmuted by default, I have the last one unmuted because mine is 1,9 and the middle 2 are muted.  But initially try all of them unmuted, for example "S/PDIF 1" would need to be unmuted if yours is 0,7

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                     F1:  Help               &#9474;
&#9474; Chip: Nvidia GPU 14 HDMI/DP                          F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                        &#9474;
&#9474;                       &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;                        &#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                        &#9474;
&#9474;                    < S/PDIF >S/PDIF 1 S/PDIF 2 S/PDIF 3                      &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

---

### Post by tjones00 on 2011-01-12
Man he's so close I hope he does the final touches then his first step into linux geekdom will be complete. *sniff* *sniff* his first hack they grow up so fast.

As proved last night on the other thread there should be no problem with his card in 10.10.

---

### Post by ialvik on 2011-01-12
I just put these files out here if anyone can see something wrong..

asound.conf

> 

pcm.dmixer { 
  type dmix 
  ipc_key 2048 
  slave { 
    pcm "hw:0,7" # Always use pure hw. dmix will reformat/resample audio. 
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





> 

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hv:0,7
#load-module module-alsa-source device=hw:0,7
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
load-module module-alsa-sink device=hw:0.7
.else  
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input




Just feel to close to give up now... :confused:  all your help are greatly appreciated. :KS

---

### Post by ialvik on 2011-01-12
This one looks ok to..  

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                        F1:  Help               &#9474;
&#9474; Chip: Nvidia GPU 0b HDMI/DP                             F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                            Esc: Exit               &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                         &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                         &#9474;
&#9474;                         &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                         &#9474;
&#9474;                         &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                         &#9474;
&#9474;                      < S/PDIF >S/PDIF 1 S/PDIF 2 S/PDIF 3                       &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9474;                                                                                 &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by tjones00 on 2011-01-12
Your asound.conf looks good. Ensure it is located at /etc/asound.conf.

Your default.pa has a typo

> ### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hv:0,7

load module line should read.

load-module module-alsa-sink device=hw:0,7


For the automatic section

> ### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
load-module module-alsa-sink device=hw:0.7

You shouldn't need the 2nd entry but I guess this doesn't hurt.

---

### Post by ialvik on 2011-01-12
Still not working... Starting to think I didn't get this GIT files right or something?

---

### Post by tjones00 on 2011-01-13
Ah it just occurred to me that the asound.conf could be messed up. Is that an exact copy and paste that you've listed?

Whitespace could be the issue (the indentations) for whatever CLI is used for the asound.conf. eg. python requires proper whitespace
Replace that file with an EXACT copy and paste of the following.

```
pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:0,7" # Always use pure hw. dmix will reformat/resample audio.
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
```Also make sure there are no .asoundrc files on the system. .asoundrc will override the asound.conf

From the alsa wiki.

> Where does .asoundrc live?

The .asoundrc file is typically installed in a user's home directory ($HOME/.asoundrc) and is called from /usr/share/alsa/alsa.conf. It is also possible to install a system-wide configuration file as /etc/asound.conf. When an ALSA application starts both configuration files are read but the settings in the .asoundrc file override the settings in the /etc/asound.conf settings. The only other thing I can think of is the issue of you running as root user by default and some settings aren't being applied properly. Unfortunately I have no experience with such a setup.

If it still doesn't work at this point you could try a pulseaudio purge to just get rid of any "wack-a-mole" settings it might require. Pulseaudio isn't required for audio only alsa. It's installed ontop of alsa to act as an audio interface that allows simultaneous audio control from multiple programs to alsa. Like a big fancy mixer that is unfortunately full of bugs and doesn't seem to be as kept up to date as alsa.

Eg. with pulseaudio you can have two applications playing audio with independent volume controls, without pulseaudio you only have a single volume control for the device(the master).

You can purge pulseaudio with the following command. In your case omit the sudo. I'm using it in the example as a reference for others.

```
sudo apt-get remove --purge pulseaudio
```Then you don't  have to worry about any pulseaudio settings, default.pa, cookies or other pulseaudio settings/files.

To reinstall pulseaudio

```
sudo apt-get install pulseaudio
```

---

