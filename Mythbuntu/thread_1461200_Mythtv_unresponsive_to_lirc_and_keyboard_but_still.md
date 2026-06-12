---
title: "Mythtv unresponsive to lirc and keyboard but still playing livetv"
date: 2010-04-23
forum: Mythbuntu
---

### Post by lpnb on 2010-04-23
Hi guys, 

this has been plaguing me through 2 ground up builds and also one upgrade. 

I am currently running an upgrade to mythbuntu 10.04 rc from 9.10.

I have searched for many months for an answer but I just can't seem to make any progress.

Description of symptom:

Only while watching TV AND recording 1 or more shows on the same or any other tuner will it completely stop responding to keypresses on the remote and the keyboard. The show keeps playing without interruption and the other shows recording will continue to record. 

Control will return when the backend stops recording whatever it is recording.

all other apps are working perfectly, so that means I can alt tab to firefox say, and then I can kill the mythfrontend and restart it. 

While recording I can browse any of the other features and menus in mythtv. I can also watch any recordings with no issue. but as soon as I go back into live tv it will "hang". as soon as mythbackend stops recording I have full control again...

```
2010-04-24 12:15:29.425 Opening ALSA audio device 'default'.
2010-04-24 12:15:29.531 mixer unable to find control Master 1
2010-04-24 12:15:29.531 NVP(8): Enabling Audio
2010-04-24 12:15:29.640 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-04-24 12:15:31.091 NVP(8): prebuffering pause 
2010-04-24 12:15:32.657 NVP(8): prebuffering pause
2010-04-24 12:15:32.908 NVP(8): prebuffering pause
2010-04-24 12:15:33.357 NVP(8): prebuffering pause
2010-04-24 12:15:35.640 NVP(8): prebuffering pause
2010-04-24 12:15:36.090 NVP(8): prebuffering pause
2010-04-24 12:15:39.256 TV: ASK_RECORDING 1 0 0 0 hasrec: 0 haslater: 0
2010-04-24 12:15:40.191 TV: ASK_RECORDING 6 0 0 0 hasrec: 0 haslater: 0
2010-04-24 12:15:44.171 NVP(8): prebuffering pause
2010-04-24 12:15:48.453 NVP(8): prebuffering pause
2010-04-24 12:16:03.733 NVP(8): prebuffering pause
2010-04-24 12:16:07.065 NVP(8): prebuffering pause
2010-04-24 12:16:07.531 NVP(8): prebuffering pause
2010-04-24 12:16:14.279 NVP(8): prebuffering pause
```


As you can see about from mythfrontend.log 010-04-24 12:15:39.256 there is no errors there at all.

here is some more log info after that point, during this part the frontend is still unresponsive and a recording is still going on.

```
2010-04-24 12:16:29.742 NVP(8): prebuffering pause
2010-04-24 12:17:02.650 NVP(8): prebuffering pause
2010-04-24 12:17:34.674 NVP(8): prebuffering pause
2010-04-24 12:17:45.255 NVP(8): prebuffering pause
2010-04-24 12:19:04.251 NVP(8): prebuffering pause
2010-04-24 12:19:34.059 NVP(8): prebuffering pause
2010-04-24 12:19:34.311 VDPAU: Created 2 output surfaces.
2010-04-24 12:19:34.311 VDPAU: Created VDPAU render device 1360x768
2010-04-24 12:19:34.340 NVP(8): Forcing decode extra audio option on (Video method requires it).
2010-04-24 12:19:34.341 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-04-24 12:19:34.341 AFD: Opened codec 0x7f33457908e0, id(MPEG2VIDEO) type(Video)
2010-04-24 12:19:34.341 AFD: codec MP3 has 0 channels
2010-04-24 12:19:34.341 AFD: Opened codec 0x7f3344b845b0, id(MP3) type(Audio)
2010-04-24 12:19:34.341 AFD Error: Could not find decoder for codec (DVB_TELETEXT), ignoring.
2010-04-24 12:19:34.341 NVP(8): Disabling Audio, params(0,0,0)
2010-04-24 12:19:34.444 VDPAU: Created 2 output surfaces.
2010-04-24 12:19:34.444 VDPAU: Created VDPAU render device 1360x768
2010-04-24 12:19:34.474 NVP(8): Forcing decode extra audio option on (Video method requires it).
2010-04-24 12:19:34.475 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-04-24 12:19:34.550 AFD: Setting channels to 0
2010-04-24 12:19:34.550 [mp3 @ 0x7f335ba9e380]Header missing
2010-04-24 12:19:34.550 NVP(8): Disabling Audio, params(0,0,0)
2010-04-24 12:19:34.550 AFD: Setting channels to 0
2010-04-24 12:19:34.654 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-04-24 12:19:34.654 Opening ALSA audio device 'default'.
2010-04-24 12:19:34.755 mixer unable to find control Master 1
2010-04-24 12:19:34.756 NVP(8): Enabling Audio
2010-04-24 12:19:34.861 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-04-24 12:19:35.009 NVP(8): prebuffering pause
2010-04-24 12:19:39.524 NVP(8): prebuffering pause
2010-04-24 12:20:04.851 NVP(8): prebuffering pause
2010-04-24 12:20:36.892 NVP(8): prebuffering pause
2010-04-24 12:22:01.716 NVP(8): prebuffering pause
2010-04-24 12:22:07.998 NVP(8): prebuffering pause
2010-04-24 12:22:11.396 NVP(8): prebuffering pause
2010-04-24 12:22:53.100 NVP(8): prebuffering pause
2010-04-24 12:27:10.589 NVP(8): prebuffering pause
2010-04-24 12:27:41.498 [mp3 @ 0x7f335ba9e380]Header missing
2010-04-24 12:27:41.498 AFD Error: Unknown audio decoding error
2010-04-24 12:27:41.498 [mp3 @ 0x7f335ba9e380]Header missing
2010-04-24 12:27:41.498 AFD Error: Unknown audio decoding error
2010-04-24 12:27:41.503 [mp3 @ 0x7f335ba9e380]Header missing
2010-04-24 12:27:41.503 AFD Error: Unknown audio decoding error
2010-04-24 12:27:41.981 NVP(8): prebuffering pause
2010-04-24 12:27:42.429 NVP(8): prebuffering pause
2010-04-24 12:27:43.496 NVP(8): prebuffering pause

```

There are some errors in there and I only just noticed that when they occur the TV playback glitches for 10th of a second... 

Anyway, any help would be greatly appreciated.

---

### Post by azmyth on 2010-04-24
I ran into a similar problem. I can't remember the steps I did to recreate. Basically, I had to ssh into the frontend to kill it. I fixed it by turning browse all channels off.

[http://svn.mythtv.org/trac/ticket/7411](http://svn.mythtv.org/trac/ticket/7411)

---

### Post by lpnb on 2010-04-24
Thanks for the response. I checked that setting under "General" "Browse change channels from channel group" and it was already off. is that the setting you mean? 

I think there is a setting somewhere that says use a tuner that is not being used for live tv for recording.

Any way I will try switching it 'ON' and see what happens.

---

### Post by lpnb on 2010-04-24
why do I see this in the backend status.....there are two tuners and I think I set it to a max of 2 streams per tuner so why does it say 1,2,6,7?? instead of 1,2,3,4??

Encoder 1 is local on mythbox and is not recording.
Encoder 2 is local on mythbox and is not recording.
Encoder 6 is local on mythbox and is not recording.
Encoder 7 is local on mythbox and is not recording.

---

### Post by lpnb on 2010-04-24
boy i'm frustrated...I promised myself I would not install again from scratch....all I did was turn that option mentioned above off and add an entry into fstab to try to fix one of the other 101 problems I am having and now my network card is not working...

every time I fix something, two other things break. 

I have been playing with mythtv for about 5 years now. you'd think I would have it sorted by now! and considering I am a sysadmin and make my living in IT, you might understand how frustrated I am getting with my own abilities...LOL

anyway, I am a realist and do realise that everything linux is built by a whole lot of unpaid enthusiasts....so I guess I have to live with things not working...

Oh well....I'll keep on trying until one day I mythtv running so that even my better half can use it....thats the goal anyway.

---

