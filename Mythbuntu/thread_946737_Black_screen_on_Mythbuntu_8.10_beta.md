---
title: "Black screen on Mythbuntu 8.10 beta"
date: 2008-10-13
forum: Mythbuntu
---

### Post by zaurus on 2008-10-13
Hello

I upgraded to Mythbuntu beta and get black screen when try to watch TV. On 8.04 I upgraded from everything was OK. What could be a problem? Codecs, graphic, something else?

KR

---

### Post by mrand on 2008-10-13
> **zaurus said:**
> Hello

I upgraded to Mythbuntu beta and get black screen when try to watch TV. On 8.04 I upgraded from everything was OK. What could be a problem? Codecs, graphic, something else?

KRHowdy KR,
Does the black screen stay there until you hit exit LiveTV, or does it show black for a bit and then exit back automatically?

Also, does mythfrontend.log or mythbackend.log show anything of interest around the timeframe the you perform this action?

[INDENT]Marc[/INDENT]

---

### Post by zaurus on 2008-10-13
> **mrand said:**
> Howdy KR,
Does the black screen stay there until you hit exit LiveTV, or does it show black for a bit and then exit back automatically?

Also, does mythfrontend.log or mythbackend.log show anything of interest around the timeframe the you perform this action?

[INDENT]Marc[/INDENT]

It stays black untill I hit twice exit.

I can see in mythfrontend.log:
"2008-10-13 21:40:47.642 Connected to database 'mythconverg' at host: localhost
2008-10-13 21:40:47.646 DPMS Deactivated 
2008-10-13 21:40:47.666 NVP: Disabling Audio, params(-1,2,44100)
2008-10-13 21:40:47.755 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-13 21:40:47.756 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-10-13 21:40:47.756 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x3834a60) visual(0x3834860) 
                        XJ_depth(24) WxH(1360x768) bpl(4080)
2008-10-13 21:40:47.756 VideoOutputXv Error: Failed to create X buffers.
2008-10-13 21:40:47.809 GLVid, Error: Fatal error
2008-10-13 21:40:47.822 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-13 21:40:47.823 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***
2008-10-13 21:40:47.876 OSD Theme Dimensions W: 640 H: 480
2008-10-13 21:40:48.796 TV: Changing from None to WatchingLiveTV
2008-10-13 21:40:48.803 Realtime priority would require SUID as root.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2008-10-13 21:40:48.856 Video timing method: USleep with busy wait
2008-10-13 21:40:53.028 VideoOutputXv Error: 
***
* Your system is not capable of displaying the
* full framerate at 1360x768 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

And for mythbackend.log I can see this:

"2008-10-13 21:37:17.287 DVBChan(1:0) Warning: Your frequency setting (11900100) is out of range. (min/max:950000/2150000)
2008-10-13 21:37:17.340 DVBChan(1:0) Warning: Unsupported fec_inner parameter.
2008-10-13 21:37:18.291 DVBChan(2:0) Warning: Your frequency setting (11900100) is out of range. (min/max:950000/2150000)
2008-10-13 21:37:18.332 DVBChan(2:0) Warning: Unsupported fec_inner parameter."

Is that explains something?

KR

---

### Post by mrand on 2008-10-21
> **zaurus said:**
> It stays black untill I hit twice exit.
<...>
"2008-10-13 21:37:17.287 DVBChan(1:0) Warning: Your frequency setting (11900100) is out of range. (min/max:950000/2150000)
2008-10-13 21:37:17.340 DVBChan(1:0) Warning: Unsupported fec_inner parameter.
2008-10-13 21:37:18.291 DVBChan(2:0) Warning: Your frequency setting (11900100) is out of range. (min/max:950000/2150000)
2008-10-13 21:37:18.332 DVBChan(2:0) Warning: Unsupported fec_inner parameter."

Is that explains something?

KR

Sorry - I missed your reply on this.  As I'm sure you can see, the frontend.log shows all sorts of video related errors.  Searching around google on VideoOutputXv Error: provides a few hits, including possible changes to the xorg.conf to work correctly with your video card and drivers.
On recommendation was to change
Option      "OpenGLOverlay" "no"
to
Option     "TVOverlay"

If that doesn't work, you might search a bit more and post back if you find a combination of settings that work.

But before doing that, it might be worth tackling the error in the backend.log  The fec_inner error and out of range frequency setting both seem like two things ripe for fixing.  Unfortunately the extent of my knowledge about digital tuning frequencies on MythTV is that you can easily change it on Mythweb.  If they are set correct, I'm afraid I don't have additional ideas.

Hopefully someone else will pipe up with more questions for you!

[INDENT]Marc[/INDENT]

---

