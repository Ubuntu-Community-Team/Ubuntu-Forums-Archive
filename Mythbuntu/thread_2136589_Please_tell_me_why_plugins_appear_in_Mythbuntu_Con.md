---
title: "Please tell me why plugins appear in Mythbuntu Control Center but not MythTV frontend"
date: 2013-04-18
forum: Mythbuntu
---

### Post by Bullwinkle_Moose on 2013-04-18
I'm relatively new to Mythbuntu and MythTV and there is one thing I don't understand (actually several things, but this is the one that is bothering me right now).  I am running the MythTV frontend on a separate Ubuntu system from the backend, if that makes any difference.

In Mythbuntu Control Center on the backend, it show four plugins:

MythBrowser
MythMusic
MythGallery
MythWeb

However none of these seem to appear on the frontend, which as I say is running on a separate Ubuntu (not Mythbuntu) machine.

Should I install the mythplugins package on the frontend?  According to Synaptic it is not installed now.

Should I install the mythbuntu-control-centre package on the frontend, or is that for the backend only, or for Mythbuntu systems only (remember that my frontend is NOT Mythbuntu, so I am assuming the answer to this in no).

As a side note, one thing I'd like to do is be able to play miscellaneous video files stored in the Video directory on the frontend system.  I do not want them indexed or scraped or anything like that, because many will be played once and then deleted.  I'd just like to be able to play them without having to move them to the backend.  Is that possible?

---

### Post by AlecJ on 2013-04-18
in a word yes, the remote frontends just read the backend and so would the plugins if installed. 
mythbuntu-control-centre is the way to go, then you can stream videos and music.
You don't need Mythweb on a frontend

---

### Post by Bullwinkle_Moose on 2013-04-19
> **AlecJ said:**
> mythbuntu-control-centre is the way to go, then you can stream videos and music.

Thanks for the reply.  But would you install that on a frontend that is NOT running Mythbuntu, just bare MythTV under stock Ubuntu?

As a test I tried installing mythmusic on the frontend and it appears to work but I can't figure out how to configure it to actually find the music on my local hard drive.  But that's not a big deal to me right now because I have other ways to play music.

Really all I want to do is to play videos that are stored on the local (frontend) hard drive using the MythTV frontend.  And the reason I want to do that is because occasionally I watch what amounts to a video lecture where the speaker talks soooo slooooow that it puts me to sleep, and MythTV is the only thing I have found that will let you speed up recorded video.  But these videos do not need to be on the backend because they are generally viewed once, then erased.  I suppose I should probably start another thread for this question, but will have to wait until later to do it.

What I don't want to do is install something that will bring in a bunch of extra software packages that are not necessary for what I want to do.

---

### Post by tgm4883 on 2013-04-19
> **Bullwinkle_Moose said:**
> Thanks for the reply.  But would you install that on a frontend that is NOT running Mythbuntu, just bare MythTV under stock Ubuntu?

As a test I tried installing mythmusic on the frontend and it appears to work but I can't figure out how to configure it to actually find the music on my local hard drive.  But that's not a big deal to me right now because I have other ways to play music.

Really all I want to do is to play videos that are stored on the local (frontend) hard drive using the MythTV frontend.  And the reason I want to do that is because occasionally I watch what amounts to a video lecture where the speaker talks soooo slooooow that it puts me to sleep, and MythTV is the only thing I have found that will let you speed up recorded video.  But these videos do not need to be on the backend because they are generally viewed once, then erased.  I suppose I should probably start another thread for this question, but will have to wait until later to do it.

What I don't want to do is install something that will bring in a bunch of extra software packages that are not necessary for what I want to do.

Then install the plugins you want on the frontend. The backend doesn't use plugins.

In your case it sounds like you want mythvideo

---

### Post by Bullwinkle_Moose on 2013-04-19
> **tgm4883 said:**
> Then install the plugins you want on the frontend. The backend doesn't use plugins.

In your case it sounds like you want mythvideo

Thanks, but I don't see any mythvideo in the repository.  All I see are:

mytharchive *
mythbrowser
mythexport
mythgallery *
mythgame *
mythimport
mythmusic
mythnettv (and mythnettv-gui)
mythnetvision *
mythnews *
mythplugins (a metapackage)
mythtvfs
mythweather *
mythweb *
mythzoneminder


Note that mythplugins installs apache, php5 and a bunch of other stuff that seems suspiciously more appropriate for the backend than the frontend, and which I wouldn't want running on my frontend.  It also installs the plugins I have starred above.  I have a feeling that most of the unwanted stuff is brought in for the benefit of mythweb, which is the one thing that should only be run on the backend IMHO (and I do have it running there, and it works).

But mythvideo?  Not seeing that one. I even looked on the backend system to see if maybe it was something exclusive to Mythbuntu but it's not showing up there, either.

---

### Post by tgm4883 on 2013-04-19
> **Bullwinkle_Moose said:**
> Thanks, but I don't see any mythvideo in the repository.  All I see are:

mytharchive *
mythbrowser
mythexport
mythgallery *
mythgame *
mythimport
mythmusic
mythnettv (and mythnettv-gui)
mythnetvision *
mythnews *
mythplugins (a metapackage)
mythtvfs
mythweather *
mythweb *
mythzoneminder


Note that mythplugins installs apache, php5 and a bunch of other stuff that seems suspiciously more appropriate for the backend than the frontend, and which I wouldn't want running on my frontend.  It also installs the plugins I have starred above.  I have a feeling that most of the unwanted stuff is brought in for the benefit of mythweb, which is the one thing that should only be run on the backend IMHO (and I do have it running there, and it works).

But mythvideo?  Not seeing that one. I even looked on the backend system to see if maybe it was something exclusive to Mythbuntu but it's not showing up there, either.

mythplugins install all plugins and is not what you want. I forgot mythvideo was integrated into the frontend in either 0.25 or 0.26, so you should already have it with your frontend.

---

### Post by dannyboy79 on 2013-04-21
go into MythFrontend > Setup > Media Settings > Video Settings > General Settings  and the top line is where you set the folder where your videos are.

---

### Post by Bullwinkle_Moose on 2013-04-21
> **dannyboy79 said:**
> go into MythFrontend > Setup > Media Settings > Video Settings > General Settings  and the top line is where you set the folder where your videos are.

Thanks, that did the trick!

---

