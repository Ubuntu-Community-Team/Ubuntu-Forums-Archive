---
title: "DVD Playback Issues with MythDVD (Internal Player)"
date: 2008-08-21
forum: Mythbuntu
---

### Post by SeanOB on 2008-08-21
Hello,

I'm having issues playing some newer DVDs.  My old DVDs still play just fine.  I'm not sure if this an ARccOS issue or something else.

When I play the movie the previews and menus are fine but when the movie starts I see a lot of blocking, stuttering, and sometimes the player just gives up.

Is anyone else seeing this?

If it helps I've seen this issue with these titles:
Running with Scissors
Stranger than Fiction
The Illusionist

Should I revert to using xine? Will that even work?
And if so - anyone have the xine entry for the 'external player' line?  And I'm also going to need the "old" lircrc that works with xine.

Thanks!

-Sean

---

### Post by pootle42 on 2008-08-21
I think I may have this too.  I can only play a few minutes into the golden compass and it dies.  On a Windows PC, I can play the while movie using powerdvd no problem.

---

### Post by nrune on 2008-08-21
Yes I am seening pretty much the same thing with any movie. 

From the logs, not sure if it helps.

```
2008-08-20 14:27:02.845 Detected MediaType MEDIATYPE_DVD
2008-08-20 14:27:07.177 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000160
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001f520
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00034e1c
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/nrune/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-08-20 14:27:07.569 Opened DVD device at //cdrom/
2008-08-20 14:27:07.569 There are 1 titles on the disk
2008-08-20 14:27:07.569 Title 0 has 0 parts.
2008-08-20 14:27:07.580 DPMS Deactivated 
2008-08-20 14:27:07.792 AFD: Opened codec 0x3a8afc0, id(MPEG2VIDEO) type(Video)
2008-08-20 14:27:07.793 NVP: Disabling Audio, params(-1,-1,-1)
2008-08-20 14:27:07.804 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-08-20 14:27:07.811 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-20 14:27:07.876 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2008-08-20 14:27:07.903 OSD Theme Dimensions W: 640 H: 480
2008-08-20 14:27:09.640 TV: Changing from None to WatchingPreRecorded
2008-08-20 14:27:09.752 OpenGLVideoSync()
2008-08-20 14:27:09.787 Video timing method: SGI OpenGL
2008-08-20 14:27:10.204 AFD: Warning, video codec 0x3a8afc0 id(MPEG2VIDEO) type (Video) already open.
2008-08-20 14:27:10.293 AFD: codec AC3 has 0 channels
2008-08-20 14:27:10.383 AFD: Opened codec 0xb2c8c0, id(AC3) type(Audio)
2008-08-20 14:27:10.384 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-20 14:27:10.385 Opening ALSA audio device 'default'.
2008-08-20 14:27:10.429 NVP: Enabling Audio
2008-08-20 14:27:10.429 AFD: Warning, audio codec 0xb2c8c0 id(AC3) type (Audio) already open, leaving it alone.
2008-08-20 14:27:10.429 AFD: codec AC3 has 2 channels
2008-08-20 14:27:22.611 AFD: Warning, video codec 0x3a8afc0 id(MPEG2VIDEO) type (Video) already open.
2008-08-20 14:27:22.623 AFD: Opened codec 0x4c81d10, id(DVD_SUBTITLE) type(Subtitle)
2008-08-20 14:27:22.623 NVP: Disabling Audio, params(-1,-1,-1)
2008-08-20 14:27:22.666 AFD: Warning, video codec 0x3a8afc0 id(MPEG2VIDEO) type (Video) already open.
2008-08-20 14:27:22.666 AFD: codec AC3 has 0 channels
2008-08-20 14:27:22.667 AFD: Opened codec 0x53a8fc0, id(AC3) type(Audio)
2008-08-20 14:27:22.670 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-20 14:27:22.670 Opening ALSA audio device 'default'.
2008-08-20 14:27:22.714 NVP: Enabling Audio
2008-08-20 14:27:36.294 [ac3 @ 0x7f9975a475b0]cplendf = 2 < cplbegf = 9
2008-08-20 14:27:36.294 [ac3 @ 0x7f9975a475b0]error parsing the audio block
2008-08-20 14:27:36.296 WriteAudio: buffer underrun
2008-08-20 14:27:36.390 DPMS Deactivated 
2008-08-20 14:27:53.279 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2008-08-20 14:27:53.294 NVP: prebuffering pause
2008-08-20 14:27:53.297 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2008-08-20 14:27:53.305 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2008-08-20 14:27:54.355 AFD: Opened codec 0x3a8afc0, id(MPEG2VIDEO_XVMC) type(Video)
2008-08-20 14:27:54.355 AFD: Opened codec 0x4c81d10, id(DVD_SUBTITLE) type(Subtitle)
2008-08-20 14:27:54.355 NVP: Disabling Audio, params(-1,-1,-1)
2008-08-20 14:27:54.561 AFD: Warning, video codec 0x3a8afc0 id(MPEG2VIDEO_XVMC) type (Video) already open.
2008-08-20 14:27:54.715 AFD: codec AC3 has 0 channels
2008-08-20 14:27:54.720 AFD: Opened codec 0x564a820, id(AC3) type(Audio)
2008-08-20 14:27:54.721 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-20 14:27:54.721 Opening ALSA audio device 'default'.
2008-08-20 14:27:54.757 NVP: Enabling Audio
2008-08-20 14:27:54.764 NVP: Prebuffer wait timed out 10 times.
2008-08-20 14:27:54.786 AFD: Warning, video codec 0x3a8afc0 id(MPEG2VIDEO_XVMC) type (Video) already open.
2008-08-20 14:27:54.786 AFD: Warning, audio codec 0x564a820 id(AC3) type (Audio) already open, leaving it alone.
2008-08-20 14:27:54.786 AFD: codec AC3 has 2 channels
2008-08-20 14:27:54.786 AFD: codec AC3 has 0 channels
2008-08-20 14:27:54.787 AFD: Opened codec 0x5167b20, id(AC3) type(Audio)
2008-08-20 14:27:54.787 NVP: Disabling Audio, params(0,0,0)
2008-08-20 14:27:54.821 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-20 14:27:54.821 Opening ALSA audio device 'default'.
2008-08-20 14:27:54.857 NVP: Enabling Audio
2008-08-20 14:27:54.858 AFD: Warning, audio codec 0x564a820 id(AC3) type (Audio) already open, leaving it alone.
2008-08-20 14:27:54.858 AFD: codec AC3 has 2 channels
2008-08-20 14:27:54.858 AFD: Warning, audio codec 0x5167b20 id(AC3) type (Audio) already open, leaving it alone.
2008-08-20 14:27:54.858 AFD: codec AC3 has 2 channels
2008-08-20 14:27:55.537 NVP: prebuffering pause
2008-08-20 14:27:55.538 WriteAudio: buffer underrun
2008-08-20 14:27:55.563 NVP: prebuffering pause
2008-08-20 14:27:55.581 NVP: prebuffering pause
2008-08-20 14:27:55.596 NVP: prebuffering pause
2008-08-20 14:30:46.037 [ac3 @ 0x7f9975a475b0]delta bit allocation strategy reserved
2008-08-20 14:30:46.037 [ac3 @ 0x7f9975a475b0]error parsing the audio block
2008-08-20 14:30:46.139 [mpegvideo_xvmc @ 0x7f9975a475b0]mb incr damaged
2008-08-20 14:30:46.139 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 13 18
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 4 19
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid cbp at 26 20
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid cbp at 0 21
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid mb type in B Frame at 3 22
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid mb type in B Frame at 9 23
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 4 24
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]mb incr damaged
2008-08-20 14:30:46.140 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid mb type in B Frame at 23 26
2008-08-20 14:30:46.141 [mpegvideo_xvmc @ 0x7f9975a475b0]Warning MVs not available
2008-08-20 14:30:46.364 Error reading block from DVD: Expected NAV packet but none found.
2008-08-20 14:30:46.367 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 31 8
2008-08-20 14:30:46.367 [mpegvideo_xvmc @ 0x7f9975a475b0]mb incr damaged
2008-08-20 14:30:46.367 [mpegvideo_xvmc @ 0x7f9975a475b0]mb incr damaged
2008-08-20 14:30:46.367 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid mb type in P Frame at 8 16
2008-08-20 14:30:46.368 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 16 18
2008-08-20 14:30:46.368 [mpegvideo_xvmc @ 0x7f9975a475b0]slice mismatch
2008-08-20 14:30:46.368 [mpegvideo_xvmc @ 0x7f9975a475b0]slice mismatch
2008-08-20 14:30:46.368 [mpegvideo_xvmc @ 0x7f9975a475b0]mb incr damaged
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid cbp at 14 23
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 5 22
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid mb type in P Frame at 36 23
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]slice mismatch
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 1 25
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]invalid mb type in P Frame at 4 26
2008-08-20 14:30:46.369 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 0 27
2008-08-20 14:30:46.370 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 0 28
2008-08-20 14:30:46.370 [mpegvideo_xvmc @ 0x7f9975a475b0]ac-tex damaged at 0 29
2008-08-20 14:30:46.370 [mpegvideo_xvmc @ 0x7f9975a475b0]Warning MVs not available
2008-08-20 14:30:46.378 Error reading block from DVD: Expected NAV packet but none found.
```

---

### Post by lledurt on 2009-02-18
I am having a similar issue with newer DVD's.  The newer DVD's have a little trouble playing on the internal player.  I ripped them to iso files and then they will play on my ubuntu 8.04 computers remotely using the mythfrontend but not my mythbuntu 8.10 computer.  Here is the thread I started.  I hope that this will help help.  

[http://ubuntuforums.org/showthread.php?p=6759536#post6759536](http://ubuntuforums.org/showthread.php?p=6759536#post6759536)

---

### Post by klc5555 on 2009-02-19
> **SeanOB said:**
> Hello,

I'm having issues playing some newer DVDs.  My old DVDs still play just fine.  I'm not sure if this an ARccOS issue or something else.

When I play the movie the previews and menus are fine but when the movie starts I see a lot of blocking, stuttering, and sometimes the player just gives up.

Is anyone else seeing this?

If it helps I've seen this issue with these titles:
Running with Scissors
Stranger than Fiction
The Illusionist

Should I revert to using xine? Will that even work?
And if so - anyone have the xine entry for the 'external player' line?  And I'm also going to need the "old" lircrc that works with xine.

Thanks!

-Sean

I have to say that I've found myth's internal player to be so hit-and-miss with regard to what commercial DVDs it will play, or stutter, or lock up and crash on (with Linux players in general not being that much better) that I gave up on the whole business. I have a cheap dedicated DVD player hooked to the composite input of a Hauppauge PVR 150 that I use for watching commercial DVDs on the myth machines. It's saved me untold hours of frustration and vastly improved the WAF in the 5 months since I hooked it up that way.

---

### Post by 4ebees on 2009-02-23
> **klc5555 said:**
> I have to say that I've found myth's internal player to be so hit-and-miss with regard to what commercial DVDs it will play, or stutter, or lock up and crash on (with Linux players in general not being that much better) that I gave up on the whole business. I have a cheap dedicated DVD player hooked to the composite input of a Hauppauge PVR 150 that I use for watching commercial DVDs on the myth machines. It's saved me untold hours of frustration and vastly improved the WAF in the 5 months since I hooked it up that way.

Hi Klc5555,

I'm curious as to how you 'see' the DVD playing. What do you tune your mythbuntu box to?

I guess I'm asking for a 'how do you do this', if you don't mind :)) as this sounds like it may be the solution for my problem.

---

### Post by klc5555 on 2009-02-23
> **4ebees said:**
> Hi Klc5555,

I'm curious as to how you 'see' the DVD playing. What do you tune your mythbuntu box to?

I guess I'm asking for a 'how do you do this', if you don't mind :)) as this sounds like it may be the solution for my problem.

The cheapo DVD player has a composite output (in addition to coax), which I patch into the composite ports on the 150. I set up a new Video Source in the backend (with "no grabber configured"), called it "External DVD" and in Input Connections linked it to the 150's "Composite" option. No channel needs to be set up or tuned to. "External DVD" becomes a choice in the "Change Input" in the "m" key on screen menu while watching TV.

Because no channel is configured, whenever exiting the backend setup, myth fusses about the composite having "add channel" set as the default for "composite", but this of course can be ignored.

Two very minor quirks: since mythtv buffers everything to hard disk, remote commands given to the DVD player take 4 seconds or more to be seen on screen. And when playing widescreen movies I need to set the aspect ratio to 14:9 or 16:9 in myth's onscreen "m" menu when I begin to watch, since the PVR150 is set to default to 4:3. But these quirks amount to nothing compared to the negative WAF of the previous scenario, where an HBO DVD or similar would be put into myth's internal player and either have unwatchably stuttery playback or would crash the internal player (or mplayer, or xine, or VLC) outright. 

As an aside, I also still occasionally use an old VCR, which lacks composite output. This gets hooked straight into the PVR150's coax port, where the card tunes it at my otherwise empty channel 3, just as used to be done when the VCR was hooked to an analog TV. Makes it easy to archive old tapes to DVD.

Cheers! :)

---

