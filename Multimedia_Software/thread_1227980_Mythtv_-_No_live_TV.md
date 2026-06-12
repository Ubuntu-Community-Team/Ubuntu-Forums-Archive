---
title: "Mythtv - No live TV"
date: 2009-07-31
forum: Multimedia Software
---

### Post by imperial_oz on 2009-07-31
Ok I am very new at using Mythtv and have setup a Hauppage hvr-2200 tv card.

I have followed the instruction to load the beta drivers and that seemed to work. I have also followed the instructions on how to set up Mythtv.

My problem is whenever I go to watch live tv, I get a blank screen for a very short time (under 1 second) then it returns to the menu. It doesnt actually play any live tv and Im not sure how to identify the problem.

Any assistance would greatly appreciated.

Thanks in advance

---

### Post by imperial_oz on 2009-08-01
I thought I would add further information, so started mythfrontend from the command line and this is the result:

2009-08-01 16:30:25.282 Using runtime prefix = /usr                                                                                               
2009-08-01 16:30:26.742 DPMS is disabled.
2009-08-01 16:30:26.743 Empty LocalHostName.
2009-08-01 16:30:26.743 Using localhost value of XXX
2009-08-01 16:30:26.749 New DB connection, total: 1
2009-08-01 16:30:26.753 Connected to database 'mythconverg' at host: localhost
2009-08-01 16:30:26.754 Could not open settings file /home/XXX/.mythtv/config.xml for writing
2009-08-01 16:30:26.754 Closing DB connection named 'DBManager0'
2009-08-01 16:30:26.755 Primary screen 0.
2009-08-01 16:30:26.755 Connected to database 'mythconverg' at host: localhost
2009-08-01 16:30:26.756 Using screen 0, 1680x1050 at 0,0
2009-08-01 16:30:26.761 New DB connection, total: 2
2009-08-01 16:30:26.761 Connected to database 'mythconverg' at host: localhost
2009-08-01 16:30:26.763 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-01 16:30:26.763 Enabled verbose msgs:  important general
2009-08-01 16:30:27.024 No theme dir: /home/XXX/.mythtv/themes/Mythbuntu-8.04
2009-08-01 16:30:27.026 Primary screen 0.
2009-08-01 16:30:27.026 Using screen 0, 1680x1050 at 0,0
2009-08-01 16:30:27.026 No theme dir: /home/XXX/.mythtv/themes/Mythbuntu-8.04
2009-08-01 16:30:27.027 Switching to square mode (Mythbuntu-8.04)
2009-08-01 16:30:27.048 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-08-01 16:30:27.048 lirc_init failed for mythtv, see preceding messages
2009-08-01 16:30:27.048 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tom/.mythtv/joystickmenurc
2009-08-01 16:30:27.741 Specified base font 'medium' does not exist for font clock
2009-08-01 16:30:27.742 Specified base font 'medium' does not exist for font small
2009-08-01 16:30:27.742 Specified base font 'medium' does not exist for font medium
2009-08-01 16:30:27.742 Specified base font 'medium' does not exist for font large
2009-08-01 16:30:27.742 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-01 16:30:27.771 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-01 16:30:27.792 Registering Internal as a media playback plugin.
2009-08-01 16:30:27.823 No theme dir: /home/XXX/.mythtv/themes/Mythbuntu-8.04
2009-08-01 16:30:28.580 Using NV NPOT texture extension
2009-08-01 16:30:30.852 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-01 16:30:3 0853 Using protocol version 40
2009-08-01 16:30:30.860 TV: Attempting to change from None to WatchingLiveTV
2009-08-01 16:30:30.860 Using protocol version 40
2009-08-01 16:30:32.242 GetEntryAt(-1) failed.
2009-08-01 16:30:32.243 EntryToProgram(0@Thu Jan 1 08:00:00 1970) failed to get pginfo
2009-08-01 16:30:32.243 TV Error: LiveTV not successfully started
2009-08-01 16:30:32.243 TV Error: LiveTV not successfully started
2009-08-01 16:30:32.265 TV: Deleting TV Chain in destructor
2009-08-01 16:30:35.712 Deleting UPnP client...

*****************************************************

I am using Kubuntu 9.04 64 bit.

If anybodyu has any ideas I would be extremely grateful as I just cannot get Mythtv to work.

Alternatively, can I use anything else rather than Mythtv to get this card working?

Thanks

---

