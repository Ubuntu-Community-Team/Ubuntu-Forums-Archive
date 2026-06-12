---
title: "MythTV doesn't show recordings"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by hambone79 on 2007-05-04
I hope this is the right place to post this...

I installed MythTV on an older computer with a PVR-150 card using the Ubuntu howto. I was able to get everything up and running without any problems (even the remote control), but I have one little annoying problem. For some reason, the shows that I record are not showing up in my Recordings list. The shows exist in the /var/lib/mythtv/recordings directory, and I can see that they were recorded in the recording schedule, but they still do not show up in the Recordings list.

Does anyone know what the problem might be?

---

### Post by superm1 on 2007-05-04
I'm *hoping* your not the 4th corrupted database i've seen this week, but unfortunately this sounds like a possible symptom.  The best thing to do:
install mythweb.
Go through the different pages, TV listings, upcoming recordings, recorded programs, etc.  If there are any SQL errors, you will see them here.

---

### Post by pdragon04 on 2007-09-15
I may have a fix for this... 

I just got Mythtv installed and working last night myself and had this exact thing happen. Saw this older post come up from a Google search. Did what the first responder said and didn't see any SQL errors in Mythweb. In fact, my recorded program showed up fine in MythWeb even though it didn't in Watched Recordings.

All that was showing up in my Watched Recordings was the last few Live TV sessions. I didn't need them anymore so I figured I'd try just deleting them. As soon as I deleted them, exited Watched Recordings and went back in, now my Scheduled Recording showed up!

Still don't know what caused it. Going to see if the same thing happens again when I get a few more Live TV recordings in and schedule some others. Anyone know if there's any known bugs mentioning this happen?

---

### Post by oyvinst on 2007-09-20
> **pdragon04 said:**
> I may have a fix for this... 


Cool, I'm new to MythTV and have experienced the exact same issue. However, after deleting all the live TV recordings, suddenly all my scheduled recordings showed up for the first time in Mythfrontend :). I knew there actually were recordings made, because they showed up just fine in Mythweb, before. It's all a matter of setting playback group filters correct, I guess.. Anyway, I'm finding the various settings in Mythfrontend and Mythtv-setup a bit confusing, not the most intuitive layout IMHO.But hey, it works ..

---

### Post by EtanSivad on 2007-09-30
I rebuilt my mythbox last night  (Fedora Core 4 was getting on my nerves) and I had the exact same issue.  Recordings show up fine in the web interface, but not the "Watch recordings" page.  The watch recordings page had 1 program of live TV I had watched a little of the night before, but not the scheduled programs.

I'm not sure why yet, but sometimes when you go into "Watch recordings" it brings up a filter list and I had previously selected "Live TV".   I deleted the bit of live TV it had recorded, backed out and went back in.  Viola, the filters menu popped up again.  I selected "All" and everything came up.

Very odd.  I'm not sure how you bring that filter list up in the first place.  :confused:

---

### Post by EtanSivad on 2007-09-30
Found it.  When you're on the Watch Recordings page, hit M on the keyboard.  That'll pop up the Group filter list.

---

### Post by SuperDodge on 2008-01-23
> **EtanSivad said:**
> Found it.  When you're on the Watch Recordings page, hit M on the keyboard.  That'll pop up the Group filter list.

THANK YOU!!  This worked...

Why in the world would MythTV default to showing livetv recordings only?

---

### Post by Weidbrewer on 2008-04-08
The problem that I'm having is that, if I set up two programs to record, only the later one seems to be there.   I can't find any record of the file in the folders, but it says that it recorded.   Also, the two programs (repeated three times) are an hour apart.

Finally, I am not using mythweb...but that's because I've not had a reason to access it remotely.

---

