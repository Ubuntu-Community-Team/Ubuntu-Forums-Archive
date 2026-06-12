---
title: "Watch TV function fails....GetEntryAt(-1) failed."
date: 2009-05-23
forum: Mythbuntu
---

### Post by williammanda on 2009-05-23
Hi all!
I've used mythtv for a few years now and I am stumped with this issue. When I select Watch TV, the screen goes blank for 1 second then returns to the menu. I researched the error and found that several people fixed this by properly setting mythtv as the owner and group user of the recording folder. I have done this even though it was correct to start out with and have a photo below to show it. Also I have attached my Frontend log. Lastly TV recordings work, you can see a couple on the photo. They were recording while I took the snapshot.
Thanks


```
Starting mythfrontend.real..
2009-05-23 20:29:50.693 New DB connection, total: 2
2009-05-23 20:29:50.694 Connected to database 'mythconverg' at host: 192.168.1.100
2009-05-23 20:29:50.695 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-23 20:29:50.695 Enabled verbose msgs:  important general
2009-05-23 20:29:50.833 No theme dir: /home/william/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-23 20:29:50.834 Primary screen 0.
2009-05-23 20:29:50.834 Using screen 0, 1366x768 at 0,0
2009-05-23 20:29:50.834 No theme dir: /home/william/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-23 20:29:50.834 Switching to wide mode (Mythbuntu-8.04-wide)
2009-05-23 20:29:50.847 Using the Qt painter
2009-05-23 20:29:50.847 JoystickMenuClient Error: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-23 20:29:50.847 lirc_init failed for mythtv, see preceding messages
2009-05-23 20:29:51.437 Specified base font 'medium' does not exist for font clock
2009-05-23 20:29:51.437 Specified base font 'medium' does not exist for font small
2009-05-23 20:29:51.437 Specified base font 'medium' does not exist for font medium
2009-05-23 20:29:51.437 Specified base font 'medium' does not exist for font large
2009-05-23 20:29:51.438 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-05-23 20:29:51.463 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-23 20:29:51.482 Registering Internal as a media playback plugin.
2009-05-23 20:29:51.520 No theme dir: /home/william/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-23 20:29:53.085 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2009-05-23 20:29:53.085 Using protocol version 40
2009-05-23 20:29:53.104 TV: Attempting to change from None to WatchingLiveTV
2009-05-23 20:29:53.105 Using protocol version 40
2009-05-23 20:29:53.118 [B]GetEntryAt(-1) failed.
2009-05-23 20:29:53.118 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-05-23 20:29:53.118 TV Error: LiveTV not successfully started
2009-05-23 20:29:53.119 TV Error: LiveTV not successfully started
2009-05-23 20:29:53.206 TV: Deleting TV Chain in destructor[/B]
2009-05-23 20:29:53.207 DPMS Deactivated 
2009-05-23 20:29:53.207 DPMS Reactivated.
2009-05-23 20:29:55.445 Deleting UPnP client...
```[COLOR="DarkOrange"][/COLOR]

---

### Post by williammanda on 2009-05-24
After reading on some other sites, it seemed it was a database issue with a bad channel. I have to setup all the info for the channels since Comcast doesn't supply any info. Something must have happen during that process because the Watch TV function was working prior to my issue. I deleted all the tuners and entered new ones. This seemed the easiest way since I can't edit the database.

---

### Post by williammanda on 2009-05-24
Well I attempted to watch tv again an hour later after getting it working and it's doing the same thing again. I select Watch TV and the screen goes black then the menu returns. I haven't changed anything since my last post. Any help appreciated.
Thanks

---

### Post by williammanda on 2009-05-24
OK it looks like the case is closed. After troubleshooting to when the problem occured, I found that my slave backend ....backend ip address was set to 127.0.01 (this is on the 1st screen of the backend setup), I changed it to the computers ip address. This is a default setting that I always change but overlooked this time.

---

