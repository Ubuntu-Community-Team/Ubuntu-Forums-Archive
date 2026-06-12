---
title: "MythTV Freezing after update last week"
date: 2008-03-18
forum: Mythbuntu
---

### Post by Tteddo on 2008-03-18
Hello all! I have a combo Backend/Frontend in my living room that works great after the update. I have a laptop in my office (Acer Aspire 5050) that was running the frontend fine across the network (just slight glitches in the CNN footer, not too bad), but after the update to .21 when I go to run live TV or aplay a recording it will play about 1 second of video and just freeze. The audio continues fine. When I hit ESC to back out in crashes.
So I then ran it from terminal and the following is what I got (copying right after the audio started):
> 2008-03-18 10:27:34.350 Opening ALSA audio device 'default'.
2008-03-18 10:27:34.395 Mixer unable to find control Master
2008-03-18 10:27:34.395 Mixer unable to find control Master
2008-03-18 10:27:34.441 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-03-18 10:27:34.441 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2008-03-18 10:27:34.441 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x83632f0) visual(0x83650d0) 
                        XJ_depth(24) WxH(1280x800) bpl(3840)
2008-03-18 10:27:34.442 VideoOutputXv Error: Failed to create X buffers.
2008-03-18 10:27:34.502 Couldn't load deinterlace filter 
2008-03-18 10:27:34.507 OSD Theme Dimensions W: 640 H: 480
2008-03-18 10:27:34.785 New DB connection, total: 3
2008-03-18 10:27:34.786 Realtime priority would require SUID as root.
2008-03-18 10:27:34.786 TV: Changing from None to WatchingLiveTV
2008-03-18 10:27:34.787 Connected to database 'mythconverg' at host: 192.168.0.146
2008-03-18 10:27:34.822 OpenGLVideoSync()
2008-03-18 10:27:34.823 ~OpenGLVideoSync() -- begin
2008-03-18 10:27:34.823 ~OpenGLVideoSync() -- middle
2008-03-18 10:27:34.823 ~OpenGLVideoSync() -- end
2008-03-18 10:27:34.825 Video timing method: USleep with busy wait
2008-03-18 10:27:41.194 WriteAudio: buffer underrun
2008-03-18 10:27:41.318 WriteAudio: buffer underrun
2008-03-18 10:27:41.448 TV: Attempting to change from WatchingLiveTV to None
2008-03-18 10:27:41.486 WriteAudio: buffer underrun
2008-03-18 10:27:41.526 WriteAudio: buffer underrun
2008-03-18 10:27:41.748 TV: Changing from WatchingLiveTV to None
2008-03-18 10:27:41.764 DPMS Reactivated.
Segmentation fault (core dumped)

I imaging that this:
> 2008-03-18 10:27:34.441 VideoOutputXv: Falling back to X11 video output over a network socket.
is the beginning of the problem, but how do I fix that?

---

### Post by superm1 on 2008-03-18
Well find out why your video driver isn't showing Xv.  the 'xvinfo' utility will tell you when Xv is on/off.  AMD cards with their proprietary driver need to have it explicitly turned on.

Also, you can only run one Xv app (with one hardware overlay) at a time.

---

### Post by Tteddo on 2008-03-18
xvinfo reports: 
> X-Video Extension version 2.2
screen #0
 no adaptors present
so I did a quick Google search, and added:
> Load  "xv"
Under my Module section in xorg.conf, then rebooted.

xvinfo still says the same, and playback is the same.

Could I be missing that module? I have xserver-xgl uninstalled as it wouldn't allow mythtv playback before, and was causing a freeze every couple of days.

I looked through Synaptic and found xvfb, installed that, and reloaded X with the same result, so I guess that wasn't it.

---

### Post by nelsonmuntz on 2008-06-01
Hi Tteddo,

did you get to the bottom of this?

I'm also currently not able to get Xv working. I've a Radeon Mobility HD3400 graphics card and despite having installed the ATI proprietary driver and enabled Xv it explicitly in xorg.conf with:

	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"

xvinfo still reports no adapters present.

If you managed to get around this, I'd love to hear how you did it!

---

### Post by Tteddo on 2008-06-01
Wow, it's been awhile. I think what I mentioned on the bottom of this thread:
[http://ubuntuforums.org/showthread.php?t=655669]("http://ubuntuforums.org/showthread.php?t=655669")
About the > Option "VideoOverlay" "on" is what finally fixed it back then.
I do know that after some MythTV updates since then, and upgrading that laptop to Hardy, I have had zero problems connecting to the backend and playing stuff. I did have to disable Compiz on that machine also and I have never turned that back on. For an easy way to enable/disable Compiz try this:
[Forlong's blog]("http://forlong.blogage.de/article/2008/5/1/Compiz-Switch-04-released#")
It works pretty slick.

---

