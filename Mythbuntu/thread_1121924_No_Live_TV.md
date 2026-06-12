---
title: "No Live TV"
date: 2009-04-10
forum: Mythbuntu
---

### Post by Billsputters on 2009-04-10
I can't watch TV. Hit the button, get a brief flash and back to the menu.

I've read that it might be down to no access to disc space, but I've checked this and it seems OK.

Any other avenues I should explore.

---

### Post by iponeverything on 2009-04-10
so it worked and then stoped at some point? -- (my mind reading skills are getting rusty)

what are you seeing in /var/log/mythtv/mythfrontend.log and /var/log/mythtv/mythbackend.log

---

### Post by Billsputters on 2009-04-10
Sorry, should have specified. I've never managed to get live TV to work.

The logs are as follows

Backend
```

2009-04-11 01:33:56.429 Using runtime prefix = /usr
2009-04-11 01:33:56.495 Empty LocalHostName.
2009-04-11 01:33:56.509 Using localhost value of mythtv-be
2009-04-11 01:33:56.588 New DB connection, total: 1
2009-04-11 01:33:56.620 Connected to database 'mythconverg' at host: localhost
2009-04-11 01:33:56.642 Closing DB connection named 'DBManager0'
2009-04-11 01:33:56.665 Connected to database 'mythconverg' at host: localhost
2009-04-11 01:33:56.666 New DB connection, total: 2
2009-04-11 01:33:56.685 Connected to database 'mythconverg' at host: localhost
2009-04-11 01:33:56.734 Current Schema Version: 1214
Starting up as the master server.
2009-04-11 01:33:57.856 New DB connection, total: 3
2009-04-11 01:33:57.864 Connected to database 'mythconverg' at host: localhost
2009-04-11 01:33:58.057 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-04-11 01:33:58.068 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-04-11 01:33:58.144 New DB scheduler connection
2009-04-11 01:33:58.182 Connected to database 'mythconverg' at host: localhost
2009-04-11 01:33:58.245 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-04-11 01:33:58.267 Main::Registering HttpStatus Extension
2009-04-11 01:33:58.284 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-04-11 01:33:58.285 Enabled verbose msgs:  important general
2009-04-11 01:33:58.337 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-04-11 01:34:01.203 Reschedule requested for id -1.
2009-04-11 01:34:01.316 Scheduled 0 items in 0.1 = 0.10 match + 0.01 place
2009-04-11 01:34:01.327 Seem to be woken up by USER
2009-04-11 01:35:18.204 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-04-11 01:37:11.064 MainServer::HandleAnnounce Monitor
2009-04-11 01:37:11.068 adding: mythtv-be as a client (events: 0)
2009-04-11 01:37:11.069 MainServer::HandleAnnounce Monitor
2009-04-11 01:37:11.070 adding: mythtv-be as a client (events: 1)
2009-04-11 01:37:11.073 MainServer::HandleAnnounce Playback
2009-04-11 01:37:11.088 adding: mythtv-be as a client (events: 0)
2009-04-11 01:37:11.089 TVRec(1): Changing from None to WatchingLiveTV
2009-04-11 01:37:11.094 TVRec(1): HW Tuner: 1->1
2009-04-11 01:37:11.101 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-04-11 01:37:11.101 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-04-11 01:37:11.102 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-04-11 01:37:11.102 TVRec(1): Changing from WatchingLiveTV to None

```

and the Frontend

```
Starting mythfrontend.real..
2009-04-11 01:34:11.690 New DB connection, total: 2
2009-04-11 01:34:11.691 Connected to database 'mythconverg' at host: localhost
2009-04-11 01:34:11.692 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-04-11 01:34:11.692 Enabled verbose msgs:  important general
2009-04-11 01:34:11.747 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-04-11 01:34:14.124 No theme dir: /home/richard/.mythtv/themes/blootubelite-wide
2009-04-11 01:34:14.125 Primary screen 0.
2009-04-11 01:34:14.125 Using screen 0, 720x576 at 0,0
2009-04-11 01:34:14.126 No theme dir: /home/richard/.mythtv/themes/blootubelite-wide
2009-04-11 01:34:14.126 Switching to wide mode (blootubelite-wide)
2009-04-11 01:34:14.267 Using the Qt painter
2009-04-11 01:34:14.267 JoystickMenuClient Error: Joystick disabled - Failed to read /home/richard/.mythtv/joystickmenurc
2009-04-11 01:34:14.268 lirc init success using configuration file: /home/richard/.mythtv/lircrc
2009-04-11 01:34:16.356 Specified base font 'medium' does not exist for font small
2009-04-11 01:34:16.356 Specified base font 'medium' does not exist for font medium
2009-04-11 01:34:16.356 Specified base font 'medium' does not exist for font large
2009-04-11 01:34:16.357 Specified base font 'medium' does not exist for font clock
2009-04-11 01:34:16.357 Loading from: /usr/share/mythtv/themes/blootubelite-wide/base.xml
2009-04-11 01:34:16.388 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-04-11 01:34:16.439 Registering Internal as a media playback plugin.
2009-04-11 01:34:16.720 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-04-11 01:34:17.028 Failed to run 'cdrecord --scanbus'
2009-04-11 01:34:17.031 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-04-11 01:34:17.035 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-04-11 01:34:17.054 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2009-04-11 01:34:17.223 NetworkControl: Listening for remote connections on port 6546
2009-04-11 01:34:17.224 No theme dir: /home/richard/.mythtv/themes/blootubelite-wide
2009-04-11 01:37:11.063 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-04-11 01:37:11.064 Using protocol version 40
2009-04-11 01:37:11.072 TV: Attempting to change from None to WatchingLiveTV
2009-04-11 01:37:11.073 Using protocol version 40
2009-04-11 01:37:11.104 GetEntryAt(-1) failed.
2009-04-11 01:37:11.109 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2009-04-11 01:37:11.109 TV Error: LiveTV not successfully started
2009-04-11 01:37:11.110 TV Error: LiveTV not successfully started
2009-04-11 01:37:11.202 TV: Deleting TV Chain in destructor
2009-04-11 01:37:11.205 DPMS Deactivated 
2009-04-11 01:37:11.206 DPMS Reactivated.
```

EntryTo Program Jan 1 1970! I knew MythTV alters the way you watch TV, but going back nearly 40 years is amazing! That might be something to do with it. But where?

---

### Post by iponeverything on 2009-04-10
Does the recording part work?

Anyway -- here is the problem. It is configured to start at channel 1 and there is no channel 1.  Go into mythtv-setup and change it start at another channel.

```
2009-04-11 01:37:11.101 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-04-11 01:37:11.102 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None

```

---

### Post by Billsputters on 2009-04-11
I've tried different channels with no luck.

I'm using a PVR 150 coming in on the composite input - so what channel should I use?

---

### Post by Billsputters on 2009-04-13
Bumpty Bump

I am at a dead end here. I've taken to reinstalling and left everything as Mythbuntu defaults. I can access the storage space in /var/.. etc all ok - I can import MP3's.

I am running composite in with an external tuner so no channel changinh takes place within the Myth system. But I am still getting this non complance with 'Watch TV' a quick flash to black and then the main menu again. It seems to be coupled with the TV channel error outlined above. I have set the start channel to 1 (in menu 4 of BE setup). I really don't know where to go from here. Someone, somewhere must be running the same setup and had a functioning system. How can I watch TV?

---

### Post by nickrout on 2009-04-14
its not really going to work unless you have set up an epg etc. Have you done that?

In fact have you worked your way through the whole mythtv-setup thing?

---

### Post by Billsputters on 2009-04-14
Yep, been right through the setup.

Have loaded a programme guide, via XMLTV, using the Freeview via Sky setup, which is what I am testing the system on. I can edit the channel setup via Mythweb. As far as I can see I have missed nothing.

The only thing I can think of is that as I've set it up with Sky Freeview Channels, I don't have a IR blaster configured to change the channels yet, that was going to be left as a manual operation.

---

