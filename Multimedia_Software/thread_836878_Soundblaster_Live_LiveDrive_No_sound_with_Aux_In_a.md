---
title: "Soundblaster Live LiveDrive: No sound with Aux In and CD player!"
date: 2008-06-21
forum: Multimedia Software
---

### Post by Robertjm on 2008-06-21
Hi all,

Got a sound problem that I hope can be resolved. 

Using Hardy Heron and have a Soundblaster 5.1 installed, which came with the LiveDrive that fits in a 5.25" drive bay.

Today I hooked up a Technics tape player to the Aux inputs on the front panel, but I'm getting no sound through my speakers. The front panel of the Technics shows levels of the music just fine. When I go into the Alsa Mixer I unmute the Aux In, and the made sure the volume is cranked up full. Still nothing. 

Another problem I'm having is with playing audio CDs. When I put a CD in the tray it detects that new media is in there and offers me several options to choose from, including playing through Noatumn, which is what I choose. The player recognizes that there's a track there and can even get the track info from CDDB, however, no sound is played. When I try playing the CD with Amarok, it doesn't even show up in the player!! Again, I checked volume to make sure CD is on in Alsa, and that its levels are up, which there are.

What's odd is that if I throw a DVD in the player it will launch through XINE and sound plays just fine.

Anyone have any thoughts on this? I'm trying to copy some old audio tapes for my church to CD, but can't do it if I can't get the AUX In working.

Here's the log from amixer if it helps:

robertjm@robertjm-desktop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 21 [68%] [-15.00dB] [on]
  Front Right: Playback 21 [68%] [-15.00dB] [on]
Simple mixer control 'Headphone LFE',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Headphone',1
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 97 [97%] [-1.20dB]
Simple mixer control 'Headphone Center',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Tone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Bass',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 21 [52%]
  Front Right: 21 [52%]
Simple mixer control 'Treble',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control '3D Control Sigmatel - Rear Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 80 [80%] [-8.00dB] [on]
  Front Right: Capture 80 [80%] [-8.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 15 [15%] [-34.00dB] Capture 0 [0%] [-99999.99dB] [on]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 31 [31%] [-27.60dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 80 [80%] [-8.00dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 80 [80%] [-8.00dB] [off]
Simple mixer control 'Wave',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB] [off]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB] [off]
Simple mixer control 'Wave Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Wave LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Wave Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [on]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [on]
Simple mixer control 'Line LiveDrive',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [on]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [on]
Simple mixer control 'Line2 LiveDrive',1
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [on]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 4 [13%] [-28.50dB] [off] Capture [off]
  Front Right: Playback 4 [13%] [-28.50dB] [off] Capture [off]
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
  Mono: Playback 31 [100%] [12.00dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958 Coaxial',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'IEC958 LiveDrive',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 99 [99%] [0.40dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 99 [99%] [0.40dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'IEC958 TTL',0
  Capabilities: pvolume cvolume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 12 [80%] [-9.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
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
Simple mixer control 'AC97',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 80 [80%] [-8.00dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 80 [80%] [-8.00dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'SB Live Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Sigmatel 4-Speaker Stereo',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Sigmatel Output Bias',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Sigmatel Surround',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Sigmatel Surround Phase Inversion Playback ',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

---

### Post by Robertjm on 2008-06-22
Just a quick note.

The LiveDrive does have connectivity in that the headphone jack is working when I plug a headset into it. What's odd is that it doesn't mute the normal speakers I use, but I can do that manually.

Can't find my mic, or I'd check the inputs on that too.

---

### Post by Wheel_nut on 2008-08-13
The Live Drive II Aux In 2 input is set to receive Digital input by default. This can be configured to receive Analogue signal but you need the AudioHQ Program that came on the CD shipped with the Live Drive II. 

There are two functions which are Soft configurable:

1} The Aux In 2 RCA Phono sockets (Digital or Analogue) - Default is Digital.

2) Speaker Mute when headphones are plugged in to the Front Panel. (Default is No Mute)

Now, There is a third quirk on the Live Drive II Front Panel. The Mic In on the Front Panel becomes a Line In 2 input if the volume control is turned down until it clicks. You can then use the 1/4" Jack socket as a stereo input at Line levels.

The answer to your obvious question is No, I don't have the AudioHQ program. Creative do not provide it as a download and although Google brings up a lot of hits, they either end up on porn sites or recurcively to the dead Creative site.

---

### Post by Robertjm on 2008-08-13
They made a linux version of audioHQ?? Since I bought the LiveDrive myself I haev all the Windows disks that came with it, but honestly don't remember that program.

How would I control those options on a Ubuntu box with Windows software? I'm not following.

Robert

---

### Post by Shazaam on 2008-08-13
Right-click the speaker icon- choose "Open Volume Control". Go to "Recording". Is it set up the way you want? Do the same with "Switches" and "Options". As an aside, the only way I could get my Live 5.1 (no Live Drive) to work for ME was to disable pulsaudio (System>Preferences>Sound, changed everthing to ALSA but left "Default Mixer Tracks" pointing to "SB Live").
Also, have you ran 
```
alsamixer
```
in terminal? Anything with an "M" is muted, hit your m key to unmute.
You can try to run AudioHQ with wine but don't know if it will work.

---

### Post by Wheel_nut on 2008-08-13
After posting earlier, I found a source for the SB Live CD software and drivers here [http://www.softwarepatch.com/utilities/creativelive3.html](http://www.softwarepatch.com/utilities/creativelive3.html) 

Now, I have to declare that my Live Drive II is in a Windows XP Pro System. What I discovered is that the Drivers installed from that download are down level from the default drivers loaded by Windoze. When I upgraded the drivers to the current levels, the AudioHQ program wouldn't work any more!

The good news (unfortunately for the Windows Driver only) is that I have discovered that there is an "Advanced" button under the Aux2 In volume slider in the Play Mixer. It has the option to "Enable" the Aux2 In input and when ticked, it enables Analogue signal on the RCA Phono sockets.

Now, if you can use the Windows Driver with a "Wrapper", it may work for you.

---

