---
title: "Clicking &quot;Watch TV&quot; doesn't do anything"
date: 2008-07-13
forum: Mythbuntu
---

### Post by mstralka on 2008-07-13
I have a Hauppauge PVR 250 and have it configured in mythbackend as MPEG2 card with my comcast cable connection (not digital).  I confirmed that the channels were downloaded from SchedulesDirect by looking at the 'programs' table in the database.  

I loaded the ivtv module manually and confirmed that it is capturing by running:
```

modprobe ivtv (added to /etc/modules now)
cat /dev/video0 > test.mpg

```

When I click "Watch TV", the screen goes black for a second, then it returns to the main frontend screen - I never see the TV.  However, it also seems to record for a second and puts an entry into the Media Library, but it says the file is not available.

Any ideas why I can't get myth to show the TV?
Thanks!

---

### Post by mstralka on 2008-07-13
More Details:
Ubuntu Hardy Heron

Here's the mythfrontend.log entries:
```

2008-07-13 08:24:03.109 Registering Internal as a media playback plugin.
2008-07-13 08:24:10.673 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-13 08:24:10.675 Using protocol version 40
2008-07-13 08:24:10.702 TV: Attempting to change from None to WatchingLiveTV
2008-07-13 08:24:10.703 Using protocol version 40
2008-07-13 08:24:11.938 GetEntryAt(-1) failed.
2008-07-13 08:24:11.941 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-07-13 08:24:11.941 TV Error: LiveTV not successfully started
2008-07-13 08:24:11.941 TV Error: LiveTV not successfully started
2008-07-13 08:24:11.953 TV: Deleting TV Chain in destructor
2008-07-13 08:24:11.969 DPMS Deactivated 
2008-07-13 08:24:11.970 DPMS Reactivated.

```

---

### Post by mstralka on 2008-07-13
Solved the problem - the 'mythtv' user did not have write permissions to the storage directory.  I changed the permissions on the storage directory and now Watch TV works!

---

### Post by k420 on 2008-07-13
would you elaborate please on how you did that:guitar:

---

### Post by tgm4883 on 2008-07-13
> **k420 said:**
> would you elaborate please on how you did that:guitar:

Common problem.  Find your storage directory that you setup in step 6 of mythtv-setup and make it owned by the mythtv user.  It also shouldn't be in your home directory

```
sudo chown mythtv:mythtv /recording/directory 
sudo chmod 775 /recording/directory
```

---

