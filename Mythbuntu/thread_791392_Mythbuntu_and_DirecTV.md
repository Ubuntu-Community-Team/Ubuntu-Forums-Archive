---
title: "Mythbuntu and DirecTV"
date: 2008-05-12
forum: Mythbuntu
---

### Post by wolfster101 on 2008-05-12
I have just installed Mythbuntu 8.04 on a machine with a Hauppauge PVR-350.  I have DirecTV and can not for the life of me get any kind of TV signal to come into the Myth box.  

What I want to do is transfer all the recorded shows on my DVR to Mythbuntu due to the limited storage space on the DVR (80gig).

I understand I will only be able to actually see the channel the DVR is set to but how do I set Mythbuntu to see it?

My DirecTV cable enters (dual) into the DVR then I have it going out through the S-video port into the Hauppague.  From the Hauppague it then goes out via component to the TV.

Can anyone help?

Thanks!

---

### Post by volkswagner on 2008-05-12
Did you set up all steps on backend?  Do you have schedules direct set up?
What are you using for channel changer?


[http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat]("http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat")
[http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial]("http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial")

---

### Post by wolfster101 on 2008-05-12
> **volkswagner said:**
> Did you set up all steps on backend?  Do you have schedules direct set up?
What are you using for channel changer?


[http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat]("http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat")
[http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial]("http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial")

I did go through all the steps for the backend, not 100% sure if I did them all correct or not.  I also have Schedules Direct which seems to be working as it lists my channels starting with channel 4.  When I click watch TV the screen goes black for a bit then comes right back to the menu options.

I am not trying to change any channels at this point, I simply want to be able to view what my STB is pushing to the video capture card first, I will tackle changing channels and remote control configuration later.

---

### Post by wolfster101 on 2008-05-12
Maybe this can help someone who understands what this means....

Mythfrontend.log
> 2008-05-12 14:15:35.181 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-12 14:15:35.184 Using protocol version 40
2008-05-12 14:15:35.215 TV: Attempting to change from None to WatchingLiveTV
2008-05-12 14:15:35.217 Using protocol version 40
2008-05-12 14:15:40.504 DPMS Deactivated
2008-05-12 14:15:40.769 Opening audio device 'default'. ch 2(2) sr 44100
2008-05-12 14:15:40.770 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-05-12 14:15:40.832 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-05-12 14:15:40.836 NVP: Enabling Audio
2008-05-12 14:15:41.026 IVD: ivtv version 1.1.0
2008-05-12 14:15:41.027 IVD Error: Failed to locate framebuffer
                        Did you load the ivtv-fb Linux kernel module?
2008-05-12 14:15:41.028 VideoOutput, Error: Not compiled with any useable video output method.
2008-05-12 14:15:41.028 Unable to initialize video.
2008-05-12 14:15:51.264 WriteAudio: buffer underrun
2008-05-12 14:15:55.338 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-05-12 14:15:55.663 TV Error: LiveTV not successfully started
2008-05-12 14:15:55.747 DPMS Reactivated.


Mythbackend.log
> 2008-05-12 14:15:35.220 adding: mythbuntu as a client (events: 0)
2008-05-12 14:15:35.293 TVRec(1): Changing from None to WatchingLiveTV
2008-05-12 14:15:35.345 TVRec(1): HW Tuner: 1->1
2008-05-12 14:15:36.592 Channel(/dev/video0) Warning: You have not set an external channel changing
                        script for a composite or s-video input. Channel changing will do nothing.
2008-05-12 14:15:38.099 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-05-12 14:15:38.102 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
2008-05-12 14:15:55.380 TVRec(1): Changing from WatchingLiveTV to None
2008-05-12 14:15:55.636 Finished recording Unknown: channel 1004
2008-05-12 14:18:37.871 Expiring 9 MBytes for 1004 @ Mon May 12 14:15:36 2008 => Unknown

---

### Post by volkswagner on 2008-05-12
Sorry I can't offer advice on sound config.  I am not running 8.04.  I would start with getting sound working with mythmusic.  Use successful mythmusic settings for mythtv.  I thought the default sound was to use pulse audio in 8.04 not alsa.

If you get sound working, you may want to try different tv playback settings.

---

### Post by Salla101 on 2008-05-12
> **volkswagner said:**
> Sorry I can't offer advice on sound config.  I am not running 8.04.  I would start with getting sound working with mythmusic.  Use successful mythmusic settings for mythtv.  I thought the default sound was to use pulse audio in 8.04 not alsa.

If you get sound working, you may want to try different tv playback settings.

I am unable to log back in with my previous account Wolfster101 for some reason.  It failed the 5 attempts and told me to wait 15 minutes however 60 minutes later it is still telling me to wait 15.

Anyway, I am not concerned about the sound settings as you mentioned.  I just want a simple display on my screen.  Is this really that difficult?  I am in no way a linux guru, master or even wrangler, I am however somewhat familiar with Linux and have been using Ubuntu for almost 2 years now.  For the life of me I cannot get this Mythbuntu to do anything more then play music off my *other* linux box.  I am (this close) to trying Mythknop or Mythdora or something.  I really wanted to stay with Mythbuntu as I am familiar with the OS but if its this difficult to set up I am at a loss.

Can someone please guide me to maybe a step by step with the Hauppauge PVR-350 and DirecTV or something?  I am absolutely clueless here.

---

### Post by volkswagner on 2008-05-12
I just suggested starting with sound, since it can halt playback.

---

### Post by fenian on 2008-05-12
When you setup Mythtv with a satellite or cabel box/dvr you use the tuner in the satellite/cable box and control it (change channels) with an [IR Blaster]("http://www.mythtv.org/wiki/index.php/Using_an_IR_Blaster_with_MythTV") or In some cases a [serial]("http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial") or [firewire ]("http://www.mythtv.org/wiki/index.php/FireWire")connection.Even if you don't have one of these you can still get it to display the currnet channel selected on the satellite box however any program info will  be unavailable or incorrect in mythtv.To set it up to just get the signal do this...

Open Mythtv backend setup (System>Administration>MythTV Backend Setup).

Go to the Input Connections section.

On the first page choose the S-Video option ( [MPEG : /dev/video0 ] (S-Video ...)

On the next screen in "preset tuner to channel" section set this to 3.

---

### Post by Salla101 on 2008-05-13
> **fenian said:**
> When you setup Mythtv with a satellite or cabel box/dvr you use the tuner in the satellite/cable box and control it (change channels) with an [IR Blaster]("http://www.mythtv.org/wiki/index.php/Using_an_IR_Blaster_with_MythTV") or In some cases a [serial]("http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial") or [firewire ]("http://www.mythtv.org/wiki/index.php/FireWire")connection.Even if you don't have one of these you can still get it to display the currnet channel selected on the satellite box however any program info will  be unavailable or incorrect in mythtv.To set it up to just get the signal do this...

Open Mythtv backend setup (System>Administration>MythTV Backend Setup).

Go to the Input Connections section.

On the first page choose the S-Video option ( [MPEG : /dev/video0 ] (S-Video ...)

On the next screen in "preset tuner to channel" section set this to 3.

I have followed these steps and when I select WATCH TV I get the same thing, a black screen for a moment then it goes right back to the menu.

My sound works fine, I know the log file said it had some issue but I think that was with the sound on the Hauppage card, the sound on the motherboard plays the music in Mythbuntu without issue.

Is there some where we can begin at the begining to start troubleshooting this?  Is there some config files I can look through, what about different log files?  Should I start with the backend first or the frontend?  I am really clueless here about what the problem is and where to start to begin to fix it.

Thanks for your suggestions!

---

### Post by volkswagner on 2008-05-13
> **wolfster101 said:**
> I have just installed Mythbuntu 8.04 on a machine with a Hauppauge PVR-350.  I have DirecTV and can not for the life of me get any kind of TV signal to come into the Myth box.  

What I want to do is transfer all the recorded shows on my DVR to Mythbuntu due to the limited storage space on the DVR (80gig).

I understand I will only be able to actually see the channel the DVR is set to but how do I set Mythbuntu to see it?

My DirecTV cable enters (dual) into the DVR then I have it going out through the S-video port into the Hauppague.  From the Hauppague it then goes out via component to the TV.

Can anyone help?

Thanks!

Well I guess I overlooked some info here.  First just to correct your terminology the yellow port for tv out is called composite.  :)

You don't have a video card with tv out?  You will need to search these forums to get the tvout working on pvr350.  You should have the check box selected for use pvr350 out.  You should also be using the ivtv selected for playback.

So the crux of the matter is to get tvout on pvr350.  Concentrate there.

Search results for pvr350 tv out:
[http://ubuntuforums.org/showthread.php?t=568074&highlight=pvr350+tv]("http://ubuntuforums.org/showthread.php?t=568074&highlight=pvr350+tv")

---

### Post by Salla101 on 2008-05-13
> **volkswagner said:**
> Well I guess I overlooked some info here.  First just to correct your terminology the yellow port for tv out is called composite.  :)

You don't have a video card with tv out?  You will need to search these forums to get the tvout working on pvr350.  You should have the check box selected for use pvr350 out.  You should also be using the ivtv selected for playback.

So the crux of the matter is to get tvout on pvr350.  Concentrate there.

Search results for pvr350 tv out:
[http://ubuntuforums.org/showthread.php?t=568074&highlight=pvr350+tv]("http://ubuntuforums.org/showthread.php?t=568074&highlight=pvr350+tv")

What I have for actual display is a monitor cable connected to the Nvidia video card to the TV.  Yes, the TV has a 15 pin video connection so the TV is in reality my monitor.  If this is the case do I still need to select PVR-350 and ivtv for playback?  

I have the S-video (round with about 4 pins) coming from the DirecTV box into the Hauppauge S-video port.

---

### Post by volkswagner on 2008-05-13
No, do not select tv out for pvr350.  You also wont want that as your decoder either. What is the composite out doing then?

You should try different playback settings then.  Depending if your video card is opengl try with and without it selected.  Try the different pre-configured modes (normal, cpu--, cpu+, etc).  You can also edit them for deinterlacing and renderer, etc.

---

### Post by Salla101 on 2008-05-13
> **volkswagner said:**
> No, do not select tv out for pvr350.  You also wont want that as your decoder either. What is the composite out doing then?

You should try different playback settings then.  Depending if your video card is opengl try with and without it selected.  Try the different pre-configured modes (normal, cpu--, cpu+, etc).  You can also edit them for deinterlacing and renderer, etc.

Where do I find the different playback settings again?  
Is there somewhere to define which card it should display on?  I am wondering if I can even watch TV on a monitor without a TV involved at all.

---

### Post by Salla101 on 2008-05-13
I feel as though I might be getting closer however it might just be wishful thinking!  :lolflag:

Anyway, from CLI I type  cat /dev/video0 > /tmp/text_capture.mpg and then I can view it by opening mplayer however....if I try and view it from CLI with the command mplayer /tmp/text_capture.mpg I get some errors.

> mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /tmp/text_capture.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
vo: couldn't open the X11 display ()!
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Cannot sync MAD frame3 (07.2)  5.0% 
Cannot sync MAD frame
Cannot sync MAD frame3 (07.2)  5.0% 
A:   7.7 (07.7) of 7.3 (07.2)  5.0% 

Exiting... (End of file)

---

### Post by Salla101 on 2008-05-13
OK, when I run mplayer from command line with a driver I get results!

mplayer -vo svga /tmp/text_capture.mpg

So the question is...How do I tell Mythbuntu to use svga (nvidia) for playback?

---

### Post by Salla101 on 2008-05-13
Here is something interesting...

I installed libsdl1.2debian-all did something else (go figure) and rebooted and now I get display as I should!

I figure something in mplayer was not right from install and this caused my problems.

---

