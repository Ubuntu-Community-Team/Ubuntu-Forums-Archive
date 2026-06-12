---
title: "ffmpeg screencast sound issues (only mic input being recorded)"
date: 2013-03-07
forum: Multimedia Software
---

### Post by mgompert on 2013-03-07
So, I am trying to jump on the lets play bandwagon
I use this code to record videos
ffmpeg -f alsa -i hw:0 -f x11grab -r 25 -s 1600x900 -minrate 512k -i :0.0 -sameq output.mkv

it works great records the mic input well and that is fine the audio drifts a bit but no big deal, well I noticed it was not recording the speaker audio. so I am making videos of me playing with no game audio, which takes a lot out of the video(I hear some thing in game and the viewers cannot)

so I googled aroudn and found this

ffmpeg -f alsa -ac 2 -ab 192k -i pulse -f x11grab -s $(xwininfo -root | awk '/geometry/ {print $2}') -r 30 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 /home/user/capturedvideo.avi

that gives me this error
Unrecognized option 'preset'

so I start removing parts that are throwing errors(why do I need them if the top shorter code records right?)
I get down to this code

ffmpeg -f alsa -ac 2 -ab 192k -i pulse -f x11grab -s $(xwininfo -root | awk '/geometry/ {print $2}') -r 30 -i :0.0 -acodec pcm_s16le -vcodec capturedvideo.avi

which then it tells me(here is every thing it says when I paste the code in

ffmpeg version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0xa9fa80] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0xa9fa80] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1362715859.029417, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0xaa1b40] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1600 height: 900
[x11grab @ 0xaa1b40] shared memory extension  found
[x11grab @ 0xaa1b40] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1362715859.073517, bitrate: 1382400 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1600x900, 1382400 kb/s, 30 tbr, 1000k tbn, 30 tbc
At least one output file must be specified

so I figure what I need is the pulse part of the code and I try a bit of mix and match
I make this up

ffmpeg -f alsa -ac 2 -ab 192k -i pulse -f x11grab -r 25 -s 1600x900 -minrate 512k -i :0.0 -sameq bothaudiosourcestest.mkv

now this records but only the mic audio and super scratchy.
if I open the pulseaudio volume control and go to recording devices while ffmpeg is runnign I can switch between the mic input and the monitor of the audio out but I cannot record both at once

when I try
ffmpeg -f alsa -i hw:0 -ac 2 -ab 192k -f alsa -ac 2 -ab 192k -i pulse -f x11grab -r 25 -s 1600x900 -minrate 512k -i :0.0 -sameq bothaudiosourcestest.mkv

it hangs after the "[alsa @ 0xa9fa80] capture with some ALSA plugins, especially dsnoop, may hang." line

when I try
ffmpeg -f alsa -i hw:0 -ac 2 -ab 192k -i pulse -f x11grab -r 25 -s 1600x900 -minrate 512k -i :0.0 -sameq bothaudiosourcestest.mkv

it gives me this error
pulse: No such file or directory


so I have no idea what do try next. is there a way to loop the speaker audio into the mic, I would rather do that than have the mic play through the speakers as I have no headset and this will undoubtedly cause feedback.

---

### Post by mgompert on 2013-03-08
if I pipe the mic into the speakers with this
parec --latency-msec=1 | pacat --latency-msec=1

and then chose the monitor in pulse audio mixer I can get both audio's into the video. but wiht out a headet that can reach the computer that is kinda pointless and I would much ratehr not have to switch plugs around on the back of the computer to make videos
if any one knows a way to send the speaker out to the mic in instead of the otehr way around that would be super helpful

thanks

---

