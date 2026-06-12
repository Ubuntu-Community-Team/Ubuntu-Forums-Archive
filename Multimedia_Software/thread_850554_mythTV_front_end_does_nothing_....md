---
title: "mythTV front end does nothing ..."
date: 2008-07-05
forum: Multimedia Software
---

### Post by Ck.asdf on 2008-07-05
Hello, I got a lot of progress today compared to the last time I tried getting mythTV working, but I still ran into road blocks.

I got the back end working properly, thanks to this guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I started on the front end, had a small hitch when trying to set up the Video Source (then tried schedulesdirect.org which gives a free trial), and eventually, had everything set up, I think, to work.

I did everything it asked, and once "mythfilldatabase" was finished, I ran the front end, which opened, etc.  But when I chose "Watch TV" the screen flashed black, then returned to the front end menu.  I chose it again, and it did it again, on and on, and never showed tv.

I have a Hauppauge WinTV PVR 150, and it works great in Windows, but I'd like to get it in Linux (one of the few reasons I need Windows right now).
I tried in one console running "cat /dev/video0 > tv0" in one console, and then in another, running "mplayer /dev/tv0" and I got one channel ... with no ability to change channel.  But this shows that it works, because I get both video and audio.


Suggestions? Any more info you need?
I'm using Ubuntu 8.04 64bit
I have all updates ...


Per a suggestion I read to run the front end in the console, I did, and got some output when I chose "Watch TV."  It is as follows:

```
2008-07-05 20:27:23.099 TV: Attempting to change from None to WatchingLiveTV
2008-07-05 20:27:23.100 Using protocol version 40
2008-07-05 20:27:24.267 GetEntryAt(-1) failed.
2008-07-05 20:27:24.268 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-07-05 20:27:24.268 TV Error: LiveTV not successfully started
2008-07-05 20:27:24.269 TV Error: LiveTV not successfully started
2008-07-05 20:27:24.306 TV: Deleting TV Chain in destructor
2008-07-05 20:27:24.309 DPMS Deactivated 
2008-07-05 20:27:24.309 DPMS Reactivated.
```


Thanks for any suggestions!
-Chris

---

### Post by Ck.asdf on 2008-07-05
Okay, I've been reading, and I've looked in the /var/log/mythtv location and read some errors about the backend and frontend, so I fixed some of those ... so now, instead of a quick second of black screen after choosing to watch tv, it's several seconds of black, and then back to the menu.  obviously, I made it better or worse ...

Now, my backend log says (near the end, when it says it's trying to start):

```
2008-07-05 21:22:12.059 TVRec(1): Changing from None to WatchingLiveTV
2008-07-05 21:22:12.085 TVRec(1): HW Tuner: 1->1
2008-07-05 21:22:12.198 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2008-07-05 21:22:13.372 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-05 21:22:13.439 NVR(/dev/video0): Won't work with the streaming interface, falling back
strange error flushing buffer ...
VIDIOCGMBUF:: Invalid argument
2008-07-05 21:22:53.448 TVRec(1): Changing from WatchingLiveTV to None
2008-07-05 21:22:53.459 Finished recording 48 Hours Mystery "No Way Out": channel 1002
2008-07-05 21:24:23.083 Expiring 0 MBytes for 1002 @ Sat Jul 5 21:00:00 2008 => 48 Hours Mystery "No Way Out"
```


The frontend log shows:

```
Starting mythfrontend.real..
2008-07-05 12:11:39.163 New DB connection, total: 2
2008-07-05 12:11:39.164 Connected to database 'mythconverg' at host: localhost
2008-07-05 12:11:39.167 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-05 12:11:39.167 Enabled verbose msgs:  important general
2008-07-05 12:11:39.852 Primary screen 0.
2008-07-05 12:11:39.853 Using screen 0, 1024x768 at 0,0
2008-07-05 12:11:39.855 Switching to square mode (G.A.N.T)
2008-07-05 12:11:39.900 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-05 12:11:39.901 lirc_init failed for mythtv, see preceding messages
2008-07-05 12:11:39.902 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ck/.mythtv/joystickmenurc
2008-07-05 12:11:41.271 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-07-05 12:11:41.366 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-05 12:11:41.452 Registering Internal as a media playback plugin.
2008-07-05 12:11:45.850 Connecting to backend server: 192.168.1.2:6543 (try 1 of 5)
2008-07-05 12:11:45.863 Using protocol version 40
2008-07-05 12:11:45.876 TV: Attempting to change from None to WatchingLiveTV
2008-07-05 12:11:45.877 Using protocol version 40
2008-07-05 12:11:47.244 GetEntryAt(-1) failed.
2008-07-05 12:11:47.246 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-07-05 12:11:47.247 TV Error: LiveTV not successfully started
2008-07-05 12:11:47.247 TV Error: LiveTV not successfully started
2008-07-05 12:11:47.293 TV: Deleting TV Chain in destructor
2008-07-05 12:11:47.298 DPMS Deactivated
2008-07-05 12:11:47.300 DPMS Reactivated.
2008-07-05 12:11:52.698 Deleting UPnP client...
```

---

### Post by Ck.asdf on 2008-07-08
suggestions?

---

### Post by Scorpuk on 2008-07-08
Were you able to scan for channels with mythtv?

Could you set mythtv to record a channel and see what happens?

If it does start to record, then try viewing that recording.

---

### Post by Ck.asdf on 2008-07-11
I'm not sure if I need to wait until the recording is over to watch it, but I started the recording a few minutes ago, and then tried to view it, but the screen went blank, and went back, like with live tv.  There were several other recordings in there I know I didn't tell it to record, but when I tried playing them, it said it couldn't find the recordings. 

I know the tuner is working by itself at least, because I can use "totem /dev/video0" and it will play the tv, and then using ivtv-utils, I can change the channel.  But I'd like to get myth tv set up, if I can ...

---

### Post by SupraGuy on 2010-01-31
> **Ck.asdf said:**
> I did everything it asked, and once "mythfilldatabase" was finished, I ran the front end, which opened, etc. But when I chose "Watch TV" the screen flashed black, then returned to the front end menu. I chose it again, and it did it again, on and on, and never showed tv.
I'm having the same issues. Mythbuntu installed on 9.04 with a Hauppage HVR-1600 tuner.

---

### Post by sports.car.guy on 2010-01-31
> **SupraGuy said:**
> I'm having the same issues. Mythbuntu installed on 9.04 with a Hauppage HVR-1600 tuner.


I can tell you what is happening with the black recordings, at least in my case it was this. It is an initialization problem. The packages on the Ubuntu repositories made this problem a big one for me. I had to keep the card constantly initialized for it to work without a black screen. I ended up setting up both my MythTV clients and server to use the Mythbuntu nightly builds of the stable branch 0.22. I still have it give the black screen in recording occasionally but that is because I haven't switch to the card as an input since rebooting the server. Once I view TV off it, it records fine.

Another thing 9.04 does not have the firmware necessary for the 1600, did you install it according to the linuxtv.org wiki? It is the v4l's website and they have a lot of documentation on getting supported cards up and running.

---

