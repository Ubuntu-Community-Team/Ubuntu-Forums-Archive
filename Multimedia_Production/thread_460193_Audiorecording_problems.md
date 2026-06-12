---
title: "Audio/recording problems"
date: 2007-05-31
forum: Multimedia Production
---

### Post by jamis on 2007-05-31
Hello, I'm completely new to Ubuntu and overall really like it for all purposes other than one: I'm a musician and can't record anything at a halfway decent quality.  I've searched this forum for possible solutions for the past 2 months to no avail.

I've looked into every possible issue I can think of: Alsa, jack, hda-intel, etc.  When I try to record (on Ubuntu Studio or any other distro) I get the same thing, a slow unbearably scratchy sound quality whenever I use jack in ardour or whatever else.  The same goes for when I try to record more than one track (plugging my guitar directly into the mic input) through Audacity (and Audacitybeta); it is slow and scratchy, impossible to use.  The best I can do is a single track on Audacity plugged into the mic input; but I can't do any playthrough without the aforementioned problems, whether it's two tracks at once or listening to the track as it records.  So as far as I know I can only record with one track Audacity (using OSS only, will not work with Alsa).

So I've also tried to use my FireWire Solo which is supposed to be compatible but I get nothing.  No luck following any howto's or forum posts, or anywhere else online (i.e., Alsa, jack and/or freebob websites).

I'm not sure what information will be most useful to you but I'm on a Dell Inspiron 6400.  Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832

aplay -l output:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards output:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 19

lsmod | grep snd output:
snd_rtctimer            4768  1 
snd_hda_intel         244632  1 
snd_pcm_oss            44672  0 
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  5 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  12 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

amixer output:
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 195 [76%] [-12.00dB]
  Front Right: Playback 195 [76%] [-12.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 11 [73%] [16.50dB] [on]
  Front Right: Capture 11 [73%] [16.50dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 3 [75%] [30.00dB]
  Front Right: 3 [75%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic'
  Item0: 'Mic'

If you need any more information I will gladly supply it.  I've been very patient on trying to fix this problem but I'm not much of a computer expert or programmer.  I know my computer and hardware works under windows and it looks like I will have to dual boot it again, though that's the last thing I want to do.  Proprietary programs like protools work well with no problems with what I have, but I can't afford that being a graduate student totally in debt.

Please help if you can, or point me in the right direction.

Thanks in advance.

---

### Post by Bungo Pony on 2007-05-31
I've also had the scratchy sound problems with Jack. It's unfortunate because I'd love to switch my studio over to Linux. But with this problem, it's not happening until things get ironed out.

If you want to try something somewhat decent for windows, download the lite version of Multitrack Studio. Even with the lite version, it's quite functional. I've been using it long before I started using Linux, and I'm still using it until Jack starts to work for me.

---

### Post by euchrid on 2007-06-07
Don't know if the problem is related, but I couldn't record sound at all. Seems like it was a problem with the Alsa driver. I updated it, and everything's fine now.

Instructions and further information here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Let me know if it's useful!

---

### Post by dabl on 2007-06-07
I have the same Intel HDA sound system on my Intel motherboard as jamis.  I've been capturing old 78 rpm record albums (and they are REALLY "albums"!) using Audacity and then Gnome Wave Cleaner "gwc" to de-click and denoise.

I use Ubuntu 64-bit low-latency kernel for the OS to do this work with. Neither Audacity nor the gnome mixer is the most forgiving app I've ever worked with, but I have beat them pretty much into doing what I want.  I have to shut down Firefox before running Audacity -- it apparently grabs the HDA system, leaving Audacity with no output device.  I run it as ALSA, both input and output.  I capture at 48000 Hz.  I can capture mono from the 78s, or stereo from 33s, and it does a great job.  Audacity has several annoying habits, including keeping the file name on the active window after you close a track, and it still keeps it when you record a new track, so if you're not careful and click "save project" instead of "save project as", you will overwrite your previous track.  Since gwc won't work with anything other than 16-bit wav files, I can't take advantage of the 32-bit export capability in Audacity, but you should be able to make excellent high quality sound files if you don't need the 16-bit limit.  I will check my aplay and alsa outputs tonight and compare them, to see if there's any explanation for the problem you're seeing.  :)

---

### Post by dabl on 2007-06-07
> lsmod | grep snd
snd_hda_intel          24480  4 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            50176  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                93960  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            37248  0 
snd_seq_midi           11008  0 
snd_rawmidi            30336  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                62752  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27656  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69800  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11040  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm

and
> 
amixer
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 192 [75%] [-12.60dB]
  Front Right: Playback 192 [75%] [-12.60dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 109 [86%] [-13.50dB] [on]
  Front Right: Playback 109 [86%] [-13.50dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 112 [88%] [-11.25dB] [off]
  Front Right: Playback 112 [88%] [-11.25dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 120 [94%] [-5.25dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Line In as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 3 [21%] [4.50dB] [on]
  Front Right: Capture 3 [21%] [4.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Line'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

I'll attach a screenshot of the little ALSA mixer control settings for "recording", just in case it reveals anything.

Hope this helps.  :)

---

### Post by jamis on 2007-06-09
> **euchrid said:**
> Don't know if the problem is related, but I couldn't record sound at all. Seems like it was a problem with the Alsa driver. I updated it, and everything's fine now.

Instructions and further information here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Let me know if it's useful!

Thanks.  I gave this a try and still have the same issues unfortunately.  Still at a loss.

---

### Post by nalmeth on 2007-06-09
What are your jack settings, and are you getting a lot of xruns? You can see this in qjackctl.

Scratchy skippy audio, that sounds like xruns

---

### Post by jamis on 2007-06-09
> **dabl said:**
> and


I'll attach a screenshot of the little ALSA mixer control settings for "recording", just in case it reveals anything.

Hope this helps.  :)

My Alsa mixer only shows "capture" under the recording tab, and has "capture mux" under the playback tab.  Also only have choice of "mic" input source, no "line in" choice.  

I can record single track audio in Audacity, but it's impossible to record multiple tracks (which is what I am trying to do).  Using playthrough (playing the first recorded track and listening to the newly recorded track, while playing it live, at the same time) results in complete interference, with slow scratchy playback.  It's like the system is overloaded or something, like it can't handle both at the same time.  

Honestly, what I was hoping to do was to use the new Ardour under Ubuntu Studio, but I get a similar type of interference/problems, when trying to record on a single track (much less multiple), using jack.  Also, it's the same when I try to play live on ubuntu studio using jack with creox (the guitar effects processor).  A very similar "overloaded" sound results, like my system can't handle it, which I know it can because I can do everything in windows.

Thanks for the help.  Still want to solve this.  Cheers.

---

### Post by jamis on 2007-06-09
> **nalmeth said:**
> What are your jack settings, and are you getting a lot of xruns? You can see this in qjackctl.

Scratchy skippy audio, that sounds like xruns

Yes, I get continuous xruns.  I will attach a screenshot of my current Jack settings, though I've tried many different ones.  Cheers.

---

### Post by nalmeth on 2007-06-09
I think you can safely raise the latency, you have it fairly low, and since ubuntu's stock kernel (and even the "low-latency" kernel) doesn't properly support real-time preemption, you are going to run into alot of xruns trying to maintain such a low-latency.

Bump up the frames per period to start, you may not like this setting, but try it to see if we can help your performance.

I've attached a screenshot of my current settings in ubuntu, and I'm getting decent quality recordings, no xruns. Tho I have a different system than you.

Remember that onboard devices are generally poor for audio recording, a lot of the higher end cards actually take care of latency themselves, but for now we can try to work with your current hardware.

If this doesn't help much, or you don't like the result, there are other options to pursue

EDIT: I noticed you have a firewire device, I recommend starting a new thread to help get that setup. I will help if I can

---

### Post by jamis on 2007-06-10
> **nalmeth said:**
> I think you can safely raise the latency, you have it fairly low, and since ubuntu's stock kernel (and even the "low-latency" kernel) doesn't properly support real-time preemption, you are going to run into alot of xruns trying to maintain such a low-latency.

Bump up the frames per period to start, you may not like this setting, but try it to see if we can help your performance.

I've attached a screenshot of my current settings in ubuntu, and I'm getting decent quality recordings, no xruns. Tho I have a different system than you.

Remember that onboard devices are generally poor for audio recording, a lot of the higher end cards actually take care of latency themselves, but for now we can try to work with your current hardware.

If this doesn't help much, or you don't like the result, there are other options to pursue

EDIT: I noticed you have a firewire device, I recommend starting a new thread to help get that setup. I will help if I can

Thanks alot.  Tweaking the settings, particularly the frames per period, did help with the xruns, though obviously with more latency issues (but at tolerable levels).  But it's a start and I'm finally getting some performance.  You're right about the onboard sound devices being far from ideal.  The integrated hda-intel which I have seems to be extra problematic from what I've found searching the forums.

But I will definitely start a new thread regarding getting my M-Audio FireWire Solo up and working, which it should be compatible.  That's the ultimate goal for me obviously.  So I'll get that started and work with it from there.  Thanks for the help.

---

