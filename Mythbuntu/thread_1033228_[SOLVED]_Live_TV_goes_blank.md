---
title: "[SOLVED] Live TV goes blank"
date: 2009-01-07
forum: Mythbuntu
---

### Post by RonPDX on 2009-01-07
Good morning everyone, 

I finally have everything configured (or so I thought) and when I go to watch live tv the screen goes blank for 5-10 seconds. Here is my front end log if that helps. The problem appears to be at the bottom and from what I can find it may be a database issue but I really don't know for sure.

Thanks, 

Ron

```
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-01-07 02:20:59.502 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-07 02:20:59.504 Using protocol version 40
Destroying SipFsm object 
2009-01-07 02:21:02.125 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-07 02:29:54.784 New DB connection, total: 2
2009-01-07 02:29:54.786 Connected to database 'mythconverg' at host: localhost
2009-01-07 02:29:54.790 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-07 02:29:54.791 Enabled verbose msgs:  important general
2009-01-07 02:29:56.919 No theme dir: /home/stiles/.mythtv/themes/Mythbuntu-8.04
2009-01-07 02:29:56.924 Primary screen 0.
2009-01-07 02:29:56.925 Using screen 0, 1024x768 at 0,0
2009-01-07 02:29:56.928 No theme dir: /home/stiles/.mythtv/themes/Mythbuntu-8.04
2009-01-07 02:29:56.929 Switching to square mode (Mythbuntu-8.04)
2009-01-07 02:29:57.066 Using the Qt painter
2009-01-07 02:29:57.068 JoystickMenuClient Error: Joystick disabled - Failed to read /home/stiles/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-07 02:29:57.072 lirc_init failed for mythtv, see preceding messages
2009-01-07 02:29:59.590 Specified base font 'medium' does not exist for font clock
2009-01-07 02:29:59.591 Specified base font 'medium' does not exist for font small
2009-01-07 02:29:59.591 Specified base font 'medium' does not exist for font medium
2009-01-07 02:29:59.592 Specified base font 'medium' does not exist for font large
2009-01-07 02:29:59.595 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-07 02:29:59.761 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-07 02:29:59.980 Registering Internal as a media playback plugin.
2009-01-07 02:30:00.387 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-07 02:30:01.000 MythMusic adding CD-Writer: 1,0,0 -- CD-RW  CRX320EE 
2009-01-07 02:30:01.001 MythMusic adding CD-Writer: 1,1,0 -- LTN486S 48x Max 
2009-01-07 02:30:01.126 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.5:5060 NAT address 192.168.0.5
SIP: Cannot register; proxy, username or password not set
2009-01-07 02:30:02.228 No theme dir: /home/stiles/.mythtv/themes/Mythbuntu-8.04
2009-01-07 02:30:08.694 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-07 02:30:08.697 Using protocol version 40
2009-01-07 02:30:08.745 TV: Attempting to change from None to WatchingLiveTV
2009-01-07 02:30:08.747 Using protocol version 40
2009-01-07 02:30:14.185 [B]GetEntryAt(-1) failed.
2009-01-07 02:30:14.188 EntryToProgram(0@Wed Dec 31 16:00:00 1969) failed to get pginfo
2009-01-07 02:30:14.188 TV Error: LiveTV not successfully started
2009-01-07 02:30:14.189 TV Error: LiveTV not successfully started[/B]
2009-01-07 02:30:14.205 TV: Deleting TV Chain in destructor
2009-01-07 02:30:14.218 DPMS Deactivated 
2009-01-07 02:30:14.220 DPMS Reactivated.
2009-01-07 02:30:18.722 TV: Attempting to change from None to WatchingLiveTV
2009-01-07 02:30:18.724 Using protocol version 40
2009-01-07 02:30:24.065 [B]GetEntryAt(-1) failed.
2009-01-07 02:30:24.067 EntryToProgram(0@Wed Dec 31 16:00:00 1969) failed to get pginfo
2009-01-07 02:30:24.067 TV Error: LiveTV not successfully started
2009-01-07 02:30:24.068 TV Error: LiveTV not successfully started[/B][/B]
2009-01-07 02:30:24.151 TV: Deleting TV Chain in destructor
2009-01-07 02:30:24.160 DPMS Deactivated 
2009-01-07 02:30:24.161 DPMS Reactivated.
```

---

### Post by insanity54 on 2009-01-26
I'm having this same problem, I've been working on it for close to a week and can't figure out what is up. Could you perhaps post the solution to this problem?

Thank you,

Chris

---

### Post by rupert80 on 2009-01-31
I have exactly the same problem.  I know the tuner works because I can watch live tv using me-tv.  Here is a snippet of my log:

2009-01-31 20:46:45.581 Connecting to backend server: 192.168.19.100:6543 (try 1 of 5)
2009-01-31 20:46:45.581 Using protocol version 40
2009-01-31 20:46:45.591 TV: Attempting to change from None to WatchingLiveTV
2009-01-31 20:46:45.592 Using protocol version 40
2009-01-31 20:46:45.765 GetEntryAt(-1) failed.
2009-01-31 20:46:45.765 EntryToProgram(0@Thu Jan 1 08:00:00 1970) failed to get pginfo
2009-01-31 20:46:45.765 TV Error: LiveTV not successfully started
2009-01-31 20:46:45.766 TV Error: LiveTV not successfully started
2009-01-31 20:46:45.792 TV: Deleting TV Chain in destructor
2009-01-31 20:46:45.796 DPMS Deactivated
2009-01-31 20:46:45.797 DPMS Reactivated.

Would love to see your solution!

---

### Post by tufcamman on 2009-02-16
*sigh*

Having the same problem.  Any help on this would be great.

Thanks

---

### Post by nerver on 2009-03-06
I don't know if this is the same for you guys, but I have the same error and it seems mine is caused by having a channel change script in place. As soon as I go into the backend settings and remove the script, livetv works fine. I don't understand why though.

---

### Post by tufcamman on 2009-03-06
Hey,

I found the solution for me.  It was all in the folder permissions.  I had set the default recording directory to my home folder, which the user mythtv was not allows to write to.  A quick chmod solved this problem for me.

---

