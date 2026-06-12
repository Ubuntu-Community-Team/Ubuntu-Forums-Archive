---
title: "How do you know if VDPAU is being used?"
date: 2010-01-26
forum: Mythbuntu
---

### Post by 4dognight on 2010-01-26
I set my config in the frontend to use VDPAU.
I dont see any messages in the log that would indicate its being used.
What should I see to verify its being used?
I have a nvidia 9600 GSO card.
I have an AMD 4850e (dual 2.5)
Playing back a HD recording my CPU is about 80% idle. I read ppl are seeing single digit utilization.

---

### Post by 4dognight on 2010-01-27
No one has any suggestions?
I checked my xord log, but nothing in there. dmesg has nothing either.

---

### Post by bbruenfl on 2010-01-27
you can check the mythfrontend logs...
```
locate mythfrontend.log
```if that doesn't answer your question try this....
shutdown the frontend
then, from a command prompt type...
```
mythfrontend -v playback > mythfrontend.playback
```navigate directly to a video that should be played with vdpau and play it for a few seconds.  hit esc then exit the frontend.

now use your favorite text editor to read the log. Something like...
```
gedit mythfrontend.playback
```You are looking for the initial call for the video file you were watching or you can look near the end for the ports and stuff to be closed.

For what it is worth, in my experience, if vdpau fails it reverts to Xvideo.  So if you see something like 
```
VideoOutputXv: Closing XVideo port 131
```i'd say vdpau aint workin too good.

Hope that helps.

---

### Post by 4dognight on 2010-01-27
Here is my frontend log when I start watching a channel in HD.


2010-01-27 21:11:29.734 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-27 21:11:29.744 MythContext: Connecting to backend server: 192.168.2.6:6543 (try 1 of 1)
2010-01-27 21:11:29.746 Using protocol version 50
2010-01-27 21:11:29.787 Spawning LiveTV Recorder -- begin
2010-01-27 21:11:30.051 Spawning LiveTV Recorder -- end
2010-01-27 21:11:30.200 We have a playbackURL(myth://192.168.2.6:6543/4080_20100127211058.mpg) & cardtype(DUMMY)
2010-01-27 21:11:30.201 We have a RingBuffer
2010-01-27 21:11:30.254 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2010-01-27 21:11:30.497 NVP(d): Disabling Audio, params(-1,2,44100)
2010-01-27 21:11:30.898 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-01-27 21:11:30.938 OSD Theme Dimensions W: 640 H: 480
2010-01-27 21:11:31.261 Unknown font: descriptfont in textarea: description
2010-01-27 21:11:32.195 OpenGLVideoSync()
2010-01-27 21:11:32.193 Realtime priority would require SUID as root.
2010-01-27 21:11:32.225 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2010-01-27 21:11:32.225 TV: Changing from None to Watching WatchingLiveTV
2010-01-27 21:11:32.225 TV: State is LiveTV & mctx == ctx
2010-01-27 21:11:32.233 TV: UpdateOSDInput done
2010-01-27 21:11:32.233 TV: UpdateLCD done
2010-01-27 21:11:32.234 TV: ITVRestart done
2010-01-27 21:11:32.304 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-27 21:11:32.336 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-01-27 21:11:32.492 Video timing method: SGI OpenGL
2010-01-27 21:11:33.427 NVP(d): Forcing decode extra audio option on (Video method requires it).
2010-01-27 21:11:33.594 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-01-27 21:11:33.596 AFD: Opened codec 0x9ec9000, id(MPEG2VIDEO) type(Video)
2010-01-27 21:11:33.596 AFD: codec AC3 has 6 channels
2010-01-27 21:11:33.596 AFD: Opened codec 0xa5463c0, id(AC3) type(Audio)
2010-01-27 21:11:33.609 Opening audio device 'spdif'. ch 2(2) sr 48000
2010-01-27 21:11:33.638 Opening ALSA audio device 'spdif'.
2010-01-27 21:11:33.711 NVP(d): Enabling Audio
2010-01-27 21:11:33.713 Opening audio device 'spdif'. ch 2(2) sr 48000
2010-01-27 21:11:33.713 Opening ALSA audio device 'spdif'.

---

### Post by bbruenfl on 2010-01-28
I think what your are looking for is below this in the log.  Try running the frontend from the command line as detailed above and post what you get if you can't figure out which video module your frontend is using.

---

### Post by jMon54 on 2010-01-28
I use VDPAU and all I can say is I can tell it's working because otherwise I cannot watch HDTV.  If I try the other playback options I get unacceptable video quality.

---

### Post by 4dognight on 2010-01-28
OK, I tried what you suggested, and it quite obvious it is using VDPAU. 
:p

Thanks


2010-01-28 15:13:50.172 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2010-01-28 15:13:50.173 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-28 15:13:50.173 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-28 15:13:50.173 VDP: LoadBestPreferences(1920x1080, 60)
2010-01-28 15:13:50.185 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2010-01-28 15:13:50.186 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-28 15:13:50.186 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-28 15:13:50.186 VDP: LoadBestPreferences(1920x1080, 60)
2010-01-28 15:13:50.208 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2010-01-28 15:13:50.209 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-28 15:13:50.209 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-28 15:13:50.209 VDP: LoadBestPreferences(1920x1080, 60)

---

