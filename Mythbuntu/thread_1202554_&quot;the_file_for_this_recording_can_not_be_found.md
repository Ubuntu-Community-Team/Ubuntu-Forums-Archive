---
title: "&quot;the file for this recording can not be found&quot;"
date: 2009-07-02
forum: Mythbuntu
---

### Post by mookie60 on 2009-07-02
mythbuntu 9.04, up-to-date
hauppauge 1600
front/backend single machine

The machine was running fine - made no changes.  This morning i attempted to play last nights recordings (which are displayed on the list of recorded programs) but it generated the following error - "_the file for this recording can not be found_".   This was the case for both the analog and digital tuner recordings.   I can neither play, nor delete these files, if they actually exist.

This happened once before, and a rescan of the tuner channels at least let me delete and/or watch the programs.   I can't recall for sure, it's been about 2 months.   I must have at least been able to delete the troublesome programs, as they're no longer present.  Programs recorded prior to last evening still play fine.

So I reset both tuners and rescanned the channels, but still can't play or delete these particular recordings.   A test recording of both tuners shows they are now working.

I tried searching the archives for this error msg, but didn't find anything useful.

any ideas how to fix these programs, or prevent this from happening again?

Thanks

---

### Post by Jayy on 2009-07-02
I got that error when I "suspended" my computer the evening before recording TV, because my computer doesn't (yet) wake up to record the TV.

---

### Post by mookie60 on 2009-07-02
I have had some issues where powersave or screensave (not sure which) kicked-in (blank screen) and wouldn't acknowledge input from either the remote or keyboard, forcing me to reboot - but these problems had not been associated with the current "file ... not found" problem.  About a month ago I just turned off the powersave (or whatever it's called) and just use the screensaver to blank the screen.   So the powersaver should not be related.  

I don't use "wake-up" or suspend.   

Thanks Jayy

---

### Post by Jayy on 2009-07-02
Okay. Well, then I don't know what the problem is. :?

---

### Post by crez79 on 2009-07-03
When this happens to me, usually it is because the recorded file can't be found, or the file is invalid for some reason. Without knowing the specifics of you system, I would first check that the folders you have set up for recorded tv are both mounted and accessible. I would also check in mythweb under recorded programs under the specific recordings and make sure the size isn't 0, or 'B'. The way myth handles recorded tv is it knows the name of the file it is looking for, and it looks in all the directories set up in the storage groups until it finds it. If it can't, it tosses up this error message.

This happen every so often to me, sometimes when the cable goes out and it doesn't record properly or when for whatever reason the recording doesn't happen, but myth thinks it does and keeps the metadata.

Check the backend log to see if it says anything pertanint also.

---

### Post by mookie60 on 2009-07-03
thanks "crez".

mythweb does show the size of the problem files as "B".   so is "B" confirmation it can't locate the file, or that it didn't record and it's really a zero file size.   I've never made any changes to the storage directories, the default setup is fine for me.

I'm incline to believe it's a cable/tuner problem as you suggested.  It may be related to the poor performance of the digital tuner; glitches during digital recordings are common, and the signal strength of digital channels is always zero.

i may have to learn to live with it.  or, i'm considering a new digital tuner, then i'd discontinue use of the hauppauge digital tuner, or just set the tuner priority really low.

thanks again

---

### Post by roundhay on 2009-07-06
I seemed to have solved my problem, this fix came about by chance but it does work as i had the probelem on a second PC and the fixed solved the issue there as well.

I ran:
 
sudo dpkg-reconfigure mythtv database 

and chaged the final setting so that remote connects could be made to the database. I did this so my remote frontends could connect to the backend but it also seems to have solved the recording issues. I'm not expert enough to know why this worked but it did. 

The recordings now work and I can access them.

---

### Post by NautiusMaximus on 2009-07-07
I've just had exactly the same error message. I'm using Mythbuntu 8.10.

This is puzzling, as I've had my machine working for about 6 months now. In all that time, it has been 100% reliable in recording programs and playing them back when I ask it to. Until this evening (the recording I wanted to watch is a few weeks old: plenty of stuff recorded before and since is easily accessible).

How do I go about troubleshooting this? This talk of Mythweb is going slightly over my head: I haven't yet set up or used Mythweb. Do I need to? Or is there another way of determining whether the program has recorded and the file somehow can't be found or whether it never recorded in the first place?

I have just the one box running both frontend and backend, so is there any point in trying roundhay's fix?

Thanks
NM

---

### Post by crez79 on 2009-07-07
In the recorded programs where you would pick the recording you want to watch, highlight the program that won't play and hit 'u' and it will bring up information about the recording including the filename mythtv is looking for and the size. You can then check your recordings folder to see if you can find the file name and try to play it. Also check the permissions of the file. I have seen some crazy things happen every once in a while. Maybe this will help find the problem. 

I think mythweb is one of the coolest features of mythtv. It is easy to set up from mythbuntu-control-centre and makes managing the recording schedules and changing settings easy and doesn't tie up the tv when I want to tinker.

---

### Post by NautiusMaximus on 2009-07-08
Thanks for that. Hitting U as you suggest didn't give a file name. Doing the same for a program that can be played OK did give a file name. I guess that means it's reasonable to conclude that the file simply doesn't exist?

Also, thanks for the tip about Mythweb. It was in fact already set up. Once I'd managed to find out how to access it from another PC (bizarrely not described in the Mythweb wiki, as far as I could tell, but for the benefit of others simply type [http://[insert](http://[insert) computer name or IP address here]/mythweb into a browser), it just worked. Possibly the first thing I've come across on Mythbuntu that "just worked"! I shall certainly have fun playing with it.

Anyway, the file size as shown in Mythweb was "B", which I guess is consistent with the conclusion that the file never recorded in the first place.

Does this mean that the programme is lost forever?

---

### Post by crez79 on 2009-07-08
According to mythtv, the program is lost. It might have possibly still been recorded but just entered into the data base wrong. You could try to look in your recorded programs folder for a file that was modified about the same time as when the program you want to watch was recorded. 

Unless this show is never going to be on again, it would be easiest to record it again. You could try hulu or the network's website to see if you can watch it online. Doing it that was isn't very user friendly, but for just one show it isn't that bad. I have done this a couple times when the show wasn't recorded properly or I forgot to record it.

---

