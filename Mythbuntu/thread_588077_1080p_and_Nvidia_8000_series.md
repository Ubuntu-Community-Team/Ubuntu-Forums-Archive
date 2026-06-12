---
title: "1080p and Nvidia 8000 series"
date: 2007-10-23
forum: Mythbuntu
---

### Post by davecurtains on 2007-10-23
Hi,

Firstly - the 7.10 release is fantastic - congratulations on a fine release.

I do have a question regarding 1080p playback that I can't seem to find a sensible answer for.  

I'm using the Nividia 100.14.19 drivers with a MSI 8600GT card.  When I playback a 720p or 1080p video file I get occasional stutter in the stream - especially noticeable where you have a panning camera scene.  Is this my hardware not keeping up?

I'm on an AMD X2 4200 - and using top I see about 30% - 60% CPU usage on busy scenes using mplayer and xine on these files.  My resolution is running at 1920x1080.

So - question is - Should I "downgrade" to an Nividia 7x series card so I can use xvmc in the driver.  Or should I upgrade the processor to something faster like an 4800+ ?

Disks are SATA-II BTW - don't think the bottle neck is there.

Thanks!
Steve

---

### Post by superm1 on 2007-11-15
You should be able to use Xvmc with this card and the newest driver.  You sure you're not able to activate it?

---

### Post by davecurtains on 2007-11-16
Hiya,

No, the 8000 series is confirmed as not having any XvMC support, see this thread;

[http://www.nvnews.net/vbulletin/showthread.php?t=90484](http://www.nvnews.net/vbulletin/showthread.php?t=90484)

I'm still confused as to why I'm getting jitter on playback of Higher-Def content.  I played a DVD image from hard disk the other day and even that was struggling on fast moving scenes.  

I'll try and get hold of a 7600 card and report back here my findings!  Any other thoughts appreciated :-)

Cheers.

---

### Post by davecurtains on 2007-11-20
Update.

Ok, So I've downgraded to a 7600GT, I can confirm that XvMC is now indeed working - Black and White OSD.

I'm now using mplayer with -vo xv  and its no different at all.  If I check "top" my CPU never hits above 25% when playing back 720p content.  Yet every second I'm getting a slight stutter on playback.  This is the same with Xine too - there must be a bottle neck somewhere I just have no idea where?

I'm really confused.  Help!

---

### Post by newlinux on 2007-11-20
Could you describe your setup more? Are your backend and frontend on the same machine (rule out network problems)? HAve you looked at your frontend log for clues? What kind of hard drive are your storing your recordings on - if it is IDE is DMA enabled? might want to check the speed of the hard drive reads:
```

sudo hdparm -tT /dev/DISKDEVICENAME

```
replace DISKDEVICENAME with whatever disk device you are using.

Your processor and GPU should be able to playback 1080p without XvMC. What are your playback settings?

---

### Post by davecurtains on 2007-11-20
Hiya,

Thanks for the reply.  

My setup is:
AMD Athlon X2 64 4200+
1Gb DDR2 800Mhz Ram
Point of View Nvidia 7600GT 256Mb PCI-E
Audio going out on SPDIF output on M/B to Sound Receiver

Mythbuntu is installed onto a 500Gb IDE Drive (has TV recordings too)
Videos and media are on a seperate SATAII 500Gb drive.
Sharp 42" HDMI 1080p display running at 1920x1080 60Hz

Mythbuntu 7.10 Release - Patched and up to date.

I thought the system should be cutting through 720p stuff like hot butter.  When I run top, I see only max 30% utilisation. Thats the highest I've ever got it.  I've tried mplayer and xine, both stutter on HiDef rips (x264 etc) - even though CPU usage is running low.  Standard Def TV playback is perfect.

Disk Details as below;

/dev/hda1: (This is Ext3)
 Timing cached reads:   2540 MB in  2.00 seconds = 1271.22 MB/sec
 Timing buffered disk reads:  228 MB in  3.06 seconds =  74.45 MB/sec

/dev/sda1: (This is configured with XFS)
 Timing cached reads:   2460 MB in  2.00 seconds = 1231.14 MB/sec
 Timing buffered disk reads:  238 MB in  3.01 seconds =  79.09 MB/sec

mplayer playback set to:
mplayer -fs -vo xv -quiet -monitoraspect 16:9 %s

Audio is fine, stutter is really noticable on slow panning scenes.  

Thanks again!
Steve.

---

### Post by newlinux on 2007-11-20
Unfortunately, I don't know much about setting up mplayer with proper filters, but from those specs, it ain't a disk problem and it isn't network problem, and I'm sure it's not a processing power problem (I have similar and lesser hardware with that have no problems with 1080p or 720p).

It looks like a playback configuration problem.

So if I may focus on mythplayback (using the internal player with hi-def recordings) can I ask what your playback settings are (deinterlace settings, mpeg2 decoder, openGL, audio buffering, etc.). You should probably play with those settings. Chances are this is a problem with your playback settings and/or xorg.conf settings. What type of display are you using and how are you connected to it?

Sorry for all the questions, but this is how I troubleshoot. There are so many variables (and I've had a few playback problems myself that just took a lot of tweaking).

---

### Post by davecurtains on 2007-11-20
Hi,

No problems for the questions - I'm keen to learn - I've already spent ages trying to sort out what the problem may be so any assistance is greatly appreciated.

I've got no HDTV tuners in my rig, and being in the UK we only get 480p ( I think) so it copes with these without a problem.

I've generally ignored the MythTV setup as I thought that when I ran Mplayer to playback a video it effectivly dropped out of MythTV and was running Mplayer native.  In fact, if I quit MythTV frontend and run mplayer I still have the problem even if the video is not full screened. Same with Xine, it seems as soon as I go for higher quality videos, say a 1080p trailor, I get jitter/stutter.

I'm running DVI to HDMI on a 42" Sharp display.  

Thanks for any pointers...!

---

