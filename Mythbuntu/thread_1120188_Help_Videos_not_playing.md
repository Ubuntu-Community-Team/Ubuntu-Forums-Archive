---
title: "Help Videos not playing"
date: 2009-04-08
forum: Mythbuntu
---

### Post by adamjseed on 2009-04-08
Hello,
(sorry for the long post)
firstly these forums are great and have provided a wealth of knowledge for me. I have been "battling" with mythtv for some time now but this one has got the better of me. I am also fairly new to linux so please keep that in mind :)

I have 2 pc's running ubuntu, a server and a media pc in the lounge; so I have mythtv backend on the server and mythtv fontend on the media pc. I have got everything working fine even NFS sharing! my problem is that when I choose the video file I wish to play, via mythvideo, it freezes (only Mythtv frontend) when it tries to play.
Now I have done some reading and here is what my fontend log is saying:
-------------------------------------------------------------
Playing /mnt/video/temp.avi
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  704x384  24bpp  23.976 fps  874.5 kbps (106.8 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...

-----------------------------------------------------------------


as far as I can tell this is a problem with xvinfo and again im presuming this is a video driver issue? 

so I ran vxinfo with the output:
[I]X-Video Extension version 2.2
screen #0
 no adaptors present[/I]

this is now where im stuck. I did look and it said I should check my /dev/X11/xorg.conf file and the devices which reads:
[I]Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection[/I]

the gfx card i have is a nvidia 9400gt

I can play the videos though the standard player so I dont know where im going wrong. 

any help would be appreciated!

regards

Adam

---

### Post by adamjseed on 2009-04-21
i thought id post as i have now fixed this issue through trial and error,

I firstly installed nvidia driver via synampic package manager

then installed xine and changed myth video launch string to:
xine -pfhq --no-splash --keymap=file:/path/to/.xine/keymap.video %s

as shown in [http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)

I dont know which fix helped but i think the xine change did the job. hope this helps anyone else with the errors

---

