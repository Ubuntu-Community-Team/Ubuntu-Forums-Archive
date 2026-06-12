---
title: "Choppy Live TV"
date: 2009-02-26
forum: Mythbuntu
---

### Post by dave00001 on 2009-02-26
I have an older system (not too old) that I just put mythbuntu on.  At this point I would be happy with watching live TV - then figure the rest out as I go along - but the video and sound output is really choppy and freezes every second or so.

I've got a pretty bit 22' monitor here that I was hoping to catch the HD and SD OTA broadcasts on.  Between the Mythbuntu manual and the forums, I've managed to scan and pick up 10 HD - quality channels that all come in between 50 and 90%.  If I could solve this choppy output problem I would be in heaven....

I heard from other posts that it could be an XvMC issue, but I think I have the proper driver downloaded for my NVIDIA GEforce 6600, so this can't be the issue can it??

My Specs:
P4 2.0 GHz 1.2 GB RAM
GEforce 6600 OC
On-board sound
PCHDTV-5500 capture card

---

### Post by dave00001 on 2009-02-26
Ok - so I may be in the deep stuff now...  I tried the following to enable XvMC:

gksu mousepad /etc/X11/XmVCConfig

Then I changed the line to 

libXvMCNVIDIA.so.1  

and made sure the driver in my Xorg.conf was set to "nvidia".

Now when I try to watch live TV I get nothing....  help!

EDIT:
I also changed the Xorg.conf line under device to say:

Option "RenderAccel" "true"
Option "NVAGP" "1"
Option "UseEvents" "True"
Option "XvmcUsesTextures" "false" 

This helped a little bit, but it's still pretty choppy....  I'll keep working on this but any help is appreciated

---

### Post by Hipstor on 2009-03-11
Dave
Is the choppy playback just on live TV? Or is it still choppy when watching prerecorded shows? As a test try recording a 30min show and then watch it when nothing else is recording. Yes I know you want it live, this is only a test. ;)

My theory is that your comp has the horsepower to show HD (at least 2Ghz minimum). But HD choppiness can be caused by static. On analog TV static shows up as snow on the screen. But ATSC is all digital, you either get a perfect picture or you don't get anything. It is immune to static right up to the point that a burst of static drowns out the signal and you lose your picture. Then when the static fades a millisecond later your picture shows up again. See it's choppy. Other symptoms of static include high pitched squeaks and strange blocks of color appearing on your screen. 

Another test you may try is moving or upgrading your antenna. While analog is still being broadcast try borrowing a friend's old TV. Hook it to your antenna. Adjust the antenna for best analog reception. Then without moving the antenna AT ALL, hook it back up to your computer and try watching live HD again.

You probably already did this but try [http://www.antennaweb.org/aw/Address.aspx]("http://www.antennaweb.org/aw/Address.aspx") It will at least tell you where to point your antenna for best reception.

---

### Post by newlinux on 2009-03-12
Have you setup your playback profiles to use XvMC? A 2.0Ghgz CPU will probably need XvMC for smooth playback. have you verified that it is actually using XvMC (you can check the logs, but the easiest way to know is that your OSD when using XvMC will be black and white).

---

### Post by dave00001 on 2009-03-19
I just tried doing a 30-minute recording.  The signal strength seemed to be around 80-90% over the 30-minute interval, but when I tried to play it back I had the same choppyness.  I even built a different antenna (see [http://uhfhdtvantenna.blogspot.com/](http://uhfhdtvantenna.blogspot.com/)) and hooked up my balun right at the antenna to avoid signal distortion.  The way I see it, my problem is with either a) not good enough signal or b) not a fast enough cpu...

And I have no idea whether I'm using xmvc...  I don't know what you mean by OSD - but when I change channels trying to view live tv the little tab is pink... does this help?

---

### Post by stevecartermo on 2009-03-19
I also use a P4 2.0 GHZ machine with an NVIDIA 5200 using XvMC and it is OK for watching ATSC OTA signals.

---

### Post by dave00001 on 2009-03-20
Well there is hope for me yet!
If I may ask, are you viewing 1080p and if so, how did you get xvmc to work???  I can't seem to get a very good answer for this anywhere....  Also, how is your signal strength?


EDIT:  Just figured out what OSD means.  And it's blue, not black.

---

### Post by newlinux on 2009-03-20
> **dave00001 said:**
> Well there is hope for me yet!
If I may ask, are you viewing 1080p and if so, how did you get xvmc to work???  I can't seem to get a very good answer for this anywhere....  Also, how is your signal strength?


EDIT:  Just figured out what OSD means.  And it's blue, not black.

If there is blue in it, you're definitely not using XvMC. 
[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC) gives you the instructions. In a nutshell - you need to:

1. create the file /etc/X111/XvMCConfig and put ```
libXvMCNVIDIA_dynamic.so.1
``` in it.

2. Modify your /etc/X11/xorg.conf file and put
```
        Option		"UseEvents" 	"on"
``` in your nvidia driver device section
3. Restart your X display (Ctrl-alt-Backspace). to verify XvMC is available to be used do:
```
cat /var/log/Xorg.0.log | grep Motion 
```

You should see a line about Xvideo Motion Compensation being loaded

4. In myth, you need to modify your playback profiles to use XvMC  (use the standard XvMC decoder, make sure Max CPUs is set to 1).

If you have problems let us know and I can help you troubleshoot.

---

### Post by stevecartermo on 2009-03-20
I believe the maximum signal I am watching is 1080i. They are all ATSC digital TV broadcasts. My tuning has to be above 70% or the picture and sound breaks up and eventually the frontend will lockup.

Sounds like your XvMC isn't working yet.

---

### Post by dave00001 on 2009-03-21
So, I've added the line in xorg.conf, and created the XvMCConfig file, as directed.  I checked using 

cat /var/log/Xorg.0.log | grep Motion

and it came back as

(II) Loading extension XVideo-MotionCompensation

which makes me think XvMC is working properly.  However, after I restart my X-display, I still get the same blue OSD and choppy audio/video.  (Note - I did set my playback profile to use Standard XvMC and Max CPU = 1)

I'm not sure if if it's an issue, but I have an AGP video card - and this site:

[http://www.mythtv.org/wiki/XvMC#NVIDIA_2](http://www.mythtv.org/wiki/XvMC#NVIDIA_2)

says there may be a problem with them...  I've even tried adding the line

Option "NVAGP" = "0"

as the above link suggested, to my xorg.conf file and no changes noticed.

---

### Post by newlinux on 2009-03-21
which playback profile are you using? Did you set the decoder to xvmc for the right resolution? To start, the easiest thing to do is create a new playback profile that uses XvMC for all resolutions, using standard xvmc decoder and xvmc-blit, 1CPU, bob 2x deinterlacer, and one field fallback deinterlacer. Then check your frontend logs to see what is happening. XvMC is loaded, but myth isn't using it yet, for some reason. The logs should tell you definitively.

---

### Post by dave00001 on 2009-03-21
Ok.  So I deleted all my playback profiles, and added a new one just as you said...  It still doesn't help, but maybe these frontend logs will shed some light:

Starting mythfrontend.real..
2009-03-21 14:20:30.248 New DB connection, total: 2
2009-03-21 14:20:30.248 Connected to database 'mythconverg' at host: localhost
2009-03-21 14:20:30.252 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-21 14:20:30.253 Enabled verbose msgs:  important general
2009-03-21 14:20:30.931 No theme dir: /home/dave/.mythtv/themes/Mythbuntu-8.04
2009-03-21 14:20:30.933 Primary screen 0.
2009-03-21 14:20:30.934 Using screen 0, 1680x1050 at 0,0
2009-03-21 14:20:30.935 No theme dir: /home/dave/.mythtv/themes/Mythbuntu-8.04
2009-03-21 14:20:30.936 Switching to square mode (Mythbuntu-8.04)
2009-03-21 14:20:30.960 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-21 14:20:30.961 lirc_init failed for mythtv, see preceding messages
2009-03-21 14:20:30.962 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dave/.mythtv/joystickmenurc
2009-03-21 14:20:32.938 Specified base font 'medium' does not exist for font clock
2009-03-21 14:20:32.938 Specified base font 'medium' does not exist for font small
2009-03-21 14:20:32.938 Specified base font 'medium' does not exist for font medium
2009-03-21 14:20:32.939 Specified base font 'medium' does not exist for font large
2009-03-21 14:20:32.941 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-03-21 14:20:33.183 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-21 14:20:33.253 Registering Internal as a media playback plugin.
2009-03-21 14:20:33.393 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-21 14:20:33.455 Failed to run 'cdrecord --scanbus'
2009-03-21 14:20:33.461 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-21 14:20:33.467 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-21 14:20:33.523 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.3:5060 NAT address 192.168.2.3
SIP: Cannot register; proxy, username or password not set
2009-03-21 14:20:33.704 No theme dir: /home/dave/.mythtv/themes/Mythbuntu-8.04
2009-03-21 14:20:38.029 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-21 14:20:38.030 Using protocol version 40
2009-03-21 14:20:38.047 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 14:20:38.048 Using protocol version 40
2009-03-21 14:20:39.215 New DB connection, total: 3
2009-03-21 14:20:39.216 Connected to database 'mythconverg' at host: localhost
2009-03-21 14:20:39.242 NVP: Disabling Audio, params(-1,2,44100)
2009-03-21 14:20:39.259 DPMS Deactivated 
2009-03-21 14:20:39.291 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-21 14:20:39.296 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-21 14:20:39.392 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-21 14:20:39.400 OSD Theme Dimensions W: 640 H: 480
2009-03-21 14:20:40.092 TV: Changing from None to WatchingLiveTV
2009-03-21 14:20:40.102 Realtime priority would require SUID as root.
2009-03-21 14:20:40.202 Video timing method: USleep with busy wait
2009-03-21 14:20:42.188 RingBuf(/var/lib/mythtv/recordings/1081_20090321142039.mpg): Waited 1.0 seconds for data to become available...
2009-03-21 14:20:42.188 Checking to see if there's a new livetv program to switch to..
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
2009-03-21 14:20:42.982 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-21 14:20:42.987 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-21 14:20:43.364 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-21 14:20:43.687 AFD: Opened codec 0xaddb760, id(MPEG2VIDEO) type(Video)
2009-03-21 14:20:43.688 AFD: codec AC3 has 6 channels
2009-03-21 14:20:43.689 AFD: Opened codec 0x9fa6240, id(AC3) type(Audio)
2009-03-21 14:20:43.846 NVP: Prebuffer wait timed out 10 times.
2009-03-21 14:20:43.991 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-21 14:20:43.991 Opening ALSA audio device 'default'.
2009-03-21 14:20:44.023 NVP: Enabling Audio
2009-03-21 14:20:45.577 NVP: prebuffering pause
2009-03-21 14:20:46.657 NVP: prebuffering pause
2009-03-21 14:20:47.840 WriteAudio: buffer underrun
2009-03-21 14:20:47.901 WriteAudio: buffer underrun
2009-03-21 14:20:47.959 WriteAudio: buffer underrun
2009-03-21 14:20:48.055 WriteAudio: buffer underrun
2009-03-21 14:20:48.116 WriteAudio: buffer underrun
2009-03-21 14:20:48.191 WriteAudio: buffer underrun
2009-03-21 14:20:48.266 WriteAudio: buffer underrun
2009-03-21 14:20:48.330 WriteAudio: buffer underrun
2009-03-21 14:20:48.399 WriteAudio: buffer underrun
2009-03-21 14:20:48.468 WriteAudio: buffer underrun
2009-03-21 14:20:48.531 WriteAudio: buffer underrun
2009-03-21 14:20:48.594 WriteAudio: buffer underrun
2009-03-21 14:20:48.669 WriteAudio: buffer underrun
2009-03-21 14:20:48.729 WriteAudio: buffer underrun
2009-03-21 14:20:48.798 WriteAudio: buffer underrun
2009-03-21 14:20:48.869 WriteAudio: buffer underrun
2009-03-21 14:20:48.932 WriteAudio: buffer underrun
2009-03-21 14:20:49.001 WriteAudio: buffer underrun
2009-03-21 14:20:49.075 WriteAudio: buffer underrun
2009-03-21 14:20:49.138 WriteAudio: buffer underrun
2009-03-21 14:20:49.217 WriteAudio: buffer underrun
2009-03-21 14:20:49.301 WriteAudio: buffer underrun
2009-03-21 14:20:49.381 WriteAudio: buffer underrun
2009-03-21 14:20:49.459 WriteAudio: buffer underrun
2009-03-21 14:20:49.543 WriteAudio: buffer underrun
2009-03-21 14:20:49.562 NVP: prebuffering pause
2009-03-21 14:20:50.921 NVP: prebuffering pause
2009-03-21 14:20:51.110 TV: Attempting to change from WatchingLiveTV to None
2009-03-21 14:20:51.667 TV: Changing from WatchingLiveTV to None
2009-03-21 14:20:51.714 DPMS Reactivated.
Destroying SipFsm object 
2009-03-21 14:20:54.631 Deleting UPnP client...


Sorry it's so long.


PS - how do you post terminal output so it doesn't take up so much space???

EDIT:  If I'm not mistaken, I think the important line might be 

Desired video renderer 'xvmc-blit' not available. codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.

Hmmm...

---

### Post by newlinux on 2009-03-21
2009-03-21 14:20:39.291 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.

that is problem... Myth still thinks xvmc isn't available. Not sure why...

Try playing back the while running mythfrontend with the -v playback option (for more verbose logging)
```

mythfrontend -v playback

```

---

### Post by dave00001 on 2009-03-22
Ok - here is the output (note I cut off the first bit which was exactly the same verbatim as previously posted, so I will start from when I initialize live TV viewing)


2009-03-21 22:39:17.212 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 22:39:17.213 Using protocol version 40
2009-03-21 22:39:18.348 LiveTVChain(live-dave-desktop-2009-03-21T22:39:17): ReloadAll(): Added new recording
2009-03-21 22:39:18.367 TV: StartRecorder(): took 1 ms to start recorder.
2009-03-21 22:39:18.395 New DB connection, total: 3
2009-03-21 22:39:18.395 Connected to database 'mythconverg' at host: localhost
2009-03-21 22:39:18.422 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-03-21 22:39:18.428 NVP: Disabling Audio, params(-1,2,44100)
2009-03-21 22:39:18.429 DPMS Deactivated 
2009-03-21 22:39:18.442 VideoOutput: Allowed renderers: xv-blit,xshm,opengl,xlib
2009-03-21 22:39:18.443 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,xv-blit,opengl
2009-03-21 22:39:18.447 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-21 22:39:18.451 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-21 22:39:18.452 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-21 22:39:18.452 VDP: LoadBestPreferences(720x576, 60)
2009-03-21 22:39:18.452 VideoOutput: Trying video renderer: xv-blit
2009-03-21 22:39:18.454 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-21 22:39:18.455 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-21 22:39:18.455 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-21 22:39:18.489 VideoOutputXv: ctor
2009-03-21 22:39:18.491 XOff: 0, YOff: 0
2009-03-21 22:39:18.491 VDP: LoadBestPreferences(720x576, 60)
2009-03-21 22:39:18.492 Display Rect  left: 0, top: 0, width: 1680, height: 1050, aspect: 1.33333
2009-03-21 22:39:18.492 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-03-21 22:39:18.494 VideoOutputXv: Pixel dimensions: Screen 1680x1050, window 1680x1050
2009-03-21 22:39:18.496 VideoOutputXv: Estimated display dimensions: 427x267 mm  Aspect: 1.59925
2009-03-21 22:39:18.496 VideoOutputXv: Estimated window dimensions: 427x267 mm  Aspect: 1.59925
2009-03-21 22:39:18.497 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xv-blit,xshm,opengl,xlib
2009-03-21 22:39:18.497 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-21 22:39:18.497 VDP: SetVideoRenderer(xv-blit)
2009-03-21 22:39:18.498 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-21 22:39:18.498 VDP: New preferences: rend(xv-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-21 22:39:18.506 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-21 22:39:18.506 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-21 22:39:18.506 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-21 22:39:18.506 VDP: LoadBestPreferences(720x576, 60)
2009-03-21 22:39:18.507 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  18
2009-03-21 22:39:18.507 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.508 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.508 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:18.508 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.508 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.509 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:18.509 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  8
2009-03-21 22:39:18.509 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.509 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.510 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-21 22:39:18.510 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.510 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.510 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-21 22:39:18.511 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask XvImageMask  10
2009-03-21 22:39:18.511 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.511 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.511 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:18.511 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.511 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.512 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:18.512 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask  0
2009-03-21 22:39:18.512 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:18.512 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:18.517 VideoOutputXv: Here...
2009-03-21 22:39:18.518 VideoOutputXv: Grabbed xv port 275
2009-03-21 22:39:18.518 VideoOutputXv: XVideo surface found on port 275
2009-03-21 22:39:18.519 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-21 22:39:18.519 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-03-21 22:39:18.519 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-03-21 22:39:18.520 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-03-21 22:39:18.520 VideoOutputXv: XVideo Format #3 is 'I420'
2009-03-21 22:39:18.520 VideoOutputXv: Using XVideo Format 'YV12'
2009-03-21 22:39:18.520 VideoOutputXv: CreateShmImages(32): video_dim: 720x576
2009-03-21 22:39:18.620 VDP: SetVideoRenderer(xv-blit)
2009-03-21 22:39:18.620 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-03-21 22:39:18.621 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-03-21 22:39:18.621 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-21 22:39:18.621 Display Rect  left: 139, top: 0, width: 1401, height: 1050, aspect: 1.59925
2009-03-21 22:39:18.622 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-03-21 22:39:18.625 Over/underscan. V: 0, H: 0
2009-03-21 22:39:18.625 Display Rect  left: 139, top: 0, width: 1401, height: 1050, aspect: 1.59925
2009-03-21 22:39:18.625 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-03-21 22:39:18.626 VDP: LoadBestPreferences(720x576, 25)
2009-03-21 22:39:18.627 NVP: LoadFilters(''..) -> 0
2009-03-21 22:39:18.631 OSD Theme Dimensions W: 640 H: 480
2009-03-21 22:39:19.283 TV: StartPlayer(): took 838 ms to start player.
2009-03-21 22:39:19.283 TV: Changing from None to WatchingLiveTV
2009-03-21 22:39:19.283 NVP: ClearAfterSeek(1)
2009-03-21 22:39:19.297 VideoOutputXv: ClearAfterSeek()
2009-03-21 22:39:19.302 VideoOutputXv: DiscardFrames(0)
2009-03-21 22:39:19.302 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:19.303 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:19.303 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:19.306 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2009-03-21 22:39:19.308 Using deinterlace method bobdeint
2009-03-21 22:39:19.312 Realtime priority would require SUID as root.
2009-03-21 22:39:19.319 rate: 25 speed: 1 skip: 1 = interval 40000
2009-03-21 22:39:19.414 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-03-21 22:39:19.414 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-03-21 22:39:19.414 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2009-03-21 22:39:19.414 Set video sync frame interval to 40000
2009-03-21 22:39:19.415 Using audio as timebase
2009-03-21 22:39:19.415 Video timing method: USleep with busy wait
2009-03-21 22:39:19.415 Refresh rate: 16679, frame interval: 40000
2009-03-21 22:39:19.455 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:20.421 LiveTVChain(live-dave-desktop-2009-03-21T22:39:17): ReloadAll(): Added new recording
2009-03-21 22:39:20.422 LiveTVChain(live-dave-desktop-2009-03-21T22:39:17): SwitchTo(1)
2009-03-21 22:39:20.422 LiveTVChain(live-dave-desktop-2009-03-21T22:39:17): Entry@1: '1081_20090321223919'
2009-03-21 22:39:20.423 JumpToProgram(void)
2009-03-21 22:39:20.458 RingBuf(/var/lib/mythtv/recordings/1081_20090321223917.mpg): OpenFile(/var/lib/mythtv/recordings/1081_20090321223919.mpg, 12)
2009-03-21 22:39:20.504 RingBuf(/var/lib/mythtv/recordings/1081_20090321223919.mpg): CalcReadAheadThresh(3050047825 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-21 22:39:20.542 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:20.742 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:20.750 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:20.950 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:20.958 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.158 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.166 NVP: Waiting for prebuffer.. 3 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.366 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.374 NVP: Waiting for prebuffer.. 4 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.575 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.582 NVP: Waiting for prebuffer.. 5 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.679 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 18296000 at 0x0xa1f8b30
2009-03-21 22:39:21.681 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-21 22:39:21.682 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-21 22:39:21.682 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-21 22:39:21.682 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-21 22:39:21.682 Using 0 CPUs for decoding
2009-03-21 22:39:21.684 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-21 22:39:21.684 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-21 22:39:21.685 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-21 22:39:21.685 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-21 22:39:21.687 VideoOutputXv: XvMC version: 1.1
2009-03-21 22:39:21.689 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 306, 2750 <=p, port, surfNum)
2009-03-21 22:39:21.693 Trying XvMC port 275
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
2009-03-21 22:39:21.695 Trying XvMC port 276
2009-03-21 22:39:21.695 Trying XvMC port 277
2009-03-21 22:39:21.695 Trying XvMC port 278
2009-03-21 22:39:21.695 Trying XvMC port 279
2009-03-21 22:39:21.695 Trying XvMC port 280
2009-03-21 22:39:21.695 Trying XvMC port 281
2009-03-21 22:39:21.695 Trying XvMC port 282
2009-03-21 22:39:21.695 Trying XvMC port 283
2009-03-21 22:39:21.696 Trying XvMC port 284
2009-03-21 22:39:21.696 Trying XvMC port 285
2009-03-21 22:39:21.696 Trying XvMC port 286
2009-03-21 22:39:21.696 Trying XvMC port 287
2009-03-21 22:39:21.696 Trying XvMC port 288
2009-03-21 22:39:21.696 Trying XvMC port 289
2009-03-21 22:39:21.696 Trying XvMC port 290
2009-03-21 22:39:21.696 Trying XvMC port 291
2009-03-21 22:39:21.696 Trying XvMC port 292
2009-03-21 22:39:21.697 Trying XvMC port 293
2009-03-21 22:39:21.697 Trying XvMC port 294
2009-03-21 22:39:21.697 Trying XvMC port 295
2009-03-21 22:39:21.697 Trying XvMC port 296
2009-03-21 22:39:21.697 Trying XvMC port 297
2009-03-21 22:39:21.697 Trying XvMC port 298
2009-03-21 22:39:21.697 Trying XvMC port 299
2009-03-21 22:39:21.697 Trying XvMC port 300
2009-03-21 22:39:21.697 Trying XvMC port 301
2009-03-21 22:39:21.698 Trying XvMC port 302
2009-03-21 22:39:21.698 Trying XvMC port 303
2009-03-21 22:39:21.698 Trying XvMC port 304
2009-03-21 22:39:21.698 Trying XvMC port 305
2009-03-21 22:39:21.698 Trying XvMC port 306
2009-03-21 22:39:21.698 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 338, 3070 <=p, port, surfNum)
2009-03-21 22:39:21.699 Trying XvMC port 307
2009-03-21 22:39:21.699 Trying XvMC port 308
2009-03-21 22:39:21.700 Trying XvMC port 309
2009-03-21 22:39:21.700 Trying XvMC port 310
2009-03-21 22:39:21.700 Trying XvMC port 311
2009-03-21 22:39:21.700 Trying XvMC port 312
2009-03-21 22:39:21.700 Trying XvMC port 313
2009-03-21 22:39:21.700 Trying XvMC port 314
2009-03-21 22:39:21.700 Trying XvMC port 315
2009-03-21 22:39:21.700 Trying XvMC port 316
2009-03-21 22:39:21.700 Trying XvMC port 317
2009-03-21 22:39:21.701 Trying XvMC port 318
2009-03-21 22:39:21.701 Trying XvMC port 319
2009-03-21 22:39:21.701 Trying XvMC port 320
2009-03-21 22:39:21.701 Trying XvMC port 321
2009-03-21 22:39:21.701 Trying XvMC port 322
2009-03-21 22:39:21.701 Trying XvMC port 323
2009-03-21 22:39:21.701 Trying XvMC port 324
2009-03-21 22:39:21.701 Trying XvMC port 325
2009-03-21 22:39:21.702 Trying XvMC port 326
2009-03-21 22:39:21.702 Trying XvMC port 327
2009-03-21 22:39:21.702 Trying XvMC port 328
2009-03-21 22:39:21.702 Trying XvMC port 329
2009-03-21 22:39:21.702 Trying XvMC port 330
2009-03-21 22:39:21.702 Trying XvMC port 331
2009-03-21 22:39:21.702 Trying XvMC port 332
2009-03-21 22:39:21.702 Trying XvMC port 333
2009-03-21 22:39:21.702 Trying XvMC port 334
2009-03-21 22:39:21.702 Trying XvMC port 335
2009-03-21 22:39:21.703 Trying XvMC port 336
2009-03-21 22:39:21.703 Trying XvMC port 337
2009-03-21 22:39:21.703 Trying XvMC port 338
2009-03-21 22:39:21.703 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 306, 2750 <=p, port, surfNum)
2009-03-21 22:39:21.709 Trying XvMC port 275
2009-03-21 22:39:21.709 Trying XvMC port 276
2009-03-21 22:39:21.709 Trying XvMC port 277
2009-03-21 22:39:21.709 Trying XvMC port 278
2009-03-21 22:39:21.709 Trying XvMC port 279
2009-03-21 22:39:21.709 Trying XvMC port 280
2009-03-21 22:39:21.710 Trying XvMC port 281
2009-03-21 22:39:21.710 Trying XvMC port 282
2009-03-21 22:39:21.710 Trying XvMC port 283
2009-03-21 22:39:21.710 Trying XvMC port 284
2009-03-21 22:39:21.710 Trying XvMC port 285
2009-03-21 22:39:21.710 Trying XvMC port 286
2009-03-21 22:39:21.710 Trying XvMC port 287
2009-03-21 22:39:21.710 Trying XvMC port 288
2009-03-21 22:39:21.711 Trying XvMC port 289
2009-03-21 22:39:21.711 Trying XvMC port 290
2009-03-21 22:39:21.711 Trying XvMC port 291
2009-03-21 22:39:21.711 Trying XvMC port 292
2009-03-21 22:39:21.711 Trying XvMC port 293
2009-03-21 22:39:21.711 Trying XvMC port 294
2009-03-21 22:39:21.711 Trying XvMC port 295
2009-03-21 22:39:21.711 Trying XvMC port 296
2009-03-21 22:39:21.711 Trying XvMC port 297
2009-03-21 22:39:21.712 Trying XvMC port 298
2009-03-21 22:39:21.712 Trying XvMC port 299
2009-03-21 22:39:21.712 Trying XvMC port 300
2009-03-21 22:39:21.712 Trying XvMC port 301
2009-03-21 22:39:21.712 Trying XvMC port 302
2009-03-21 22:39:21.712 Trying XvMC port 303
2009-03-21 22:39:21.712 Trying XvMC port 304
2009-03-21 22:39:21.712 Trying XvMC port 305
2009-03-21 22:39:21.712 Trying XvMC port 306
2009-03-21 22:39:21.712 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 338, 3070 <=p, port, surfNum)
2009-03-21 22:39:21.713 Trying XvMC port 307
2009-03-21 22:39:21.713 Trying XvMC port 308
2009-03-21 22:39:21.713 Trying XvMC port 309
2009-03-21 22:39:21.713 Trying XvMC port 310
2009-03-21 22:39:21.713 Trying XvMC port 311
2009-03-21 22:39:21.713 Trying XvMC port 312
2009-03-21 22:39:21.713 Trying XvMC port 313
2009-03-21 22:39:21.713 Trying XvMC port 314
2009-03-21 22:39:21.714 Trying XvMC port 315
2009-03-21 22:39:21.714 Trying XvMC port 316
2009-03-21 22:39:21.714 Trying XvMC port 317
2009-03-21 22:39:21.714 Trying XvMC port 318
2009-03-21 22:39:21.715 Trying XvMC port 319
2009-03-21 22:39:21.715 Trying XvMC port 320
2009-03-21 22:39:21.715 Trying XvMC port 321
2009-03-21 22:39:21.715 Trying XvMC port 322
2009-03-21 22:39:21.715 Trying XvMC port 323
2009-03-21 22:39:21.715 Trying XvMC port 324
2009-03-21 22:39:21.715 Trying XvMC port 325
2009-03-21 22:39:21.715 Trying XvMC port 326
2009-03-21 22:39:21.716 Trying XvMC port 327
2009-03-21 22:39:21.716 Trying XvMC port 328
2009-03-21 22:39:21.716 Trying XvMC port 329
2009-03-21 22:39:21.716 Trying XvMC port 330
2009-03-21 22:39:21.716 Trying XvMC port 331
2009-03-21 22:39:21.716 Trying XvMC port 332
2009-03-21 22:39:21.716 Trying XvMC port 333
2009-03-21 22:39:21.716 Trying XvMC port 334
2009-03-21 22:39:21.716 Trying XvMC port 335
2009-03-21 22:39:21.717 Trying XvMC port 336
2009-03-21 22:39:21.717 Trying XvMC port 337
2009-03-21 22:39:21.717 Trying XvMC port 338
2009-03-21 22:39:21.717 AFD: InitVideoCodec() 0xafb7960 id(MPEG2VIDEO) type (Video).
2009-03-21 22:39:21.718 VideoOutputXv: InputChanged(1920,1088,1.77778) 'None'->'MPEG2'
2009-03-21 22:39:21.718 VDP: LoadBestPreferences(1920x1088, 25)
2009-03-21 22:39:21.718 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2009-03-21 22:39:21.720 Using deinterlace method bobdeint
2009-03-21 22:39:21.720 VideoOutputXv: DiscardFrames(1)
2009-03-21 22:39:21.721 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.721 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:21.721 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:21.721 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:21.721 VideoOutputXv: DiscardFrames(1)
2009-03-21 22:39:21.722 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.722 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:21.722 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:21.722 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:21.722 VideoOutputXv: DiscardFrames(1)
2009-03-21 22:39:21.723 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:21.723 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:21.723 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:21.723 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:21.726 VideoOutputXv: Closing XVideo port 275
2009-03-21 22:39:21.733 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xv-blit,xshm,opengl,xlib
2009-03-21 22:39:21.733 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-21 22:39:21.734 VDP: SetVideoRenderer(xv-blit)
2009-03-21 22:39:21.734 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-21 22:39:21.734 VDP: New preferences: rend(xv-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-21 22:39:21.737 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-21 22:39:21.737 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-21 22:39:21.737 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-21 22:39:21.737 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-21 22:39:21.738 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  18
2009-03-21 22:39:21.738 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.738 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.738 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:21.738 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.738 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.739 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:21.739 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  8
2009-03-21 22:39:21.739 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.739 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.739 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-21 22:39:21.739 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.739 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.739 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-21 22:39:21.740 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask XvImageMask  10
2009-03-21 22:39:21.740 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.740 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.740 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:21.740 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.740 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.740 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-21 22:39:21.740 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask  0
2009-03-21 22:39:21.740 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-21 22:39:21.741 VideoOutputXv: Has XVideo flags...
2009-03-21 22:39:21.741 VideoOutputXv: Here...
2009-03-21 22:39:21.741 VideoOutputXv: Grabbed xv port 275
2009-03-21 22:39:21.741 VideoOutputXv: XVideo surface found on port 275
2009-03-21 22:39:21.741 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-21 22:39:21.741 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-03-21 22:39:21.741 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-03-21 22:39:21.751 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-03-21 22:39:21.751 VideoOutputXv: XVideo Format #3 is 'I420'
2009-03-21 22:39:21.751 VideoOutputXv: Using XVideo Format 'YV12'
2009-03-21 22:39:21.751 VideoOutputXv: CreateShmImages(32): video_dim: 1920x1088
2009-03-21 22:39:22.127 VDP: SetVideoRenderer(xv-blit)
2009-03-21 22:39:22.127 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-03-21 22:39:22.128 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-03-21 22:39:22.128 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-21 22:39:22.128 Display Rect  left: 0, top: 52, width: 1680, height: 945, aspect: 1.59925
2009-03-21 22:39:22.128 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-03-21 22:39:22.128 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:22.137 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-03-21 22:39:22.428 NVP: ClearAfterSeek(1)
2009-03-21 22:39:22.429 VideoOutputXv: ClearAfterSeek()
2009-03-21 22:39:22.429 VideoOutputXv: DiscardFrames(0)
2009-03-21 22:39:22.429 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:22.429 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:22.429 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:22.430 NVP: LoadFilters(''..) -> 0
2009-03-21 22:39:22.430 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1088) ->Interlaced Scan
2009-03-21 22:39:22.430 AFD: EIA-708 caption service #1 is in the English language.
2009-03-21 22:39:22.430 AFD: Using ffmpeg for video decoding
2009-03-21 22:39:22.430 AFD: Looking for decoder for MPEG2VIDEO
2009-03-21 22:39:22.431 AFD: Opened codec 0xafb7960, id(MPEG2VIDEO) type(Video)
2009-03-21 22:39:22.431 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0xa45b7e0
2009-03-21 22:39:22.431 AFD: codec AC3 has 6 channels
2009-03-21 22:39:22.431 AFD: Looking for decoder for AC3
2009-03-21 22:39:22.456 AFD: Opened codec 0xafbe340, id(AC3) type(Audio)
2009-03-21 22:39:22.508 NVP: Waiting for prebuffer.. 6 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:22.517 RingBuf(/var/lib/mythtv/recordings/1081_20090321223919.mpg): CalcReadAheadThresh(3050048141 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-21 22:39:22.530 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-21 22:39:22.530 Opening ALSA audio device 'default'.
2009-03-21 22:39:22.563 NVP: Enabling Audio
2009-03-21 22:39:22.563 Dec: Trying to select track (w/lang)
2009-03-21 22:39:22.563 Dec: Selecting first track
2009-03-21 22:39:22.563 Dec: Selected track #1 in the Unknown language(0)
2009-03-21 22:39:22.563 Dec: Selected track #1 in the English language(6647399)
2009-03-21 22:39:22.563 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(0)
2009-03-21 22:39:22.565 Position map filled from DB to: 0
2009-03-21 22:39:22.565 SyncPositionMap watchingrecording, from DB: 1 entries
2009-03-21 22:39:22.566 Filling position map from 1 to 54
2009-03-21 22:39:22.567 Position map filled from Encoder to: 27
2009-03-21 22:39:22.567 SyncPositionMap watchingrecording total: 2 entries
2009-03-21 22:39:22.567 SyncPositionMap, new totframes: 27, new length: 0, posMap size: 2
2009-03-21 22:39:22.567 AFD: Partial position map found
2009-03-21 22:39:22.568 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1081_20090321223919.mpg". novideo(0)
2009-03-21 22:39:22.572 NVP: DoPlay: rate: 29.97 speed: 1 skip: 1 => new interval 33366
2009-03-21 22:39:22.577 Set video sync frame interval to 33366
2009-03-21 22:39:22.578 NVP: Stretch Factor 1, allow passthru 
2009-03-21 22:39:22.579 RingBuf(/var/lib/mythtv/recordings/1081_20090321223919.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-21 22:39:22.580 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-03-21 22:39:22.581 Position map filled from DB to: 0
2009-03-21 22:39:22.581 SyncPositionMap watchingrecording, from DB: 1 entries
2009-03-21 22:39:22.582 Filling position map from 1 to 54
2009-03-21 22:39:22.583 Position map filled from Encoder to: 27
2009-03-21 22:39:22.583 SyncPositionMap watchingrecording total: 2 entries
2009-03-21 22:39:22.641 NVP: Waiting for prebuffer.. 7 LLAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:22.774 NVP: Waiting for prebuffer.. 8 ULUULAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:22.908 NVP: Waiting for prebuffer.. 9 UUUUuUULLAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:23.041 NVP: Prebuffer wait timed out 10 times.
2009-03-21 22:39:23.042 NVP: Waiting for prebuffer.. 0 UUUUUUUuUULULAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:23.546 NVP: Video is 3.18962 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.574 NVP: Video is 4.00312 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.605 NVP: Video is 4.62075 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.636 NVP: Video is 5.02404 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.666 NVP: Video is 5.29653 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.691 NVP: Video is 5.49341 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.722 NVP: Video is 5.56612 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.755 NVP: Video is 5.63565 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.781 NVP: Video is 5.64284 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.813 NVP: Video is 5.59579 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.845 NVP: Video is 5.56797 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.871 NVP: Video is 5.52464 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.903 NVP: Video is 5.45468 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.936 NVP: Video is 5.39471 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.963 NVP: Video is 5.32728 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:23.994 NVP: Video is 5.23173 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.028 NVP: Video is 5.1376 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.055 NVP: Video is 5.08197 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.086 NVP: Video is 5.02527 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.117 NVP: Video is 4.93029 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.143 NVP: Video is 4.85159 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.174 NVP: Video is 4.7326 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.205 NVP: Video is 4.61341 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.206 NVP: prebuffering pause
2009-03-21 22:39:24.206 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAAAAAAAAuAALLA
2009-03-21 22:39:24.340 NVP: Waiting for prebuffer.. 1 LAULAAAAAAAAAAAAAAAAAAAAAUAAuUU
2009-03-21 22:39:24.473 NVP: Waiting for prebuffer.. 2 ULUULUUAAAAAAAAAAAAAAAAAAUAAUUU
2009-03-21 22:39:24.570 NVP: Video is 4.50902 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.865 NVP: Video is 3.19187 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.893 NVP: Video is 4.0273 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.924 NVP: Video is 4.61641 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.957 NVP: Video is 5.03576 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:24.985 NVP: Video is 5.34277 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.012 NVP: Video is 5.54307 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.042 NVP: Video is 5.64083 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.072 NVP: Video is 5.6842 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.099 NVP: Video is 5.70173 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.129 NVP: Video is 5.64746 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.160 NVP: Video is 5.60673 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.186 NVP: Video is 5.54621 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.218 NVP: Video is 5.44839 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.249 NVP: Video is 5.36004 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.275 NVP: Video is 5.27879 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.306 NVP: Video is 5.15042 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.341 NVP: Video is 5.06162 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.370 NVP: Video is 4.99502 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.403 NVP: Video is 4.94509 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:25.405 NVP: prebuffering pause
2009-03-21 22:39:25.405 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAALAALAUAAAAAAAAA
2009-03-21 22:39:25.407 WriteAudio: buffer underrun
2009-03-21 22:39:25.540 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAAAAAAAUAALAULUUAAAAAA
2009-03-21 22:39:25.673 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAAAAAAAUAAUAUuUULUUALA
2009-03-21 22:39:25.806 NVP: Waiting for prebuffer.. 3 AALAAAAAAAAAAAAAUAAUAUUUUuUULUU
2009-03-21 22:39:25.838 NVP: Video is 4.81772 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.257 NVP: Video is 3.81751 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.386 NVP: Video is 5.50803 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.520 NVP: Video is 7.48771 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.654 NVP: Video is 9.73674 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.679 WriteAudio: buffer underrun
2009-03-21 22:39:26.756 WriteAudio: buffer underrun
2009-03-21 22:39:26.796 NVP: Video is 12.1653 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.813 NVP: Video is 14.2265 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.824 NVP: Video is 15.5176 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.841 NVP: Video is 16.2312 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.846 WriteAudio: buffer underrun
2009-03-21 22:39:26.852 NVP: Video is 16.5266 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.869 NVP: Video is 16.5759 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.884 NVP: Video is 16.4779 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.894 NVP: Video is 16.1947 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.911 NVP: Video is 15.735 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.922 NVP: Video is 15.1354 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.937 NVP: Video is 14.446 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.952 NVP: Video is 13.6742 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.955 WriteAudio: buffer underrun
2009-03-21 22:39:26.964 NVP: Video is 12.8481 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.980 NVP: Video is 12.0562 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:26.995 NVP: Video is 11.3274 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:27.011 NVP: Video is 10.571 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:27.027 NVP: Video is 9.76395 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:27.040 NVP: Video is 8.89642 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:27.056 NVP: Video is 7.9985 frames behind audio (too slow), dropping frame to catch up.
2009-03-21 22:39:27.057 NVP: prebuffering pause
2009-03-21 22:39:27.058 NVP: Waiting for prebuffer.. 0 AAAAAAAAAALAALAAAAUAAAAAAAAAAAA
2009-03-21 22:39:27.058 WriteAudio: buffer underrun
2009-03-21 22:39:27.069 TV: Attempting to change from WatchingLiveTV to None
2009-03-21 22:39:27.070 TV: StopStuff() -- begin
2009-03-21 22:39:27.070 TV: StopStuff(): stopping ring buffer[s]
2009-03-21 22:39:27.088 TV: StopStuff(): stopping player[s] (1/2)
2009-03-21 22:39:27.088 TV: StopStuff(): stopping recorder[s]
2009-03-21 22:39:27.116 NVP: Exited decoder loop.
2009-03-21 22:39:27.191 VideoOutputXv: dtor
2009-03-21 22:39:27.191 VideoOutputXv: DiscardFrames(1)
2009-03-21 22:39:27.191 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAuAALAAAAUAuAAAAAAAAAA
2009-03-21 22:39:27.192 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:27.192 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:27.192 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:27.192 VideoOutputXv: DiscardFrames(1)
2009-03-21 22:39:27.192 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-21 22:39:27.192 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:27.192 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-21 22:39:27.193 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-21 22:39:27.199 VideoOutputXv: Closing XVideo port 275
2009-03-21 22:39:27.561 TV: StopStuff(): stopping player[s] (2/2)
2009-03-21 22:39:27.607 TV: StopStuff() -- end
2009-03-21 22:39:27.608 TV: Changing from WatchingLiveTV to None
2009-03-21 22:39:27.675 DPMS Reactivated.
Destroying SipFsm object 
2009-03-21 22:39:31.830 Deleting UPnP client...


Let me know if you have any ideas or if I haven't posted enough info! - PS Thanks for all your help thus far!

---

### Post by newlinux on 2009-03-22
do you have:
libXvMCNVIDIA.so.1 

or

libXvMCNVIDIA_dynamic.so.1

in your XvMCConfig file? Should be the second one. Your logs make me think you put the first one in there. If it isn't the second one, change it and restart X and try again.

---

### Post by dibuntux on 2009-03-22
Following your posts, I realized XvMC is enabled by the book but not working in my PC. I was using CPU-- profile, but realized it falls back tou using xvblit instead. If I force an XvMC only profile I get this over and over in my frontend log:
2008-05-25 16:13:44.347 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil)
2008-05-25 16:13:44.347 AFD Error: Unknown decoding error

with a black screen.

Hope this can help sort the matter out.

TIA

My system: Mythbuntu 8.10
Athlon 1700+ 512MB SDRAM PC133
Nvidia FX5200 256 MB
Hauppauge HVR 1110 DV-T
SkyStar 2.6 DVB-S

---

### Post by dave00001 on 2009-03-22
I did have the wrong line in my XvMCConfig file - I changed it to say libXvMCNVIDIA_dynamic.so.1 and restarted X.  But, still no change with either the OSD or the choppy output.

To shed some more light, here is the output once again of 
mythfrontend -v playback

2009-03-22 15:00:16.932 Using runtime prefix = /usr
2009-03-22 15:00:17.467 XScreenSaver support enabled
2009-03-22 15:00:17.468 DPMS is active.
2009-03-22 15:00:17.469 Empty LocalHostName.
2009-03-22 15:00:17.469 Using localhost value of dave-desktop
2009-03-22 15:00:17.484 New DB connection, total: 1
2009-03-22 15:00:17.490 Connected to database 'mythconverg' at host: localhost
2009-03-22 15:00:17.493 Closing DB connection named 'DBManager0'
2009-03-22 15:00:17.495 Primary screen 0.
2009-03-22 15:00:17.514 Connected to database 'mythconverg' at host: localhost
2009-03-22 15:00:17.519 Using screen 0, 1680x1050 at 0,0
2009-03-22 15:00:17.535 user: 1000 effective user: 1000 before privileged thread
2009-03-22 15:00:17.536 user: 1000 effective user: 1000 run_priv_thread
2009-03-22 15:00:17.539 user: 1000 effective user: 1000 after privileged thread
2009-03-22 15:00:17.542 New DB connection, total: 2
2009-03-22 15:00:17.542 Connected to database 'mythconverg' at host: localhost
2009-03-22 15:00:17.547 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-22 15:00:17.547 Enabled verbose msgs:  important general playback
2009-03-22 15:00:18.085 max_width: 1680 max_height: 1050
2009-03-22 15:00:18.254 No theme dir: /home/dave/.mythtv/themes/Mythbuntu-8.04
2009-03-22 15:00:18.256 Primary screen 0.
2009-03-22 15:00:18.257 Using screen 0, 1680x1050 at 0,0
2009-03-22 15:00:18.257 No theme dir: /home/dave/.mythtv/themes/Mythbuntu-8.04
2009-03-22 15:00:18.258 Switching to square mode (Mythbuntu-8.04)
2009-03-22 15:00:18.419 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-22 15:00:18.420 lirc_init failed for mythtv, see preceding messages
2009-03-22 15:00:18.421 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dave/.mythtv/joystickmenurc
2009-03-22 15:00:20.342 Specified base font 'medium' does not exist for font clock
2009-03-22 15:00:20.342 Specified base font 'medium' does not exist for font small
2009-03-22 15:00:20.343 Specified base font 'medium' does not exist for font medium
2009-03-22 15:00:20.343 Specified base font 'medium' does not exist for font large
2009-03-22 15:00:20.345 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-03-22 15:00:20.587 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-22 15:00:20.664 Registering Internal as a media playback plugin.
2009-03-22 15:00:20.810 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-22 15:00:20.881 Failed to run 'cdrecord --scanbus'
2009-03-22 15:00:20.887 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-22 15:00:20.898 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-22 15:00:20.961 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.3:5060 NAT address 192.168.2.3
SIP: Cannot register; proxy, username or password not set
2009-03-22 15:00:21.160 No theme dir: /home/dave/.mythtv/themes/Mythbuntu-8.04
2009-03-22 15:00:25.061 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-22 15:00:25.063 Using protocol version 40
2009-03-22 15:00:25.084 TV: Attempting to change from None to WatchingLiveTV
2009-03-22 15:00:25.085 Using protocol version 40
2009-03-22 15:00:26.215 LiveTVChain(live-dave-desktop-2009-03-22T15:00:25): ReloadAll(): Added new recording
2009-03-22 15:00:26.227 TV: StartRecorder(): took 1 ms to start recorder.
2009-03-22 15:00:26.257 New DB connection, total: 3
2009-03-22 15:00:26.258 Connected to database 'mythconverg' at host: localhost
2009-03-22 15:00:26.279 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-03-22 15:00:26.290 NVP: Disabling Audio, params(-1,2,44100)
2009-03-22 15:00:26.296 VideoOutput: Allowed renderers: xv-blit,xshm,opengl,xlib
2009-03-22 15:00:26.297 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,xv-blit,opengl
2009-03-22 15:00:26.300 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-22 15:00:26.307 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 15:00:26.307 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 15:00:26.307 VDP: LoadBestPreferences(720x576, 60)
2009-03-22 15:00:26.308 VideoOutput: Trying video renderer: xv-blit
2009-03-22 15:00:26.310 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-22 15:00:26.310 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 15:00:26.310 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 15:00:26.324 DPMS Deactivated 
2009-03-22 15:00:26.345 VideoOutputXv: ctor
2009-03-22 15:00:26.348 XOff: 0, YOff: 0
2009-03-22 15:00:26.348 VDP: LoadBestPreferences(720x576, 60)
2009-03-22 15:00:26.348 Display Rect  left: 0, top: 0, width: 1680, height: 1050, aspect: 1.33333
2009-03-22 15:00:26.349 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-03-22 15:00:26.350 VideoOutputXv: Pixel dimensions: Screen 1680x1050, window 1680x1050
2009-03-22 15:00:26.352 VideoOutputXv: Estimated display dimensions: 427x267 mm  Aspect: 1.59925
2009-03-22 15:00:26.358 VideoOutputXv: Estimated window dimensions: 427x267 mm  Aspect: 1.59925
2009-03-22 15:00:26.359 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xv-blit,xshm,opengl,xlib
2009-03-22 15:00:26.360 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-22 15:00:26.360 VDP: SetVideoRenderer(xv-blit)
2009-03-22 15:00:26.360 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-22 15:00:26.360 VDP: New preferences: rend(xv-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-22 15:00:26.364 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-22 15:00:26.364 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 15:00:26.364 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 15:00:26.364 VDP: LoadBestPreferences(720x576, 60)
2009-03-22 15:00:26.365 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  18
2009-03-22 15:00:26.365 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.366 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.366 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:26.366 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.366 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.367 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:26.367 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  8
2009-03-22 15:00:26.367 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.367 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.367 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 15:00:26.368 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.373 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.373 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 15:00:26.373 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask XvImageMask  10
2009-03-22 15:00:26.374 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.374 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.374 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:26.374 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.374 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.375 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:26.375 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask  0
2009-03-22 15:00:26.375 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:26.375 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:26.375 VideoOutputXv: Here...
2009-03-22 15:00:26.376 VideoOutputXv: Grabbed xv port 275
2009-03-22 15:00:26.376 VideoOutputXv: XVideo surface found on port 275
2009-03-22 15:00:26.376 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-22 15:00:26.377 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-03-22 15:00:26.377 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-03-22 15:00:26.377 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-03-22 15:00:26.377 VideoOutputXv: XVideo Format #3 is 'I420'
2009-03-22 15:00:26.378 VideoOutputXv: Using XVideo Format 'YV12'
2009-03-22 15:00:26.378 VideoOutputXv: CreateShmImages(32): video_dim: 720x576
2009-03-22 15:00:26.480 VDP: SetVideoRenderer(xv-blit)
2009-03-22 15:00:26.481 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-03-22 15:00:26.481 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-03-22 15:00:26.481 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-22 15:00:26.482 Display Rect  left: 139, top: 0, width: 1401, height: 1050, aspect: 1.59925
2009-03-22 15:00:26.482 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-03-22 15:00:26.485 Over/underscan. V: 0, H: 0
2009-03-22 15:00:26.486 Display Rect  left: 139, top: 0, width: 1401, height: 1050, aspect: 1.59925
2009-03-22 15:00:26.486 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-03-22 15:00:26.486 VDP: LoadBestPreferences(720x576, 25)
2009-03-22 15:00:26.488 NVP: LoadFilters(''..) -> 0
2009-03-22 15:00:26.491 OSD Theme Dimensions W: 640 H: 480
2009-03-22 15:00:27.207 TV: StartPlayer(): took 908 ms to start player.
2009-03-22 15:00:27.208 TV: Changing from None to WatchingLiveTV
2009-03-22 15:00:27.207 NVP: ClearAfterSeek(1)
2009-03-22 15:00:27.210 VideoOutputXv: ClearAfterSeek()
2009-03-22 15:00:27.210 VideoOutputXv: DiscardFrames(0)
2009-03-22 15:00:27.210 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:27.210 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:27.211 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:27.214 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2009-03-22 15:00:27.216 Using deinterlace method bobdeint
2009-03-22 15:00:27.220 Realtime priority would require SUID as root.
2009-03-22 15:00:27.227 rate: 25 speed: 1 skip: 1 = interval 40000
2009-03-22 15:00:27.321 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-03-22 15:00:27.321 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-03-22 15:00:27.321 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2009-03-22 15:00:27.321 Set video sync frame interval to 40000
2009-03-22 15:00:27.322 Using audio as timebase
2009-03-22 15:00:27.322 Video timing method: USleep with busy wait
2009-03-22 15:00:27.322 Refresh rate: 16679, frame interval: 40000
2009-03-22 15:00:27.362 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.111 LiveTVChain(live-dave-desktop-2009-03-22T15:00:25): ReloadAll(): Added new recording
2009-03-22 15:00:28.114 LiveTVChain(live-dave-desktop-2009-03-22T15:00:25): SwitchTo(1)
2009-03-22 15:00:28.114 LiveTVChain(live-dave-desktop-2009-03-22T15:00:25): Entry@1: '1081_20090322150026'
2009-03-22 15:00:28.114 JumpToProgram(void)
2009-03-22 15:00:28.138 RingBuf(/var/lib/mythtv/recordings/1081_20090322150025.mpg): OpenFile(/var/lib/mythtv/recordings/1081_20090322150026.mpg, 12)
2009-03-22 15:00:28.167 RingBuf(/var/lib/mythtv/recordings/1081_20090322150026.mpg): CalcReadAheadThresh(3050928465 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 15:00:28.210 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.410 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.418 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.618 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.625 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.826 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:28.834 NVP: Waiting for prebuffer.. 3 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.034 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.043 NVP: Waiting for prebuffer.. 4 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.244 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.252 NVP: Waiting for prebuffer.. 5 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.292 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 18296000 at 0x0x8f37960
2009-03-22 15:00:29.295 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-22 15:00:29.295 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 15:00:29.296 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 15:00:29.296 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-22 15:00:29.296 Using 0 CPUs for decoding
2009-03-22 15:00:29.298 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-22 15:00:29.299 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 15:00:29.299 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 15:00:29.299 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-22 15:00:29.301 VideoOutputXv: XvMC version: 1.1
2009-03-22 15:00:29.302 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 306, 2750 <=p, port, surfNum)
2009-03-22 15:00:29.308 Trying XvMC port 275
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
2009-03-22 15:00:29.309 Trying XvMC port 276
2009-03-22 15:00:29.309 Trying XvMC port 277
2009-03-22 15:00:29.310 Trying XvMC port 278
2009-03-22 15:00:29.310 Trying XvMC port 279
2009-03-22 15:00:29.310 Trying XvMC port 280
2009-03-22 15:00:29.310 Trying XvMC port 281
2009-03-22 15:00:29.310 Trying XvMC port 282
2009-03-22 15:00:29.310 Trying XvMC port 283
2009-03-22 15:00:29.310 Trying XvMC port 284
2009-03-22 15:00:29.310 Trying XvMC port 285
2009-03-22 15:00:29.310 Trying XvMC port 286
2009-03-22 15:00:29.311 Trying XvMC port 287
2009-03-22 15:00:29.311 Trying XvMC port 288
2009-03-22 15:00:29.311 Trying XvMC port 289
2009-03-22 15:00:29.311 Trying XvMC port 290
2009-03-22 15:00:29.311 Trying XvMC port 291
2009-03-22 15:00:29.311 Trying XvMC port 292
2009-03-22 15:00:29.311 Trying XvMC port 293
2009-03-22 15:00:29.311 Trying XvMC port 294
2009-03-22 15:00:29.311 Trying XvMC port 295
2009-03-22 15:00:29.312 Trying XvMC port 296
2009-03-22 15:00:29.312 Trying XvMC port 297
2009-03-22 15:00:29.312 Trying XvMC port 298
2009-03-22 15:00:29.312 Trying XvMC port 299
2009-03-22 15:00:29.312 Trying XvMC port 300
2009-03-22 15:00:29.312 Trying XvMC port 301
2009-03-22 15:00:29.312 Trying XvMC port 302
2009-03-22 15:00:29.312 Trying XvMC port 303
2009-03-22 15:00:29.312 Trying XvMC port 304
2009-03-22 15:00:29.313 Trying XvMC port 305
2009-03-22 15:00:29.313 Trying XvMC port 306
2009-03-22 15:00:29.313 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 338, 3070 <=p, port, surfNum)
2009-03-22 15:00:29.313 Trying XvMC port 307
2009-03-22 15:00:29.313 Trying XvMC port 308
2009-03-22 15:00:29.313 Trying XvMC port 309
2009-03-22 15:00:29.313 Trying XvMC port 310
2009-03-22 15:00:29.313 Trying XvMC port 311
2009-03-22 15:00:29.314 Trying XvMC port 312
2009-03-22 15:00:29.314 Trying XvMC port 313
2009-03-22 15:00:29.314 Trying XvMC port 314
2009-03-22 15:00:29.314 Trying XvMC port 315
2009-03-22 15:00:29.314 Trying XvMC port 316
2009-03-22 15:00:29.314 Trying XvMC port 317
2009-03-22 15:00:29.314 Trying XvMC port 318
2009-03-22 15:00:29.314 Trying XvMC port 319
2009-03-22 15:00:29.314 Trying XvMC port 320
2009-03-22 15:00:29.314 Trying XvMC port 321
2009-03-22 15:00:29.315 Trying XvMC port 322
2009-03-22 15:00:29.315 Trying XvMC port 323
2009-03-22 15:00:29.315 Trying XvMC port 324
2009-03-22 15:00:29.315 Trying XvMC port 325
2009-03-22 15:00:29.316 Trying XvMC port 326
2009-03-22 15:00:29.316 Trying XvMC port 327
2009-03-22 15:00:29.316 Trying XvMC port 328
2009-03-22 15:00:29.316 Trying XvMC port 329
2009-03-22 15:00:29.316 Trying XvMC port 330
2009-03-22 15:00:29.316 Trying XvMC port 331
2009-03-22 15:00:29.316 Trying XvMC port 332
2009-03-22 15:00:29.316 Trying XvMC port 333
2009-03-22 15:00:29.316 Trying XvMC port 334
2009-03-22 15:00:29.316 Trying XvMC port 335
2009-03-22 15:00:29.317 Trying XvMC port 336
2009-03-22 15:00:29.317 Trying XvMC port 337
2009-03-22 15:00:29.317 Trying XvMC port 338
2009-03-22 15:00:29.317 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 306, 2750 <=p, port, surfNum)
2009-03-22 15:00:29.323 Trying XvMC port 275
2009-03-22 15:00:29.323 Trying XvMC port 276
2009-03-22 15:00:29.323 Trying XvMC port 277
2009-03-22 15:00:29.323 Trying XvMC port 278
2009-03-22 15:00:29.324 Trying XvMC port 279
2009-03-22 15:00:29.324 Trying XvMC port 280
2009-03-22 15:00:29.324 Trying XvMC port 281
2009-03-22 15:00:29.324 Trying XvMC port 282
2009-03-22 15:00:29.324 Trying XvMC port 283
2009-03-22 15:00:29.324 Trying XvMC port 284
2009-03-22 15:00:29.324 Trying XvMC port 285
2009-03-22 15:00:29.324 Trying XvMC port 286
2009-03-22 15:00:29.324 Trying XvMC port 287
2009-03-22 15:00:29.324 Trying XvMC port 288
2009-03-22 15:00:29.324 Trying XvMC port 289
2009-03-22 15:00:29.325 Trying XvMC port 290
2009-03-22 15:00:29.325 Trying XvMC port 291
2009-03-22 15:00:29.325 Trying XvMC port 292
2009-03-22 15:00:29.325 Trying XvMC port 293
2009-03-22 15:00:29.325 Trying XvMC port 294
2009-03-22 15:00:29.325 Trying XvMC port 295
2009-03-22 15:00:29.325 Trying XvMC port 296
2009-03-22 15:00:29.325 Trying XvMC port 297
2009-03-22 15:00:29.325 Trying XvMC port 298
2009-03-22 15:00:29.325 Trying XvMC port 299
2009-03-22 15:00:29.325 Trying XvMC port 300
2009-03-22 15:00:29.325 Trying XvMC port 301
2009-03-22 15:00:29.325 Trying XvMC port 302
2009-03-22 15:00:29.326 Trying XvMC port 303
2009-03-22 15:00:29.326 Trying XvMC port 304
2009-03-22 15:00:29.326 Trying XvMC port 305
2009-03-22 15:00:29.326 Trying XvMC port 306
2009-03-22 15:00:29.326 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 338, 3070 <=p, port, surfNum)
2009-03-22 15:00:29.326 Trying XvMC port 307
2009-03-22 15:00:29.326 Trying XvMC port 308
2009-03-22 15:00:29.326 Trying XvMC port 309
2009-03-22 15:00:29.326 Trying XvMC port 310
2009-03-22 15:00:29.326 Trying XvMC port 311
2009-03-22 15:00:29.327 Trying XvMC port 312
2009-03-22 15:00:29.327 Trying XvMC port 313
2009-03-22 15:00:29.327 Trying XvMC port 314
2009-03-22 15:00:29.327 Trying XvMC port 315
2009-03-22 15:00:29.327 Trying XvMC port 316
2009-03-22 15:00:29.327 Trying XvMC port 317
2009-03-22 15:00:29.327 Trying XvMC port 318
2009-03-22 15:00:29.327 Trying XvMC port 319
2009-03-22 15:00:29.327 Trying XvMC port 320
2009-03-22 15:00:29.327 Trying XvMC port 321
2009-03-22 15:00:29.328 Trying XvMC port 322
2009-03-22 15:00:29.328 Trying XvMC port 323
2009-03-22 15:00:29.328 Trying XvMC port 324
2009-03-22 15:00:29.328 Trying XvMC port 325
2009-03-22 15:00:29.328 Trying XvMC port 326
2009-03-22 15:00:29.328 Trying XvMC port 327
2009-03-22 15:00:29.328 Trying XvMC port 328
2009-03-22 15:00:29.329 Trying XvMC port 329
2009-03-22 15:00:29.329 Trying XvMC port 330
2009-03-22 15:00:29.329 Trying XvMC port 331
2009-03-22 15:00:29.329 Trying XvMC port 332
2009-03-22 15:00:29.329 Trying XvMC port 333
2009-03-22 15:00:29.329 Trying XvMC port 334
2009-03-22 15:00:29.329 Trying XvMC port 335
2009-03-22 15:00:29.329 Trying XvMC port 336
2009-03-22 15:00:29.329 Trying XvMC port 337
2009-03-22 15:00:29.330 Trying XvMC port 338
2009-03-22 15:00:29.330 AFD: InitVideoCodec() 0x9a1f700 id(MPEG2VIDEO) type (Video).
2009-03-22 15:00:29.330 VideoOutputXv: InputChanged(1920,1088,1.77778) 'None'->'MPEG2'
2009-03-22 15:00:29.331 VDP: LoadBestPreferences(1920x1088, 25)
2009-03-22 15:00:29.331 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2009-03-22 15:00:29.340 Using deinterlace method bobdeint
2009-03-22 15:00:29.340 VideoOutputXv: DiscardFrames(1)
2009-03-22 15:00:29.340 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.341 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:29.341 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:29.341 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:29.341 VideoOutputXv: DiscardFrames(1)
2009-03-22 15:00:29.341 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.341 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:29.342 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:29.342 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:29.342 VideoOutputXv: DiscardFrames(1)
2009-03-22 15:00:29.342 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.342 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:29.342 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:29.343 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:29.345 VideoOutputXv: Closing XVideo port 275
2009-03-22 15:00:29.354 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xv-blit,xshm,opengl,xlib
2009-03-22 15:00:29.355 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-22 15:00:29.355 VDP: SetVideoRenderer(xv-blit)
2009-03-22 15:00:29.355 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-22 15:00:29.355 VDP: New preferences: rend(xv-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-22 15:00:29.358 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(0) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-03-22 15:00:29.359 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 15:00:29.359 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 15:00:29.359 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-22 15:00:29.360 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  18
2009-03-22 15:00:29.360 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.360 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.360 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:29.361 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.361 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.361 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:29.361 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  8
2009-03-22 15:00:29.361 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.361 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.362 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 15:00:29.362 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.362 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.362 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 15:00:29.362 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask XvImageMask  10
2009-03-22 15:00:29.362 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.363 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.363 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:29.363 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.363 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.363 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 15:00:29.369 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask  0
2009-03-22 15:00:29.370 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 15:00:29.370 VideoOutputXv: Has XVideo flags...
2009-03-22 15:00:29.370 VideoOutputXv: Here...
2009-03-22 15:00:29.370 VideoOutputXv: Grabbed xv port 275
2009-03-22 15:00:29.370 VideoOutputXv: XVideo surface found on port 275
2009-03-22 15:00:29.370 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-22 15:00:29.371 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-03-22 15:00:29.371 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-03-22 15:00:29.371 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-03-22 15:00:29.371 VideoOutputXv: XVideo Format #3 is 'I420'
2009-03-22 15:00:29.371 VideoOutputXv: Using XVideo Format 'YV12'
2009-03-22 15:00:29.371 VideoOutputXv: CreateShmImages(32): video_dim: 1920x1088
2009-03-22 15:00:29.746 VDP: SetVideoRenderer(xv-blit)
2009-03-22 15:00:29.746 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-03-22 15:00:29.747 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-03-22 15:00:29.747 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-22 15:00:29.747 Display Rect  left: 0, top: 52, width: 1680, height: 945, aspect: 1.59925
2009-03-22 15:00:29.747 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-03-22 15:00:29.747 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:29.755 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-03-22 15:00:30.045 NVP: ClearAfterSeek(1)
2009-03-22 15:00:30.045 VideoOutputXv: ClearAfterSeek()
2009-03-22 15:00:30.046 VideoOutputXv: DiscardFrames(0)
2009-03-22 15:00:30.046 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:30.046 VideoBuffers:: DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:30.046 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:30.046 NVP: LoadFilters(''..) -> 0
2009-03-22 15:00:30.046 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1088) ->Interlaced Scan
2009-03-22 15:00:30.047 AFD: EIA-708 caption service #1 is in the English language.
2009-03-22 15:00:30.047 AFD: Using ffmpeg for video decoding
2009-03-22 15:00:30.047 AFD: Looking for decoder for MPEG2VIDEO
2009-03-22 15:00:30.048 AFD: Opened codec 0x9a1f700, id(MPEG2VIDEO) type(Video)
2009-03-22 15:00:30.048 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0x8ec4e30
2009-03-22 15:00:30.048 AFD: codec AC3 has 6 channels
2009-03-22 15:00:30.048 AFD: Looking for decoder for AC3
2009-03-22 15:00:30.074 AFD: Opened codec 0x9a1bba0, id(AC3) type(Audio)
2009-03-22 15:00:30.127 NVP: Waiting for prebuffer.. 6 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:30.294 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:30.314 RingBuf(/var/lib/mythtv/recordings/1081_20090322150026.mpg): CalcReadAheadThresh(3050928781 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 15:00:30.331 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-22 15:00:30.336 Opening ALSA audio device 'default'.
2009-03-22 15:00:30.396 NVP: Enabling Audio
2009-03-22 15:00:30.398 Dec: Trying to select track (w/lang)
2009-03-22 15:00:30.399 Dec: Selecting first track
2009-03-22 15:00:30.399 Dec: Selected track #1 in the Unknown language(0)
2009-03-22 15:00:30.399 Dec: Selected track #1 in the English language(6647399)
2009-03-22 15:00:30.399 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-03-22 15:00:30.401 Position map filled from DB to: 0
2009-03-22 15:00:30.401 SyncPositionMap watchingrecording, from DB: 1 entries
2009-03-22 15:00:30.404 Filling position map from 1 to 60
2009-03-22 15:00:30.405 Position map filled from Encoder to: 54
2009-03-22 15:00:30.406 SyncPositionMap watchingrecording total: 3 entries
2009-03-22 15:00:30.410 SyncPositionMap, new totframes: 54, new length: 1, posMap size: 3
2009-03-22 15:00:30.411 AFD: Partial position map found
2009-03-22 15:00:30.411 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1081_20090322150026.mpg". novideo(0)
2009-03-22 15:00:30.418 NVP: DoPlay: rate: 29.97 speed: 1 skip: 1 => new interval 33366
2009-03-22 15:00:30.423 Set video sync frame interval to 33366
2009-03-22 15:00:30.428 NVP: Stretch Factor 1, allow passthru 
2009-03-22 15:00:30.436 NVP: Waiting for prebuffer.. 7 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:30.439 RingBuf(/var/lib/mythtv/recordings/1081_20090322150026.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 15:00:30.440 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-03-22 15:00:30.442 Position map filled from DB to: 0
2009-03-22 15:00:30.442 SyncPositionMap watchingrecording, from DB: 1 entries
2009-03-22 15:00:30.444 Filling position map from 1 to 61
2009-03-22 15:00:30.445 Position map filled from Encoder to: 54
2009-03-22 15:00:30.445 SyncPositionMap watchingrecording total: 3 entries
2009-03-22 15:00:30.570 NVP: Waiting for prebuffer.. 8 uLULAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:30.703 NVP: Waiting for prebuffer.. 9 UuUULULAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:30.837 NVP: Prebuffer wait timed out 10 times.
2009-03-22 15:00:30.837 NVP: Waiting for prebuffer.. 0 UUUUUUULUULAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:31.415 NVP: Video is 4.41749 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.448 NVP: Video is 5.35111 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.475 NVP: Video is 6.04382 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.504 NVP: Video is 6.54088 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.533 NVP: Video is 6.86124 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.560 NVP: Video is 7.07154 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.592 NVP: Video is 7.1768 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.622 NVP: Video is 7.25574 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.648 NVP: Video is 7.28499 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.680 NVP: Video is 7.25448 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.712 NVP: Video is 7.2166 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.739 NVP: Video is 7.16571 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.773 NVP: Video is 7.0826 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.805 NVP: Video is 7.03525 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.831 NVP: Video is 6.98475 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.863 NVP: Video is 6.89441 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.896 NVP: Video is 6.81919 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.921 NVP: Video is 6.74027 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.947 WriteAudio: buffer underrun
2009-03-22 15:00:31.953 NVP: Video is 6.63616 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:31.986 NVP: Video is 6.49811 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.012 NVP: Video is 6.32716 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.017 NVP: prebuffering pause
2009-03-22 15:00:32.018 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAAAAAAAALAULAA
2009-03-22 15:00:32.019 WriteAudio: buffer underrun
2009-03-22 15:00:32.151 NVP: Waiting for prebuffer.. 1 LALAAAAAAAAAAAAAAAAAAAAAAUAUuUU
2009-03-22 15:00:32.285 NVP: Waiting for prebuffer.. 2 uLUUALAAAAAAAAAAAAAAAAAAAUAUUUU
2009-03-22 15:00:32.416 NVP: Video is 5.95169 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.449 NVP: Video is 5.06318 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.474 NVP: Video is 4.3743 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.503 NVP: Video is 3.79021 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.535 NVP: Video is 3.32968 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.566 NVP: Video is 3.00674 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.750 NVP: Video is 3.33783 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.780 NVP: Video is 3.57481 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.806 NVP: Video is 3.73005 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.837 NVP: Video is 3.80153 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.870 NVP: Video is 3.84017 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.897 NVP: Video is 3.86915 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.929 NVP: Video is 3.83094 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.962 NVP: Video is 3.80228 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:32.990 NVP: Video is 3.7733 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.024 NVP: Video is 3.70662 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.025 NVP: prebuffering pause
2009-03-22 15:00:33.025 NVP: Waiting for prebuffer.. 0 AAAAAAAAAALAALAUAAAAAAAAAAAAAAA
2009-03-22 15:00:33.159 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAUAAuAULUUAAAAAAAAAAAA
2009-03-22 15:00:33.293 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAUAAUAUuUULUUALAAAAAAA
2009-03-22 15:00:33.438 NVP: Video is 3.66409 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.824 NVP: Video is 4.34244 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.851 NVP: Video is 5.27984 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.879 NVP: Video is 5.95292 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.909 NVP: Video is 6.39777 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.939 NVP: Video is 6.70896 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:33.970 NVP: Video is 6.97231 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.001 NVP: Video is 7.12486 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.035 NVP: Video is 7.20182 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.062 NVP: Video is 7.25205 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.094 NVP: Video is 7.23728 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.222 NVP: Video is 7.22619 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.259 WriteAudio: buffer underrun
2009-03-22 15:00:34.328 WriteAudio: buffer underrun
2009-03-22 15:00:34.359 NVP: Video is 7.92217 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.418 WriteAudio: buffer underrun
2009-03-22 15:00:34.486 NVP: Video is 8.69892 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.498 WriteAudio: buffer underrun
2009-03-22 15:00:34.574 WriteAudio: buffer underrun
2009-03-22 15:00:34.625 NVP: Video is 9.28148 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.664 WriteAudio: buffer underrun
2009-03-22 15:00:34.736 WriteAudio: buffer underrun
2009-03-22 15:00:34.762 NVP: Video is 10.1904 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.819 WriteAudio: buffer underrun
2009-03-22 15:00:34.895 NVP: Video is 11.052 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:34.906 WriteAudio: buffer underrun
2009-03-22 15:00:34.976 WriteAudio: buffer underrun
2009-03-22 15:00:35.029 NVP: Video is 11.7281 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.058 WriteAudio: buffer underrun
2009-03-22 15:00:35.153 WriteAudio: buffer underrun
2009-03-22 15:00:35.162 NVP: Video is 12.475 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.231 WriteAudio: buffer underrun
2009-03-22 15:00:35.295 NVP: Video is 13.1325 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.309 WriteAudio: buffer underrun
2009-03-22 15:00:35.392 WriteAudio: buffer underrun
2009-03-22 15:00:35.432 NVP: Video is 13.7456 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.475 WriteAudio: buffer underrun
2009-03-22 15:00:35.552 WriteAudio: buffer underrun
2009-03-22 15:00:35.564 NVP: Video is 14.4301 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.635 WriteAudio: buffer underrun
2009-03-22 15:00:35.694 NVP: Video is 15.056 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.718 WriteAudio: buffer underrun
2009-03-22 15:00:35.792 WriteAudio: buffer underrun
2009-03-22 15:00:35.831 NVP: Video is 15.6377 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:35.885 WriteAudio: buffer underrun
2009-03-22 15:00:35.956 WriteAudio: buffer underrun
2009-03-22 15:00:35.966 NVP: Video is 16.2988 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.038 WriteAudio: buffer underrun
2009-03-22 15:00:36.096 NVP: Video is 16.8246 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.130 WriteAudio: buffer underrun
2009-03-22 15:00:36.206 WriteAudio: buffer underrun
2009-03-22 15:00:36.240 NVP: Video is 17.4062 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.286 WriteAudio: buffer underrun
2009-03-22 15:00:36.374 WriteAudio: buffer underrun
2009-03-22 15:00:36.375 NVP: Video is 18.0822 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.455 WriteAudio: buffer underrun
2009-03-22 15:00:36.522 NVP: Video is 18.5743 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.546 NVP: Video is 19.4153 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.556 WriteAudio: buffer underrun
2009-03-22 15:00:36.566 NVP: Video is 19.7913 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.577 NVP: Video is 19.8935 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.594 NVP: Video is 19.8503 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.608 NVP: Video is 19.6156 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.623 NVP: Video is 19.1848 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.637 NVP: Video is 18.607 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.653 NVP: Video is 17.9263 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.670 NVP: Video is 17.1686 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.681 NVP: Video is 16.3455 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.682 WriteAudio: buffer underrun
2009-03-22 15:00:36.699 NVP: Video is 15.5184 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.709 NVP: Video is 14.7408 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.726 NVP: Video is 14.0227 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.742 NVP: Video is 13.2218 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.753 NVP: Video is 12.3815 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.771 NVP: Video is 11.5039 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.783 NVP: Video is 10.591 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.798 WriteAudio: buffer underrun
2009-03-22 15:00:36.805 NVP: Video is 9.65159 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.818 NVP: Video is 8.77468 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.828 NVP: Video is 7.92969 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:36.837 NVP: prebuffering pause
2009-03-22 15:00:36.837 NVP: Waiting for prebuffer.. 0 LAAAAAAAULAAAAAAAAAAAAAAAAAAaAA
2009-03-22 15:00:36.839 WriteAudio: buffer underrun
2009-03-22 15:00:36.972 NVP: Waiting for prebuffer.. 1 uLAAAAAAUUAUuAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:37.106 NVP: Waiting for prebuffer.. 2 UUAALAALUUAUUAUUAAAAAAAAAAAAAAA
2009-03-22 15:00:37.239 NVP: Waiting for prebuffer.. 3 UUAAUAALUULUUAUUAUUAAAAAAAAAAAA
2009-03-22 15:00:37.252 NVP: Video is 7.14608 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.267 NVP: Video is 6.09384 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.285 NVP: Video is 5.16978 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.294 NVP: Video is 4.3119 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '62950.77', std. dev. = '76548.49', fps = '15.89'
2009-03-22 15:00:37.314 NVP: Video is 3.49616 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.596 NVP: Video is 3.64713 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.604 NVP: Video is 4.00908 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.619 NVP: Video is 4.07825 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.634 NVP: Video is 4.00276 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.649 NVP: Video is 3.79629 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.665 NVP: Video is 3.51406 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.676 NVP: Video is 3.175 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.847 NVP: Video is 3.13112 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.854 NVP: Video is 3.25493 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.871 NVP: Video is 3.14551 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.948 NVP: Video is 3.06929 frames behind audio (too slow), dropping frame to catch up.
2009-03-22 15:00:37.949 NVP: prebuffering pause
2009-03-22 15:00:37.949 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAALAALAAAAAAAU
2009-03-22 15:00:38.084 NVP: Waiting for prebuffer.. 1 AAUUAAAAAAAAAAAAAAAUAALAALAAAAU
2009-03-22 15:00:38.171 TV: Attempting to change from WatchingLiveTV to None
2009-03-22 15:00:38.171 TV: StopStuff() -- begin
2009-03-22 15:00:38.171 TV: StopStuff(): stopping ring buffer[s]
2009-03-22 15:00:38.178 TV: StopStuff(): stopping player[s] (1/2)
2009-03-22 15:00:38.178 TV: StopStuff(): stopping recorder[s]
2009-03-22 15:00:38.217 NVP: Waiting for prebuffer.. 2 AAUUAUUAAAAAAAAAAAAUAAUAALAALAU
2009-03-22 15:00:38.227 NVP: Exited decoder loop.
2009-03-22 15:00:38.350 VideoOutputXv: dtor
2009-03-22 15:00:38.351 VideoOutputXv: DiscardFrames(1)
2009-03-22 15:00:38.351 VideoBuffers:: DiscardFrames(1): AAUUAUUAAAAAAAAAAAAUAAUAAuAALAU
2009-03-22 15:00:38.351 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:38.351 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:38.351 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:38.351 VideoOutputXv: DiscardFrames(1)
2009-03-22 15:00:38.351 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 15:00:38.352 VideoBuffers:: DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:38.352 VideoBuffers:: DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-03-22 15:00:38.352 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-03-22 15:00:38.358 VideoOutputXv: Closing XVideo port 275
2009-03-22 15:00:38.580 TV: StopStuff(): stopping player[s] (2/2)
2009-03-22 15:00:38.628 TV: StopStuff() -- end
2009-03-22 15:00:38.628 TV: Changing from WatchingLiveTV to None
2009-03-22 15:00:38.673 DPMS Reactivated.
Destroying SipFsm object 
2009-03-22 15:00:41.081 Deleting UPnP client...

---

### Post by newlinux on 2009-03-22
```
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext 
```

Is still in your log. Make sure that /etc/X11/XvMCConfig is exactly:

libXvMCNVIDIA_dynamic.so.1

And that you restarted X after making that change...
 Can you post your xorg.conf?

also what do:
```

locate libXvMCNVIDIA_dynamic.so.1

```
and
```

locate libXvMC.so.1

```

return?

---

### Post by dave00001 on 2009-03-22
newlinux you are a lifesaver.

I was wondering why the line:

/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext

kept coming up, and I was SURE I had the correct /etc/X11/XvMCConfig file.

However after going through it I noticed that I had originally created a file called XmVCConfig (not XvMCConfig).  Pushing the "up" cursor on my terminal for commands for the past two weeks kept me making this mistake.  (See my second post for the proof! :P)

I have changed it now - and - thankfully - the OSD is B&W, and my 1080i is displaying pretty well!  It takes 5-6 seconds for the audio and video to sync up but after that I can't complain! 

Even HD basketball recordings are coming in clear!  Anything above 70% signal strength comes in really well.  March madness here I come.....

Thanks to all (esp. newlinux) for your help, and if anyone else is looking for a fix to this, here is the directions for my fix (note this only pertains to nvidia users):

1)  Make sure you have the correct driver to display XvMC.  Synaptic or Envy can do this.
2)  Change or create your /etc/X11/XvMCConfig file to display libXvMCNVIDIA_dynamic.so.1 
3)  Change your /etc/x11/xorg.conf file.  Make sure your driver is set to "nvidia" and not "nv".

Also, under device, add the lines:

Option "RenderAccel" "true"
Option "NVAGP" "0"
Option "UseEvents" "True"
Option "XvmcUsesTextures" "false"


Note - some people think putting a "1" or "2" into the NVAGP line works better for them.  

4)  Set your playback profiles (as suggested by newlinux) to using standard xvmc decoder and xvmc-blit, 1CPU, bob 2x deinterlacer, and one field fallback deinterlacer.


For more info see 

[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

Everything you could think of will be on there.

Avoid Typos.  It will save time in the end ;)

---

### Post by dibuntux on 2009-03-23
Checked all & tried again: got audio but no video, only a blue screen. This is the text I got in the terminal were I run the frontend:

2009-03-23 15:11:27.752 Using runtime prefix = /usr
2009-03-23 15:11:28.332 XScreenSaver support enabled
2009-03-23 15:11:28.333 DPMS is active.
2009-03-23 15:11:28.346 Empty LocalHostName.
2009-03-23 15:11:28.346 Using localhost value of mitouno
2009-03-23 15:11:28.413 New DB connection, total: 1
2009-03-23 15:11:28.421 Connected to database 'mythconverg' at host: localhost
2009-03-23 15:11:28.424 Closing DB connection named 'DBManager0'
2009-03-23 15:11:28.427 Primary screen 0.
2009-03-23 15:11:28.428 Connected to database 'mythconverg' at host: localhost
2009-03-23 15:11:28.439 Using screen 0, 1280x720 at 0,0
2009-03-23 15:11:28.480 New DB connection, total: 2
2009-03-23 15:11:28.483 Connected to database 'mythconverg' at host: localhost
2009-03-23 15:11:28.494 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-23 15:11:28.495 Enabled verbose msgs:  important general
2009-03-23 15:11:29.882 No theme dir: /home/davidino/.mythtv/themes/blootube-wide
2009-03-23 15:11:29.885 Primary screen 0.
2009-03-23 15:11:29.886 Using screen 0, 1280x720 at 0,0
2009-03-23 15:11:29.888 No theme dir: /home/davidino/.mythtv/themes/blootube-wide
2009-03-23 15:11:29.889 Switching to wide mode (blootube-wide)
2009-03-23 15:11:29.969 Using the Qt painter
2009-03-23 15:11:29.974 JoystickMenuClient Error: Joystick disabled - Failed to read /home/davidino/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-23 15:11:29.993 lirc_init failed for mythtv, see preceding messages
2009-03-23 15:11:30.908 Specified base font 'medium' does not exist for font clock
2009-03-23 15:11:30.908 Specified base font 'medium' does not exist for font small
2009-03-23 15:11:30.909 Specified base font 'medium' does not exist for font medium
2009-03-23 15:11:30.909 Specified base font 'medium' does not exist for font large
2009-03-23 15:11:30.911 Loading from: /usr/share/mythtv/themes/blootube-wide/base.xml
2009-03-23 15:11:31.066 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-23 15:11:31.140 Registering Internal as a media playback plugin.
2009-03-23 15:11:31.367 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-23 15:11:31.479 Failed to run 'cdrecord --scanbus'
2009-03-23 15:11:31.488 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-23 15:11:31.503 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-23 15:11:31.586 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.100:5060 NAT address 192.168.1.100
SIP: Cannot register; proxy, username or password not set
2009-03-23 15:11:31.868 No theme dir: /home/davidino/.mythtv/themes/blootube-wide
2009-03-23 15:11:42.039 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2009-03-23 15:11:42.043 Using protocol version 40
2009-03-23 15:11:42.129 TV: Attempting to change from None to WatchingLiveTV
2009-03-23 15:11:42.139 Using protocol version 40
2009-03-23 15:11:44.594 DPMS Deactivated 
2009-03-23 15:11:44.792 NVP: Disabling Audio, params(-1,2,44100)
2009-03-23 15:11:44.951 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-03-23 15:11:44.958 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Overlay'
2009-03-23 15:11:45.173 OSD Theme Dimensions W: 1280 H: 720
2009-03-23 15:11:45.954 Unknown altfont: infofont in textarea: callsign
2009-03-23 15:11:47.331 TV: Changing from None to WatchingLiveTV
2009-03-23 15:11:47.358 Realtime priority would require SUID as root.
2009-03-23 15:11:47.698 Video timing method: USleep with busy wait
2009-03-23 15:11:49.150 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Overlay'
2009-03-23 15:11:49.536 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-03-23 15:11:49.538 AFD: Opened codec 0x9eb6890, id(MPEG2VIDEO_XVMC) type(Video)
2009-03-23 15:11:49.538 AFD: codec MP3 has 2 channels
2009-03-23 15:11:49.538 AFD: Opened codec 0x9eb6e60, id(MP3) type(Audio)
2009-03-23 15:11:49.538 AFD: codec MP3 has 2 channels
2009-03-23 15:11:49.539 AFD: Opened codec 0x9eb72d0, id(MP3) type(Audio)
2009-03-23 15:11:49.609 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-23 15:11:49.610 Opening ALSA audio device 'default'.
2009-03-23 15:11:49.737 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-03-23 15:11:50.002 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-03-23 15:11:50.006 NVP: Enabling Audio
2009-03-23 15:11:50.033 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-03-23 15:11:50.186 XvMC: picture structure FRAME
2009-03-23 15:12:04.469 TV: Attempting to change from WatchingLiveTV to None
2009-03-23 15:12:04.890 TV: Changing from WatchingLiveTV to None
2009-03-23 15:12:04.961 DPMS Reactivated.
tail: error reading `/proc/driver/nvidia/agp': Is a directory
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory

Any help?

---

### Post by newlinux on 2009-03-23
@dibuntix

post your xorg.conf, and tell us your playback profile settings. Also, I'm note sure I get the last three lines of your log... Those are from the frontend logs?

Also have you tried using xvmc outside of myth - like with mplayer, to verify it is working.

---

### Post by dibuntux on 2009-03-23
Ok, thank you in advance for help! 
The profile I use is one I created with :
if rez > 00 -> XvMC decoder: standard XvMC, 1 CPU, video render xvmc-blit OSD chromakey no fade, deint Bob 2x fallback 1 field
In mplayer I also get audio and a blue screen:

mplayer -vo xvmc -vc ffmpeg12mc 8125_20081225233100.mpg
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 1800+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 8125_20081225233100.mpg.
TS file format detected.
VIDEO MPEG2(pid=730) AUDIO MPA(pid=731) NO SUBS (yet)!  PROGRAM N. 1
VIDEO:  MPEG2  704x576  (aspect 2)  25.000 fps  10000.0 kbps (1250.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Forced video codec: ffmpeg12mc
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC accelerated codec.
Selected video codec: [ffmpeg12mc] vfm: ffmpeg (FFmpeg MPEG-1/2 (XvMC))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] Trying pixfmt=0.
VDec: vo config request - 704 x 576 (preferred colorspace: MPEG1/2 Motion Compensation and IDCT)
VDec: using MPEG1/2 Motion Compensation and IDCT as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xvmc] 704x576 => 768x576 MPEG1/2 Motion Compensation and IDCT 
vo_xvmc: Port 245 grabed
vo_xvmc: Found matching surface with id=54434449 on 245 port at 0 adapter
vo_xvmc: Allocated Direct Context
vo_xvmc: data_blocks allocated
vo_xvmc: mv_blocks allocated
vo_xvmc: Motion Compensation context allocated - 8 surfaces
vo_xvmc: idct=1 unsigned_intra=0
vo_xvmc: looking for OSD support
    Subpicture id 0x34344149
vo_xvmc: OSD support by additional frontend rendering
[mpegvideo_xvmc @ 0x896a290]skipped MB in I frame at 0 1
[mpegvideo_xvmc @ 0x896a290]invalid mb type in I Frame at 0 17
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 18
[mpegvideo_xvmc @ 0x896a290]invalid mb type in I Frame at 0 19
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 20
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 21
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 22
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 23
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 24
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 25
[mpegvideo_xvmc @ 0x896a290]ac-tex damaged at 0 26
[mpegvideo_xvmc @ 0x896a290]Warning MVs not available
[mpegvideo_xvmc @ 0x896a290]concealing 176 DC, 176 AC, 176 MV errors
[mpegvideo_xvmc @ 0x896a290]concealing 176 DC, 176 AC, 176 MV errors0 
[mpegvideo_xvmc @ 0x896a290]concealing 176 DC, 176 AC, 176 MV errors0 
No bind found for key 'MOUSE_BTN0'.                         3.2% 8 0 
No bind found for key 'c'.                          9%  3%  3.2% 8 0 
A:39132.0 V:39132.1 A-V: -0.007 ct: -0.587 562/562  9%  3%  3.0% 8 0 

MPlayer interrupted by signal 2 in module: sleep_timer
vo_xvmc::uninit surface_render[2].status=1
GNOME screensaver enabled


This is mi xorg.conf:
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"OPTi Optoma HD65"
	Horizsync	15.0	-	120.0
	Vertrefresh	15.0	-	99.0
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Option		"DPI"	"100x100"
	Option		"AddARGBVisuals"	"1"
	Option		"AddARGBGLXVisuals"	"1"
	Option		"NoLogo"	"true" # by dav
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Option		"UseEvents"	"true"	
	Option		"RenderAccel"	"true" # by dav
	Option		"XvmcUsesTextures" "false"	# by dav
	Option		"NVAGP" "1"		# by dav
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce FX 5200"
 EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"	"1920x1080"	"1280x720"	"1024x768"	"720x480"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"1280x720 +0+0; nvidia-auto-select +0+0; 720x480 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection

# by dav sec extension to disable composite
Section "Extensions"
	Option "Composite" "Disabled"
EndSection

My system: Mythbuntu 8.10
Athlon 1700+ 512MB SDRAM PC133
Nvidia FX5200 256 MB
Hauppauge HVR 1110 DV-T
SkyStar 2.6 DVB-S

---

### Post by newlinux on 2009-03-23
> **dibuntux said:**
> Following your posts, I realized XvMC is enabled by the book but not working in my PC. I was using CPU-- profile, but realized it falls back tou using xvblit instead. If I force an XvMC only profile I get this over and over in my frontend log:
2008-05-25 16:13:44.347 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil)
2008-05-25 16:13:44.347 AFD Error: Unknown decoding error

with a black screen.

Hope this can help sort the matter out.

TIA

My system: Mythbuntu 8.10
Athlon 1700+ 512MB SDRAM PC133
Nvidia FX5200 256 MB
Hauppauge HVR 1110 DV-T
SkyStar 2.6 DVB-S

Don't thank me yet. I haven't helped you :) Hopefully I can. I quoted this one because you no longer get these errors in your logs. What did you change? I remember having this errors on my system when XvMC was working, but only partially (didn't work in myth for 1080i recordings, but worked for everything else). From your mplayer output and recent mythfrontend log output it looks like now XvMC isn't working at all. Just curious what changed since you got those get_buffer errors.

Some xorg.conf observations: Not all the options in the wiki were needed, and some of them are outdated or not appropriate for some distros/hardware. Setting NVAGP to 1 means to use NvAGP if possible instead of AGPGART, but in ubuntu agpgart is loaded in the kernel, and you can't use NvAGP if that is true (you have to disable agpgart at boot). So that option is probably useless, unless you disable agpgart. NvAGP only works on some chipsets anyway (and obviously only for AGP cards)

False is the default for XvmCUseTextures
Option "AddARGBGLXVisuals" "1" - I think only works if composite is enabled, and the default is "1" anyway..
Option "AddARGBVisuals" "1" - not sure what this is...

The machine I have that uses XvMC is a nvidia 6150. Below is releveant sections of my xorg.conf (very few options specified):

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
        Option		"UseEvents" 	"on"
#	Option "XvmcUsesTextures" "true"  


EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
 #Section "Extensions"
 #     Option "Composite" "Disabled"
 #EndSection

```

Note the sections I commented out as something to try...

Of course, my guess is none of this is your problem, unfortunately. I'll see if I can look into it a bit more...
Maybe post your /var/log/Xorg.0.log to see what X is doing.

FWIW, you might get more help if you create a new thread so people can start off seeing your problem and config etc. They have to go through a lot in this thread to get there...

Also, it could just be that even with XvMC there isn't enough juice in an athlon 1700+ - but I think I've seen others get HD working with XvMC on that proc. What happens when you watch SD Mpeg-2 content and try to use XvMC?

---

### Post by dibuntux on 2009-03-23
It now WORKS! The OSD is in B/W for 1st time!
It also works in mplayer. So thank you! You are definitely helping! Still some issues..

This section must be disabled in xorg.conf

# by dav sec extension to disable composite
# Section "Extensions"
# Option "Composite" "Disabled"
# EndSection

and Option "NVAGP" "1" # by dav must be present

I'm now trying with Option "NVAGP" "0" and it seems less prone to crash...

What I do not understand is that the profile is set for using Bob 2x or Onefield deinterlacer but I get always an interlaced image, either in LiveTv or recordings
I have to manually set Progressive from the source menu.
What can I do to automatically set on progressive?

Thanks again in advance!

---

### Post by newlinux on 2009-03-23
Glad you are a step farther. I want to make sure I understand what problem you are having. Are you saying that when you are watching something you have to go to "video scan" in the menu and change it to progressive? The autodetect doesn't work or something? What do you mean by "source menu?" What effect is this having on your picture? what type of monitor is your display connected to?

BTW, if you have a nvidia 5200, you can actually get the OSD to be in color, while using XvMC. Unfortunately, from what I remember, you have to disable the composite extension, which apparently was causing problems from you (and you have to disable the XvMCTextures. I think others have had success using the xvmc-openGL renderer and opengl OSD and color... I don't have a 5 series to test this on, however (color OSD doesn't work on 6 or 7 series).

---

### Post by dibuntux on 2009-03-24
Ok, some more informations:
1) I'm using an DLP projector - Optoma HD700x at 720p res.
2) The menu is badly translated in italian as "Ricerca segnale" (signal search - it should be "Scansione") and gives the option Sense (default), Progressive, Interlaced (normal) & Interlaced (inverted). When I switch from Sense to Progressive the OSD is normally readable, otherwise its quality is very poor. The screen image also looks more stable, expecially on edges and CG graphics. Since the DLP is only capable of displaying progressive is difficult to say; it just seems better if I switch to progressive, at least for OSD.
3) As for your suggestion, I tried xvmc-openGL renderer and opengl OSD, but it remains the same in B/W.
4) Myth seems more sensible to hangs of the frontend when something goes wrong, like an encrypted program. Sometimes even when using the OSD menu. Exiting I found in terminal "VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock". Sometimes I had to restart the PC instead of just re-logging.
5) Maybe I should help with MythTV translation...

---

### Post by newlinux on 2009-03-24
The problem is probably your deinterlacer. Bob 2x will sometimes do that (and give jittery video) if all your video settings (especially openGL, you may want to play with your nvidia-settings openGL settings) aren't right for your display. Maybe you could try disabling the interlacer in your playback profile (set them both to none) or using one field. I don't know of anyways to force it to use progressive...

---

### Post by sawbuck on 2009-09-23
Not sure if this thread is the right place for this but here goes.  I have similar problems with "choppy Live TV" in both audio and video.  My system is:

Hardware
-----------


Motherboard: ASUS P4B533
CPU: Intel 2.4 Ghz
RAM: 2 Gb
Video Card: EVGA 6200 AGP 8x 512 Mb (NVIDIA GeForce chip)
Sound Card: integrated onboard
HD: Samsung 250Gb
Remote: none
Tuners: Haupauge HVR 1600 (using ATSC)
Country: US
TV provider: US Broadcast
TV signal type: Digital (HD & DTV)
Mythbuntu Version: 9.04

Mythbuntu 9.04 is not the 3rd installation on this H/W except now with a larger HDD.  I won't go into that too much except to say the first time around member klc5555 (I believer) helped me get beyond the TV card issues as well as getting XvMC up and configured back on the initial installation where I was able to watch live SD TV with no video or audio issues.  This current installation I managed to get TV card/NVIDIA card issue resolved but when I followed the same process for XvMC as before I get different results - that being choppy video and audio inb HD but only choppy auduo in SD.

Following are files and logs similar to what I've seen folks post.  I'm not sure what is needed for anyone to offer help but let me know what else is needed.  I'm totally puzzled......

BTW, my recorded shows also havev the same problem as live TV - Both audio and video choppy in HD and audio only choppy in SD.  Transcoded to 720 x auto (guess that's ~496?) both are fine.  When I have used mplayer on a recording I get good sound initially then frame count errors make a mess of things - haven't looked at a transcoded one in mplayer yet but suspect .nuv file wouldn't play, anyway.

Any help appreciated!!!!

Files, etc, follow---

-----------------------------------------

Here;s the  /etc/X11/xorg.conf file
:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option    "UseEvents"    "true"
    Option    "DPI"    "100x100"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
        Option  "XvmcUsesTextures" "false"
        Option  "NVAGP" "1"
EndSection


#Section "Extensions"
        #Option "Composite" "Disabled"
#EndSection

----------------------------------------------

And the etc/X11/XvMCConfig file:

libXvMCNVIDIA_dynamic.so.1

-------------------------------------------

And finally the Mythgrabber errors.log (a biggie!)

==> /var/log/mythtv/mythbackend.log <==
2009-09-23 16:50:19.242 AFD: Opened codec 0x90e2e00, id(MPEG2VIDEO) type(Video)
2009-09-23 16:50:19.257 AFD: codec AC3 has 6 channels
2009-09-23 16:50:19.259 AFD: Opened codec 0x90e33f0, id(AC3) type(Audio)
2009-09-23 16:50:19.830 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090923164953.mpg' 1920x1088@64s
2009-09-23 16:50:29.415 TVRec(1): Changing from WatchingLiveTV to None
2009-09-23 16:50:30.097 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:51:17.114 Reloading backend settings
2009-09-23 16:51:21.106 MainServer::HandleAnnounce Playback
2009-09-23 16:51:21.108 adding: Frank4 as a client (events: 0)
2009-09-23 16:51:21.111 TVRec(1): Changing from None to WatchingLiveTV
2009-09-23 16:51:21.119 TVRec(1): HW Tuner: 1->1
2009-09-23 16:51:22.237 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-09-23 16:51:23.407 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:51:24.470 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:51:24.539 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-09-23 16:51:24.807 Using runtime prefix = /usr
2009-09-23 16:51:24.815 DBHostName is not set in mysql.txt
2009-09-23 16:51:24.816 Assuming localhost
2009-09-23 16:51:24.817 Empty LocalHostName.
2009-09-23 16:51:24.820 Using localhost value of Frank4
2009-09-23 16:51:24.836 New DB connection, total: 1
2009-09-23 16:51:24.843 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:51:24.845 Closing DB connection named 'DBManager0'
2009-09-23 16:51:24.855 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:51:24.858 New DB connection, total: 2
2009-09-23 16:51:24.861 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:51:24.868 Current Schema Version: 1214
2009-09-23 16:51:24.886 Preview Error: Previewer file '/var/lib/mythtv/recordings/1022_20090923165121.mpg' is not valid.
2009-09-23 16:51:24.888 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1022_20090923165121.mpg'
2009-09-23 16:51:24.904 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1022_20090923165121.mpg.png) exists: 0 readable: 0 size: 0
2009-09-23 16:51:34.974 TVRec(1): Changing from WatchingLiveTV to None
2009-09-23 16:51:35.658 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:52:39.620 Expiring 0 MBytes for 1051 @ Wed Sep 23 16:00:00 2009 => Oprah Winfrey
2009-09-23 16:52:39.624 Expiring 27 MBytes for 1051 @ Wed Sep 23 16:00:00 2009 => Oprah Winfrey
2009-09-23 16:52:39.632 Expiring 0 MBytes for 1022 @ Wed Sep 23 16:30:00 2009 => WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse"
2009-09-23 16:52:39.634 Expiring 4 MBytes for 1022 @ Wed Sep 23 16:30:00 2009 => WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse"
2009-09-23 16:52:39.635 Expiring 0 MBytes for 1022 @ Wed Sep 23 16:30:00 2009 => WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse"
2009-09-23 16:52:58.715 New DB connection, total: 4
2009-09-23 16:52:58.718 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:53:12.834 Reloading backend settings
2009-09-23 16:53:18.115 MainServer::HandleAnnounce Playback
2009-09-23 16:53:18.117 adding: Frank4 as a client (events: 0)
2009-09-23 16:53:18.121 TVRec(1): Changing from None to WatchingLiveTV
2009-09-23 16:53:18.129 TVRec(1): HW Tuner: 1->1
2009-09-23 16:53:19.244 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-09-23 16:53:20.402 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:53:21.464 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:53:21.537 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-09-23 16:53:21.786 Using runtime prefix = /usr
2009-09-23 16:53:21.791 DBHostName is not set in mysql.txt
2009-09-23 16:53:21.792 Assuming localhost
2009-09-23 16:53:21.793 Empty LocalHostName.
2009-09-23 16:53:21.796 Using localhost value of Frank4
2009-09-23 16:53:21.812 New DB connection, total: 1
2009-09-23 16:53:21.819 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:53:21.821 Closing DB connection named 'DBManager0'
2009-09-23 16:53:21.833 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:53:21.842 New DB connection, total: 2
2009-09-23 16:53:21.849 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:53:21.860 Current Schema Version: 1214
2009-09-23 16:53:21.881 Preview Error: Previewer file '/var/lib/mythtv/recordings/1022_20090923165318.mpg' is not valid.
2009-09-23 16:53:21.882 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1022_20090923165318.mpg'
2009-09-23 16:53:21.895 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1022_20090923165318.mpg.png) exists: 0 readable: 0 size: 0
2009-09-23 16:54:05.104 TVRec(1): Changing from WatchingLiveTV to None
2009-09-23 16:54:05.793 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:54:39.642 Expiring 3 MBytes for 1022 @ Wed Sep 23 16:30:00 2009 => WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse"
2009-09-23 16:54:39.645 Expiring 0 MBytes for 1022 @ Wed Sep 23 16:30:00 2009 => WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse"
2009-09-23 16:56:39.658 Expiring 18 MBytes for 1022 @ Wed Sep 23 16:30:00 2009 => WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse"
2009-09-23 16:58:03.821 MainServer::HandleAnnounce Monitor
2009-09-23 16:58:03.826 adding: Frank4 as a client (events: 0)
2009-09-23 16:58:03.827 MainServer::HandleAnnounce Monitor
2009-09-23 16:58:03.828 adding: Frank4 as a client (events: 1)
2009-09-23 16:58:09.060 MainServer::HandleAnnounce Playback
2009-09-23 16:58:09.061 adding: Frank4 as a client (events: 0)
2009-09-23 16:58:09.065 TVRec(1): Changing from None to WatchingLiveTV
2009-09-23 16:58:09.073 TVRec(1): HW Tuner: 1->1
2009-09-23 16:58:10.191 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-09-23 16:58:11.438 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:58:12.500 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022
2009-09-23 16:58:12.565 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-09-23 16:58:12.823 Using runtime prefix = /usr
2009-09-23 16:58:12.851 DBHostName is not set in mysql.txt
2009-09-23 16:58:12.853 Assuming localhost
2009-09-23 16:58:12.857 Empty LocalHostName.
2009-09-23 16:58:12.861 Using localhost value of Frank4
2009-09-23 16:58:12.884 New DB connection, total: 1
2009-09-23 16:58:12.891 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:58:12.894 Closing DB connection named 'DBManager0'
2009-09-23 16:58:12.901 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:58:12.910 New DB connection, total: 2
2009-09-23 16:58:12.917 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:58:12.928 Current Schema Version: 1214
2009-09-23 16:58:12.948 Preview Error: Previewer file '/var/lib/mythtv/recordings/1022_20090923165809.mpg' is not valid.
2009-09-23 16:58:12.950 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1022_20090923165809.mpg'
2009-09-23 16:58:12.962 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1022_20090923165809.mpg.png) exists: 0 readable: 0 size: 0
2009-09-23 16:58:50.026 TVRec(1): Changing from WatchingLiveTV to None
2009-09-23 16:58:50.722 Finished recording WordGirl "Granny's Goodtime All-Cure Spritzer; Mecha-Mouse": channel 1022

==> /var/log/mythtv/mythfrontend.log <==
2009-09-23 16:58:38.581 WriteAudio: buffer underrun
2009-09-23 16:58:38.714 WriteAudio: buffer underrun
2009-09-23 16:58:38.915 WriteAudio: buffer underrun
2009-09-23 16:58:38.980 WriteAudio: buffer underrun
2009-09-23 16:58:39.114 WriteAudio: buffer underrun
2009-09-23 16:58:39.181 WriteAudio: buffer underrun
2009-09-23 16:58:39.315 WriteAudio: buffer underrun
2009-09-23 16:58:39.381 WriteAudio: buffer underrun
2009-09-23 16:58:39.516 WriteAudio: buffer underrun
2009-09-23 16:58:39.582 WriteAudio: buffer underrun
2009-09-23 16:58:39.715 WriteAudio: buffer underrun
2009-09-23 16:58:39.782 WriteAudio: buffer underrun
2009-09-23 16:58:39.915 WriteAudio: buffer underrun
2009-09-23 16:58:40.318 WriteAudio: buffer underrun
2009-09-23 16:58:40.383 WriteAudio: buffer underrun
2009-09-23 16:58:40.516 WriteAudio: buffer underrun
2009-09-23 16:58:40.716 WriteAudio: buffer underrun
2009-09-23 16:58:40.783 WriteAudio: buffer underrun
2009-09-23 16:58:40.916 WriteAudio: buffer underrun
2009-09-23 16:58:40.984 WriteAudio: buffer underrun
2009-09-23 16:58:41.117 WriteAudio: buffer underrun
2009-09-23 16:58:41.200 WriteAudio: buffer underrun
2009-09-23 16:58:41.317 WriteAudio: buffer underrun
2009-09-23 16:58:41.384 WriteAudio: buffer underrun
2009-09-23 16:58:41.517 WriteAudio: buffer underrun
2009-09-23 16:58:41.584 WriteAudio: buffer underrun
2009-09-23 16:58:41.717 WriteAudio: buffer underrun
2009-09-23 16:58:41.986 WriteAudio: buffer underrun
2009-09-23 16:58:42.117 WriteAudio: buffer underrun
2009-09-23 16:58:42.317 WriteAudio: buffer underrun
2009-09-23 16:58:42.498 WriteAudio: buffer underrun
2009-09-23 16:58:42.565 WriteAudio: buffer underrun
2009-09-23 16:58:42.698 WriteAudio: buffer underrun
2009-09-23 16:58:42.765 WriteAudio: buffer underrun
2009-09-23 16:58:42.898 WriteAudio: buffer underrun
2009-09-23 16:58:43.098 WriteAudio: buffer underrun
2009-09-23 16:58:43.165 WriteAudio: buffer underrun
2009-09-23 16:58:43.299 WriteAudio: buffer underrun
2009-09-23 16:58:43.366 WriteAudio: buffer underrun
2009-09-23 16:58:43.499 WriteAudio: buffer underrun
2009-09-23 16:58:43.567 WriteAudio: buffer underrun
2009-09-23 16:58:43.699 WriteAudio: buffer underrun
2009-09-23 16:58:43.769 WriteAudio: buffer underrun
2009-09-23 16:58:43.899 WriteAudio: buffer underrun
2009-09-23 16:58:43.966 WriteAudio: buffer underrun
2009-09-23 16:58:44.099 WriteAudio: buffer underrun
2009-09-23 16:58:44.167 WriteAudio: buffer underrun
2009-09-23 16:58:44.300 WriteAudio: buffer underrun
2009-09-23 16:58:44.568 WriteAudio: buffer underrun
2009-09-23 16:58:44.700 WriteAudio: buffer underrun
2009-09-23 16:58:44.767 WriteAudio: buffer underrun
2009-09-23 16:58:44.900 WriteAudio: buffer underrun
2009-09-23 16:58:44.967 WriteAudio: buffer underrun
2009-09-23 16:58:45.100 WriteAudio: buffer underrun
2009-09-23 16:58:45.168 WriteAudio: buffer underrun
2009-09-23 16:58:45.300 WriteAudio: buffer underrun
2009-09-23 16:58:45.367 WriteAudio: buffer underrun
2009-09-23 16:58:45.502 WriteAudio: buffer underrun
2009-09-23 16:58:45.568 WriteAudio: buffer underrun
2009-09-23 16:58:45.701 WriteAudio: buffer underrun
2009-09-23 16:58:45.768 WriteAudio: buffer underrun
2009-09-23 16:58:45.901 WriteAudio: buffer underrun
2009-09-23 16:58:45.969 WriteAudio: buffer underrun
2009-09-23 16:58:46.101 WriteAudio: buffer underrun
2009-09-23 16:58:46.169 WriteAudio: buffer underrun
2009-09-23 16:58:46.302 WriteAudio: buffer underrun
2009-09-23 16:58:46.369 WriteAudio: buffer underrun
2009-09-23 16:58:46.502 WriteAudio: buffer underrun
2009-09-23 16:58:46.784 WriteAudio: buffer underrun
2009-09-23 16:58:46.903 WriteAudio: buffer underrun
2009-09-23 16:58:46.969 WriteAudio: buffer underrun
2009-09-23 16:58:47.102 WriteAudio: buffer underrun
2009-09-23 16:58:47.172 WriteAudio: buffer underrun
2009-09-23 16:58:47.303 WriteAudio: buffer underrun
2009-09-23 16:58:47.370 WriteAudio: buffer underrun
2009-09-23 16:58:47.503 WriteAudio: buffer underrun
2009-09-23 16:58:47.569 WriteAudio: buffer underrun
2009-09-23 16:58:47.703 WriteAudio: buffer underrun
2009-09-23 16:58:47.771 WriteAudio: buffer underrun
2009-09-23 16:58:47.903 WriteAudio: buffer underrun
2009-09-23 16:58:47.971 WriteAudio: buffer underrun
2009-09-23 16:58:48.103 WriteAudio: buffer underrun
2009-09-23 16:58:48.704 WriteAudio: buffer underrun
2009-09-23 16:58:48.771 WriteAudio: buffer underrun
2009-09-23 16:58:48.904 WriteAudio: buffer underrun
2009-09-23 16:58:48.974 WriteAudio: buffer underrun
2009-09-23 16:58:49.104 WriteAudio: buffer underrun
2009-09-23 16:58:49.174 WriteAudio: buffer underrun
2009-09-23 16:58:49.305 WriteAudio: buffer underrun
2009-09-23 16:58:49.371 WriteAudio: buffer underrun
2009-09-23 16:58:49.505 WriteAudio: buffer underrun
2009-09-23 16:58:49.572 WriteAudio: buffer underrun
2009-09-23 16:58:49.705 WriteAudio: buffer underrun
2009-09-23 16:58:49.776 WriteAudio: buffer underrun
2009-09-23 16:58:49.905 WriteAudio: buffer underrun
2009-09-23 16:58:49.972 WriteAudio: buffer underrun
2009-09-23 16:58:49.999 TV: Attempting to change from WatchingLiveTV to None
2009-09-23 16:58:50.765 TV: Changing from WatchingLiveTV to None
2009-09-23 16:58:50.800 DPMS Reactivated.
2009-09-23 16:58:55.356 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Sep 23 07:50:01 Frank4 /USR/SBIN/CRON[8303]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 08:00:01 Frank4 /USR/SBIN/CRON[8579]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 08:00:01 Frank4 /USR/SBIN/CRON[8582]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 08:09:01 Frank4 /USR/SBIN/CRON[9003]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 08:10:01 Frank4 /USR/SBIN/CRON[9222]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 08:17:01 Frank4 /USR/SBIN/CRON[9491]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 08:20:01 Frank4 /USR/SBIN/CRON[9706]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 08:30:01 Frank4 /USR/SBIN/CRON[9975]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 08:39:01 Frank4 /USR/SBIN/CRON[10244]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 08:40:01 Frank4 /USR/SBIN/CRON[10463]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 08:50:01 Frank4 /USR/SBIN/CRON[10732]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 09:00:01 Frank4 /USR/SBIN/CRON[11008]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 09:00:01 Frank4 /USR/SBIN/CRON[11011]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 09:09:01 Frank4 /USR/SBIN/CRON[11430]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 09:10:01 Frank4 /USR/SBIN/CRON[11649]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 09:17:01 Frank4 /USR/SBIN/CRON[11918]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 09:20:01 Frank4 /USR/SBIN/CRON[12133]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 09:30:01 Frank4 /USR/SBIN/CRON[12402]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 09:39:01 Frank4 /USR/SBIN/CRON[12671]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 09:40:01 Frank4 /USR/SBIN/CRON[12890]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 09:46:47 Frank4 ntpd[3792]: kernel time sync status change 4001
Sep 23 09:50:01 Frank4 /USR/SBIN/CRON[13159]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 10:00:01 Frank4 /USR/SBIN/CRON[13430]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 10:00:01 Frank4 /USR/SBIN/CRON[13442]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 10:09:01 Frank4 /USR/SBIN/CRON[13857]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 10:10:01 Frank4 /USR/SBIN/CRON[14076]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 10:17:01 Frank4 /USR/SBIN/CRON[14345]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 10:20:01 Frank4 /USR/SBIN/CRON[14560]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 10:30:01 Frank4 /USR/SBIN/CRON[14829]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 10:38:02 Frank4 ntpd[3792]: kernel time sync status change 0001
Sep 23 10:39:01 Frank4 /USR/SBIN/CRON[15098]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 10:40:01 Frank4 /USR/SBIN/CRON[15317]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 10:50:01 Frank4 /USR/SBIN/CRON[15586]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 11:00:01 Frank4 /USR/SBIN/CRON[15862]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 11:00:01 Frank4 /USR/SBIN/CRON[15865]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 11:09:01 Frank4 /USR/SBIN/CRON[16284]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 11:10:01 Frank4 /USR/SBIN/CRON[16503]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 11:17:01 Frank4 /USR/SBIN/CRON[16772]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 11:20:01 Frank4 /USR/SBIN/CRON[16987]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 11:30:01 Frank4 /USR/SBIN/CRON[17256]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 11:39:01 Frank4 /USR/SBIN/CRON[17525]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 11:40:01 Frank4 /USR/SBIN/CRON[17744]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 11:46:20 Frank4 ntpd[3792]: kernel time sync status change 4001
Sep 23 11:50:01 Frank4 /USR/SBIN/CRON[18013]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 12:00:01 Frank4 /USR/SBIN/CRON[18289]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 12:00:01 Frank4 /USR/SBIN/CRON[18292]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 12:09:01 Frank4 /USR/SBIN/CRON[18711]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 12:10:01 Frank4 /USR/SBIN/CRON[18930]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 12:17:01 Frank4 /USR/SBIN/CRON[19199]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 12:20:01 Frank4 /USR/SBIN/CRON[19414]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 12:20:28 Frank4 ntpd[3792]: kernel time sync status change 0001
Sep 23 12:30:01 Frank4 /USR/SBIN/CRON[19683]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 12:39:01 Frank4 /USR/SBIN/CRON[19952]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 12:40:01 Frank4 /USR/SBIN/CRON[20171]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 12:50:01 Frank4 /USR/SBIN/CRON[20440]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 13:00:01 Frank4 /USR/SBIN/CRON[20711]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 13:00:01 Frank4 /USR/SBIN/CRON[20726]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 13:09:01 Frank4 /USR/SBIN/CRON[21084]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 13:10:01 Frank4 /USR/SBIN/CRON[21303]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 13:17:01 Frank4 /USR/SBIN/CRON[21572]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 13:20:01 Frank4 /USR/SBIN/CRON[21787]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 13:28:47 Frank4 ntpd[3792]: kernel time sync status change 4001
Sep 23 13:30:01 Frank4 /USR/SBIN/CRON[22056]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 13:39:01 Frank4 /USR/SBIN/CRON[22325]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 13:40:01 Frank4 /USR/SBIN/CRON[22544]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 13:50:01 Frank4 /USR/SBIN/CRON[22813]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:00:01 Frank4 /USR/SBIN/CRON[23089]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:00:01 Frank4 /USR/SBIN/CRON[23092]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 14:09:01 Frank4 /USR/SBIN/CRON[23511]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 14:10:01 Frank4 /USR/SBIN/CRON[23730]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:17:01 Frank4 /USR/SBIN/CRON[23999]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 14:20:01 Frank4 /USR/SBIN/CRON[24214]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:20:01 Frank4 ntpd[3792]: kernel time sync status change 0001
Sep 23 14:30:01 Frank4 /USR/SBIN/CRON[24483]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:39:01 Frank4 /USR/SBIN/CRON[24752]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 14:40:01 Frank4 /USR/SBIN/CRON[24971]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:50:01 Frank4 /USR/SBIN/CRON[25240]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 14:54:11 Frank4 ntpd[3792]: kernel time sync status change 4001
Sep 23 15:00:01 Frank4 /USR/SBIN/CRON[25516]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 15:00:01 Frank4 /USR/SBIN/CRON[25519]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 15:09:01 Frank4 /USR/SBIN/CRON[25938]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 15:10:01 Frank4 /USR/SBIN/CRON[26157]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 15:11:15 Frank4 ntpd[3792]: kernel time sync status change 0001
Sep 23 15:17:01 Frank4 /USR/SBIN/CRON[26426]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 15:20:01 Frank4 /USR/SBIN/CRON[26641]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 15:30:01 Frank4 /USR/SBIN/CRON[26910]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 15:39:01 Frank4 /USR/SBIN/CRON[27179]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 15:40:01 Frank4 /USR/SBIN/CRON[27398]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 15:49:09 Frank4 kernel: [34345.808893] mythfilldatabas[27668]: segfault at 6b ip b5d5c190 sp b452679c error 6
Sep 23 15:50:01 Frank4 /USR/SBIN/CRON[27676]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 16:00:01 Frank4 /USR/SBIN/CRON[27952]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep 23 16:00:01 Frank4 /USR/SBIN/CRON[27955]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 16:09:01 Frank4 /USR/SBIN/CRON[28374]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 16:10:01 Frank4 /USR/SBIN/CRON[28593]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 16:17:01 Frank4 /USR/SBIN/CRON[28862]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 16:20:01 Frank4 /USR/SBIN/CRON[29077]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 16:30:01 Frank4 /USR/SBIN/CRON[29400]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 16:39:01 Frank4 /USR/SBIN/CRON[29829]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 23 16:40:01 Frank4 /USR/SBIN/CRON[30048]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 23 16:50:01 Frank4 /USR/SBIN/CRON[30367]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

==> /var/log/Xorg.0.log <==
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     Acer X191W (CRT-0)
(--) NVIDIA(0): Acer X191W (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0

==> /home/frank/.xsession-errors <==
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-09-23 06:54:10.636 Using runtime prefix = /usr
2009-09-23 06:54:11.184 XScreenSaver support enabled
2009-09-23 06:54:11.185 DPMS is active.
2009-09-23 06:54:11.186 DBHostName is not set in mysql.txt
2009-09-23 06:54:11.186 Assuming localhost
2009-09-23 06:54:11.186 Empty LocalHostName.
2009-09-23 06:54:11.186 Using localhost value of Frank4
2009-09-23 06:54:11.197 New DB connection, total: 1
2009-09-23 06:54:11.202 Connected to database 'mythconverg' at host: localhost
2009-09-23 06:54:11.211 Closing DB connection named 'DBManager0'
2009-09-23 06:54:11.213 Primary screen 0.
2009-09-23 06:54:11.214 Connected to database 'mythconverg' at host: localhost
2009-09-23 06:54:11.232 Using screen 0, 1440x900 at 0,0

** (gnome-system-monitor:6127): WARNING **: SELinux was found but is not enabled.

Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-09-23 16:26:47.564 Using runtime prefix = /usr
2009-09-23 16:26:48.143 XScreenSaver support enabled
2009-09-23 16:26:48.143 DPMS is active.
2009-09-23 16:26:48.144 DBHostName is not set in mysql.txt
2009-09-23 16:26:48.144 Assuming localhost
2009-09-23 16:26:48.144 Empty LocalHostName.
2009-09-23 16:26:48.144 Using localhost value of Frank4
2009-09-23 16:26:48.180 New DB connection, total: 1
2009-09-23 16:26:48.185 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:26:48.194 Closing DB connection named 'DBManager0'
2009-09-23 16:26:48.197 Primary screen 0.
2009-09-23 16:26:48.197 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:26:48.199 Using screen 0, 1440x900 at 0,0
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-09-23 16:31:29.645 Using runtime prefix = /usr
2009-09-23 16:31:30.182 XScreenSaver support enabled
2009-09-23 16:31:30.183 DPMS is active.
2009-09-23 16:31:30.183 DBHostName is not set in mysql.txt
2009-09-23 16:31:30.184 Assuming localhost
2009-09-23 16:31:30.184 Empty LocalHostName.
2009-09-23 16:31:30.184 Using localhost value of Frank4
2009-09-23 16:31:30.196 New DB connection, total: 1
2009-09-23 16:31:30.201 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:31:30.203 Closing DB connection named 'DBManager0'
2009-09-23 16:31:30.206 Primary screen 0.
2009-09-23 16:31:30.207 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:31:30.209 Using screen 0, 1440x900 at 0,0
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
E: context.c: waitpid(): No child processes
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-09-23 16:44:14.018 Using runtime prefix = /usr
2009-09-23 16:44:14.554 XScreenSaver support enabled
2009-09-23 16:44:14.555 DPMS is active.
2009-09-23 16:44:14.555 DBHostName is not set in mysql.txt
2009-09-23 16:44:14.556 Assuming localhost
2009-09-23 16:44:14.556 Empty LocalHostName.
2009-09-23 16:44:14.556 Using localhost value of Frank4
2009-09-23 16:44:14.567 New DB connection, total: 1
2009-09-23 16:44:14.573 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:44:14.575 Closing DB connection named 'DBManager0'
2009-09-23 16:44:14.577 Primary screen 0.
2009-09-23 16:44:14.578 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:44:14.580 Using screen 0, 1440x900 at 0,0
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-09-23 16:55:55.133 Using runtime prefix = /usr
2009-09-23 16:55:55.669 XScreenSaver support enabled
2009-09-23 16:55:55.670 DPMS is active.
2009-09-23 16:55:55.670 DBHostName is not set in mysql.txt
2009-09-23 16:55:55.671 Assuming localhost
2009-09-23 16:55:55.671 Empty LocalHostName.
2009-09-23 16:55:55.671 Using localhost value of Frank4
2009-09-23 16:55:55.683 New DB connection, total: 1
2009-09-23 16:55:55.688 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:55:55.690 Closing DB connection named 'DBManager0'
2009-09-23 16:55:55.692 Primary screen 0.
2009-09-23 16:55:55.693 Connected to database 'mythconverg' at host: localhost
2009-09-23 16:55:55.695 Using screen 0, 1440x900 at 0,0

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  6.4G  4.1G  61% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  364K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  164K 1007M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
lrm                  1007M  2.4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6             222G  2.6G  220G   2% /var/lib

==> uname -a <==
Linux Frank4 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
02:0d.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/agp <==

==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

==> /proc/driver/nvidia/warnings <==
Model:          GeForce 6200
IRQ:            16
Video BIOS:      05.44.a2.10.00
Card Type:      AGP
DMA Size:      32 bits
DMA Mask:      0xffffffff
Bus Location:      01.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2013MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.4
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia:0
                description: Multimedia audio controller
                product: CM8738
                vendor: C-Media Electronics Inc
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 81
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=[REMOVED] latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
           *-multimedia:1
                description: Multimedia video controller
                product: CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx18 latency=64 maxlatency=200 mingnt=2 module=cx18
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by sawbuck on 2009-09-23
[quote=sawbuck;7996327].....
.
.
.
.
BTW, my recorded shows also havev the same problem as live TV - Both audio and video choppy in HD and audio only choppy in SD. Transcoded to 720 x auto (guess that's ~496?) both are fine. When I have used mplayer on a recording I get good sound initially then frame count errors make a mess of things - haven't looked at a transcoded one in mplayer yet but suspect .nuv file wouldn't play, anyway.....
.
.
./quote]

Edited most of the stuff out of my quoted post except the above.  I am trying to learn this stuff so forgive my lack of understanding of the mythtv tools.  However, I did ue mplayer to play one of my transcoded files and of course it plays .nuv files fine.  No choppy audio or video.  However, as soon as it opens I get an error message:  

       "AO: [Pulse] failed to connect to server : internal error"

WHAZZAT??   The video and sound remained perfect even after killing the error box

Guess the next move will be to search the forums for that phrase.  Might have a bearing on my other sound issues??

---

