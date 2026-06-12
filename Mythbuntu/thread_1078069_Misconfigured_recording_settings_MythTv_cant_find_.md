---
title: "Misconfigured recording settings: MythTv cant find files but they are really there"
date: 2009-02-22
forum: Mythbuntu
---

### Post by slick666 on 2009-02-22
I'm new to recording tv and after recording my first couple shows the recording would appear but the error I would get is that the recording file could not be found. As part of the initial setup I created a folder in my home directory for all the recording to be dumped into. I checked and low and behold the files are all there. 

So the questions I have is what configurations do I have mismatched to get this problem. I figure all I have to do is change some setting to look in the directory I've set them to record to but what two settings they are I have no idea.

---

### Post by klc5555 on 2009-02-23
> **slick666 said:**
> I'm new to recording tv and after recording my first couple shows the recording would appear but the error I would get is that the recording file could not be found. As part of the initial setup I created a folder in my home directory for all the recording to be dumped into. I checked and low and behold the files are all there. 

So the questions I have is what configurations do I have mismatched to get this problem. I figure all I have to do is change some setting to look in the directory I've set them to record to but what two settings they are I have no idea.

Probably an owner/group/permissions snafu caused by setting up the primary Storage Group directory in your home directory. The backend can write files there, but the "mythtv" user can't read them there from the frontend.

Usually, the storage group directories are set up outside the primary users home directory (and preferably outside the root partition, to avoid eventual filled-root-partition lockups). In Mythbuntu, wherever the storage directories are should be set to owner=mythtv (not "root", or you), group=mythtv (and your username should be added to the mythtv group), and permissions should be set to 775 or above. This normally fixes all such problems in Mythbuntu proper, which creates a mythtv user as part of the standard installation. 

In installations of mythtv as an app to an existing system, where a mythtv user is not generally created and all backend/MySQL activities are likely controlled by root, other workarounds may become necessary.

Cheers! :)

---

