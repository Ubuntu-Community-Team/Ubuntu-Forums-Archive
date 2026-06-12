---
title: "mythcommflag errors in 12.04 and .26"
date: 2012-10-24
forum: Mythbuntu
---

### Post by dheianevans on 2012-10-24
Made the double move to 12.04 and .26 on the weekend, I've started getting random mythcommflag errors and seem to be the only one on the list getting them. Have you guys seen these audio decoding errors with either 12.04 or .26? Never had this issue before:

Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I ProgramInfoUpdater mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.145:6543 (try 1 of 1)
Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I ProgramInfoUpdater mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I CoreContext avformatdecoder.cpp:2141 (ScanStreams) AFD: Opened codec 0x1dcc820, id(MPEG2VIDEO) type(Video)
Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I CoreContext avformatdecoder.cpp:1999 (ScanStreams) AFD: codec AC3 has 6 channels
Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I CoreContext avformatdecoder.cpp:2141 (ScanStreams) AFD: Opened codec 0x1dcd180, id(AC3) type(Audio)
Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I CoreContext ClassicCommDetector.cpp:360 (go) Finding Logo
Oct 24 23:22:24 buster mythlogserver: mythcommflag[28601]: I Decoder avformatdecoder.cpp:4285 (ProcessAudioPacket) AFD: Audio stream changed
Oct 24 23:22:25 buster mythlogserver: mythcommflag[28601]: E Decoder avformatdecoder.cpp:4297 (ProcessAudioPacket) AFD: Unknown audio decoding error
Oct 24 23:22:35 buster mythlogserver: mythcommflag[28601]: E Decoder avformatdecoder.cpp:4297 (ProcessAudioPacket) AFD: Unknown audio decoding error

---

### Post by GaryP2 on 2012-11-14
dheianevans &#8211; how big of an issue has this been for you since a couple weeks have gone by using 12.04/.26? Is mythcommflag segfaulting or anything on those lines? Are there any indications when actually watching a flagged show that something is amiss? Or are these errors primarily log noise annoyance?
 
I&#8217;m doing my homework before the upgrade from 12.04/.25 to .26 to understand what I may be up against. Sorry that I can&#8217;t provide specific feedback to help.Thanks much.

---

### Post by dheianevans on 2012-11-14
it seems to have settled down a little bit. Have noticed that it will fail flagging more than it did under .25 but the number know is quite low.

---

### Post by GaryP2 on 2012-11-14
Thanks for the update. 
 
I don’t always update to the next version quite this soon after the release, but I’m not reading about many issues with .26 and in a couple weeks I’m going to have some time to focus on it. I appreciate your feedback.

---

### Post by Hidyman on 2012-11-23
I'm also having the same error after upgrading to .26.
If I re-queue the jobs they seem to work.
The worst part I have is the the system message pops up over the frontend and I have to go in and close it.  
Very annoying.

Update:  Now it seems that re-queue is not working.

Also, don't know if it makes a difference, but I'm using HDHomerun tuners.
Didn't have this problem until I switched to .25.

---

### Post by ertyu on 2012-11-27
Getting the same thing here, HDHomerun also. I'm guessing its based on discontinuities in the video data.

---

### Post by gtippitt on 2013-01-25
This problem is not limited to HDHomeRun tuners.  I'm getting the same errors with the 3 different tuners below.  I've given up on commercial detection for now and set both of my backends to NOT run commercial detection jobs so they will run stable.  

System 1
Master Backend with database and 2 tuners that do most of my recording
Frontend installed, but used only for debug and setup.
PCIe tuner - Hauppauge WinTV HVR-1850 - ATSC HDTV  
USB  tuner - KWORLD ATSC 315U

System 2
Frontend and slave backend
1 tuner used primarily for watching LiveTV or if needed for recording a 3rd show
USB tuner - Sasem OnAir

I'm recording local OTA ATSC station

I'm running Ubuntu 12.04 LTS with a fresh install of MythTV 0.26 from PPA

Other than this error my systems are both really stable and 26 is looking good.

---

### Post by Ubu_Fester on 2013-04-07
I am having similar issues, but I have a different setup (Ubuntu 12.04 LTS and .25+fixes) and different tuners (Hauppauge 1600/single tuner and 2250/dual ).  The errors do not happen on every commflag process -- fairly random but does happen 3-4 times per week.  I am recording Over the Air (OTA) shows and am using analog audio drivers/connections.

My thoughts now include:    
1) possible audio issue, but I don't know where to start,    
2) commflag issue for High Def or long programs (sports or movies).  My recent test included recording and commflagging about a half dozen short TV shows.  All shows recorded find and no errors.  

My recent logs can be found at...
**[SIZE=2]See Thread: [MythTV backend setup has closed unexpectedly]("http://ubuntuforums.org/showthread.php?t=2133073")    [/SIZE]**[http://ubuntuforums.org/showthread.php?t=2133073](http://ubuntuforums.org/showthread.php?t=2133073)

---

