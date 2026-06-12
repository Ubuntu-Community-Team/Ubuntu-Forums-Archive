---
title: "attempting to run MythVideo only, keeps trying to connect to &quot;Master Backend server&quot;"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by hotani on 2007-03-25
For over a year I have been using MythVideo only. No backend server, no PVR, just the video portion. If I accidentally went into programs, I'd get an error such as "could not connect to backend server, bla bla bla..." but I would never see it otherwise.

Now it comes up right away, and I cannot do anything to make it stop. This just started, and I did not change anything in MythTV recently. I cannot use mythVideo at all, because this error is constantly up. As soon as I clear it, it comes back. How can I make MythTV STOP trying to access the backend server?

Most of the help and documentation on the website involves setting up the PVR, which I am not doing. I do not have a tuner card, all my content is manually ripped or downloaded and I just want a nice frontend to access it. 

What happened?

This is the output - why is it trying to connect to the backend server?
```

miranda:hotani> mythfrontend 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-03-25 23:08:31.950 Using runtime prefix = /usr
2007-03-25 23:08:31.976 Gnome-Screensaver support enabled
2007-03-25 23:08:31.977 DPMS is active.
2007-03-25 23:08:32.028 New DB connection, total: 1
2007-03-25 23:08:32.038 Connected to database 'mythconverg' at host: localhost
2007-03-25 23:08:32.042 Total desktop dim: 1920x1080, with 1 screen[s].
2007-03-25 23:08:32.048 Using screen 0, 1920x1080 at 0,0
2007-03-25 23:08:32.081 Current Schema Version: 1160
2007-03-25 23:08:32.081 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-03-25 23:08:32.082 Enabled verbose msgs:  important general
2007-03-25 23:08:32.737 Total desktop dim: 1920x1080, with 1 screen[s].
2007-03-25 23:08:32.738 Using screen 0, 1920x1080 at 0,0
2007-03-25 23:08:32.739 Switching to square mode (sleek)
2007-03-25 23:08:32.753 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-03-25 23:08:33.250 Joystick disabled.
2007-03-25 23:08:33.550 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-03-25 23:08:34.517 Registering Internal as a media playback plugin.
2007-03-25 23:08:34.536 Registering MythDVD DVD Media Handler as a media handler ext()
2007-03-25 23:08:34.537 Registering MythDVD VCD Media Handler as a media handler ext()
2007-03-25 23:08:39.817 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-25 23:08:39.818 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
sh: rrrr: not found
2007-03-25 23:08:44.809 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-25 23:08:44.810 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-03-25 23:08:49.809 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-25 23:08:54.813 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
[.... and so on.....]

```

---

