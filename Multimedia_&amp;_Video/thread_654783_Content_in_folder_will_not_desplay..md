---
title: "Content in folder will not desplay."
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by SoLost on 2007-12-31
This is so weird, I have a bunch of Mp3s in my music folder. I have them organized all nice and have a bunch of folders in the music folder. When making a CD I like to jump from folder to folder to find songs to "mix" and put in to a new folder before putting them on a CD. Every thing works good for a wile but some were along the line my computer will just stop letting me in to theses folders, it wont let me in to any folder in fact. it some times says contents in folder cant be displayed. some time I just click the music folder and nothing at all will happen.I always have to restart the computer to get my folders back. Then the problem will come back eventually??????.

---

### Post by markharding557 on 2007-12-31
this is due nautilus crashing,not sure why
see if the same happens with another file manager program
also you shouldn't need to reboot,try logging out and then back in and all should load back up

---

### Post by tcdrewiv on 2007-12-31
Had a similar problem with nautilus when I had a corrupted video file in the folder I was trying to open.  I could not open the folder until I switched off icon view/file preview in nautilus settings. 
Once it opened I could locate and delete the corrupted file.

---

### Post by disturbed1 on 2007-12-31
As above, the problem is with nautilus/gstreamer. You can add these 2 things to list of what to do when it crashes. Open the System Monitor (System -> Administration) right click on nautilus and kill it. Nautilus will relaunch on it's own. Drop to a terminal and issue ***sudo killall nautilus***

The reason this happens is because of a *bad* file. Usually the header is messed up somehow. This happens mostly to me when I obtain an incorrectly encoded FLAC file which for somereason has an MP3 header :roll: You could load the directory in Rhythmbox to see which files have errors, then either delete, re-encode, re-rip, whatever. Or turn off previews in nautilus (Edit -> Preferences -> Preview)

---

