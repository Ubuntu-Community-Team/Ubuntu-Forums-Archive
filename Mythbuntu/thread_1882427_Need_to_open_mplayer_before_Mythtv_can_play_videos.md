---
title: "Need to open mplayer before Mythtv can play videos"
date: 2011-11-17
forum: Mythbuntu
---

### Post by oct on 2011-11-17
Hello,

I finished a fresh install of Mythbuntu 11.10 64bit. When I try to play any video or Live TV, or recording, I get a black screen, although audio is ok. The same happens with VLC. After some codec reinstall and Google search, I ended installing Mplayer, that plays all files correctly. The strange issue is that, after a reboot, I need to play a video file with Mplayer before being able to play any file on Mythtv. If I don't play a video file with Mythtv (opening Mplayer is not enough, I have to open a file), I get the black screen again.

Any ideas?

thanks,

Oct

---

### Post by nickrout on 2011-11-17
> **oct said:**
> Hello,

I finished a fresh install of Mythbuntu 11.10 64bit. When I try to play any video or Live TV, or recording, I get a black screen, although audio is ok. The same happens with VLC. After some codec reinstall and Google search, I ended installing Mplayer, that plays all files correctly. The strange issue is that, after a reboot, I need to play a video file with Mplayer before being able to play any file on Mythtv. If I don't play a video file with Mythtv (opening Mplayer is not enough, I have to open a file), I get the black screen again.

Any ideas?

thanks,

Oct

Yes, show us your frontend logs when you play a video both before and after you have run mplayer.

---

### Post by shad0w_walker on 2011-11-18
I'll second the request for logs. My gut is saying it might be a compositing problem, though I don't recall Mythbuntu turning compiz on by default. I recall something of a similar problem when Compiz starting becoming popular, with green screens instead of video playback. Might be worth having a poke at your graphics drivers.

But definitely post some logs from before/after as that's going to give better results than any of my hunches :P

---

### Post by oct on 2011-11-19
Yes, of course. Here are the logs. The first one is the log when trying to play a recording just after a reboot. I got the black screen. The second one corresponds to the log when playing the same recording just after opening a video with mplayer. I see the video now.

Before mplayer:

[FONT="Courier New"][SIZE="2"]2011-11-18 19:34:34.796 TV: Attempting to change from None to WatchingPreRecorded
2011-11-18 19:34:35.140 AFD: Opened codec 0x3d11400, id(MPEG2VIDEO) type(Video)
2011-11-18 19:34:35.140 AFD: codec MP2 has 2 channels
2011-11-18 19:34:35.140 AFD: Opened codec 0x3d16f40, id(MP2) type(Audio)
2011-11-18 19:34:35.140 AFD: codec MP2 has 1 channels
2011-11-18 19:34:35.140 AFD: Opened codec 0x3d175c0, id(MP2) type(Audio)
2011-11-18 19:34:35.140 AFD: codec MP2 has 1 channels
2011-11-18 19:34:35.140 AFD: Opened codec 0x3d13e50, id(MP2) type(Audio)
2011-11-18 19:34:35.141 AFD: Opened codec 0x3d09450, id(DVB_SUBTITLE) type(Subtitle)
2011-11-18 19:34:35.269 AO: Opening audio device 'default:CARD=PCH' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-11-18 19:34:35.271 ALSA, Error: Setting hardware audio buffer size to 6016
2011-11-18 19:34:35.271 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-11-18 19:34:35.271 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-11-18 19:34:35.271 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-11-18 19:34:35.273 AudioPlayer: Enabling Audio
2011-11-18 19:34:35.368 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-11-18 19:34:35.387 OSD: Base theme size: 1280x720
2011-11-18 19:34:35.387 OSD: Scaling factors: 0.5625x0.8
2011-11-18 19:34:35.410 OSD: Base theme size: 1280x720
2011-11-18 19:34:35.410 OSD: Scaling factors: 0.5625x0.8
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2011-11-18 19:34:35.417 Player(0): Video timing method: USleep with busy wait
2011-11-18 19:34:35.418 TV: Changing from None to WatchingPreRecorded
2011-11-18 19:34:35.458 OSD: Base theme size: 1280x720
2011-11-18 19:34:35.458 OSD: Scaling factors: 0.5625x0.683333
2011-11-18 19:34:35.479 VideoOutput: Created YV12 OSD.
2011-11-18 19:35:02.014 TV: Attempting to change from WatchingPreRecorded to None
2011-11-18 19:35:02.036 TV: Changing from WatchingPreRecorded to None
2011-11-18 19:35:02.068 lcddevice: WARNING: Something is getting passedto LCDServer that it does not understand
2011-11-18 19:35:02.068 lcddevice: last command: SWITCH_TO_MENU "Recordings" TRUE "Bike attack ~ 18/11 ~ 18:02" NOTCHECKABLE TRUE FALSE 0 "La Riera - ""SEGONA VISITA DEL CRTIC GASTRONMIC
Avui ve a dinar el crtic. s la segona visita i es produeix un sabotatge a la cuina."" ~ 18/11 ~ 15:52" NOTCHECKABLE FALSE FALSE 0 "Jokebox - ""L'avi de la famlia Pinto fa una confessi important tot dibuixant. A 'Compra-t'ho ara' venen 'Guerra i pau', un clssic per fal"" ~ 17/11 ~ 00:01" NOTCHECKABLE FALSE FALSE 0 "SUPERNANNY ~ 17/11 ~ 20:00" NOTCHECKABLE FALSE FALSE 0
2011-11-18 19:35:02.129 lcddevice: WARNING: Something is getting passedto LCDServer that it does not understand
2011-11-18 19:35:02.129 lcddevice: last command: SWITCH_TO_MENU "Recordings" TRUE "Bike attack ~ 18/11 ~ 18:02" NOTCHECKABLE TRUE FALSE 0 "La Riera - ""SEGONA VISITA DEL CRTIC GASTRONMIC
Avui ve a dinar el crtic. s la segona visita i es produeix un sabotatge a la cuina."" ~ 18/11 ~ 15:52" NOTCHECKABLE FALSE FALSE 0 "Jokebox - ""L'avi de la famlia Pinto fa una confessi important tot dibuixant. A 'Compra-t'ho ara' venen 'Guerra i pau', un clssic per fal"" ~ 17/11 ~ 00:01" NOTCHECKABLE FALSE FALSE 0 "SUPERNANNY ~ 17/11 ~ 20:00" NOTCHECKABLE FALSE FALSE 0
[/SIZE][/FONT]
After mplayer:

[FONT="Courier New"][SIZE="3"][SIZE="2"]2011-11-18 19:37:54.400 TV: Attempting to change from None to WatchingPreRecorded
2011-11-18 19:37:54.640 AFD: Opened codec 0x7f131f2fbbf0, id(MPEG2VIDEO) type(Video)
2011-11-18 19:37:54.640 AFD: codec MP2 has 2 channels
2011-11-18 19:37:54.640 AFD: Opened codec 0x7f131f2d6f60, id(MP2) type(Audio)
2011-11-18 19:37:54.640 AFD: codec MP2 has 1 channels
2011-11-18 19:37:54.640 AFD: Opened codec 0x7f131f2d73c0, id(MP2) type(Audio)
2011-11-18 19:37:54.640 AFD: codec MP2 has 1 channels
2011-11-18 19:37:54.640 AFD: Opened codec 0x7f131f2d7a40, id(MP2) type(Audio)
2011-11-18 19:37:54.641 AFD: Opened codec 0x7f131f2c51b0, id(DVB_SUBTITLE) type(Subtitle)
2011-11-18 19:37:54.715 AO: Opening audio device 'default:CARD=PCH' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-11-18 19:37:54.716 ALSA, Error: Setting hardware audio buffer size to 6016
2011-11-18 19:37:54.716 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-11-18 19:37:54.716 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-11-18 19:37:54.716 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-11-18 19:37:54.717 AudioPlayer: Enabling Audio
2011-11-18 19:37:54.733 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-11-18 19:37:54.751 OSD: Base theme size: 1280x720
2011-11-18 19:37:54.751 OSD: Scaling factors: 0.5625x0.8
2011-11-18 19:37:54.769 OSD: Base theme size: 1280x720
2011-11-18 19:37:54.769 OSD: Scaling factors: 0.5625x0.8
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2011-11-18 19:37:54.772 Player(1): Video timing method: USleep with busy wait
2011-11-18 19:37:54.773 TV: Changing from None to WatchingPreRecorded
2011-11-18 19:37:54.812 OSD: Base theme size: 1280x720
2011-11-18 19:37:54.812 OSD: Scaling factors: 0.5625x0.683333
2011-11-18 19:37:54.831 VideoOutput: Created YV12 OSD.
2011-11-18 19:38:00.782 TV: Attempting to change from WatchingPreRecorded to None
2011-11-18 19:38:00.797 TV: Changing from WatchingPreRecorded to None
2011-11-18 19:38:00.828 lcddevice: WARNING: Something is getting passedto LCDServer that it does not understand
2011-11-18 19:38:00.828 lcddevice: last command: SWITCH_TO_MENU "Recordings" TRUE "Bike attack ~ 18/11 ~ 18:02" NOTCHECKABLE TRUE FALSE 0 "La Riera - ""SEGONA VISITA DEL CRTIC GASTRONMIC
Avui ve a dinar el crtic. s la segona visita i es produeix un sabotatge a la cuina."" ~ 18/11 ~ 15:52" NOTCHECKABLE FALSE FALSE 0 "Jokebox - ""L'avi de la famlia Pinto fa una confessi important tot dibuixant. A 'Compra-t'ho ara' venen 'Guerra i pau', un clssic per fal"" ~ 17/11 ~ 00:01" NOTCHECKABLE FALSE FALSE 0 "SUPERNANNY ~ 17/11 ~ 20:00" NOTCHECKABLE FALSE FALSE 0
2011-11-18 19:38:00.891 lcddevice: WARNING: Something is getting passedto LCDServer that it does not understand
2011-11-18 19:38:00.892 lcddevice: last command: SWITCH_TO_MENU "Recordings" TRUE "Bike attack ~ 18/11 ~ 18:02" NOTCHECKABLE TRUE FALSE 0 "La Riera - ""SEGONA VISITA DEL CRTIC GASTRONMIC
Avui ve a dinar el crtic. s la segona visita i es produeix un sabotatge a la cuina."" ~ 18/11 ~ 15:52" NOTCHECKABLE FALSE FALSE 0 "Jokebox - ""L'avi de la famlia Pinto fa una confessi important tot dibuixant. A 'Compra-t'ho ara' venen 'Guerra i pau', un clssic per fal"" ~ 17/11 ~ 00:01" NOTCHECKABLE FALSE FALSE 0 "SUPERNANNY ~ 17/11 ~ 20:00" NOTCHECKABLE FALSE FALSE 0[/SIZE][/SIZE][/FONT]

Thanks

Oct

---

### Post by oct on 2011-11-22
Well, problem solved. It was a video driver issue. for some reason (probably a mistake) I had selected version 173 of Nvidia driver, instead of the recommended one. I activated the recommended version and now it works.

Thanks all

Oct

---

