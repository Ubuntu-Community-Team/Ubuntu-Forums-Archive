---
title: "Mythbuntu new install"
date: 2010-09-19
forum: Multimedia Software
---

### Post by nojstevens on 2010-09-19
Hello,

I just finished a clean install of Muthbuntu (10.4) and added my HDHomeRun and HD PVR. I have my STB set up to change channels via Firewire.

An hour ago everything worked great - went into Watch TV - guide appeared, I could change channels and was really pleased.

Now, when I go into Watch TV, it says 'Please Wait...' for 5 seconds then main menu appears again.

I checked my HD PVR was working ok by writing a test.ts from /dev/video0 and all is good.

In my mythfrontend logs I see:


2010-09-19 10:07:53.494 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-09-19 10:07:53.494 Using protocol version 56
2010-09-19 10:07:53.515 Spawning LiveTV Recorder -- begin
2010-09-19 10:07:53.599 Spawning LiveTV Recorder -- end
2010-09-19 10:07:53.599 GetEntryAt(-1) failed.
2010-09-19 10:07:53.599 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-09-19 10:07:53.599 TV Error: HandleStateChange(): LiveTV not successfully started
2010-09-19 10:07:53.599 We have a RingBuffer
2010-09-19 10:07:53.651 TV Error: LiveTV not successfully started
2010-09-19 10:08:00.029 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml


Not sure where to start to look, so coming here for some help

Thanks

Jon

EDIT - I can schedule a recording and play it back ok.

---

### Post by nojstevens on 2010-09-19
In case I broke something i just did a fresh install. Updated ubuntu etc, configured backend, installed Firewire STB chaghing stuff, ran MythFrontEnd - same thing - Please Wait and then back to main menu. mythfrontend.log says the same...


2010-09-19 14:29:20.641 MythContext: Connecting to backend server: 10.0.1.80:6543 (try 1 of 1)
2010-09-19 14:29:20.641 Using protocol version 56
2010-09-19 14:29:20.682 Spawning LiveTV Recorder -- begin
2010-09-19 14:29:20.965 Spawning LiveTV Recorder -- end
2010-09-19 14:29:20.966 GetEntryAt(-1) failed.
2010-09-19 14:29:20.967 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-09-19 14:29:20.967 TV Error: HandleStateChange(): LiveTV not successfully started
2010-09-19 14:29:20.967 We have a RingBuffer
2010-09-19 14:29:21.018 TV Error: LiveTV not successfully started


Any ideas anyone?

Jon

---

### Post by joiningtheherd on 2010-10-13
I've tried Mythbuntu (and a MythTV install under vanilla Ubuntu) in the past and had a lot of headaches.  This time things are moving along comparatively well.  IT seems to be talking to the backend, schedulesdirect.org has updated.  LiveTV presents a problem.  I get a similar set of error messages to those posted on this forum.  The link to my front end log is [[COLOR="Blue"]**here**[/COLOR]]("http://mythbuntu.pastebin.com/CbmLxtHv"). 

Here is what I believe to be the pertinent part of that log:
```

2010-10-13 23:11:48.292 TV: Attempting to change from None to WatchingLiveTV
2010-10-13 23:11:48.298 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-10-13 23:11:48.301 Using protocol version 23056
2010-10-13 23:11:48.424 Spawning LiveTV Recorder -- begin
2010-10-13 23:11:55.427 MythSocket(ffffffffa88f7108:49): readStringList: Error, timed out after 7000 ms.
2010-10-13 23:11:55.427 RemoteEncoder::SendReceiveStringList(): No response.
2010-10-13 23:11:55.428 Spawning LiveTV Recorder -- end
2010-10-13 23:11:55.429 GetEntryAt(-1) failed.
2010-10-13 23:11:55.432 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-10-13 23:11:55.432 TV Error: HandleStateChange(): LiveTV not successfully started
2010-10-13 23:11:55.432 We have a RingBuffer
2010-10-13 23:11:55.494 TV Error: LiveTV not successfully started
2010-10-13 23:12:06.898 Deleting UPnP client...
```

I made sure that the mythtv user (in fact all users) had permissions to write to directories 
```
sudo chmod -R 777 /var/lib/mythtv/
```

I set the starting channel to 4 in the backend setup.  4 is a channel that was auto detected and mapped during initial probe.

Any Ideas?    I'll know if a recording worked in the morning.

---

