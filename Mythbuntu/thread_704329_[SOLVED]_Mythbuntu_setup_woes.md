---
title: "[SOLVED] Mythbuntu setup woes"
date: 2008-02-22
forum: Mythbuntu
---

### Post by MishaK on 2008-02-22
Hi all,

I've been working on this for a couple days now and the frustration factor is starting to get pretty high. I'm setting up a new HTPC with a pcHDTV HD-5500 card. I've got basic Comcast cable, though they also broadcast the local network channels in HD, which I'd like to get set up as well. 

Myth installed without a hitch and everything seems to function properly, except for the TV tuning which is a pretty big issue. I'm just working on getting the normal channels set up at first, not even worrying about the HD channels. 

I've followed the instructions here:
[http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500)

mythtv-setup scans the channels and finds all of the channels. I run mythfilldatabase, and it downloads the schedules properly from SchedulesDirect. When I go into mythfrontend however, I can't tune any of the channels.

Here's the backend log when I try and tune:
```

2008-02-22 09:24:19.992 Using runtime prefix = /usr
2008-02-22 09:24:20.041 New DB connection, total: 1
2008-02-22 09:24:20.050 Connected to database 'mythconverg' at host: localhost
2008-02-22 09:24:20.055 Current Schema Version: 1160
Starting up as the master server.
2008-02-22 09:24:20.073 New DB connection, total: 2
2008-02-22 09:24:20.077 Connected to database 'mythconverg' at host: localhost
2008-02-22 09:24:20.081 EITHelper: localtime offset -5:00:00 
2008-02-22 09:24:20.091 TVRec(1) Error: Start channel invalid, setting to '10' on input Television instead.
2008-02-22 09:24:20.096 New DB connection, total: 3
2008-02-22 09:24:20.109 Connected to database 'mythconverg' at host: localhost
2008-02-22 09:24:20.140 TVRec(1) Error: Setting start channel '10' failed, 
                        and backup '3' failed as well.
2008-02-22 09:24:20.170 New DB scheduler connection
2008-02-22 09:24:20.171 Connected to database 'mythconverg' at host: localhost
2008-02-22 09:24:21.213 Main::Registering HttpStatus Extension
2008-02-22 09:24:21.215 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-22 09:24:21.215 Enabled verbose msgs:  important general
2008-02-22 09:24:21.216 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-02-22 09:24:21.217 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-02-22 09:24:22.185 Reschedule requested for id -1.
2008-02-22 09:24:22.228 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-02-22 09:24:22.234 Seem to be woken up by USER
2008-02-22 09:27:26.209 MainServer::HandleAnnounce Monitor
2008-02-22 09:27:27.707 adding: spike as a client (events: 0)
2008-02-22 09:27:27.708 MainServer::HandleAnnounce Monitor
2008-02-22 09:27:27.709 adding: spike as a client (events: 1)
2008-02-22 09:27:27.722 Reschedule requested for id -1.
2008-02-22 09:27:27.831 Scheduled 0 items in 0.1 = 0.09 match + 0.02 place
2008-02-22 09:27:53.151 MainServer::HandleAnnounce Monitor
2008-02-22 09:27:53.155 adding: spike as a client (events: 0)
2008-02-22 09:27:53.155 MainServer::HandleAnnounce Monitor
2008-02-22 09:27:53.156 adding: spike as a client (events: 1)
2008-02-22 09:27:53.163 MainServer::HandleAnnounce Playback
2008-02-22 09:27:53.171 adding: spike as a client (events: 0)
2008-02-22 09:27:53.172 TVRec(1): Changing from None to WatchingLiveTV
2008-02-22 09:27:53.175 TVRec(1) Error: Start channel invalid, setting to '10' on input Television instead.
2008-02-22 09:27:53.176 TVRec(1): HW Tuner: 2->0
2008-02-22 09:27:53.184 TVRec(1) Error: Failed to set channel to 10.
2008-02-22 09:27:53.236 TVRec(1) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Feb 22 09:27:53 2008) endts(Fri Feb 22 09:27:53 2008)
             recstartts(Fri Feb 22 09:27:53 2008) recendts(Fri Feb 22 09:27:53 2008)
             title()
2008-02-22 09:28:35.593 TVRec(1): PauseRecorder() called with no recorder
2008-02-22 09:28:35.611 DVBChan(0) Error: Unable to find channel in database.
2008-02-22 09:28:35.619 DVBChan(0) Error: SetChannelByString(30): Failed to initialize channel options
2008-02-22 09:28:35.619 TVRec(1) Error: Failed to set channel to 30.
2008-02-22 09:28:35.625 TVRec(1) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Feb 22 09:28:35 2008) endts(Fri Feb 22 09:28:35 2008)
             recstartts(Fri Feb 22 09:28:35 2008) recendts(Fri Feb 22 09:28:35 2008)
             title()
2008-02-22 09:28:35.674 Finished recording : channel 4294967295
2008-02-22 09:28:35.690 Preview Error: Previewer file '/home/mythtv/recordings/4294967295_20080222092753.mpg' is not valid.
2008-02-22 09:28:48.009 TVRec(1): PauseRecorder() called with no recorder
2008-02-22 09:28:48.040 DVBChan(0) Error: Unable to find channel in database.
2008-02-22 09:28:48.045 DVBChan(0) Error: SetChannelByString(53): Failed to initialize channel options
2008-02-22 09:28:48.046 TVRec(1) Error: Failed to set channel to 53.
2008-02-22 09:28:48.049 TVRec(1) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Feb 22 09:28:48 2008) endts(Fri Feb 22 09:28:48 2008)
             recstartts(Fri Feb 22 09:28:48 2008) recendts(Fri Feb 22 09:28:48 2008)
             title()
2008-02-22 09:28:48.099 Finished recording : channel 4294967295
2008-02-22 09:28:48.111 Preview Error: Previewer file '/home/mythtv/recordings/4294967295_20080222092835.mpg' is not valid.
2008-02-22 09:30:40.599 Expiring  from Fri Feb 22 09:28:35 2008, 0 MBytes, forced expire (LiveTV recording)
2008-02-22 09:34:10.650 TVRec(1): Changing from WatchingLiveTV to None
2008-02-22 09:34:10.708 Finished recording : channel 4294967295

```

I've also tried rebuilding the v4l_dvb drivers myself and run into the same problem. 

Any ideas or direction would be GREATLY appreciated!
Thanks,
--Misha

---

### Post by newlinux on 2008-02-22
So right now you are trying to tune analog stations with your pchdtv 5500 and not any QAM stations? How did you setup the card in mythtv-setup (what driver, are you using analog options, scan settings, etc)? More info might help us pinpoint the problem. You should definitely be using the drivers in the kernel and this card should work out of the box - with just configuration in mythtv-setup...

---

### Post by MishaK on 2008-02-22
Thanks for the quick reply -- that was my understanding as well, but it doesn't seem to be working that way. :)

My understanding is that the normal channels are ATSC and the digital channels are QAM-256, though frankly I could be wrong on that. As I mentioned I'm only REALLY worried about the ATSC channels for now, though I'd like both eventually. 

I set up the card using the DVB DTV capture card drive in myth-setup. DVB Card #0 as this is my only tuner. Under analog settings, the card is pointing at /dev/video0. I changed the audio sampling rate to 48KHz, though I imagine the issue really doesn't have to do with that, and marked the "Open DVB card on demand" box under the recording options. 

I set up a video source with ScheduleDirect and connect it to the v4l Television input. A full scan on the v4l tuner finds all the channels I should be able to receive, but as I mentioned, mythfrontend can't obtain a lock on them. 

I'll note that I CAN watch analog tv with TVTime. 

Thanks again -- let me know if you need any more information.

---

### Post by newlinux on 2008-02-22
> **MishaK said:**
> Thanks for the quick reply -- that was my understanding as well, but it doesn't seem to be working that way. :)

My understanding is that the normal channels are ATSC and the digital channels are QAM-256, though frankly I could be wrong on that. As I mentioned I'm only REALLY worried about the ATSC channels for now, though I'd like both eventually. 

I set up the card using the DVB DTV capture card drive in myth-setup. DVB Card #0 as this is my only tuner. Under analog settings, the card is pointing at /dev/video0. I changed the audio sampling rate to 48KHz, though I imagine the issue really doesn't have to do with that, and marked the "Open DVB card on demand" box under the recording options. 

I set up a video source with ScheduleDirect and connect it to the v4l Television input. A full scan on the v4l tuner finds all the channels I should be able to receive, but as I mentioned, mythfrontend can't obtain a lock on them. 

I'll note that I CAN watch analog tv with TVTime. 

Thanks again -- let me know if you need any more information.

Okay, that adds some clarity.  If you are scanning the V4L analog tuner you won't get ATSC channels, you'll get NTSC channels. ATSC are digital over the air channels (8vsb). So which one are you trying to get right now? I'm going to guess that you have a cable connection to your card right now since you mentioned Comcast, not an antenna, so you are trying to tune NTSC channels (your basic 1-99 on cable). So a few questions:

1. Do you have any input source associated with the digital side of your card?

2. Does your program guide information look correct (have the right channels)?

From what you wrote, it looks like you did all the right things in mythtv-setup.

One thing to try is to delete all of your channels, and instead of scanning them in, simply download them from schedules direct (fetch channels from source or something like that), and then try tuning a station....

---

### Post by newlinux on 2008-02-22
oh, and what do you get on screen when you try to tune a station? Does it just go back to the mythtv main menu?

---

### Post by MishaK on 2008-02-22
Okay, 

First off -- You are correct, I am hooked up to a cable line, trying to tune the analog cable signals, so I guess NTSC. Under the general settings, should I have the format as NTSC then? Tried it both ways and it does not affect the issue.

I do not have an input associated with the DVB portion of the card at this point.

When I delete the channels and use the "Fetch listings from channel source" button, nothing happens. The button seems to "think" for a second, then just nothing. The button does not work after a scan, either -- 

The only way I can get the channels in is to do a scan, then run 
```
mythfilldatabase --do-channel-update
```
after which all of the channel names show up properly. The guide looks correct with all of the correct programming information.

When I try to tune a station, I get the onscreen display showing ```
Signal 90% | S/N 3.8dB | BE 0 | (1__) No Loc
```
and a black screen.

---

### Post by Calash on 2008-02-22
The only notification I ever get with that button is that my default channel changes to a number instead of blank.  You may want to remove your current channels, just press that button, then go to the channel editor and see if it populated anything.

That is...if you have not tried that already :)

---

### Post by MishaK on 2008-02-22
I have indeed tried that, and no dice. After clicking it (even multiple times), the channel editor is empty. It does pause for a moment when I click it, which is odd.

---

### Post by MishaK on 2008-02-25
Bump -- any other ideas for me to try? Could this be a hardware issue with the card? Thanks for any reply,

--Misha

---

### Post by newlinux on 2008-02-25
> **MishaK said:**
> I have indeed tried that, and no dice. After clicking it (even multiple times), the channel editor is empty. It does pause for a moment when I click it, which is odd.

I doubt it is the card... since it works with tvtime. When you click on fetch channels from listing, what does mythtv-setup output in terminal (run it from terminal first). I'm grasping at straws here... Maybe try tuning QAM 256 and seeing if that works on digital input. Just to see if that works...

The only thing I can think of is if you are using the V4L "childcard" of this card you have to have something tied to the parent card as well. I don't know this, but at this point I'm guessing... OR you could just set your card up as a V4L card in the beginning (not a dvb card using the analog options) and see if that works...

---

### Post by MishaK on 2008-02-26
First of all, thank you SO much for your help. If you're grasping at straws, you can imagine how I must be feeling. :)

Success! (almost)

I set up the digital tuner, did a channel scan, edited the channel info so that the channel numbers matched SchedulesDirect, and got the digital channels working perfectly. 

Next I created a new input source for the analog channels, scanned, grabbed the channel data (though I still had to do this through mythdatabasefill to get the information in the DB), and I can now tune my analog channels as well. The only remaining hurdle is that the analog channels don't have any sound, but this at least gives me some more to work with. 

Thanks again,
--Misha

---

### Post by MishaK on 2008-02-26
Scratch that -- just had to change the sound device from /dev/dsp to /dev/dsp1, and everything is working! Thanks again,

--Misha

---

### Post by CeeDub on 2008-02-28
I'm having the exact same problem as you, but I don't understand how you went about fixing it.  I feel like I've tried everything.  Could you be a little more specific for me.  Maybe you can help me out.

When I first installed mythbuntu, it wouldn't let me choose DVB DTV capture card (v3.x) .  I had to wait until I booted into the newly installed operating system until it would let me choose it.  Once I did choose it, it can scan all the channels, but when I go to watch it, it doesn't get a lock on anything.  What could be wrong?

---

### Post by Bigm8 on 2008-11-02
yea, same problem solved. delete video sources. add them back but do not set the "Preset tuner to channel" for any input that you are using with an external tuner.

---

