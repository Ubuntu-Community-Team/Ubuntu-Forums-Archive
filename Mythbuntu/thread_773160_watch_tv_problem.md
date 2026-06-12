---
title: "watch tv problem"
date: 2008-04-28
forum: Mythbuntu
---

### Post by HappyFeet on 2008-04-28
im running hardy with myth tv. ive had mythbuntu running before, but reformatted after hardy came out. im 99.99% sure that i have it setup as before. when i try to watch tv, nothing happens. this is what mythtv log gives me:
```
2008-04-28 18:05:41.085 MainServer::HandleAnnounce Monitor
2008-04-28 18:05:41.090 adding: heronhell as a client (events: 0)
2008-04-28 18:05:41.091 MainServer::HandleAnnounce Monitor
2008-04-28 18:05:41.092 adding: heronhell as a client (events: 1)
2008-04-28 18:05:41.096 MainServer::HandleAnnounce Playback
2008-04-28 18:05:41.096 adding: heronhell as a client (events: 0)
2008-04-28 18:05:41.098 TVRec(1): Changing from None to WatchingLiveTV
2008-04-28 18:05:41.107 TVRec(1): HW Tuner: 1->1
[B]2008-04-28 18:05:42.199 TFW, Error: Opening file '/home/ed/1025_20080428180541.mpg'.
			eno: Permission denied (13)
2008-04-28 18:05:42.201 TVRec(1) Error: RingBuffer '/home/ed/1025_20080428180541.mpg' not open...
2008-04-28 18:05:42.201 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-04-28 18:05:42.202 TVRec(1) Error: Failed to create RingBuffer 2[/B]
2008-04-28 18:05:42.204 TVRec(1): Changing from WatchingLiveTV to None
2008-04-28 18:05:42.207 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

	


im not sure what to do about these errors. i added myself to the mythtv group, so im not sure what it could be.

this is my frontend log: 
```
2008-04-28 18:26:24.869 TV: Attempting to change from None to WatchingLiveTV
2008-04-28 18:26:24.870 Using protocol version 40
2008-04-28 18:26:25.976 GetEntryAt(-1) failed.
2008-04-28 18:26:25.977 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-04-28 18:26:25.977 TV Error: LiveTV not successfully started
2008-04-28 18:26:25.978 TV Error: LiveTV not successfully started
2008-04-28 18:26:26.076 TV: Deleting TV Chain in destructor
2008-04-28 18:26:26.084 DPMS Deactivated 
2008-04-28 18:26:26.085 DPMS Reactivated.
2008-04-28 18:26:28.615 TV: Attempting to change from None to WatchingLiveTV
2008-04-28 18:26:28.616 Using protocol version 40
[B]2008-04-28 18:26:29.766 GetEntryAt(-1) failed.
2008-04-28 18:26:29.768 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-04-28 18:26:29.768 TV Error: LiveTV not successfully started
2008-04-28 18:26:29.769 TV Error: LiveTV not successfully started
2008-04-28 18:26:29.818 TV: Deleting TV Chain in destructor[/B]
2008-04-28 18:26:29.823 DPMS Deactivated 
2008-04-28 18:26:29.823 DPMS Reactivated.
2008-04-28 18:26:39.539 Deleting UPnP client...
```

btw, this is a standalone setup.

---

### Post by volkswagner on 2008-04-28
What are the permissions for your recording directory?  What is with the date, 1969?

---

### Post by wolfen69 on 2008-04-28
.

---

### Post by HappyFeet on 2008-04-28
i'm not sure what the problem is.

---

### Post by Jorgo on 2008-04-28
It looks like MythTV doesn't have permission to write to the /home/ed directory.  One way to fix this is to change the group owner to mythtv but that probably isn't a good idea because it is your home directory (and will possibly create other troubles).

I would suggest creating a new directory in your home directory that has the appropriate permissions for MythTV (i.e. change the group to mythtv).  This will allow MythTV to record live TV to this directory.  Obviously you will have to change the directory for recordings in the MythTV setup.

---

### Post by justanotherhack on 2008-04-29
The date is the start date of the standard unix timestamp with an offest due a different timezone. Basically the system tries to use a timestamp of 0.
(Just to clear that question.)
Usually that indicates a problem indeed, but not sure what kind of here. Prolly the aforementioned change of rights and/or directories will be enough.

---

### Post by thegizzard on 2009-01-01
GetEntryAt(-1) failed

I had this same problem.  The solution was the permissions on the recording directory.

I gave the Mythtv group write access.

Fixed.  No problem.

I hope this helps the next guy.

---

### Post by tgm4883 on 2009-01-01
Your recording directory should not be inside of your home dir.

---

### Post by thegizzard on 2009-01-01
It isn't.

I use a different disk i have mounted as:

/media/tv

The record directory is:

/media/tv/mythtvrecord

and the shared directory is:

/media/tv/mythtvexport

I needed to grant the mythtv group write access to the record directory.

at the moment I am trying to figure out why my user jobs are not working.

---

### Post by ryry46d9 on 2010-05-23
I know this is over a year old, but searching Google lead me here. 
search sting: ```
GetEntryAt(-1) failed.
```

just wanted to say thank you to every one,

and to any other users that might stumble apon this thread, make sure your mythtv dir's are not located on a NTFS mount, because I just found out they do not support ownership and permissions from this tread. 

[http://ubuntuforums.org/showthread.php?t=873176]("http://ubuntuforums.org/showthread.php?t=873176")

---

