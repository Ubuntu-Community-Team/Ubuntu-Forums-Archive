---
title: "Myth 2nd PC setup questions"
date: 2009-02-03
forum: Mythbuntu
---

### Post by rodercot on 2009-02-03
Hey All,

 I have in my main room a Primary backend with a VU 6141 rcvr running XBMC as the front end. I also have a 2nd PC in the bedroom currently just running XBMC but in that machine I have a low profile pvr-150 as well as a VU 6000 rcvr. 

 what I would like to do is rebuild the bedroom machine pretty much the same as the main rooms machine so it is a stand alone machine running myth and XBMC and the tv tuner has access to the vu 6000 rcvr in the bedroom only at this point. 

 I want to do this without the 2nd bedroom machine conflicting with the main rooms machine. when these are both setup and running I would like create a shared recording directory for both machines to use on my media server in the basement. 

 I am not sure if this is possible or not but any advice would be welcome.

 Thanks,

 Dave

---

### Post by liquidhot on 2009-02-03
I'm not entirely familiar with XBMC working with MythTV, but it looks like it should function:
[http://www.mythtv.org/wiki/Xbox_Frontend#Running_XBMC_with_native_MythTV_Support](http://www.mythtv.org/wiki/Xbox_Frontend#Running_XBMC_with_native_MythTV_Support)

What you're talking about is definitely possible with MythTV alone, so if you can get XBMC running on top of both of your front ends you should be fine.

The basic ideas are like this:
You would make one of the PCs a Master Backend. Each box that will be recording shows should have a backend installed on it and connect to the master backend. You may also want to look into storage groups depending on how much space you have where and how you want to store that information. [http://www.mythtv.org/wiki/Storage_Groups#Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups#Storage_Groups)

---

### Post by rodercot on 2009-02-03
Thanks for the reply, Yes! currently the machine in the living room is working as the master backend and xbmc works great with either the myth:// protocol or the xbmcmyth python script.

 I will setup recordings etc from mythweb when I have this all completed and basically use the main living room machine for playback of recorded shows and the bedroom tv will be live tv most of the time.

 I have lots of room on my media servers I am really not too sure how to setup the storage groups or how to direct myth to use the server as the recording storage group preference, The bedroom machine I want to rebuild has only a 20gb drive in it currently so I really do not want to set it up and have it start recording to the local drive at any time as it would fill rather quickly. 

 My media server is basically 11 drives currently and I would throw in another 750Gb I have lying around, it gets shared across the network as a std smb share of each drive like

 //TOWER/Disk1/Movies1, disk2/Movies2 etc... So I can easily create a folder called MythTv Recordings and place the video, music, pictures, LiveTV etc in that folder.

 I am not sure the format required to add these to the myth reecording folder or if I only have to create sysmlinks.
 The master backend currently has 280Gb of free space to record to and it is setup on local host on that machine currently via 127.0.0.1 and the hosts file I have not touched. 

 rgds,

 Dave

---

### Post by liquidhot on 2009-02-03
For your 11 or so hard drives you would just add all of the directories (across different hard drives) to the default storage group and Myth will automatically fill them up as it needs. Local storage will take a priority for the machine that's recording.

If you're basement machine can handle it, I would move all of your recording cards to it so that it will be able to record locally and take the load off your frontends to do other things like play HD content or other misc tasks. Of course if you're front ends are more powerful than that machine it make make sense to keep them where they are.

---

