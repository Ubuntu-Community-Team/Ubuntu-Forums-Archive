---
title: "Metadata"
date: 2010-01-30
forum: Mythbuntu
---

### Post by Sctmon on 2010-01-30
Is mythvideo meant to store metadata retrieved for videos somewhere, either in the database or in the video file somewhere?
I have just set up Mythtv (9.10) for the first time and while I am deciding on what the best DVB-T card is to get I am trying it out with a few sample TV episodes that I have copied over to the computer running the backend/frontend

I can get the metadata to download either by pressing 'w' or 'i' and 'download metadata' but when I navigate out of video manager and back in again it is gone.

I have about a dozen tv episodes that I copied over and split between /var/lib/mythtv/videos and home/scott/Videos which are the 2 temporary locations that I am using to test thing. I have changed the permissions on a few of the files but that hasn't made any difference.

---

### Post by Sctmon on 2010-02-02
.....
Is this the way the mythvideo library is meant to work or am I missing something obvious?
After downloading or manually entering the metadata for a video file it is is displayed whenever I select that file as long as I dont' exit back to the main menu or change the view. If I do that then all of the video files just have the file name and a question mark and the metadata has to be re-downloaded.

The cover art, banners, screen shots etc are all present in the respective folder (/var/lib/mythtv/...)

---

### Post by williammanda on 2010-02-02
First you will need to read this:

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide]("http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide")

Then you need to decide whether you will use storage groups or not depending on your video file format.

---

### Post by Sctmon on 2010-02-02
> **williammanda said:**
> First you will need to read this:

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

Then you need to decide whether you will use storage groups or not depending on your video file format.

Sorry.... I thought I had been pretty through with the transition guide but missed the bit about checking the 'video list loads video metadata' option in the settings.

Thanks. all works fine now.

---

