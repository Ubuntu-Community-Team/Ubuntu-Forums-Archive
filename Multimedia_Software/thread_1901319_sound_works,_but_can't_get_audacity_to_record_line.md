---
title: "sound works, but can't get audacity to record line in"
date: 2011-12-28
forum: Multimedia Software
---

### Post by jonathanstratford on 2011-12-28
Hi,

I've got a pretty clean install of Lubuntu 11.10 (installed this morning), which I'm trying to record cassette tapes with. The reason for using Lubuntu is that it's a very old machine with only 384MB RAM I think (but Lubuntu runs very well on it). So far, I have installed audacity and used alsamixer to unmute the line-in. From that point, I could hear my cassette playing through the line in and out of the speakers. 

Alsamixer has these details about my sound card (in case it's of use):

Card: Sound Fusion CS46xx                                                                          Chip: Cirrus Logic CS4297A rev 3

So in alsamixer I unmuted and increased the volume on the line in, and did the same on everything I could see (except "3D Control" which seemed to increase the hiss, so I remuted that -- no idea where that comes from, since the card only has line out, microphone and speaker sockets!). I then switched to the Capture page and set Line to Capture (there's no volume control on that though), and set Capture itself to Capture and increased the volume on that.

In Audacity, I can choose various inputs either prefixed with default: or Sound Fusion CS46xx:, but no matter which option I try, monitoring the input doesn't give any signals at all, and indeed if I try to record from each source it doesn't get any signal either. I read somewhere that there should be alsa: prefixed on some of the inputs, but I've noticed that there isn't in my case -- I don't know if that's a problem or what I was reading was out of date. In Audacity, I have ALSA as the playback device (the only option in that drop-down), with default in the next one (these relate to playback so I assume are irrelevant at this point).

Is there anything I can try to get audacity to capture the audio? I feel I'm tantalisingly close, but that hasn't changed all day! Sorry if I've missed any useful details -- I'm not sure what would help, but I don't mind providing any other information. If I need to run any commands/provide output that's fine too.

Oh -- I tried installing pulse audio which although it got as far as telling me that audacity was indeed trying to record from the line in, it made the computer run very slowly and didn't actually help audacity record from the line in, so I removed this, by naming all the packages apt-get had told me it needed to install for it and purging them, so I'm hopefully back to using ALSA.

Thanks!
Jonathan

---

### Post by Rodney9 on 2011-12-28
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by jonathanstratford on 2011-12-28
Thanks for the quick response. Sorry for wasting your time; I had already found those pages although I don't believe they help/apply to my case. I'll put some notes here in case I did anything wrong, or they help anyone later!

I looked at the troubleshooting procedure and previously hadn't tried it partly because it gives commands for when running Ubuntu (I'm running Lubuntu), and partly because it just seems to be resolving the problem of when sound doesn't work at all (mine plays fine, just won't record). A quick glance at the command in step 1 seemed to involve pulse which I know I've not got installed, but after your suggestion I gave it another look and it's actually stopping any pulse instances so that makes more sense. So I tried running it, and it initially wanted to download 90MB, including LibreOffice! This seemed a bit unnecessary, so I modified the commands to refer to lubuntu-desktop instead of ubuntu-desktop. Then it only had an issue when it came to installing gdm as it wanted to know which desktop env I wanted to use (I stuck with lxdm). Anyway, I let the command finish and then rebooted. Audacity still wouldn't record the audio that's playing happily, so I purged the additional packages again (gdm gave a warning about gdm's group being empty, but I guess I can ignore this). I believe I can ignore the rest of that guide because it seems to be getting audio to play. Please let me know if I have misunderstood.

I then moved onto the Sound Troubleshooting Guide, and my sound card was recognised in the first step, so I followed step Ac. This assured me that the computer and alsa all agreed on which card exists and is active. Not being directed anywhere else, I then tried Ad. This strangely gave me 3 options, card 0 with devices 0, 1 and 2. Device 1 claimed to be the Rear one (I only have visible ports on the back), so I tried that first, rebooted. It still wouldn't record, so I tried the other two with reboots and had the same result, the only difference being that audacity no longer listed the "default" versions of the input sources when using device 2. I'm not sure if I was supposed to try this step anyway (step Ac completed successfully, and it didn't say where to go after that). I've tried to look for additional drivers (although mine's not an NVIDIA) just in case, but nothing came up. The rest seems to be getting more drastic, and I think it all relates to sound not working at all (again, please tell me if I'm wrong), so I don't wish to carry on that route (recompiling the kernel seems somewhat excessive just to get Audacity to work!). The command for reinstalling ALSA safely (procedure Af) did not execute correctly; the command archdetect does not exist nor could I install it using apt-get, and I didn't know what the command outputs well enough to know if I could just replace it with "arch" -- the script contains big warnings so I'm a bit scared of changing it!

Can anyone advise me on whether this is likely to be an alsa problem (the guides seem to assume it is, but I'm inclined to say it isn't), or an audacity problem? I rather suspect it's actually something I'm doing wrong, although I've no idea what.

Thanks for the link to the Lubuntu One Stop Thread -- I didn't see anything specifically that would help with my issue, but I guess I could post a link to this thread there, in case anyone there could help? I don't want to annoy people by posting in lots of places. :| You seem a very helpful group, and I'm grateful for any help I can get (I'm trying to set this machine up for my dad), and hopefully one day I'll be able to help too!

Thanks!
Jonathan

---

### Post by shantiq on 2011-12-29
[**help here **]("http://ubuntuforums.org/showthread.php?t=1705651")



also 2 others routes with SoX as Audacity is really cool as sound editor in Ubuntu but can be a royal pain in the rear for recording

[**&#9658;&#9658;&#9658;1**]("http://ubuntuforums.org/showthread.php?t=1805550") 

 [**&#9658;&#9658;&#9658;2**]("http://ubuntuforums.org/showthread.php?t=1704350")

---

### Post by jonathanstratford on 2011-12-29
curiouser and curiouser...

Thanks for this. I had in fact already seen the need to unmute the line in, and as far as I can tell I have changed all the devices correctly.

However, using the suggestions in your other links of using that rec command or ffmpeg command also gives an empty sound file (importing into audacity reveals it has a duration but nothing off flatline). Commands used were:

rec -b 32 -r 44100 Desktop/sound.wav gain +10

ffmpeg -f alsa -ac 2 -i hw:0,0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y ./Desktop/sound.wav

note I used man ffmpeg to find that for alsa -i hw:x,y should be used, and changing y to 1 or 2 (as mentioned previously it said I have 3 devices on the one card) resulting in ffmpeg saying it couldn't open the device (no such file or directory), and x to 1 with y as 0 also giving this error.

I tried this with both mix and line as the capture device in alsamixer, with only flatline sound file as the result.

I installed pulse etc to follow the pavucontrol steps for the rec command but no joy either. Also, in all cases, the rec command seemed to indicate input at 0%, which I took to mean it wasn't getting a signal.

This suggests to me that the problem is not with audacity (necessarily), but before then. Is there anything else I can try, or info I can provide? To re-state where I am, sound from the line in is coming out of my computer speakers fine, but there seems to be either some problem with how I've set up the capture device, or...I don't know what. alsamixer has Line set as the capture device, and Capture also selected for capture (just tried with this unset, same result), with the volume set to maximum.

Am I missing something obvious? :| Thanks!

---

### Post by shantiq on 2011-12-30
hi again jonathan


you may have already ( you say you have ) but did you follow this (only reason i can think of here; try this carefully again mayhaps)?  it seems you are NOT on the MONITOR SETTING hence no sound on your recorded file 


5. On pavucontrol click on recording then pick "Monitor of internal audio stereo " ( or if using an external card "Monitor of whatever your external card is called") [see image]("http://ubuntuforums.org/attachment.php?attachmentid=198517&d=1311705305")  YOU NEED TO START A RECORDING TO BE ABLE TO ACCESS THE CHOICES so enter > rec -b 32 -r 44100 Desktop/sound.wav gain +10
 in your terminal then change your setting to monitor....

6. Stop recording and start again now you have the correct sound monitoring

7. At the end make sure to return pavucontrol to original setting of "internal audio stereo"


and monitor your pavucontrol during recording phase to see your sound being recorded

Best of luck   should be fine this way...

see attached

---

### Post by lidex on 2011-12-31
Can you post your amixer settings please:
```
amixer
```

---

### Post by jonathanstratford on 2012-01-01
Apologies for the silence over the last couple of days. Shantiq, I believe I did that, but shall try again just to be sure. It definitely has the dot showing the selection next to Monitor of Internal Audio Analogue Stereo, and the only other option is Internal Audio Analogue Stereo. Unfortunately I have nowhere to upload a screenshot to. rec still reports the following (note I'm using flac this time to more precisely follow the instructions) -- am I correct in thinking the "In: 0%" on the last line means there's no signal getting to it?

```

$ rec Desktop/sound.flac

Input File     : 'default' (alsa)
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Sample Encoding: 16-bit Signed Integer PCM

In:0.00% 00:00:13.40 [00:00:00.00] Out:639k  [      |      ]        Clip:0    ^C

```

Just for good measure, this is the output from the wav command I used before:

```
$ rec -b 32 -r 192000 Desktop/sound.wav gain +10
Input File     : 'default' (alsa)
Channels       : 2
Sample Rate    : 192000
Precision      : 32-bit
Sample Encoding: 32-bit Signed Integer PCM

In:0.00% 00:00:06.40 [00:00:00.00] Out:1.22M [      |      ]        Clip:0    ^C

```

Both created files contain silence according to audacity.

amixer output:

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [on]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Input',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mic'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 13 [87%] [19.50dB] [on]
  Front Right: Capture 13 [87%] [19.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'ADC',0
  Capabilities: volume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 0 [0%] Capture [off]
  Front Right: 0 [0%] Capture [off]
Simple mixer control 'DAC',0
  Capabilities: volume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 0 [0%] Capture [off]
  Front Right: 0 [0%] Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

Unfortunately apart from seeing that line and master are set to 100%, that output doesn't mean much to me -- does it say what was needed?

Thanks a lot,
Jonathan

---

### Post by lidex on 2012-01-01
OK, never mind that.

So sound comes in and can be heard, just not captured with audacity, correct?
Maybe capture wants to use PCM, which you have muted.

---

### Post by jonathanstratford on 2012-01-18
Sorry for the slow reply -- unfortunately I'm now 100 miles away from the computer in question so it's harder to try things. I did try talking someone there through checking the last suggestion, as far as we could tell PCM wasn't muted (it only appears on the playback page of alsamixer).

However, yes that is correct that sound comes out of the speakers (unless I mute line in) but can't be captured.

Thanks for all your help; I suspect there's no way to solve this though!

Jonathan

---

