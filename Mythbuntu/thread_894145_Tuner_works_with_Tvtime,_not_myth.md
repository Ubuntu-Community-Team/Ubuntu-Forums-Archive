---
title: "Tuner works with Tvtime, not myth"
date: 2008-08-19
forum: Mythbuntu
---

### Post by kristersaurus on 2008-08-19
Hey guys,

Quick question: both tvtime and mythtv are using /dev/video0 and /dev/vbi0, and tvtime works fine with my capture card, but mythtv says "tuner not available" in my frontend status and it is configured properly in my backend as far as I can tell. I added the tuner card to the backend setup and it properly shows ati tv wonder ve at /dev/video0. Thanks!

Backend log:
2008-08-18 23:45:13.657 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-18 23:45:13.662 Empty LocalHostName.
2008-08-18 23:45:13.663 Using localhost value of herbert
2008-08-18 23:45:13.675 New DB connection, total: 1
2008-08-18 23:45:13.682 Connected to database 'mythconverg' at host: localhost
2008-08-18 23:45:13.687 Closing DB connection named 'DBManager0'
2008-08-18 23:45:13.688 Connected to database 'mythconverg' at host: localhost
2008-08-18 23:45:13.691 New DB connection, total: 2
2008-08-18 23:45:13.692 Connected to database 'mythconverg' at host: localhost
2008-08-18 23:45:13.696 Current Schema Version: 1214
Starting up as the master server.
2008-08-18 23:45:13.706 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2008-08-18 23:45:13.708 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-08-18 23:45:14.938 Main::Registering HttpStatus Extension
2008-08-18 23:45:14.940 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-18 23:45:14.941 Enabled verbose msgs:  important general
2008-08-18 23:45:14.943 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

frontend log:
Starting mythfrontend.real..
2008-08-18 23:42:26.075 New DB connection, total: 2
2008-08-18 23:42:26.077 Connected to database 'mythconverg' at host: localhost
2008-08-18 23:42:26.090 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-18 23:42:26.090 Enabled verbose msgs:  important general
2008-08-18 23:42:27.012 Primary screen 0.
2008-08-18 23:42:27.013 Using screen 0, 1024x768 at 0,0
2008-08-18 23:42:27.023 Switching to square mode (blue)
2008-08-18 23:42:27.091 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-08-18 23:42:27.092 lirc_init failed for mythtv, see preceding messages
2008-08-18 23:42:27.093 JoystickMenuClient Error: Joystick disabled - Failed to read /home/krister/.mythtv/joystickmenurc
2008-08-18 23:42:29.712 Loading from: /usr/share/mythtv/themes/blue/base.xml
2008-08-18 23:42:29.893 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-18 23:42:30.015 Registering Internal as a media playback plugin.
2008-08-18 23:42:54.479 Connecting to backend server: 192.168.1.12:6543 (try 1 of 5)
2008-08-18 23:42:54.480 Using protocol version 40
2008-08-18 23:42:54.530 Received a remote 'Clear Cache' request
2008-08-18 23:42:58.832 Deleting UPnP client...

---

### Post by nasha on 2008-08-19
> 2008-08-18 23:45:13.708 ChannelBase(1) Error: InitializeInputs():
Could not get inputs for the capturecard.
Perhaps you have forgotten to bind video
sources to your card's inputs?

This here tells me that you havent correctly configured your card in mythtv-setup. Ensure both Capture Cards & Input Connections are correctly configured. The latter most likely being the cause of your problem.

---

### Post by kristersaurus on 2008-08-19
i thought that message was a little odd - i setup the card and connections via the mythtv backend gui. The capture card and the connections show up properly when I open it back up and go into their respective spots.

---

### Post by kristersaurus on 2008-08-20
Figured it out. My capture card was setup, but the connections were not. They were displaying correctly - that there were two, a composite and a coax, but I didnt realize I had to do more setup on the coax. Once i set it up and did the channel scan, things started working fine.

---

### Post by nasha on 2008-08-20
I did say it was most likely your input connections not set up correctly :P
Good to hear you got it going :) Welcome to mythtv!

---

### Post by kristersaurus on 2008-08-20
oops. yep, you did. you were definitely correct.

---

