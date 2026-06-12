---
title: "Setting up new box - frontend gets &quot;timed out waiting for recorder to start&quot;"
date: 2011-07-21
forum: Mythbuntu
---

### Post by rocketmonkeys on 2011-07-21
Hi All,

I'm having trouble setting up my mythtv box.  I used to have this working great, then the machine died.  I have a new machine now, trying to get this setup.

First, I installed stock ubuntu 11.04.  The mythtv packages there had the "v4l1 not supported" error, so I added the mythbuntu repo and updated from 0.24 to 0.24.1, which fixed that problem.  Now when I start the frontend and choose "watch live tv", it pauses for 30 seconds at the loading screen, then returns to the main menu.  In the log I get a "timed out waiting for recorder to start" error.

The setup:

PC running ubuntu 11.04 w/ mythbuntu repo installed.
Running both frontend/backend.
IP: 192.168.1.156, local network (ethernet).

Verizon FIOS STB -> Hauppauge 950Q (using RCA/composite in right now)
950Q works in tvtime (shows video from composite in)

Used mc2xml + mythfilldatabase to create 1 channel (#2 WGBH) and 1 program on default (#1) video source.
Video source set to "no grabber".

mythbackend --version:

MythTV Version   : v0.24.1-46-g63b8603
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.7.2
Options compiled in:
 linux debug using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg

Now I'm getting this error on the frontend:

2011-07-21 10:48:05.394 TV: Attempting to change from None to WatchingLiveTV
2011-07-21 10:48:05.395 MythCoreContext: Connecting to backend server: 192.168.1.156:6543 (try 1 of 1)
2011-07-21 10:48:05.395 Using protocol version 63
2011-07-21 10:48:05.501 Spawning LiveTV Recorder -- begin
2011-07-21 10:48:12.506 MythSocket(93961b0:58): readStringList: Error, timed out after 7000 ms.
2011-07-21 10:48:12.506 RemoteEncoder::SendReceiveStringList(): No response.
2011-07-21 10:48:12.506 Spawning LiveTV Recorder -- end
2011-07-21 10:48:12.515 We have a playbackURL(/var/lib/mythtv/livetv/1002_20110721104805.nuv) & cardtype(DUMMY)
2011-07-21 10:48:12.516 We have a RingBuffer
2011-07-21 10:48:12.516 MythCoreContext: Connecting to backend server: 192.168.1.156:6543 (try 1 of 1)
2011-07-21 10:48:12.517 Using protocol version 63
2011-07-21 10:48:52.518 TV Error: StartRecorder() -- timed out waiting for recorder to start
2011-07-21 10:48:52.518 TV Error: LiveTV not successfully started
2011-07-21 10:48:52.752 ScreenSaverX11Private: DPMS Deactivated 1
2011-07-21 10:54:59.659 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
2011-07-21 10:55:05.362 ScreenSaverX11Private: DPMS Reactivated 1

In the backend:

2011-07-21 10:48:05.504 TVRec(1): Changing from None to WatchingLiveTV
2011-07-21 10:48:05.668 TVRec(1) Error: Start channel invalid, setting to '2' on input Composite instead.
2011-07-21 10:48:05.708 ChannelBase(1): IsTunable(Composite1,2) Requested non-existant input 'Composite1':'-1' 
2011-07-21 10:48:05.756 TVRec(1): HW Tuner: 1->1
2011-07-21 10:48:05.837 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-07-21 10:48:05.839 LoadFromScheduler(): Error, called from backend.
2011-07-21 10:48:12.517 MainServer::ANN Playback
2011-07-21 10:48:12.568 adding: media as a client (events: 0)
2011-07-21 10:48:13.771 TVRec(1): Changing from WatchingLiveTV to None
2
2011-07-21 10:48:13.901 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffb1a0cae8)
2011-07-21 10:48:13.944 MythSocket(ffffffffb1a0cae8:-1): writeStringList: Error, socket went unconnected.
			We wrote 0 of 10 bytes with 1 errors
2011-07-21 10:48:13.978 Channel(/dev/video0) Error: InitPictureAttribute(brightness): failed to query controls.
			eno: Bad file descriptor (9)

I'm a bit lost as to the next step.  Where should I be looking?  Thanks!

---

### Post by ian dobson on 2011-07-21
Hi,

Can you actually record anything on the backend (through EPG and not through LiveTV)?

In the frontend log I see
2011-07-21 10:48:12.515 We have a playbackURL(/var/lib/mythtv/livetv/1002_20110721104805.nuv) & cardtype(DUMMY)

and
2011-07-21 10:48:05.668 TVRec(1) Error: Start channel invalid, setting to '2' on input Composite instead.
2011-07-21 10:48:05.708 ChannelBase(1): IsTunable(Composite1,2) Requested non-existant input 'Composite1':'-1' 
in the backend log

so it looks as if the tuners on the backend aren't setup correctly.

Regards
Ian Dobson

---

### Post by rocketmonkeys on 2011-07-21
> **ian dobson said:**
> Can you actually record anything on the backend (through EPG and not through LiveTV)?
I haven't tried yet, was trying to use livetv as a simple way to test if I have working video.  I've got one scheduled in a few minutes, we'll see what happens.

BTW - if I schedule a recording that would start 10 minutes ago and last until 10 minutes from now, will mythtv start recording now?  Or will it ignore the scheduled recording since it's already half-way in?

> In the frontend log I see
2011-07-21 10:48:12.515 We have a playbackURL(/var/lib/mythtv/livetv/1002_20110721104805.nuv) & cardtype(DUMMY)

and
2011-07-21 10:48:05.668 TVRec(1) Error: Start channel invalid, setting to '2' on input Composite instead.
2011-07-21 10:48:05.708 ChannelBase(1): IsTunable(Composite1,2) Requested non-existant input 'Composite1':'-1' 
in the backend log

so it looks as if the tuners on the backend aren't setup correctly.

Regards
Ian Dobson
I didn't notice the "DUMMY" there.  Where should I go to setup my cards?  I've deleted all cards before, then setup my current Hauppauge 950Q as a V4L analog tuner (to get the composite input).  That's what I'm using now.  Is there a step I forgot?

Thanks!

---

### Post by ian dobson on 2011-07-21
Hi,

So your using the composite input, how have you setup the system so that it tunes to a different channel? That could well be your problem.

Regards
Ian Dobson

---

### Post by rocketmonkeys on 2011-07-21
HOLY CRAP IT WORKED!  LiveTV is still broken, but the manual recording I scheduled works just fine.  Weird!

Re: channel changing - right now I just put "echo" as the command.  I wanted to test composite in w/o worrying about the channel changing script (since I need to use 6200ch for that, and my firewire is currently not working).  Maybe that's the problem, I can try replacing it now that I know video capture is working.

But at least now I can get recording to start working.  Thanks for the tips!

---

### Post by ian dobson on 2011-07-22
Hi,

LiveTV is not the strongest function in MythTV and most of the dev's don't use it so it doesn't get much care.

Regards
Ian Dobson

---

### Post by rocketmonkeys on 2011-07-22
> **ian dobson said:**
> Hi,

LiveTV is not the strongest function in MythTV and most of the dev's don't use it so it doesn't get much care.

Regards
Ian Dobson

That's really good to know.  Intuitively, it seemed like livetv was simpler than recording tv, so I figured livetv was a good preliminary test; also, that if livetv didn't work, not to bother testing the recording.

But this is fine.  I almost never use livetv myself.  Recordings are more important.

---

### Post by drewdin on 2012-02-21
I wonder if this is the same issue I have right now. Im going to check a scheduled recording tonight!

---

### Post by RideMan on 2012-02-22
Something to watch for if you're doing live TV...

In your tuner card setup (if I remember correctly...) there is a "Start on channel..." entry.  Obviously this doesn't apply to baseband inputs (composite, component, S-Video) but if you're using an actual tuner, make sure that the "Start on channel" entry is a valid channel!  If that is not set, or is set to a channel that won't lock, your system will time out waiting for the card to initialize before it even tries to switch to the channel you want.

If you are using baseband inputs, make sure those are correctly configured as sources as well!

--Dave Althoff, Jr.

---

