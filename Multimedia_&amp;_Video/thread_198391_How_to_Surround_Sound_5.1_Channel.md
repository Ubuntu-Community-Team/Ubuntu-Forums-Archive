---
title: "How to? Surround Sound 5.1 Channel"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by moncsco on 2006-06-17
hi. i was wondering how can i make all the channels in my soundcard work?

lspci = Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

I have VIA 8235. at the back it has 3 sockets. one of these can be used as mic input. in windows i have a utility (realtek) to make this as an output to have 3 output sockets for the 5.1 surround sound speakers. In the alsamixer utility i have set it like this:

Master      =OO, 100<>100
MasterM   =OO, 100
PCM         =OO, 100<>100
Surround  =OO, 100<>100
Surround  =Shared
Center     =OO, 100
LFE          =OO, 100
Line         =MM, 100<>100
CD           =MM, 100<>100
Mic          =MM, 100
Mic Boost =MM
Mic Select =Mic1
Phone       =MM, 100
IEC958      =PCM
IEC958 O  =OO
IEC958  P  =100
PC Speak  =OO, 100
AUX          =OO, 100<>100
Mono Out  =Mic
Channel    =6ch
Duplicat    =MM
External    =MM
Input So    =Input 2
Input So    =Input 2
and finally al the VIA DXS =100<>100

*OO means ON. MM means OFF

the 2nd surround settings which is named Surround Jack Mode in KMix, when shared the mic is off, when i set it to INDEPENDENT mic is on but the sound plays on the center speaker and the subwoofer and no sound from the 2 front speakers.

When i change the Channel Mode from 6ch to 4ch, the mic is on, music plays on the 2 front speakers and none from the center speaker and the subwoofer but when i use the mic the sound comes out of the center speakers and none on the front.

I have set all the audio of XMMS, amaroKm totem, xine, gxine,mplayer, kaffiene but nothing, even watching dvd in surround sound. I even installed the drivers from realtek, used .asoundrc. Cant make it work. Can anyone help?

---

### Post by kahsheung on 2006-06-17
hi, I'm newbie myself...I spent 2 days looking for solutions and found one that worked for me.

I have an audigy 2 zs and even though ubuntu recognize it some how the back speaker n center speaker the volume is set to 0 by default.

Try double clicking the volume icon (near the date) then Edit->Preferences and add center and surround. Then turn up the surround and center speaker volume..

---

### Post by justafish on 2006-06-21
I got my SB Live 5.1 to work by turning on 5.1-channel sound in totem (Edit/Preferences/Audio) and then bringing up alsa mixer and turn on Wave Surround.

---

### Post by moncsco on 2006-06-26
they are all at max volume. i used different mixers but nothing.  i also set the mixers in the programs but still nothing. but if i speak to the mic sound comes out of the center speaker but not on the 2front speakers. i checked on the other forums and i think i really have to edit the .asoundrc but i dont know how to config it properly. even 2 sound cards can be combined by setting .asoundrc. i only have one sound card but when i run cat /proc/asound/devices
it gives me this:
 17: [0- 1]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer

i only have 2 digital audio playback. i checked other forums they have 3 audio playback. 

if i type in dir /proc/asound/card0
the result is
codec97#0  id  oss_mixer  pcm0c  pcm0p  pcm1c  pcm1p  via82xx
pcm0c i think is the 1st capure
pcm0p is 1st playback
pcm1c is 2nd capture
pcm1p is 2nd playback.

but cat /proc/asound/card0/pcm0p/info gives:
card: 0
device: 0
subdevice: 0
stream: PLAYBACK
id: VIA 8235
name: VIA 8235
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 4
subdevices_avail: 3

it has 4 subdevices. 

can anyone tell me if it has to do with .asoundrc with my problems on surround sound? if so how can i modify .asoundrc?

---

