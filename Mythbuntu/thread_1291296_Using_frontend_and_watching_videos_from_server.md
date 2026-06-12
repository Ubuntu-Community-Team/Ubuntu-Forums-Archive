---
title: "Using frontend and watching videos from server"
date: 2009-10-14
forum: Mythbuntu
---

### Post by sydneysuder on 2009-10-14
Hi,

I setup a computer as mythtv server. I addes a second HDD for storage (500GB) and have configured myth to store all files on that drive.

I installed the frontend (from sniderpad) on a couple of Mac computers. I can watch tv and recorder programs from those computers. My problem is watching ripped DVDs and music.

1. On the server I setup videos to go to /video/videos (/video is where the second HDD is mounted)
2. I copied a DVD (Eve - a Sydney Film School movie)
3. I can start the frontend on the server, navigate to videos and watch it.
4. When I try to do the same on one of the frontends I am able to see the listing for the movie but when I try to play it I get an error "/video/videos/evexxx is missing". This makes sense from the point of view of the frontend computer which would not have that path available locally. But from the frontend/backend setup of Myth makes no sense at all.

Am I missing something in the setup?

Any help would be greately appreciated.

---

### Post by tgm4883 on 2009-10-14
> **sydneysuder said:**
> Hi,

I setup a computer as mythtv server. I addes a second HDD for storage (500GB) and have configured myth to store all files on that drive.

I installed the frontend (from sniderpad) on a couple of Mac computers. I can watch tv and recorder programs from those computers. My problem is watching ripped DVDs and music.

1. On the server I setup videos to go to /video/videos (/video is where the second HDD is mounted)
2. I copied a DVD (Eve - a Sydney Film School movie)
3. I can start the frontend on the server, navigate to videos and watch it.
4. When I try to do the same on one of the frontends I am able to see the listing for the movie but when I try to play it I get an error "/video/videos/evexxx is missing". This makes sense from the point of view of the frontend computer which would not have that path available locally. But from the frontend/backend setup of Myth makes no sense at all.

Am I missing something in the setup?

Any help would be greately appreciated.

You need to mount the network share locally. If you are using MythTV 0.22, you can use storage groups as long as the files are not ISO's

---

### Post by larsolav on 2009-10-14
> **tgm4883 said:**
> You need to mount the network share locally. If you are using MythTV 0.22, you can use storage groups as long as the files are not ISO's
Just curious, why don't ISOs work with storage groups under 0.22?

---

### Post by iamlindoro on 2009-10-14
Hello,

I am MythTV's MythVideo maintainer.  Storage Groups are a streaming method of transmitting material to a frontend, meaning they don't provide block-level access to the file in question.  an ISO is a disk image, and libdvdnav/libdvdcss, the libraries used to view DVDs/DVD images, requires block-level access.  We have a plan to simulate a block device across the network using NBD for .23, but as mentioned in the MythTV wiki MythVideo .22 transition page, Storage Groups in MythVideo are meant to be used as a technology preview only-- the implementation is not complete.  Thanks to some serious hard work in the past few months, almost everything works, but use of external players (because they don't speak the myth:// streaming protocol) and use of ISOs in storage groups is not presently possible.

Please see:

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

---

### Post by larsolav on 2009-10-14
Thanks, iamlindoro, for the detailed explanation. And thanks to all the MythTV and Mythbuntu developers for all the work and help. You guys are awesome.

---

### Post by sydneysuder on 2009-10-14
> **tgm4883 said:**
> You need to mount the network share locally. If you are using MythTV 0.22, you can use storage groups as long as the files are not ISO's


OK. Let me get this straight:

I have two options.
- Mount the network share locally and change the configuration settings on the frontend to look for videos on /mountpoint/blah
-Use storage groups.

Is that correct?

I think I can do the network share mounting quicker than the other option but I may try both for the sake of it.

---

### Post by SiHa on 2009-10-15
Just one additional pointer.
The mountpoint on the remote frontend should be the same as the path to that directory on the backend. I believe it can screw up the metadata if you have two frontends, both of which think the videos are in different places.

---

### Post by tgm4883 on 2009-10-15
Yes, those are your 2 options. And Yes, they do have to be at the same path.
[http://www.mythtv.org/wiki/Mediashares](http://www.mythtv.org/wiki/Mediashares)

---

