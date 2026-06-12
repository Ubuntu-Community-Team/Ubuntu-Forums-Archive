---
title: "Feisty upgrade no microphone for Skype and Audicity"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by El Viejo Lobo on 2007-04-22
My Presario v2000 with ATI IXP Alsa audio control a clean upgrade from Edgy to Feisty.
I can not talk on Skype and can not record with Audicity. I do ear myself on the Laptop  speakers.
I tried different mic's. I went to System/Preferences/ Sound Preferences/Sound Capture.
Tested and got no audio on it.  I did any thing possible with the Volume control. With Edgy I learn to change capture from talking 1cm from the mic. keeping the surrounding noises out of my Skype or 3 meters from it so I could walk around and keep talking. Now I am happy with feisty but have to go to my desktop Edgy Eft and make my skype calls. I hope that some one help me out.:(

---

### Post by jjalocha on 2007-04-22
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=418396](http://ubuntuforums.org/showthread.php?t=418396)
try posting your hardware, so that others with more experience can guide you.

---

### Post by El Viejo Lobo on 2007-04-22
This is what I got from:
[http://ubuntuforums.org/showthread.php?t=418396](http://ubuntuforums.org/showthread.php?t=418396)

lobo@lobo-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lobo@lobo-laptop:~$ 00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
bash: 00:14.2: command not found
lobo@lobo-laptop:~$ 



Feisty comes with 'alsa-utils'  but I can see nothing of it..
My Device Manager tels me that the machine have:
ATI Technologies Inc
IXP SB400 AC'97 Audio

It hope that I will not have to get a doctorate on this problem like I had to do with my BCM4318 wireless.

---

### Post by jjalocha on 2007-04-22
Sorry, I'm not sure if I understand you correctly...
'alsa-utils' are command line tools, so you have to use [FONT="Fixedsys"]alsamixer[/FONT] and [FONT="Fixedsys"]amixer[/FONT] in a terminal.
If that's not what you meant, please sorry...

---

### Post by El Viejo Lobo on 2007-04-22
Copy/Paste from your thread

This is my experience with microphone input problems, and how I solved them. Many people are having different problems with microphone input in Ubuntu, so I hope this post is helpful for some of them.

Both, with Edgy and Feisty, my hardware gets detected correctly out of the box, but I was unable to record anything, using a microphone plugged into the jack.

This is my soundcard:

Code:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]

  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci gives different output in Edgy and Feisty:

Edgy:

Code:

00:14.2 Audio device: ATI Technologies Inc Unknown device 4383

Feisty:

Code:

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia

[COLOR="Blue"]The solution needs the alsamixer and amixer command line tools. If you don't have them, you need to install the 'alsa-utils' package.[/COLOR] T**[COLOR="Blue"][COLOR="Blue"][COLOR="Red"][B][B]his 'alsa-utlis' is a package from Synaptic that is installed at the Feisty Fawn installation. **[/B][/COLOR][/COLOR][/COLOR][/B]

You can use alsamixer, using TAB for selecting the main window, and LEFT, RIGHT for the channel. Make sure you get the following settings right:
I do have alsamixer but it looks that some thing is missing.
Thanks.

---

### Post by El Viejo Lobo on 2007-04-23
It is no new problem, but where is the fix for it?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99135](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99135)

[https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531)

I am attaching the alsamixer window. I can not change the capture control - I do not see it.
I can not boost mic too - it just do not react.
:(  I am a st:( arting to think that Feisty will have to home get itself better and **I will call Edgy back from the bench.  **

---

### Post by realstraw on 2007-04-23
I have got the same problem too, is there a solution?

---

### Post by jjalocha on 2007-04-23
Lobo, in your screenshot, you are showing me your 'Playback' settings. In order to set-up 'Capture', you have to press TAB. 'viev' in the left upper corner will change, as well as all sliders. Then, use the keys I showed in my other thread: LEFT/RIGHT to change the channel, UP/DOWN for volume, SPACE for switching sources.
Good luck!

---

### Post by jjalocha on 2007-04-23
I don't have the Mic-Boost option in my alsamixer, so can please someone with more experience guide the parent poster at how to set this up?

Here's also another post with a successful microphone setup:
[http://ubuntuforums.org/showpost.php...13&postcount=3](http://ubuntuforums.org/showpost.php...13&postcount=3)

---

### Post by El Viejo Lobo on 2007-04-23
I clicked here and clicked there in alasmixer and Volume Control and MY MIC. IS WORKING.  
I have some strange things like alsamixer on terminal shows that mic boos is off and Volume Control shows that switches/moicrophone capture is on.  Is it ok? How I can get more capture for my mic? It used to have about 3 meters of capture with Edgy Eft.
The No.1 screenshot shows 
amixer in terminal before my clicking gave fruit.

The folowing Terminal copy/paste is after my cliking got the Mic. to work - a lot of words of difference, I hope that someone will learn something of it so we will have better idea of what is going on with Feisy and the Mic.
obo@lobo-laptop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [10.50dB] [on]
  Front Right: Playback 30 [97%] [10.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 30 [97%] [10.50dB] [on] Capture [off]
  Front Right: Playback 30 [97%] [10.50dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [7.50dB] [on] Capture [off]
  Front Right: Playback 28 [90%] [7.50dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
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
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
lobo@lobo-laptop:~$ 

The No 2 screenshot
Shows the Volume Control Switch 'NO' microphone capture.

The No 3 screenshot
Shows the alsamixer terminal with the mic boost "OFF"

The screenshot No. 4
Shows the ALSA Mixer GUI

The No.5 screenshot
Shows Audicity outputting the graphics of the audio but I hear nothing.

I hope that all this will help to get some thing easy for all the new comers to the Ubuntu world.

:guitar:

P.S.   This is the alsamixer  Wiki for the new guys in the Ubuntu town. I  think that  a lot  of us do not know about it's existence before they got problems with their Mics [http://alsa.opensrc.org/Alsamixer#NAME](http://alsa.opensrc.org/Alsamixer#NAME)

---

### Post by El Viejo Lobo on 2007-04-28
Still did not found why volume up/down/mute buttons become microphone control and 
how to fix it

---

### Post by euchrid on 2007-06-07
I managed to fix this issue on my system by updating the Alsa drivers. I posted how I did it here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055](http://ubuntuforums.org/showthread.php?p=2798055#post2798055) 

Hope it helps! Not sure about your weirdness with Alsamixer, though, although it might not matter if everything else works, I guess.

---

### Post by psyk0ninja on 2007-06-26
im having the same problem. can someone please help? tell me what info you need and i'll post it.

---

### Post by El Viejo Lobo on 2007-06-26
m having the same problem. can someone please help? tell me what info you need and i'll post it.
__________________

I reinstalled Feisty Fwan and it was fixed. I never found any other way to fix it.  Sorry :(

---

