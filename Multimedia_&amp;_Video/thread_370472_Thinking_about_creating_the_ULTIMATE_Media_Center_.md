---
title: "Thinking about creating the ULTIMATE Media Center lol"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by dfreer on 2007-02-25
Sorry in advance, this is going to be a long post. Thanks to anyone who cares to comment/give me some advice :D

So I've got some money to spend, and I'm looking to build a Media Center/File Sharing server. I'm having a bit of trouble deciding which MoBo to buy, and also I'm just not sure that Linux will be able to do everything I want it to do. Also, I have a home web-server, and I would like to be able to enjoy my videos/music (located on the media center) from the internet (streaming everything, and secure). Here's my expectations for this server:

Note: I have never done a mythtv or RAID before, this is going to be a great learning experience!

Hardware expectations:
 - RAID 5 with SATA
 - Socket 775
 - Output to TV with standard Coaxial Cable
 - IR Remote control to control MythTV 
 - DVD-RW DL
 - 5.1 Surround Sound with output to 1/8" (3.5 mm) jacks and/or RCA jacks
     --> Be able to upmix 2.0 Stereo to my surround sound
     --> Be able to *actually* play DVD's in Surround Sound

MythTV Expectations:
Note - I want to be able to do the following without a keyboard/mouse; just with my remote control.
 - Be able to schedule and record Cable TV. Be able to watch live TV at the same time.
 - Be able to watch DVD in surround sound.
 - Rip DVDs to .avi
 - Copy DVDs to Dual-Layer DVD
 - Copy DVDs and shrink it to 4.7 GB DVD (single-layer)
 - After I plug in some USB controllers, be able to play SNES, NES, PSX games
 - Watch ANY Video format (is there any formats that Linux CANNOT play?)
 - Play MP3's with dynamic playlists, random.
 - Be able to create video/music playlists.
 - Watch video playlist randomly
 - Be able to actually fast-forward/rewind video files (either by seeking +10 secs for example, or by actually controlling the playback speed)

From my web site, I would like to be able to play a video file and watch it on an intergrated web player (like google or youtube). 
 
My questions:
(1). Does anyone see anything wrong with this setup? anything that simply won't work or could work better?
(2). As I understand it, I can add additional hard drives to RAID 5 without having to rebuild my array. Problem is, most MoBo's (at least the cheap desktop one's I can afford) will only have 4 SATA channels. Will I be able to throw in a SATA controller card and still use the Mother Board's onboard RAID?
(3). From what I understand, MythTV can use SNES9X... but I would like to use ZSNES (probably the best SNES emulator around), and ePSXe. Can I ssh to my server, drop out of MythTV, and though the command line launch ZSNES etc? Will it still output to the TV?

---

### Post by coxc24 on 2007-02-26
I can answer some of your questions, or at least try to!

I have just completed a new media centre and have been very pleased with the results. The hardware setup I used is as follows:

Intel Pentium 4 650 3.4Ghz Socket 775 800mhz 2mb Cache
Seagate 7200.10 320GB SATAII/300 8.5ms 7200RPM 16MB Cache
Asus Nvidia 7300GS 256MB PCI-E 111197
Casecom KL-787 Black Midi-Tower Case - With 350W PSU
Ebuyer 1GB DDR2 533MHz PC2-4200 240pin Extra Value Ram
Logitech Cordless Desktop EX 110 - USB/PS2
NEC AD-5170A-0B 18xDVD±RW DL Black - Bare Drive
MSI 945P Neo3-F i945P Socket 775 SATA 8-channel audio ATX
Maxter 40GB 5200RPM IDE

The above does not contain info on my TV cards because I am in the UK and what you buy will depend greatly on where you are and what you want. I have used the 40GB drive for the SWAP and root partitions. The 320GB is split 250GB for recordings in MYthTV and 70GB for my /home mount. I am using Kubuntu 6.10 with MythTV because I prefer KDE and it's apps, but that's just me.

1 - I can't see a reason for the setup not working, but you might find your TV out is composite or SVideo.

2 - I have not used SATA RAID and have only played around with software RAID 0 and 1 with IDE devices. If you use a RAID array/controller then there would be no need to use the SATA ports on your motherboard. They will only support a software RAID which is pretty pointless anyway (feel free to correct me if I am wrong).

3 - I have no knowledge of anything in this area, sorry.

MythTV will allow you to play DVDs and MPEG4 through it's front end providing you have the plugins and DVD play back packages installed. You can also play music through it. As for full surround sound when watching a DVD; I only have 2 speakers so can't really comment. I can't see a reason for it not working if you have a full 5.1 or 7.1 set of speakers. I have read about up mixing stereo to surround but you will probably need additional hardware to do it.

K9Copy will handle the shrinking of DVDs for backup purposes e.g. 8GB dual layer to 4.7GB single layer. It will also convert a DVD to MPEG4. This is a KDE app so would be available to Kubuntu and not Ubuntu. You may be able to use it in Ubuntu but someone who has done it may be better help than me. Most video files will play, I think there may be issues with some of the Microsoft and Apple stuff though. That will be worth checking out first.

MythTV will allow you to pause, fast forward and rewind both live TV and recordings.

If you have any questions then let me know, I hope this is of some use.


For further info on MythTV on Ubuntu have a read of the wiki pages, they can be adapted to use Kubuntu if you wish:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by dfreer on 2007-02-26
Thanks for the reply.

It looks like I might have to buy an Video Tuner Card (to accept digital, analog, and HDTV broadcasts) and standard Video Output Card (with composite/S-Video out. I cannot find anywhere a card that can output to Coaxial Cable, wonder why...?).

According to the [MythTV Official Plugins]("http://www.mythtv.org/wiki/index.php/Category:Plugins"), MythTV supports ZSNES, FCE-Ultra, and ePSXe which makes me quite happy, quite happy indeed. It also will play video files, even using Xine if MythTV's internal player can't handle the codec. I Saw in the Unofficlal Plugin List that it can play network streams too, so maybe I will get everything I want to work.

In fact, just looking under MythTV's Official Plugins I see that most of the things I want to do and more. I'm literally blown away by how awesome MythTV appears to be. I can't wait to get started building my system.

---

### Post by coxc24 on 2007-02-26
Good luck!

---

