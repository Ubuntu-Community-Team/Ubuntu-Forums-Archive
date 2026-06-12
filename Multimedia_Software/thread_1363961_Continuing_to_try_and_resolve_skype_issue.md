---
title: "Continuing to try and resolve skype issue"
date: 2009-12-25
forum: Multimedia Software
---

### Post by ruthy on 2009-12-25
Some one posted this as a solution, but i don't know how to go about doing it.


downgrading to previous version was indeed the only solution I found to solve my sound issues. There is however an easier way to do it through the Synaptic Package Manager:
- add "http://packages.medibuntu.org/ jaunty free non-free" to your repositories (in Settings-Repositories-Other Software)
- look for skype
- and Force version 2.0.0.72 (jaunty) (in Package-Force Version)

---

### Post by MusJet on 2009-12-25
Hi ruthy !  Are you using 9.10 ? I made one set "Pulse Audio Device chooser" (aka "padevchooser").
Here I got success with audio at skype (2.1.0.47-0medibuntu2) but getting problems with my webcam pleomax
(Bus 004 Device 003: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 Webcam). 
The image is slow and up side down. Its hell !!
Others ubuntu versions (8.10 and 9.04) was working pretty nice.
I have modules loaded like show "lsmod".
I need help also !!  :)

See you,
  Musjet

sudo lsmod
Module                  Size  Used by
snd_opl3_synth         11616  0
snd_seq_midi_emul       6332  1 snd_opl3_synth
binfmt_misc             8356  1
ppdev                   6688  0
snd_usb_audio          84224  1
snd_usb_lib            16284  1 snd_usb_audio
iptable_filter          3100  0
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_cmipci             33408  2
gameport               11368  1 snd_cmipci
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_usb_audio,snd_cmipci,snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_opl3_lib           10396  2 snd_opl3_synth,snd_cmipci
snd_hwdep               7200  2 snd_usb_audio,snd_opl3_lib
snd_mpu401_uart         6940  1 snd_cmipci
snd_seq_dummy           2656  0
gspca_zc3xx            47580  0
gspca_main             22812  1 gspca_zc3xx
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  8 snd_opl3_synth,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          6920  7 snd_opl3_synth,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  20 snd_opl3_synth,snd_usb_audio,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
lp                      8964  0
nvidia               9586440  26
parport                35340  2 ppdev,lp
dm_raid45              84228  0
xor                    15620  1 dm_raid45
usbhid                 38208  0
r8169                  32064  0
mii                     5212  1 r8169
intel_agp              27484  0
agpgart                34988  2 nvidia,intel_agp

EDIT: [https://lists.openwrt.org/pipermail/openwrt-devel/2009-August/004905.html](https://lists.openwrt.org/pipermail/openwrt-devel/2009-August/004905.html)

---

### Post by ruthy on 2009-12-28
Hi musjet
I'm running the latest version of Ubuntu and the latest version of skype, the one which wont detect a USB phone for some reason. I also have a microphone and some head phones. I can hear skype, but for some reason the microphone won't work with it.

---

### Post by Chronon on 2009-12-28
ruthy, have you used padevchooser to configure the sound sources for pulse?  It seems that sometimes sound sources get muted by default.  It may be that your microphone works but is muted.  Just a thought. . .

---

### Post by Jimtheplanner on 2009-12-28
Hi ruthy,

I had a similar issue with sound....

First off as we all use different hardware there is not one solution to fix everything - it can be a bit trial and error.

First off I use a Philips webcam (this is because a skype developer was photgraphed once doing some work & he used a Philips). Also is you look around Philips does not have the same issues as Logitech etc

I use Skype from Skype themselves - medibuntu has discontinued its support because it can be got from Skype directly. There's info on launchpad to this effect. 

Then I would open sounds - easiest way is to right click on the sound control top right & open the control panel. Tab along to the input screen. Then open from terminal alsamixer. Set them on the screen so can see both in operation.

I found that when I tabbed along alsamixer to the "digital" control then changed it to "Analog 1" my microphone started recording in the sound control panel. Once this worked I opened skype & the sound worked....

This worked for me.... I'm doing this from memory as I'm using Mandriva at the minute. Please ask if you need more detail.

Jim

---

### Post by ruthy on 2009-12-28
In sound preferences i found an adjustable input volume bar. This was set set just under the &#8220;unamplified&#8221; marker. I put this to maximum and now i can make a recording with the skype test call. The sound, both what the other person can hear and what i can hear, seems to fluctuate allot. Sometimes it sounds fine then in a few seconds latter i can barely here them or they can barely hear me. And allot of the time the sound has a faded quality; sort of like talking into a mug or a bowl.

---

### Post by ruthy on 2009-12-28
What I've done now is change (in sound preferences) from microphone 1 to microphone 2; i didn't think i had two microphones. And this seems to have helped the problem mentioned in the above, previous post. There is still background noise sort of like a humming. Do any of you get that, is there a way to get rid of it?

---

### Post by Chronon on 2009-12-28
Have you allowed Skype to adjust your mic levels?  This can cause fluctuations in the throughput sometimes.  

*(Nevermind.  On a second read, I see that the problem also occurs for audio transmitted to you.)*

---

### Post by Jimtheplanner on 2009-12-29
I'm pleased that you got it working ruthy. Skype can be dependant upon your connection and the time of day you use it...

I find that around peak times when everyone uses the net the skype quality can suffer.

Jim

---

### Post by ruthy on 2009-12-30
Am afraid its just not working to well. On my end its OK, but the other person says that the sound is only half as good as it is when I'm speaking on the USB phone in windows.

[QUOTE=Chronon;8572436]Have you allowed Skype to adjust your mic levels?  

I take it you mean the tick box in sound devices that says &#8220;allow skype to automatically adjust mixer levels&#8221;?

---

### Post by ruthy on 2009-12-30
it seems to be fine now, all of the sudden. But i'll keep you updated.
:)

---

### Post by ruthy on 2009-12-31
Thanks for helping me get this sorted. And it seems to be better not to let skype adjust your mic levels, as it seems to lower them to the point that the other person can't here me speak.

Have a very happy new year.

---

