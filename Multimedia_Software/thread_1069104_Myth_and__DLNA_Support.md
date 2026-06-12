---
title: "Myth and  DLNA Support"
date: 2009-02-13
forum: Multimedia Software
---

### Post by inanis on 2009-02-13
I have a Mythbuntu system running at my house with several frontend systems. Everything works (more or less) fine. I have an HD HomeRun as a TV Tuner which records to the backend with no issues. 

I recently bought a new TV (Samsung LN52A750) with DLNA compatibility. I specifically picked this TV because of the DLNA feature. Before I bought it I checked to make sure that Myth was DLNA compatible and from what I understood it was.

Yesterday I tried to use the DLNA feature. It connected to the backend Myth system just fine. I could see all my files, both music and video. The only problem was that I can't actually play any of them. No matter what I pick I get "Not Supported File Format". My guess is that I need some kind of codec installed on the Myth server, only I'm not sure exactly what that might be.

I know that none of the media I have contains any kind of DRM. I'm basically dealing with MP3's for music, ISO and VOB files for ripped DVD's and MPEG2 encoded video for the recordings.

If anyone has any advice I would greatly appreciate it. It is beyond frustrating to see the files but not actually be able to use them. I'm not very familiar with DLNA so maybe I'm missing something simple?

Thanks in advance.

---

### Post by Humorme2003 on 2009-04-30
I also have a series 8 Samsung TV that supports DLNA.  I had the same problem with my videos.  I was able to get them to play by using Nero MediaHome with the transcoding option.  It plays fine if I send the files mpeg2.

The TV will play the files from a flash drive, if directly connected to the TV. It is something when the files are transferred through the network.

---

### Post by ldillon on 2010-01-06
See [http://forums.cnet.com/5208-13973_102-0.html?threadID=336205](http://forums.cnet.com/5208-13973_102-0.html?threadID=336205)

Supposedly Samsung's DLNA isn't 100% standards compliant and addinf some http headers helps.

---

### Post by p2ranger on 2010-03-18
Looking at buying a Samsung TV myself. Just heard about this DLNA technology and I have to say I'm excited. This thread talks about how to fix your problem. Doesn't use mythtv, but it gets your media to work it says.

[http://ubuntuforums.org/showthread.php?t=1198689](http://ubuntuforums.org/showthread.php?t=1198689)

Jason

---

### Post by damvcoool on 2011-03-16
May want to try disabling the MythTV DLNA Pluging and use MiniDLNA instead, it works 100% of the times with Samsung TV, I tested it with a LN46C650 and a LN55C610.

Also Would be awesome to suggest the MythBuntu Devs to integrate this little app into MythButuntu as a replacement for the

---

### Post by johnsnails on 2012-06-10
Hey,
Just thought I would mention. I had issues with playback over dlna with a sony tv, the solution was not obvious but simple, so just throwing it out there. On your DLNA server, in my case Serviio on W7, i changed the profile from Sony 2011 tv to Sony 2009, even though it was a 2011 model and it fixed all my issues.

Not sure if this will help your particular problem, I hope it does.

---

