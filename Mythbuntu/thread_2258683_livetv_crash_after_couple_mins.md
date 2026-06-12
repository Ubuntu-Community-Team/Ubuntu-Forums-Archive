---
title: "livetv crash after couple mins"
date: 2014-12-29
forum: Mythbuntu
---

### Post by rob112 on 2014-12-29
version 14.04.1 LTS

I am using a hauppauge HDpvr box and i am getting an error 

lirc_zilog:
i2c_master_send failed with -110
polling the IR receiver chip failed, trying reset

I get this failure when ever i watch live tv for more than a couple minutes and i occasionally get it when recording.  Normally the recording will start fine and then stop after a couple minutes.  
When this happens the red light will stay on the hdpvr indefinitly saying its recording.  I have to shut the hdpvr down and restart the system for it to work again.

dmesg show the above error 

I have had it working for a few months with no problems and now just recently this issue is showing up again.
What can I check?
I cant find anything that seems to fix this specific issue.

---

### Post by Kerby_Armand on 2015-01-25
I want to chime in on this. Similar event happening. LiveTV will stop after 2-3 minutes... like it's a buffer issue. First I thought it was while the raid was rebuilding... but it's not the case.
I have HDHOMERUN dual turner OTA setup.
Nvidia Graphics card HDMI - 1920x1080

Strange things: I have another box HDMI and it runs just fine - different hardware - same tuner.

Just chiming in to keep investigating.

---

### Post by Kerby_Armand on 2015-01-26
I am adding a note because I finally reinstalled and it all works fine - so far - knock on wood.

First: When installing the first time - I choose during the install Nvidia graphics - rather than the default open source graphics.
At the time I thought since I have a good nVidia graphics card - I should have the software for it.
This time I installed using the default open source.

Second what I did differently was to set symbol links up from the original recordings directory to my Raid storage. Those worked fine.
Originally after my install I opened up the Myth Background setup and changed the storage directories to my Raid - mounted at /Storage/etc...
I can't see why that would make a difference, but the sym links work fine and I have been watching liveTV un interrupted.

The only other thing I changed was a small minor network issue: I have two machines on network with MythTv - I added a switch so that my two HDHomeRun tuners are NOT on the same switch.
That did not make any difference - but I know the response of the system and the network traffic to each machine from the tuners is not conflicting on 1 switch. So I know that it may make a difference if there was heavy traffic watching and recording 3-4 shows at a time.

So far so good. I did add a custom script to mythicalLibrarian and tested it out right away - it now takes the regular mythtv recordings, moves them to my storage raid /Episodes /Shows /Movies directories and uses HandBrakeCLI to convert them to a smaller - yet great viewing size. That is in testing but my preliminary tests are doing well.

Just an update - I am going to call my dilemma solved because I choose the open source video during install. HDMI and audio was detected just fine and works to the Epson Projector and 7.1 Surround Receiver.

Cheers - I hope this helps.

---

