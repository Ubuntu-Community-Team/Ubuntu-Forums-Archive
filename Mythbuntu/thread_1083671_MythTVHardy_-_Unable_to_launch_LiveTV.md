---
title: "MythTV/Hardy - Unable to launch LiveTV"
date: 2009-03-01
forum: Mythbuntu
---

### Post by Jonchilds on 2009-03-01
I've been having a few issues with getting LiveTV to launch on an AMD box running Hardy 8.04 and Mythtv 0.21 (not mythbuntu).

MythTV was installed from the apt-get repositiories (sudo apt-get install mythtv).

The System is a Phenom X3, ATI HD3200 IGP, M3A78 board & Leadtek DTV2000H.  Not trying to display the TV anywhere other than the LCD monitor at this stage.

I've tried everything that I can google regarding the card, and any MythTV compatibilities but have come up hard against the wall.  The card works with Me-TV (although has a flickering image where the EPG appears over the TV display).

Can anyone help here?  I have tried the Mythbuntu 8.10 distribution but had the same issues and found the interface a little difficult to use for a novice.

From console if I type mythtv backend-start:

> jon@AMDX3:~/Desktop/mythtv-0.21$ mythtv backend-start
2009-02-25 13:21:04.509 Using runtime prefix = /usr, libdir = /usr/lib
2009-02-25 13:21:04.515 XScreenSaver support enabled
2009-02-25 13:21:04.516 DPMS is active.
2009-02-25 13:21:04.516 Empty LocalHostName.
2009-02-25 13:21:04.516 Using localhost value of AMDX3
2009-02-25 13:21:04.523 New DB connection, total: 1
2009-02-25 13:21:04.527 Connected to database 'mythconverg' at host: localhost
2009-02-25 13:21:04.528 Closing DB connection named 'DBManager0'
2009-02-25 13:21:04.529 Primary screen 0.
2009-02-25 13:21:04.530 Connected to database 'mythconverg' at host: localhost
2009-02-25 13:21:04.530 Using screen 0, 1280x1024 at 0,0
2009-02-25 13:21:04.549 max_width: 1280 max_height: 1024
2009-02-25 13:21:04.555 Primary screen 0.
2009-02-25 13:21:04.555 Using screen 0, 1280x1024 at 0,0
2009-02-25 13:21:04.557 Switching to square mode (G.A.N.T)
2009-02-25 13:21:04.668 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-02-25 13:21:04.668 lirc_init failed for mythtv, see preceding messages
2009-02-25 13:21:04.668 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jon/.mythtv/joystickmenurc
2009-02-25 13:21:05.369 New DB connection, total: 2
2009-02-25 13:21:05.369 Connected to database 'mythconverg' at host: localhost
2009-02-25 13:21:05.382 Connecting to backend server: 192.168.1.2:6543 (try 1 of 5)
2009-02-25 13:21:05.382 Using protocol version 40
2009-02-25 13:21:05.390 TV: Attempting to change from None to WatchingPreRecorded
2009-02-25 13:21:05.390 RingBuf(/home/jon/Desktop/mythtv-0.21/backend-start): OpenFile(/home/jon/Desktop/mythtv-0.21/backend-start, 12)
2009-02-25 13:21:11.890 RingBuf(/home/jon/Desktop/mythtv-0.21/backend-start): Could not open /home/jon/Desktop/mythtv-0.21/backend-start.
2009-02-25 13:21:11.890 RingBuf(/home/jon/Desktop/mythtv-0.21/backend-start): CalcReadAheadThresh(0 KB)
-> threshhold(64 KB) min read(0 KB) blk size(32 KB)
Mutex destroy failure: Device or resource busy  

From console if I type mythtv:

> jon@AMDX3:~/Desktop/mythtv-0.21$ mythtv
2009-02-25 13:07:43.601 Using runtime prefix = /usr, libdir = /usr/lib
2009-02-25 13:07:43.607 XScreenSaver support enabled
2009-02-25 13:07:43.609 DPMS is active.
2009-02-25 13:07:43.610 Empty LocalHostName.
2009-02-25 13:07:43.610 Using localhost value of AMDX3
2009-02-25 13:07:43.616 New DB connection, total: 1
2009-02-25 13:07:43.620 Connected to database 'mythconverg' at host: localhost
2009-02-25 13:07:43.621 Closing DB connection named 'DBManager0'
2009-02-25 13:07:43.623 Primary screen 0.
2009-02-25 13:07:43.623 Connected to database 'mythconverg' at host: localhost
2009-02-25 13:07:43.624 Using screen 0, 1280x1024 at 0,0
2009-02-25 13:07:43.640 max_width: 1280 max_height: 1024
2009-02-25 13:07:43.642 Primary screen 0.
2009-02-25 13:07:43.642 Using screen 0, 1280x1024 at 0,0
2009-02-25 13:07:43.643 Switching to square mode (G.A.N.T)
2009-02-25 13:07:43.756 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-02-25 13:07:43.756 lirc_init failed for mythtv, see preceding messages
2009-02-25 13:07:43.756 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jon/.mythtv/joystickmenurc
2009-02-25 13:07:44.425 New DB connection, total: 2
2009-02-25 13:07:44.425 Connected to database 'mythconverg' at host: localhost
2009-02-25 13:07:44.438 Connecting to backend server: 192.168.1.2:6543 (try 1 of 5)
2009-02-25 13:07:44.438 Using protocol version 40
2009-02-25 13:07:44.445 TV: Attempting to change from None to WatchingLiveTV
2009-02-25 13:07:44.445 Using protocol version 40
2009-02-25 13:07:46.193 GetEntryAt(-1) failed.
2009-02-25 13:07:46.194 EntryToProgram(0@Thu Jan 1 08:00:00 1970) failed to get pginfo
2009-02-25 13:07:46.194 TV Error: LiveTV not successfully started
2009-02-25 13:07:46.194 TV Error: LiveTV not successfully started
2009-02-25 13:07:46.250 TV: Deleting TV Chain in destructor
Mutex destroy failure: Device or resource busy  

---

