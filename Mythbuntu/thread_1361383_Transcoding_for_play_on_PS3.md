---
title: "Transcoding for play on PS3"
date: 2009-12-21
forum: Mythbuntu
---

### Post by Brilock on 2009-12-21
I'm using an HVR-1600 tuner and followed webguy's MediaTomb tutorial here: [http://ubuntuforums.org/showthread.php?t=1061203](http://ubuntuforums.org/showthread.php?t=1061203)

I'm at the point where I have mediatomb on the machine, and the folders I've tagged show up on the PS3 but the videos do not.  My suspicion is that I need to transcode them into a different format, but can anyone verify that this would cause the problem?  When I go into 
Recording Profils > Transcoders, I have default options for Autodetect from RTjpeg/MPEG4 and Autodetect from MPEG2.  The options under them appear to be identical though...

Now that I'm this close I feel I'm missing something obvious!  Any tips out there?

---

### Post by bubonic1347 on 2009-12-22
Here's how I use my PS3 with Mythtv:

I set up my backend to talk to the network.

This then automatically makes the backend a UPnP.

I plug my PS3 into the network.

Everything I recorded on the backend is now available to stream with my PS3.

Hope that helps.

---

### Post by radnor on 2009-12-22
I can play recorded TV shows (HDHR tuner) and RIPped DVD from the BE to a PS3 w/o a problem.  For the RIP(s) something OTHER than ISO.  I use perfect.

When I log on to the PS3, I look for media servers then nav to the videos folder and select what I want from there.

---

### Post by hotshot247 on 2009-12-22
i tried to type "gedit ~/.mediatomb/config.xml" to edit the file for my ps3 and of course i have mediatomb installed but when i type that in, it comes up with a blank text file. can anybody tell me what i'm doing wrong? thanks!

---

### Post by Brilock on 2009-12-22
> **bubonic1347 said:**
> Here's how I use my PS3 with Mythtv:

I set up my backend to talk to the network.

This then automatically makes the backend a UPnP.

I plug my PS3 into the network.

Everything I recorded on the backend is now available to stream with my PS3.

Hope that helps.

Did you have to even use media tomb?  If not, maybe that's where I went wrong?

---

### Post by radnor on 2009-12-22
> **Brilock said:**
> Did you have to even use media tomb?  If not, maybe that's where I went wrong?

I never did.

---

### Post by !nkubus on 2009-12-22
> **Brilock said:**
> I'm using an HVR-1600 tuner and followed webguy's MediaTomb tutorial here: [http://ubuntuforums.org/showthread.php?t=1061203](http://ubuntuforums.org/showthread.php?t=1061203)

I'm at the point where I have mediatomb on the machine, and the folders I've tagged show up on the PS3 but the videos do not.  My suspicion is that I need to transcode them into a different format, but can anyone verify that this would cause the problem?  When I go into 
Recording Profils > Transcoders, I have default options for Autodetect from RTjpeg/MPEG4 and Autodetect from MPEG2.  The options under them appear to be identical though...

Now that I'm this close I feel I'm missing something obvious!  Any tips out there?


It might be a bit off topic, but have you tried with the software ps3mediaserver 

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

I had gread experience with this app

---

### Post by bubonic1347 on 2009-12-23
Keep in mind that the PS3 is a closed system. I bought it because I was missing playing the odd video game every now and then -something Linux does not support- and that was it. 

I had no idea that it would also stream recorded Mythtv shows, and it does.

I dunno about flac or divx or mkv or anything else. I wouldn't and don't expect a closed system to support stuff like that.

The people who make up the Linux community love to take a closed system box and make it their own with hacks and tweaks, and I respect that. Some guy had a Kindle running a form of Ubuntu!

I have a hard enough time just keeping Mythtv together, so I'm not going lift a finger regarding the PS3.

I'm plugging it into my little Ubuntu/Linux network and letting the chips fall as they may.

---

### Post by owenlinx on 2009-12-23
I've been using mythtv's built in upnp server, it works well. I went to the IRC to get some help with this and they sent me to mythexport. I created a user job for my sd & hd user job for my ps3, and also an xvid for my n800. Very easy!!!

[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

by the way: it will report as done in mythweb but it's just beginning. It will take some time and work in the background.

---

