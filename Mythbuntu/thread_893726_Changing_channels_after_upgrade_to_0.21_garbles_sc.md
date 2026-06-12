---
title: "Changing channels after upgrade to 0.21 garbles screen"
date: 2008-08-18
forum: Mythbuntu
---

### Post by sf_basilix on 2008-08-18
I've posted this over on the standard myth forum also, but haven't been able to get any bites yet.  I'm hoping someone here might be able to have more familiarity with ubuntu and mythtv...

I was running mythtv 0.20 on Ubuntu 7.04 (feisty fawn) and decided to upgrade to Ubuntu 7.10 (Gutsy Gibbon) to get mythtv 0.21. The upgrade went successful and with the exception of one mount-point, everything seemed to upgrade well. I did notice another error that flashes by extremely fast during bootup (which I did not have in the previous version) about some buffer I/O error, but not sure if it applies here. (nor have I figured out how to resolve that yet)

I am running this on a two cpu (each dual core) AMD system with 8GB of RAM. For the video capture device, I am using a plextor convertx, which I had to recompile the latest drivers to get it to work after the upgrade. I am using a nvidia s-video out and am using the nvidia drivers required for mythtv. (I did not reinstall this driver after the upgrade, however, as I think it may have done this automatically)

Watching previous recordings works fine - even watching live tv, *except* when you change channels. This used to work fine, so I'm not sure if there's been a new setting added that I need to modify to correct this.

When I enter live tv, I see a normal picture. However, once I change the channel, the screen becomes pixelated on the left side and all garbled. Further analysis reveals that the screen appears as though it is moved to the right about 1/3 the way and the cut-off portion is wrapped around the left side of the screen, almost like the sync is off.  Once I exit out of live-tv and go back, the picture returns to normal, until I change the channel again. The sound still appears to be coming through ok. I've captured the log files from when I enter live tv and then change the channels so you can review and see if there's anything odd (see below). I did notice a WriteAudio: buffer underrun, but not sure how to correct this. If I keep playing the garbled screen long enough, this error just repeats....


mythBACKend.log

2008-08-18 10:06:22.638 MainServer::HandleAnnounce Playback
2008-08-18 10:06:22.693 adding: mythtv as a client (events: 0)
2008-08-18 10:06:22.720 TVRec(1): Changing from None to WatchingLiveTV
2008-08-18 10:06:22.758 TVRec(1): HW Tuner: 1->1
2008-08-18 10:06:22.937 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2008-08-18 10:06:24.076 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
VIDIOC_S_CTRL:V4L2_CID_AUDIO_MUTE: Invalid argument
2008-08-18 10:06:37.606 TVRec(1): HW Tuner: 1->1
2008-08-18 10:06:38.039 Finished recording MythBusters: channel 1044
2008-08-18 10:06:39.155 Finished recording MythBusters: channel 1044
2008-08-18 10:06:39.375 TVRec(1): RingBufferChanged()
2008-08-18 10:06:39.562 Finished recording MythBusters: channel 1044
2008-08-18 10:06:39.600 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-18 10:06:39.634 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-08-18 10:06:39.672 Empty LocalHostName.
2008-08-18 10:06:39.736 NVR(/dev/video0) Error: Resetting and re-queueing
2008-08-18 10:06:39.762 Using localhost value of mythtv
2008-08-18 10:06:39.881 New DB connection, total: 1
2008-08-18 10:06:39.915 Connected to database 'mythconverg' at host: localhost
2008-08-18 10:06:39.962 Closing DB connection named 'DBManager0'
2008-08-18 10:06:39.995 Connected to database 'mythconverg' at host: localhost
2008-08-18 10:06:40.063 New DB connection, total: 2
2008-08-18 10:06:40.092 Connected to database 'mythconverg' at host: localhost
2008-08-18 10:06:40.149 Current Schema Version: 1214
2008-08-18 10:06:40.305 Preview: Grabbed preview '/video/recordings/1044_20080818100622.nuv' 640x480@64s
2008-08-18 10:06:56.278 TVRec(1): Changing from WatchingLiveTV to None
2008-08-18 10:06:56.733 Finished recording Mega Movers "Moving an Airport": channel 1047
2008-08-18 10:08:59.511 Expiring 3 MBytes for 1044 @ Mon Aug 18 10:00:00 2008 => MythBusters
2008-08-18 10:08:59.561 Expiring 4 MBytes for 1047 @ Mon Aug 18 10:00:00 2008 => Mega Movers "Moving an Airport"


mythFRONTend.log

2008-08-18 10:06:22.637 TV: Attempting to change from None to WatchingLiveTV
2008-08-18 10:06:22.638 Using protocol version 40
2008-08-18 10:06:24.149 DPMS Deactivated
2008-08-18 10:06:24.530 Opening audio device 'default'. ch 2(2) sr 32000
2008-08-18 10:06:24.531 Opening ALSA audio device 'default'.
2008-08-18 10:06:24.591 Mixer unable to find control Master
2008-08-18 10:06:24.591 Mixer unable to find control Master
2008-08-18 10:06:24.630 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-18 10:06:24.676 OSD Theme Dimensions W: 640 H: 480
2008-08-18 10:06:25.028 Realtime priority would require SUID as root.
2008-08-18 10:06:25.029 TV: Changing from None to WatchingLiveTV
greedyhdeint: size changed from 0 x 0 -> 640 x 480
2008-08-18 10:06:25.142 Video timing method: USleep with busy wait
2008-08-18 10:06:38.375 NVP: prebuffering pause
2008-08-18 10:06:38.432 WriteAudio: buffer underrun
2008-08-18 10:06:39.649 New DB connection, total: 4
2008-08-18 10:06:39.650 Connected to database 'mythconverg' at host: localhost
2008-08-18 10:06:40.112 NVP: Prebuffer wait timed out 10 times.
2008-08-18 10:06:56.218 TV: Attempting to change from WatchingLiveTV to None
2008-08-18 10:06:56.909 TV: Changing from WatchingLiveTV to None
2008-08-18 10:06:56.971 DPMS Reactivated.


Please let me know if you would like to see additional info - I will be happy to share.

Thanks in advance!

---

### Post by sf_basilix on 2008-08-19
anyone have any thoughts?

---

### Post by sfalcon1 on 2008-08-24
My audio gets garbled when changing channels also.  Once the overlays disappear it returns to normal.  I do not get an error and cpu usage is not high during this event.

---

### Post by sfalcon1 on 2008-08-25
Change your playback profile.  I changed mine and now when the channel information is displayed it does not trash the audio. 

I would try different profiles first and not change the settings in the profiles unless you create a custom profile.

---

### Post by BJD1233 on 2008-08-29
I've got the same thing happening when I change channels too.  I don't have a solution, but I have some more information that may be useful to someone smarter then me.  When watching live and then changing channels I get the garbled video as a result.  However, for me it only seems to be a problem for HD channels.  SD seems to tune just fine.  Also, once the channel is garbled, if I open the program guide and then exit out, it tunes in fine.  Any ideas?

---

### Post by ikaukora on 2008-10-14
I'm getting the same, or very similar, problem using Mythdora (Fedora 8 along with MythTV-0.21).

See screenshot:
[http://www.mv.helsinki.fi/ikaukora/Screenshot.png](http://www.mv.helsinki.fi/ikaukora/Screenshot.png)

Usually this occurs when changing the channel. The probablity this happening seems to be higher when there is a recording on another channel at the same time or when switching to a different broadcast band. 

The problem is usually cured by going into the EPG. When this works, the EPG itself looks normal, but the small preview window of the current channel is scrambled. After exiting from the EPG the screen returns completely to normal. Other times it is necessary to quit out of LiveTV and start it again. 

As an additional oddity, sometimes this occurs during commercial breaks, so that a single commercial is garbled but after that it fixes itself automatically. 


Once an entire recording was scrambled in this way, so the problem is not entirely confined to LiveTV. 

I really don't know what the problem could be related to, so I don't know what specs to give. But I'll make an effort: 
Two DVB-C tv-cards ( Satelco EasyWatch PCI DVB-C ) (I've tried disabling simultanious recordings, but this didn't seem to make a difference) 
GA-MA69GM-S2H motherboard, using onboard video (AMD 690G) and audio. TV-output via S-video.


I'm using DVB-C SD broadcasts, so all my channels are digital. So perhaps this problem is related to digital broadcasts in general, not only HD channels?

Or maybe this is an entirely different problem with only superficial similarities to the ones you experienced? Have you had any luck with yours?

---

