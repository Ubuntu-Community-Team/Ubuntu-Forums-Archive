---
title: "surround sound help"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by mighty_falcon on 2006-10-11
I have a 5.1 surround sound set-up (logitech speakers) which workes flawlessly with XP. I cannot seem to get them all workin in Ubuntu. I only seem to have the 3 front speakers working. 

I played around with all the volume settings but no luck. Can someone please guide me on how to get the surround sound working?

tnx alot!

---

### Post by michael117 on 2006-10-11
Well, first make sure that you have your sound card correctly set up and fully detected by Ubuntu. Ubuntu is pretty good at that though. In linux, you only get surround sound where surround sound is really supposed to be. So by default, it will only really work if you put in a DVD that has surround sound audio on it or something else like that. How do you want to use the surround sound? Where do you want to hear it? For me, I'm using XMMS right now to listen to music and I too enjoyed hearing it in virtual surround sound and playing out off all my 5.1 speakers in windows. I did some research and found this guide from someone else on the forums: [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml) . That sets up a special alsa setting to duplicate the streams that go to the front 2 speakers to play out of all the speakers to simulate true surrround sound. That may work in whatever application you may want to use.

---

### Post by mighty_falcon on 2006-10-12
tnx for the reply

i followed the guide but i could not get it to work as when i ran ./etc/rc.local it would reconize the alsa conf...

when i run alsamixer i seem to only be able to change the volume of PCM & PC SPEAKER while i can only mute/unmute surround/center/left/righy/subwoofer

on another post someone said to type

speaker-test -c6 -Dplug:surround51

to test the surround sound...when i try that I only get sound from the 2 front speakers, center one and subwoofer...

any other suggestions?

thank you!

---

### Post by mighty_falcon on 2006-10-12
actually i just figured the sound is coming from the back two after i upgraded to kernel686 butwhen im running the test its coming at the same time when the front two are being tested and not when the back two are...where would i edit all the volumes for all the speakers and all the speaker config? is it in that alsa config file?

edit: also it seems to be mono...how do i switch the sound to stereo?

this is what i get from amixer

> Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [on]
  Front Right: Playback 255 [100%] [on]
Simple mixer control 'Surround',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Center',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Side',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 15 [100%] [on]
  Front Right: Playback 15 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 30 [100%] [off]
  Front Right: Capture 30 [100%] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD'
  Item0: 'Line'


---

