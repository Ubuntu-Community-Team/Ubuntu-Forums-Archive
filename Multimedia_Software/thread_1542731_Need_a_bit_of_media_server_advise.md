---
title: "Need a bit of media server advise"
date: 2010-07-31
forum: Multimedia Software
---

### Post by sykocis on 2010-07-31
Hello all.  Please forgive me for my lack of knowledge.  I am fairly new to ubuntu.  I am running 10.4 on a laptop alongside Windows 7.  I have searched the internet as well as these forums in hopes of trying to come to a resolution for something I am working on.  I am aboard a Naval vessel and have been tasked with implementing a media network for the crew to utilize while deployed and to boast overall moral.  I have a server, but am unsure as to what OS we will be running.  I would prefer to use ubuntu, but one of the ITs wants to use Windows Home Server :(.  Here is the issue. What type of media server (ubuntu) would permit me to either stream media ( VOD-ish ) or have the media downloaded to client pc's and then rendered inoperable or deleted after a certain amount of time ( kind of like some type of DRM )?  I hope I what I said is understandable.  Thank you all in advance for your time and once again I apologize for the lack of knowledge on my part as well as for such a long post.

---

### Post by sykocis on 2010-08-01
Ok.  I see that I have XBMC and Mythbuntu as options.  What I haven't yet found is if these Media Centers have the ability to render the files inoperable or delete them after a set measure of time has expired.  Please, any help would be greatly appreciated.  Thank you.

---

### Post by jerenept on 2010-08-01
XBMC is probably a good choice, if you don't need a tv tuner.

The easiest way to do this is share the files via Samba ```
sudo apt-get install system-config-samba
```
and then delete them afterwards.
Or you could try: [http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html]("http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html")

EDIT: DRM is kind of defeating the point of the whole "Freedom" aspect of Ubuntu, if you ask me.

---

### Post by sykocis on 2010-08-01
jerenept- I do understand that.  I am not a fan of DRM myself.  Please understand though that the only reason I am looking into this is because the heads of my command are concerned with media piracy / copyright laws.  Truthfully, all of us on the ship share files amongst ourselves anyway, so I really don't see what the big deal is.  Still, I have been told that in order to get this media share network up and running, I have to somehow protect the files.  Mainly the video files.  They for some reason haven't really said much about music files.  I am looking into XBMC.  It truly looks promising.  I am just not sure of the type of configuration to go with. There will be about 280+ users once we deploy.  With only one server, streaming no longer sounds like it would be an option.  I haven't ruled it out yet though.  If I can find a means of protecting the video files, then problem solved.  Thank you for the response as well.  You have swayed me a little more towards XBMC :p

---

