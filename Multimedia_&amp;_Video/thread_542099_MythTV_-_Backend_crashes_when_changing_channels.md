---
title: "MythTV - Backend crashes when changing channels"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by Chaos5lw on 2007-09-03
I've spent the day trying to get my MCPC up and running and after wasting 12 hours with LinuxMCE I decided to scrap it and just install Xubuntu and MythTV.

What is working:
- TV Tuner (Hauppauge WinTV Express -756) has video and can be tuned to channels.
- TV listings are supposedly being fetched (although they never show up when watching TV)

What isn't working:
- No sound from the TV Tuner. (I tried [this](http://www.mythtv.org/wiki/index.php/Snd-bt87x) with no luck)

However, my main problem is that if I try and change the channel I'm watching on the TV tuner, the TV viewer will either close, or, the backend itself will crash with the following message:
> Segmentation fault (core dumped)
I don't have a clue why it should be doing that, hence why I'm here.

I also have a WindowsMCE remote that I need to get working with LIRC.

So in summary, I need some help with:
1) The MythTV backend crashing.
2) The lack of sound from my TV Tuner.
3) Setting up a WindowsMCE remote with LIRC.

Thanks.


Here's some info that may be helpful:
> 2007-09-03 19:01:13.050 MainServer::HandleAnnounce Monitor
2007-09-03 19:01:13.051 adding: bane as a client (events: 0)
2007-09-03 19:01:13.051 MainServer::HandleAnnounce Monitor
2007-09-03 19:01:13.051 adding: bane as a client (events: 1)
2007-09-03 19:01:13.059 MainServer::HandleAnnounce Playback
2007-09-03 19:01:13.059 adding: bane as a client (events: 0)
2007-09-03 19:01:13.061 TVRec(2): Changing from None to WatchingLiveTV
2007-09-03 19:01:13.065 TVRec(2): HW Tuner: 2->2
2007-09-03 19:01:13.174 Unknown video codec
2007-09-03 19:01:13.174 Please go into the TV Settings, Recording Profiles and
2007-09-03 19:01:13.174 setup the four 'Software Encoders' profiles.
2007-09-03 19:01:13.174 Assuming RTjpeg for now.
2007-09-03 19:01:13.174 NVR: Error, unknown audio codec
2007-09-03 19:01:23.202 NVR: Only read -1 bytes of 4096 bytes from '/dev/dsp1
read audio: Input/output error
2007-09-03 19:01:23.220 Finished recording Unknown: channel 1068
2007-09-03 19:01:23.304 Finished recording Unknown: channel 1068
2007-09-03 19:01:23.601 TVRec(2): RingBufferChanged()
2007-09-03 19:01:23.619 Finished recording Unknown: channel 1068
2007-09-03 19:01:33.746 NVR: Only read -1 bytes of 4096 bytes from '/dev/dsp1
read audio: Input/output error
2007-09-03 19:01:43.746 NVR: Only read -1 bytes of 4096 bytes from '/dev/dsp1
read audio: Input/output error
2007-09-03 19:01:43.775 Finished recording Unknown: channel 1072
2007-09-03 19:01:43.887 Finished recording Unknown: channel 1072
2007-09-03 19:01:44.073 TVRec(2): RingBufferChanged()
2007-09-03 19:01:44.092 Finished recording Unknown: channel 1072
2007-09-03 19:01:44.164 TVRec(2): Changing from WatchingLiveTV to None
2007-09-03 19:01:54.270 NVR: Only read -1 bytes of 4096 bytes from '/dev/dsp1
read audio: Input/output error

---

### Post by Scorpuk on 2007-09-04
Not sure of this is right or not, but I dont think analogue TV signal has EIT and your TV card is analogue.

As to why your backend is crashing, it might be down to not having the correct drivers for your card. Maybe its not supported?

If you live in an area with digital TV I would highly recommend switching to a DVB-T card. My backend server has 2 x Hauppauge Nova-T 500's, giving me 4 digital tuners. :)


Anywho on to your last item: Windows MCE remote

[http://www.mythtv.org/wiki/index.php/MCE_Remote#Newer_remote](http://www.mythtv.org/wiki/index.php/MCE_Remote#Newer_remote)
and here
[http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install](http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install)    <-- Ubuntu specific

---

