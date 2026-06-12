---
title: "Mythtv does not initialize correctly"
date: 2008-07-12
forum: Multimedia Software
---

### Post by duxducis on 2008-07-12
I have followed the instructions at [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop) to install mythtv on my Ubuntu 8.04 system (cant find any more recent docs). Everything works normal until I try to launch live tv at which point I get a black screen for a second and then it returns to the frontend. I cant for the life of me figure out whats going wrong. Here is the command line output.

electron@electron:~$ mythtv 
2008-07-11 23:51:36.492 Using runtime prefix = /usr, libdir = /usr/lib 
2008-07-11 23:51:36.513 XScreenSaver support enabled 
2008-07-11 23:51:36.514 DPMS is active. 
2008-07-11 23:51:36.516 Empty LocalHostName. 
2008-07-11 23:51:36.516 Using localhost value of electron 
2008-07-11 23:51:36.553 New DB connection, total: 1 
2008-07-11 23:51:36.564 Connected to database 'mythconverg' at host: localhost 
2008-07-11 23:51:36.567 Closing DB connection named 'DBManager0' 
2008-07-11 23:51:36.570 Primary screen 0. 
2008-07-11 23:51:36.572 Connected to database 'mythconverg' at host: localhost 
2008-07-11 23:51:36.576 Using screen 0, 1440x900 at 0,0 
2008-07-11 23:51:36.994 max_width: 1440 max_height: 1024 
2008-07-11 23:51:36.998 Primary screen 0. 
2008-07-11 23:51:37.000 Using screen 0, 1440x900 at 0,0 
2008-07-11 23:51:37.009 Switching to square mode (G.A.N.T) 
2008-07-11 23:51:37.094 Using the Qt painter 
mythtv: could not connect to socket 
mythtv: No such file or directory 
2008-07-11 23:51:37.096 lirc_init failed for mythtv, see preceding messages 
2008-07-11 23:51:37.097 JoystickMenuClient Error: Joystick disabled - Failed to read /home/electron/.mythtv/joystickmenurc 
2008-07-11 23:51:38.847 New DB connection, total: 2 
2008-07-11 23:51:38.848 Connected to database 'mythconverg' at host: localhost 
2008-07-11 23:51:38.915 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5) 
2008-07-11 23:51:38.918 Using protocol version 40 
2008-07-11 23:51:38.941 TV: Attempting to change from None to WatchingLiveTV 
2008-07-11 23:51:38.944 Using protocol version 40 
2008-07-11 23:51:40.245 GetEntryAt(-1) failed. 
2008-07-11 23:51:40.250 EntryToProgram(0@Wed Dec 31 16:00:00 1969) failed to get pginfo 
2008-07-11 23:51:40.250 TV Error: LiveTV not successfully started 
2008-07-11 23:51:40.251 TV Error: LiveTV not successfully started 
2008-07-11 23:51:40.300 TV: Deleting TV Chain in destructor 
Mutex destroy failure: Device or resource busy

---

### Post by wolfen69 on 2008-07-12
what kind of tv tuner card do you have? did you pick the right modules during setup?

---

### Post by duxducis on 2008-07-12
I have a Hauppauge PVR-150 set to mpeg-2. During mythtv setup it scans for channels successfully. I tried mplayer and got reception however it was very choppy video. As for packages I installed Mythtv Control Center and let it install what it wanted (Had the same problem when I installed mythtv from synaptic) On another note I tried using mythbuntu 8.04 and had the same issue. Would it be worth trying to install from source?

Edit:
I have come to the conclusion that somthing was wrong with my flgrx driver as it now works fine using my onboard Nvidia card

---

