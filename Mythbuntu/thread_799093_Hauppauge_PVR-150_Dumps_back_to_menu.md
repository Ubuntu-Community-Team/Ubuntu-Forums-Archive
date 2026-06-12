---
title: "Hauppauge PVR-150 Dumps back to menu"
date: 2008-05-18
forum: Mythbuntu
---

### Post by aftershockbtc on 2008-05-18
I've seen a lot of posts regarding the Hauppauge and blaster issues, a couple referring to problems with the firmware. I've tried adding the latest firmware to /lib/firmware/2.6.24-16-generic/ 

but still when I select watch tv, it goes blank for a second then dumps back to the top menu (where I just was).

any ideas?  I realize that the answer might still be burried somewhere here in the forums but thats just it, it must be burried, cause I can't find it.

Thanks oodles.

I am using version 8.04 of unbuntu and whatever the latest included in mythbuntu of mythtv.

> 2008-05-18 17:37:30.074 MainServer::HandleAnnounce Monitor
2008-05-18 17:37:30.085 adding: temple as a client (events: 0)
2008-05-18 17:37:30.086 MainServer::HandleAnnounce Monitor
2008-05-18 17:37:30.087 adding: temple as a client (events: 1)
2008-05-18 17:37:30.092 MainServer::HandleAnnounce Playback
2008-05-18 17:37:30.104 adding: temple as a client (events: 0)
2008-05-18 17:37:30.107 TVRec(2): Changing from None to WatchingLiveTV
2008-05-18 17:37:30.112 TVRec(2): HW Tuner: 2->2
2008-05-18 17:37:31.349 TFW, Error: Opening file '/home/tranquility/1002_20080518173730.mpg'.
			eno: Permission denied (13)
2008-05-18 17:37:31.354 TVRec(2) Error: RingBuffer '/home/tranquility/1002_20080518173730.mpg' not open...
2008-05-18 17:37:31.355 TVRec(2) Error: CreateLiveTVRingBuffer() failed
2008-05-18 17:37:31.355 TVRec(2) Error: Failed to create RingBuffer 2
2008-05-18 17:37:31.358 TVRec(2): Changing from WatchingLiveTV to None
2008-05-18 17:37:31.361 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-18 17:37:31.363 MythSocket(8275418:-1): writeStringList: Error, socket went unconnected.
2008-05-18 17:38:13.515 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min


> 2008-05-18 17:37:30.073 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-18 17:37:30.074 Using protocol version 40
2008-05-18 17:37:30.091 TV: Attempting to change from None to WatchingLiveTV
2008-05-18 17:37:30.092 Using protocol version 40
2008-05-18 17:37:31.359 GetEntryAt(-1) failed.
2008-05-18 17:37:31.361 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-05-18 17:37:31.361 TV Error: LiveTV not successfully started
2008-05-18 17:37:31.361 TV Error: LiveTV not successfully started
2008-05-18 17:37:31.436 TV: Deleting TV Chain in destructor
2008-05-18 17:37:31.444 DPMS Deactivated 
2008-05-18 17:37:31.445 DPMS Reactivated.


---

### Post by robho on 2008-05-18
I don't have a solution for you, but I can tell you that my PVR-150 (low profile) works well in mythbuntu 8.04 without any special firmwares/tweaking. Have you tried running mythfrontend in a shell and watched the logs when the problem happens? mythfrontend probably reports an error there if there is one.

You can try watching tv outside of mythtv by running:
mplayer - < /dev/video0 

If that works there's probably nothing wrong with your TV card. You may not get a TV picture if the tuner isn't tuned to a channel though.

I used xawtv to tune to a channel:

Scan for and store TV channels:
scantv -i Tuner 1 -C/dev/vbi0 -npal-bgh -feurope-west > ~/.xawtv
(you may want to change pal-bgh and europe-west if you're not in western europe)

Start xawtv and tune to a channel.

---

### Post by aftershockbtc on 2008-05-18
Ok, I tried cat /dev/video0 > blah.mpg. mplayer couldn't play it but vlc could. 
I have also posted some furthur log information in an edit above.  Looks like there is something wrong with the ringbuffer....or permissions...

---

### Post by robho on 2008-05-18
I think you need to set recording directory to some place where the mythtv user may write. I guess mythtv user can't write to tranquility's home directory.

Maybe change to /home/mythtv if you really want to use a user's home directory? Set it in the storage groups option in myth-setup.

But I would suggest that you use a separate directory for your recordings and not a user's home directory..

---

### Post by aftershockbtc on 2008-05-18
Ok, I created a directory /recordings/ doing chown mythtv /recordings/ didn't work.
chown tranquility /recordings/ didn't work.
but chmod a+w did. 

so it displays breifly the channel but then freezes. backend had nothing specific. front end had this > 2008-05-18 18:33:19.161 AFD: Opened codec 0x937c180, id(MPEG2VIDEO) type(Video)
2008-05-18 18:33:19.161 AFD: codec MP2 has 2 channels
2008-05-18 18:33:19.161 AFD: Opened codec 0x935d600, id(MP2) type(Audio)
2008-05-18 18:33:19.218 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-18 18:33:19.219 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-05-18 18:33:19.221 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-05-18 18:33:19.238 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-05-18 18:33:19.238 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-05-18 18:33:19.238 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x8806230) visual(0x9083828) 
                        XJ_depth(24) WxH(1440x900) bpl(4320)
2008-05-18 18:33:19.239 VideoOutputXv Error: Failed to create X buffers.
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-05-18 18:33:19.469 Couldn't load deinterlace filter 
2008-05-18 18:33:19.470 OSD Theme Dimensions W: 640 H: 480
2008-05-18 18:33:19.742 TV: Changing from None to WatchingLiveTV
2008-05-18 18:33:19.791 Realtime priority would require SUID as root.
2008-05-18 18:33:19.797 OpenGLVideoSync()
2008-05-18 18:33:19.797 ~OpenGLVideoSync() -- begin
2008-05-18 18:33:19.797 ~OpenGLVideoSync() -- middle
2008-05-18 18:33:19.797 ~OpenGLVideoSync() -- end
2008-05-18 18:33:19.797 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-05-18 18:33:19.799 Video timing method: USleep with busy wait
2008-05-18 18:33:22.469 WriteAudio: buffer underrun
2008-05-18 18:33:22.758 WriteAudio: buffer underrun
2008-05-18 18:33:23.054 WriteAudio: buffer underrun


---

### Post by robho on 2008-05-18
I think you got the permissions right so you can forget about that right now.

> **aftershockbtc said:**
> 2008-05-18 18:33:19.238 VideoOutputXv: Falling back to X11 video output over a network socket.
*** May be very slow ***


This and some other messages look strange. Aren't you running mythfrontend on your frontend machine? Looks like you're trying to run mythfrontend on some other machine. The backend perhaps?

---

### Post by aftershockbtc on 2008-05-18
I set up mythbuntu as a front/backend primary....shouldn't it be able to handle this.

---

### Post by robho on 2008-05-18
That should work. I got the impression that you were using SSH when running mythfrontend. That would give you problems. But if you're not and your DISPLAY variable (echo $DISPLAY) is really ":0.0" (local) I don't know what happens.

It also looked like you didn't have /dev/mixer and that would probably give you audio problems.

---

### Post by adubas on 2008-05-19
I am new (just built my first box on Saturday - LOVE IT) and also have this device and had the same problem but got it to work.

in myth setup:

**capture card**: make sure "mpeg-2 encoder card pvr-x50 pvr-500" is selected

**video source**: create a video source (i used schedules direct) and make sure channel frequency table = us-cable. I named my source "SD"

**Input connections**: make sure line 1 "Tuner1" has the video source (in my case I chose "SD") that you created selected as the source created above...

This is what I did and it worked... I had the same dump back to main menu when I selected "Watch TV" prior to using these settings...

---

### Post by jjlllk on 2008-05-21
Just would like to say thank you. I had trouble getting a tv-scan initiated and the above post just made me klick. ThanX

---

