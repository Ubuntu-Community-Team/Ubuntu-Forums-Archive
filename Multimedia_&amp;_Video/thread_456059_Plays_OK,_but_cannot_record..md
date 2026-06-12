---
title: "Plays OK, but cannot record."
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by undecidable on 2007-05-27
I can play just fine.
Am trying to record from line-in
into Sound Recorder, Audacity or MHWaveEdit.

I can hear sound on my speakers,
I can mute this sound with Alsamixer,
but I cannot get any app to hear this sound and record it.

In Sound Recorder have set input to Line-In, Capture and Mix
and on Alsamixer tried setting input to Line-in, Capture and Mix,
all with no effect.

No input is registered in any of these programs.  
with Sound Recorder I can save the file "recorded", but it has no sound.  

Many posts re people having a similar prob with microphones,
and bugs filed re dapper and microphones,
but no mention of line-in.

Is this a bug in Feisty, in which case I will stop messing with it,
and try to file in launchpad
or is there some other solution?


Using:Feisty.
Thinkpad TP21, SoundFusion CS46, AlsaMixer.

---

### Post by deadgobby on 2007-05-27
PLease open the terminal and input this command see what sound device you have.

asoundconf list


Then post its reply.

GObby

---

### Post by undecidable on 2007-05-27
Below is the output requested:

I have also attached the output of amixer in case it is useful.
----------------------------------
asoundconf:
  Names of available sound cards:
  CS46xx

tail -2 /proc/asound/oss/sndstat:
  Mixers:
  0: Cirrus Logic CS4297A rev 4
------------------------------------

thanks

---

### Post by undecidable on 2007-05-27
apologies, attaching didn't seem to work,
so amixer output is below:

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 28 [44%] [-52.50dB] [on]
  Front Right: Playback 52 [83%] [-16.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [off]
  Front Right: Playback 23 [74%] [-12.00dB] [off]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [7.50dB] [on] Capture [on]
  Front Right: Playback 28 [90%] [7.50dB] [on] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [off] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 24 [77%] [1.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 13 [87%] [-6.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 27 [87%] [6.00dB] [off] Capture [off]
  Front Right: Playback 27 [87%] [6.00dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 12 [80%] [18.00dB] [on]
  Front Right: Capture 12 [80%] [18.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'ADC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 32767 [100%] Capture [off]
  Front Right: 32767 [100%] Capture [off]
Simple mixer control 'DAC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 26214 [80%] Capture [off]
  Front Right: 26214 [80%] Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

---

### Post by deadgobby on 2007-05-27
GO into speaker icon and double left click. Here is some screen shot that should look like mine. A mic is just a mic. A usb mic is a hassle.
I use a line in because I use it to dub down a lot of stuff off my 4 tack mixer and not to say I oodles of tapes to dub down to mp3.

---

### Post by undecidable on 2007-05-27
My alsamixer screen (reached from vol icon) looks a bit different to yours,
as does the cmd line alsamixer output.
See 1st 3 screenshots. 
They seem to be focused on selecting a recording source via 'capture',
and you can only set the vol of capture.

However the input tab of kmix looks more similar..

I don't think the problem is that I dont know how to use the mixer.

---

### Post by deadgobby on 2007-05-28
OK looking at your sceen shot. You have Line in turn on and Mic nothing. So select line to turn off and mic on. 
GObby

---

### Post by undecidable on 2007-05-28
Don't understand - I am trying to record from line-in, not mic.
So why would I turn line off and mic on?

---

### Post by deadgobby on 2007-05-28
Sorry my bad. Have you tried to turn up the level on the line in capture.

---

### Post by undecidable on 2007-05-28
yes, I have thanks.

---

### Post by oxalá on 2007-06-23
did this go anywhere?  having similar problems.

---

### Post by undecidable on 2007-06-24
No unfortunately it did not.

It seems to be a common problem that many people have and is distribution independent, though most people mentioning it talk about difficulty recording from mic, though I imagine the underlying problem is the same.   The solutions generally offered seem to work for some people but not everybody and did not work for me.  

Apologies I can't be of more help.

---

### Post by jppaynesr on 2007-06-24
Same problem here. I have a Dell Inspiron E1505 with Ubuntu pre-installed by Dell. I cant record anything. Without the MIC working I can't use Skype.

---

### Post by obadiah on 2007-07-24
I too have the dell E1505N with ubuntu pre-installed. The mic won't record anything. I first noticed this when I tried to use skype. This is very sad. Any help would be great.

---

### Post by jppaynesr on 2007-07-25
It is disappointing but it turns out that the 1505n does not come with an internal mic. Go back and check the specs on Dell's website.  You MUST use an external mic. 

And FWIW, it also does not come with bluetooth either. . .

---

### Post by mythicalbyrd on 2007-09-25
I have a dell 1505n which I use with the Ubuntu Studio audio apps.  The laptop soundcard generally sucks for anything audio/video file playback, but I've been using a M-Audio Fast Track with a dynamic mic for recording. :guitar:

---

