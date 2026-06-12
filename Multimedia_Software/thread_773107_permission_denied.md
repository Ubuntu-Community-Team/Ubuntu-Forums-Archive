---
title: "permission denied?"
date: 2008-04-28
forum: Multimedia Software
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
2008-04-28 18:05:42.199 TFW, [B]Error: Opening file '/home/ed/1025_20080428180541.mpg'.
			eno: Permission denied (13)[/B]
2008-04-28 18:05:42.201 TVRec(1) [B]Error: RingBuffer '/home/ed/1025_20080428180541.mpg' not open...
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
[B]2008-04-28 18:26:25.976 GetEntryAt(-1) failed.
2008-04-28 18:26:25.977 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-04-28 18:26:25.977 TV Error: LiveTV not successfully started
2008-04-28 18:26:25.978 TV Error: LiveTV not successfully started[/B]
2008-04-28 18:26:26.076 TV: Deleting TV Chain in destructor
2008-04-28 18:26:26.084 DPMS Deactivated 
2008-04-28 18:26:26.085 DPMS Reactivated.
2008-04-28 18:26:28.615 TV: Attempting to change from None to WatchingLiveTV
2008-04-28 18:26:28.616 Using protocol version 40
2008-04-28 18:26:29.766 GetEntryAt(-1) failed.
2008-04-28 18:26:29.768 **EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo**
2008-04-28 18:26:29.768 TV Error: LiveTV not successfully started
2008-04-28 18:26:29.769 TV Error: LiveTV not successfully started
2008-04-28 18:26:29.818 TV: Deleting TV Chain in destructor
2008-04-28 18:26:29.823 DPMS Deactivated 
2008-04-28 18:26:29.823 DPMS Reactivated.
2008-04-28 18:26:39.539 Deleting UPnP client...
```

---

### Post by NT4usB on 2008-04-28
...been a long time since I set up MythTV but back then I installed as my user then logged in as user mythtv. mythtv didn't have permissions to the folder where live TV is cached and recordings are stored. Had to (figure out which folders, and) allow mythtv read write to get it to work.
I'm sure the install is better (since MythTV 0.18 on Dapper) so this may no longer be an issue.

---

