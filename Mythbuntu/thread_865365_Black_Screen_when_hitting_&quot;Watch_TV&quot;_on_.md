---
title: "Black Screen when hitting &quot;Watch TV&quot; on Mythbuntu 8.04"
date: 2008-07-20
forum: Mythbuntu
---

### Post by Mizled on 2008-07-20
Hello,

I have a Hauppauge PVR-500 and every time I hit "Watch TV" on Mythbuntu Frontend it goes to a black screen then hangs for about 30seconds and goes back to the main menu.

Here is my Frontend/Backend error log files...


Frontend
```
2008-07-20 14:16:21.428 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-20 14:16:21.550 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-20 14:16:21.723 Registering Internal as a media playback plugin.
2008-07-20 14:16:32.980 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-20 14:16:32.982 Using protocol version 40
2008-07-20 14:17:34.979 TV: Attempting to change from None to WatchingLiveTV
2008-07-20 14:17:34.980 Using protocol version 40
2008-07-20 14:17:36.408 DPMS Deactivated
2008-07-20 14:18:16.347 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-07-20 14:18:16.347 TV Error: LiveTV not successfully started
2008-07-20 14:18:16.362 TV: Deleting TV Chain in destructor
2008-07-20 14:18:16.364 DPMS Reactivated.
2008-07-20 14:18:57.005 Deleting UPnP client...

```

Backend
```
008-07-20 14:15:30.727 Seem to be woken up by USER
2008-07-20 14:16:32.982 MainServer::HandleAnnounce Monitor
2008-07-20 14:16:32.987 adding: ubuntu as a client (events: 0)
2008-07-20 14:16:32.989 MainServer::HandleAnnounce Monitor
2008-07-20 14:16:32.990 adding: ubuntu as a client (events: 1)
2008-07-20 14:16:47.535 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 14:17:34.980 MainServer::HandleAnnounce Playback
2008-07-20 14:17:35.000 adding: ubuntu as a client (events: 0)
2008-07-20 14:17:35.010 TVRec(3): Changing from None to WatchingLiveTV
2008-07-20 14:17:35.025 TVRec(3): HW Tuner: 3->3
2008-07-20 14:17:36.297 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-20 14:17:36.302 NVR(/dev/video0) Error: Unknown audio codec
2008-07-20 14:17:36.326 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-20 14:17:36.332 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-20 14:18:16.379 TVRec(3): Changing from WatchingLiveTV to None
2008-07-20 14:18:16.392 Finished recording Unknown: channel 1002
QDateTime::fromString: Parameter out of range
2008-07-20 14:20:47.563 Expiring 0 MBytes for 1002 @ Sun Jul 20 14:17:35 2008 => Unknown
2008-07-20 14:21:31.128 Using runtime prefix = /usr, libdir = /usr/lib

```

Any suggestions? :confused:

---

### Post by nickrout on 2008-07-20
three thoughts.

1. there has been a recent change on some systems that people have reported their pvr500 has moved from /dev/video0 and /dev/video1 to /dev/video1 and /dev/video2. Check what /dev/video files exist.

2. this line sticks out "2008-07-20 14:17:36.297 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now."

Have you followed that advice? for that matter a pvr500 shouldn't be set up as a software encoder, it has its own built in hardware encoder which encldes to mpeg2. Did you set it up right in the first place?

3. You can increase logging level. run mythfrontend --help for details.

---

### Post by tgm4883 on 2008-07-21
Did you set it up as a PVR device in mythtv-setup or as something else?

---

### Post by Chris Rogiers on 2008-09-22
A few months ago I had a running MythBuntu system. Then I had a hardware failure which required me to swap out a hard disk, and then re-install from the start. I used MythBuntu 8.04. I had the same symptoms you described: Watch TV gives black screen and returns to menu.

I tried all kinds of things, but to no avail. Typically I installed webmin (load the .deb file from the webmin site and use GDebi installer to have all dependencies met). Using webmin I checked out the MySQL permissions, did some really unsafe things like granting all privileges to just about anyone from anywhere, to no avail.

Then I downloaded MythBuntu 8.04.1 and installed that. Used Standard Installation. No messing afterwards with MySQL and used suggested
settings on most screens. And no 'Watch TV' either!

I also looked for installation documentation, none for 8.04 or 8.04.1 but some older versions to look for ideas. There was nothing that directly addressed the same problem nor could be literary applied. It give me some ideas though, which foolishly enough I applied both, hence not knowing what made the real difference.

This is what I did:

 - /etc/mysql/my.cnf : commented out bind-address line with leading #
   followed by a sudo /etc/init.d/mysql restart

 - created a /home/myusername/mythtv directory and set user and
    group both to mythtv, then made sure that this directory was
    also writable by group, after which I went into the backend setup
    under 'Storage Directories' and added that directory to it

And POOF, 'Watch TV' was operational.

Maybe you want to try it.

Chris R.

PS 
   If like me, you cannot or will not remember the command line
   commands, in this case chmod and chown, and always forget
   where you last saw their explanation, you may want to have a
   look at using mc (Midnight Commander, an ncurses based two
   pane file manager and so much more) in a terminal or some
   GUI version of it (i.e. gnome-commander). It is inspired by
   the Norton Commander from the early 90's. All available 
   in Ubuntu repositories.

---

### Post by MartinusEx on 2008-09-22
Hi 
one point to look for is the storage directories in the mythbuntu control centre.
Especially LiveTV needs a directory since the live stream is buffered there.

point the Live TV directory to an existing path which has the appropriate rights (See posting above)

if nothing else is wrong this should do it.

thunar wich comes with mythbuntu started with sudo helps do the commandline work of chmod etc. pp.
sudo thunar 
(be aware that what you do is under super user rights then, you can kill all good things)

rgds

Martinus

---

### Post by verylazyguy on 2008-10-31
I had the same problem and all I had to do to fix it was change the permissions on the livetv recording folder to be owned by the mythtv user and mythtv group.  Sometimes I hate permissions.

---

