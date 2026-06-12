---
title: "Can Mythtv databse change speaker channel routing?"
date: 2011-09-07
forum: Mythbuntu
---

### Post by larsolav on 2011-09-07
I am trying to overcome an issue with audio over HDMI sending the center audio to the left rear speaker and the left rear audio to center speaker: 
[http://ubuntuforums.org/showthread.php?t=1696331](http://ubuntuforums.org/showthread.php?t=1696331)
Figuring I would try a new install, I backed up the Mythtv database (Mythbuntu 10.10 running 0.24.1), installed Mythbuntu 11.04 and 0.24.1, and updated everything. Before restoring the database I played a video in VLC that plays the 6 channel audio separately. Everything was fine. Then I restored the old database (using a command line previously suggested by tgm4883 as the Myth Control Center restore did not work)  and the audio was being misdirected again! 

Is there something in the Myth database that can actually cause this, or am I just being crazy? (I know that both options may be true...) Is there a way to flip the two audio channels back again?

---

### Post by BicyclerBoy on 2011-09-09
To your original question. No idea but anything is possible.

Having read back thru' your old post..

It is possible that the correct channel mapping only occurred when digital pass-thru' was working. (AC3/DTS 2.0 or 5.1).

There is a difference between multi-channel LPCM over HDMI & digital pass-thru' over HDMI. One is raw PCM streams & the other is matrix encoded.

The confusing factor is that MythTV can now up-mix to AC3..but there have been multiple channel mapping bugs in ffmpeg ac3encoder.
I'm think it is likely MythTV is patched for ffmpeg bugs.

When you output 6 channel LPCM over HDMI it is possible the incorrect HDMI codecs setup maps the channels incorrectly.

The database/mythsetup could change the speaker routing if:
- you choose 5.1 up-mix ( uses ffmpeg ac3encoder)
- your soundcard definitions (channel mapping is wrong) 

The master reference for checking channel mapping:
[http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3](http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3)
I would only trust native media AC3 audio output for decode in HT amp.
Use VLC to test..
*vlc* --*aout alsa* --*alsa*-audio-device *iec958*
may have to craft the iec958 part to point to the HDMI iec958 (if this exists)

I would test MythTV with output playing the same file without 5.1 up-mix (but with direct output).
Then test MythTV with 5.1 up-mix enabled..

Can you post 
aplay -l
Are you using a mobo chipset graphics HDMI output ?
nVidia ?

---

### Post by larsolav on 2011-09-09
> **BicyclerBoy said:**
> To your original question. No idea but anything is possible.

Having read back thru' your old post..

It is possible that the correct channel mapping only occurred when digital pass-thru' was working. (AC3/DTS 2.0 or 5.1).

There is a difference between multi-channel LPCM over HDMI & digital pass-thru' over HDMI. One is raw PCM streams & the other is matrix encoded.

The confusing factor is that MythTV can now up-mix to AC3..but there have been multiple channel mapping bugs in ffmpeg ac3encoder.
I'm think it is likely MythTV is patched for ffmpeg bugs.

When you output 6 channel LPCM over HDMI it is possible the incorrect HDMI codecs setup maps the channels incorrectly.

The database/mythsetup could change the speaker routing if:
- you choose 5.1 up-mix ( uses ffmpeg ac3encoder)
- your soundcard definitions (channel mapping is wrong) 

The master reference for checking channel mapping:
[http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3](http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3)
I would only trust native media AC3 audio output for decode in HT amp.
Use VLC to test..
*vlc* --*aout alsa* --*alsa*-audio-device *iec958*
may have to craft the iec958 part to point to the HDMI iec958 (if this exists)

I would test MythTV with output playing the same file without 5.1 up-mix (but with direct output).
Then test MythTV with 5.1 up-mix enabled..

Can you post 
aplay -l
Are you using a mobo chipset graphics HDMI output ?
nVidia ?

Thank you BicyclerBoy for the detailed explanations!
Goood idea to try VLC again. I tried with the audio file you linked to and an AVI called Test_AC3.avi I had downloaded before. Both worked like a charm when played in VLC!

I then tried the avi file in MythTV under various settings under Setup->Setup->General->Audio System:
I scanned for audio devices, use ALSA:hdmi:CARD:NVidia,DEV=0
Check mark both Dolby Digital and DTS
Speaker config: 5.1
Unchecked stereo to 5.1 (also tried with this checked)
When being played by Mythtv the sound is weird. But VLC is OK...

All my recordings are OTA digital (US) and the center audio seems to come in the left rear speaker when played using Myth TV.

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

The mobo has Nvidia built in (EVGA 730i Motherboard with Integrated GeForce 9300 GPU), running NVIDIA accelerated driver, current version.

Any light you may shed is deeply appreciated!

Thanks!

---

### Post by larsolav on 2011-09-09
I also selected "ALSA:hw:CARD=NVidia,DEV=3"
I get sound, but the audio channels are still mixed up....

---

### Post by BicyclerBoy on 2011-09-10
Are you sure that with "upconvert stereo..." **unticked** you have mixed up channels ?
Set speaker config to stereo & try...

Your h/w setup allows (2) different paths for 5.1 output: AC3 digital pass-thru' & HDMI 6 ch LPCM.
So the MythTV audio config is a bit more complicated. Fairly sure the AC3 mapping is correct..

Reading the nVidia HDMI audio guide...
Your nVidia graphics HDA codec is the MCP7A like the ION.
It's multi-channel output is an aggregated collection of 2 channel DACs.
2x4 =8 channel support, single stream.

The MCP7A does not support audio ELD.
So because of that we do not know the audio capabilities of the receiver.

Can check with 
speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 6 -r 48000 -D hw:0,3
speaker-test -c 8 -r 48000 -D hw:0,3
you should close/re-open the terminal between each of the above cmds.

speaker-test can not check digital pass-thru' but we know this works from VLC AC3..

Your receiver may not support multi-ch LPCM..

MythTV:
Try for AC3 DTS digital pass-thru' S/PDIF
Do you have under audio setup: an audio setup button "Advanced audio settings" ?
You should tick the "Separate digital audio output device" & pick from the drop down list anything with iec958.
The other 48KHz options do not normally need to be ticked. Althou' AC3 & DTS must be 48KHz.
With the "upconvert stereo to 5.1"**unticked**, you should get stereo 2 ch PCM for all except AC3 or DTS audio playback..
Your config is complicated by the fact your audio h/w can (possibly) support 6/8 ch LPCM over HDMI.

I'll do some AC3 encoder expts with  Myth0.24+fixes  tomorrow..

Done some tests..
1. AC3 file playback lynne_music AC3 testtrack..
- I think this files LFE audio is missing. 
- Can't trust VLC because it decodes & then re-encodes
- MythTV can 't play it to compare..

2. test track** idch_AviaSurroundTest-AAC.mkv**
- VLC can't play multi-ch AAC (1.0.6)
- MythTV plays correctly with upconvert to AC3

3. MythTV 0.24+fixes speaker tests
- correct with upconvert to AC3

4. Direct AC3 ch mapping via THX & other DVD audio setup tests
- MythTV plays video at 6x speed & audio is out of sync & stop/start. Useless.
random pause keystrokes indicate correct mapping. 
 
I cannot test multi-channel LPCM over HDMI directly (no h/w) or indirectly because I have broken the alsa AC3 encoder a52 plugin & its mapping can not be trusted in any case.

Real shame that speaker-test does not support playback of AC3 test file over iec958.
Any transcode/conversion to media file to allow playback exposes the test track to corrupt s/w.

Conclude: (MythTV 0.24+fixes JYA 20110722.51xxx)
Very difficult to be sure of any basic facts.
MythTV's internal speaker-test works correctly (with AC3 upconvert).
MythTV **upconvert to AC3** pass thru' over S/PDIF sounds correct.
MythTV channel mapping to AC3 encoder is correct.
Multi-channel LPCM untested.

---

### Post by larsolav on 2011-09-10
Thank you so much for all your help! It is truly appreciated! 
I think I may have a problem that is not Myth specific, because when I ran
```
speaker-test -c 6 -r 48000 -D hw:0,3
```
I got the following results
 0 - Front Left: OK
 4 - Center: Played Rear Left
 1 - Front Right: OK
 3 - Rear Right: played LFE
 2 - Rear Left: Played Center
 5 - LFE: Played Rear Right

---

### Post by BicyclerBoy on 2011-09-10
Not a new problem either..
[http://mailman.alsa-project.org/pipermail/alsa-devel/2010-August/031191.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2010-August/031191.html)

Even the nVidia 'master' gets involved..

Note this only effects multi-channel LPCM..
If you use AC3 pass-thru' & MythTV's AC3 encoder this will not matter.

If you want to fix the 6 ch LPCM then it should be easy to re-route in the alsa file..
/etc/asound.conf
```

pcm.reorder {
         slave.pcm hw:0,3
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.3 1
         ttable.2.2 1
         ttable.3.5 1
         ttable.4.1 1
         ttable.5.4 1
}

```Try
speaker-test -c **6** -r 48000 -D reorder

I do not understand the alsa nomenclature, so the above is a best guess. It may require some crafting & the order correcting..
I use the ttable route function to fix the alsa a52 plugin.

---

### Post by larsolav on 2011-09-17
Hi again!And thanks for doing all this stuff to help. So much appreciated!
Finally had some time to try out the fix, but this is what I got after creating the asound.conf file:
> x:~$ speaker-test -c 6 -r 48000 -D hw:0,3

speaker-test 1.0.24.2

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib conf.c:1685: (snd_config_load1) _toplevel_:12:0:Unexpected char
ALSA lib conf.c:3467: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3326: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3713: (snd_config_update_r) hooks failed, removing configuration
Playback open error: -22,Invalid argument


I also tried the reorder command:
with the new asound.conf file:
> ox:~$ speaker-test -c -r 48000 -D reorder

speaker-test 1.0.24.2

Playback device is reorder
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib conf.c:1685: (snd_config_load1) _toplevel_:12:0:Unexpected char
ALSA lib conf.c:3467: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3326: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3713 : (snd_config_update_r) hooks failed, removing configuration
Playback open error: -22,Invalid argument


after deleting the asound.conf file:
> x:~$ speaker-test -c -r 48000 -D reorder

speaker-test 1.0.24.2

Playback device is reorder
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM reorder
Playback open error: -2,No such file or directory



I have no idea what to do to now.... It would be great if I could figure out how to just re-route the audio to the correct channels like VLC does....

Thanks a again for all the help!

---

### Post by BicyclerBoy on 2011-09-17
I'm surprised you did not have an /etc/asound.conf file already..
I'm not so surprised my quick hack failed miserably..

The re-routing was a guess at the bare minimum ripped out of my asound.conf file..

You had copied my typo in the speaker-test -D reorder command..
speaker-test -c **6** -r 48000 -D reorder


VLC only gets the channel order correct because it is using AC3 pass-thru'.

MythTV (0.24+fixes JYA) can do the same thing, you just need to find the right audio device (hdmi:iec958) & set upconvert to 5.1.

I think your MythTV audio is not encoding to AC3 because it is too clever & instead using multi-channel LPCM.

---

