---
title: "MythVideo videos disappearing"
date: 2009-11-07
forum: Multimedia Software
---

### Post by rich86 on 2009-11-07
Hi,

I am new to storage group on mythtv 0.22-release so i think this is the root of my problem, but i am not sure what to do or what some settings should be.

The basic issue is that i have run Jamu using the instructions here [http://www.mythtv.org/wiki/Jamu](http://www.mythtv.org/wiki/Jamu) for a mass update and then when I go into MythVideo most (but not all) of my videos are there.

I then click 'M' > 'scan for changes' and then half my videos disappear leaving this in the mythfrontend log:
> 2009-11-07 13:12:20.637 buildFileList directory = myth://Videos@richards/media/data/other docs/mythtv/videos/
2009-11-07 13:12:20.637 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@richards/media/data/other docs/mythtv/videos/)
2009-11-07 13:12:21.032 Removing file SG(richards) :The Inbetweeners/The Inbetweeners - S01 E04 (Girlfriend).avi: 
2009-11-07 13:12:21.032 Removing file SG(richards) :TV/Have I Got a Bit More News for You - S38E02.mp4: 
2009-11-07 13:12:21.033 Removing file SG(richards) :TV/Would I Lie To You - S03E02.mov: 
2009-11-07 13:12:21.033 Removing file SG(richards) :TV/Never Mind the Buzzcocks - S23E05.mp4: 
...

I am running a mythbackend and frontend on the same pc with no other frontends. I have set all the storage groups in mythbackend-setup to folders that excist eg 'Videos' is set to '/media/data/other docs/mythtv/videos/'
There are no errors in the mythbackend log.

On the frontend i am not sure what to set the options in: 'Utilities/Setup' > 'Setup' > 'Media Settings' > 'Videos Settings' > 'General Settings' > 'Dirs that hold videos' At the moment they are all blank. I assume this is correct as it means it is using the Storage Directories then.

I think that is all the information i can give, if you need anything else please let me know. Any one go any ideas as to why my videos keep disappearing?

Thanks in advance.

Richard

---

### Post by rich86 on 2009-11-11
Anyone got any idea how it works and to use storage directories?? 

Or even just a good article to read up on it. The one on the MythTV wiki is not all that usful.

---

### Post by rich86 on 2009-11-28
OK i gave up on storage groups and went back to setting the directory location in the frontend. Although if anyone still has any news on how to get Storage Groups working please let me know.
This is mainly as Jamu grabber doesn't like not using storage groups so i would like to go back at some point.

---

