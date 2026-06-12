---
title: "Video Issues, Possible Database Issues"
date: 2008-12-28
forum: Mythbuntu
---

### Post by novice_geek on 2008-12-28
Hello all,

I am in need of some serious help!  I've been working on this stupid thing all day, and I just FINALLY got to the step where I can test mythtv-frontend.  As you might guess, that doesn't work.  I am running Mythbuntu 8.10 with a PVR-350 card that will (hopefully) control a DirecTV D10 SD Receiver.  When I did this install last night, it didn't create the mythconverg database.  I reinstalled today after a few hours of beating my head on the case, and the same thing happened.  I finally was able to create the database after I found a hit somewhere on here.  After that, I fought with the storage directories (One of my Linux-RAIDs didn't mount at all).

After that was settled (mounted and chmodded the storage directories to 777... hopefully that is right), I went to Mythtv-frontend and went to "Watch TV", and all it did was flash once and return to the menu.  I changed some tuner-card settings, and now all it will do is show a blank screen for around one minute, and then it will go back to the menu.  I can't get any menus to come up, and hitting escape doesn't do a thing.

One more thing...  I have a Schedules-Direct subscription, and when I run mythfilldatabase, it does its thing for a few minutes, but it doesn't seem to keep any of the data it downloads.  Even in the information menu, it will acknowledge that it ran, but it will say right below that that there is no guide information and ask if I have ran mythfilldatabase.:confused:

Sorry about the book above, but I'm hoping that someone will read this and the problem will be obvious to them.  Please let me know if you guys need anything else.  Also, I'm pretty much a n00b, so any commands are greatly appreciated.

TIA!

---

### Post by ian dobson on 2008-12-29
Hi,

What do you see in your log files? The log files are usually in /var/log/mythtv.

Have you added any channels to your system? YOu need to define the channels you want to use firstly in mythtv-setup so that myth "knows" what frequency the channels have and in your XMLTV grabber (Schedules-Direct).

Mythtv is not tat easy to setup (Mythbuntu has made it much easier) but when it's running it's a really powerful system. When I think my backend has 2 DVB-C tuners and 2 Analog tuners and grabs EPG data from "all over the place" but never gets confused.

Regards
Ian Dobson

---

### Post by davidgeeee on 2008-12-29
Mythfilldatabase takes about 10-15 minutes on my system with a 3Mb/sec internet connection.  You'll have plenty of time to read what it is doing in the command window.  If it goes fast, you probably have a typo in your settings and the script give up on collecting the information.

---

### Post by novice_geek on 2008-12-29
> **ian dobson said:**
> Hi,

What do you see in your log files? The log files are usually in /var/log/mythtv.

Have you added any channels to your system? YOu need to define the channels you want to use firstly in mythtv-setup so that myth "knows" what frequency the channels have and in your XMLTV grabber (Schedules-Direct).

Mythtv is not tat easy to setup (Mythbuntu has made it much easier) but when it's running it's a really powerful system. When I think my backend has 2 DVB-C tuners and 2 Analog tuners and grabs EPG data from "all over the place" but never gets confused.

Regards
Ian Dobson

I will take a look at my log files later when I get a chance tonight.  As for channels, I do have a few defined, although it's a bit tough working with S-Video and channels (IMO).



Davidgeeee,
My mythfilldatabase takes about the same time to run, so I am assuming it is working.  I see no errors, and everything looks like it did with my old installation (which worked to a slight degree).

Thanks All!

---

### Post by novice_geek on 2008-12-31
Ok, here's my analysis of the logs.
[B]
Mythbackend.log.1[/B]
2008-12-29 07:39:25.785 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-12-29 07:39:25.802 UPnpMedia: BuildMediaMap Done. Found 0 objects
Nowhere in this or mythbackend.log is /stor/[DIRECTORY] mentioned.  Storage directories should ONLY be in /stor/


**mythbackend.log.2  [COLOR=Red](Which has 48,308 lines of text!)[/COLOR]**
2008-12-29 06:39:07.615 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.

2008-12-29 06:39:38.535 MainServer::HandleAnnounce Playback
2008-12-29 06:39:38.537 adding: Harrison-NB-Ubuntu as a client (events: 0)
2008-12-29 06:39:38.543 TVRec(1): Changing from None to WatchingLiveTV
2008-12-29 06:39:38.555 TVRec(1): HW Tuner: 1->1
2008-12-29 06:39:38.647 Channel(/dev/video0) Warning: You have not set an external channel changing
                        script for a composite or s-video input. Channel changing will do nothing.
2008-12-29 06:39:39.765 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Pro$
2008-12-29 06:39:39.784 NVR(/dev/video0) Error: Unknown audio codec
2008-12-29 06:39:39.804 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-12-29 06:39:39.805 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-12-29 06:39:39.862 MainServer::HandleAnnounce Playback
2008-12-29 06:39:39.924 adding: Harrison-NB-Ubuntu as a client (events: 0)

2008-12-29 06:41:58.452 New DB DataDirect connection

2008-12-29 06:42:11.363 MainServer::HandleAnnounce Playback
2008-12-29 06:42:11.385 adding: Harrison-NB-Ubuntu as a client (events: 0)
2008-12-29 06:42:11.392 MainServer::HandleAnnounce FileTransfer
2008-12-29 06:42:11.394 adding: Harrison-NB-Ubuntu as a remote file transfer
2008-12-29 06:42:11.398 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2008-12-29 06:42:11.402 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2008-12-29 06:42:11.405 RingBuffer::RingBuffer(): Failed to open remote file ()
2008-12-29 06:42:11.571 MainServer::HandleAnnounce Playback



**mythfrontend.log.1**
2008-12-28 21:01:15.940 JoystickMenuClient Error: Joystick disabled - Failed to read /home/harrison/.mythtv/j$
2008-12-28 21:01:17.089 Loading from: /usr/share/mythtv/themes/MythCenter/base.xml
2008-12-28 21:01:17.179 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-28 21:01:17.308 Registering Internal as a media playback plugin.
2008-12-28 21:01:17.393 No theme dir: /home/harrison/.mythtv/themes/MythCenter
2008-12-28 21:01:19.743 Connecting to backend server: 192.168.1.132:6543 (try 1 of 5)
2008-12-28 21:01:19.745 Using protocol version 40
2008-12-28 21:01:19.773 TV: Attempting to change from None to WatchingLiveTV
2008-12-28 21:01:19.774 Using protocol version 40
2008-12-28 21:01:21.082 DPMS Deactivated
2008-12-28 21:02:01.048 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-12-28 21:02:01.048 TV Error: LiveTV not successfully started
2008-12-28 21:02:01.136 TV: Deleting TV Chain in destructor
2008-12-28 21:02:01.142 DPMS Reactivated.
2008-12-28 21:02:08.456 TV: Attempting to change from None to WatchingLiveTV
2008-12-28 21:02:08.457 Using protocol version 40
2008-12-28 21:02:09.865 DPMS Deactivated
2008-12-28 21:02:49.769 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-12-28 21:02:49.790 TV Error: LiveTV not successfully started


That's about all that I see that is of use.  If you guys need a copy of all of those logs, please let me know.

Also, Harrison-NB-Ubuntu refers to a remote frontend and myth or 192.168.1.132 is the actual frontend/backend combination box.

Thanks for all of your help!

---

### Post by novice_geek on 2009-01-02
Bump.

Sorry to be a pain, but I'm ripping my hair out over this.

Thanks again!

---

### Post by EasyRiderOnTheStorm on 2009-01-06
> **novice_geek said:**
> 
2008-12-29 07:39:25.785 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-12-29 07:39:25.802 UPnpMedia: BuildMediaMap Done. Found 0 objects
Nowhere in this or mythbackend.log is /stor/[DIRECTORY] mentioned.  Storage directories should ONLY be in /stor/


Perhaps the frontend is still configured to use the default /var/lib/mythtv/videos folder. You should check the path setting under Settings -> MythVideo Settings.

> **novice_geek said:**
> 
2008-12-29 06:39:38.647 Channel(/dev/video0) Warning: You have not set an external channel changing script for a composite or s-video input. Channel changing will do nothing.
2008-12-29 06:39:39.765 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Pro$
2008-12-29 06:39:39.784 NVR(/dev/video0) Error: Unknown audio codec


It seems you'll need a channel switching script for your receiver (but that has nothing to do with the problem). It also seems you have no encoder configured (in Settings->TV Settings->Recording profiles, "encoders" or something like that); you have to set one up (even if it seems already set up when you look at it, just go clicking all the way to the "Finish"), then associate that encoder profile as the default encoding of your (s-video) input, under the input settings. If you succeed with that, live TV should start working (with whatever your external receiver is set to at the moment)

> **novice_geek said:**
> 
2008-12-29 06:41:58.452 New DB DataDirect connection

2008-12-29 06:42:11.363 MainServer::HandleAnnounce Playback
2008-12-29 06:42:11.385 adding: Harrison-NB-Ubuntu as a client (events: 0)
2008-12-29 06:42:11.392 MainServer::HandleAnnounce FileTransfer
2008-12-29 06:42:11.394 adding: Harrison-NB-Ubuntu as a remote file transfer
2008-12-29 06:42:11.398 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2008-12-29 06:42:11.402 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2008-12-29 06:42:11.405 RingBuffer::RingBuffer(): Failed to open remote file ()


I don't use DataDirect (but xmltv grabbers instead) so I'm just guessing here, but I have the impression that the server name/port is still not set up correctly somewhere - as if the guide grabbing would go OK, but mythfilldatabase would not know how to connect to the database to save it. I'm not sure where that setting would be, but you should look around in the mythbackend/frontend settings, looking for an unconfigured database host/portnumber. You could also check that /home/mythtv/.mythtv/mysql.txt exists, and the variables DBHostName, DBUserName, DBType, DBName and DBPassword in it are set properly (and the file has proper read rights).

The frontend logs seem to be of no consequence here, they just reflect the backend problem.

PS: You should also make sure that you do have some channels configured, and that they have DataDirect (or whatever is appropriate) set as their guide source.

---

### Post by novice_geek on 2009-01-08
Thanks for your input.  I'll give them a try in the morning hopefully and report back what I find.

---

### Post by rhpot1991 on 2009-01-08
It seems that your tuner is timing out, you need to get a channel changer script in place.  Alternately to check things I'd imagine you could run a cable out of your satellite box to the coax input and just try to record channel 3.

As far as the recording directories go here is the rule:
If you try to watch tv and are greeted with a blank screen and a return to the menu then please check the permissions on your recording directory. It should be owned by mythtv:mythtv, have permissions of 775, and not be inside your home directory

---

### Post by novice_geek on 2009-01-11
> **rhpot1991 said:**
> It seems that your tuner is timing out, you need to get a channel changer script in place.  Alternately to check things I'd imagine you could run a cable out of your satellite box to the coax input and just try to record channel 3.

As far as the recording directories go here is the rule:
If you try to watch tv and are greeted with a blank screen and a return to the menu then please check the permissions on your recording directory. It should be owned by mythtv:mythtv, have permissions of 775, and not be inside your home directory

I removed all of the sources and added the coaxial input and set it up for channel 3 ONLY.  There is no channel changer script or anything.  It should think it's on a CATV setup.  I'm still getting the same issues as before.

I did have the permissions set to 777, but I changed them to 775 and changed the owner to mythtv:mythtv again (just to be sure) and it still isn't working.

Also, on a side-note, has anyone had any luck with the directv.pl script and the DirecTV D10-200 receivers?  I can't get mine to work (using serial to 4P4C adapter/cable that I created).  The cable works under Windows, so I'm sure it's not the cable.

Thanks again for all of the input.

---

