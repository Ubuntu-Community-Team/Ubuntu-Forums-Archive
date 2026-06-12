---
title: "Mythtv backend is sleeping on the job!"
date: 2009-08-10
forum: Multimedia Software
---

### Post by dazer26 on 2009-08-10
Ok so i'm running kubuntu jaunty with kde 4.3 installed.  I have a Hauppague 1600 tv card with the latest driver.  I intalled the mythbuntu packages from the repos.  i'm using a combined backend/frontend system with no other frontends on other computers.  

My issue is that after rebooting my computer, I try and start up the frontend and it says that it cant find the frontend.  I have the IP set for localhost so the IP isn't the problem.  If I go into system monitor and look at the processes running I can see mythbackend is there.  Except under the cpu% it flashes "disk sleep"  What I have to do is open up a terminal and type "sudo mythbackend".  This is the output I get.



mike@mike-desktop ~/Documents $ sudo mythbackend
2009-08-10 23:05:45.391 Using runtime prefix = /usr
2009-08-10 23:05:45.392 Empty LocalHostName.
2009-08-10 23:05:45.392 Using localhost value of mike-desktop
2009-08-10 23:05:45.399 New DB connection, total: 1
2009-08-10 23:05:45.405 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:05:45.406 Closing DB connection named 'DBManager0'
2009-08-10 23:05:45.406 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:05:45.407 New DB connection, total: 2
2009-08-10 23:05:45.408 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:05:45.409 Current Schema Version: 1214
Starting up as the master server.
2009-08-10 23:05:45.542 New DB connection, total: 3
2009-08-10 23:05:45.543 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:05:45.637 New DB scheduler connection
2009-08-10 23:05:45.638 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:05:45.699 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-08-10 23:05:45.699 Main::Registering HttpStatus Extension
2009-08-10 23:05:45.699 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-10 23:05:45.700 Enabled verbose msgs:  important general
2009-08-10 23:05:45.736 AutoExpire: CalcParams(): Max required Free Space: 10.0 GB w/freq: 15 min
2009-08-10 23:05:48.640 Reschedule requested for id -1.
2009-08-10 23:05:48.658 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2009-08-10 23:05:48.660 Seem to be woken up by USER

The last line confirms that the backend is sleeping for some reason.  If I look in the system monitor again it shows 2 mythbackends, the one that was there before owned by user mythtv and it's still sleeping.  The second one is owned by user root and is running.  I probably shouldnt start all this stuff up as root, but when stuff doesn't work Root often fixes it :P
I'v searched around for a solution to this but haven't found one yet.

After waking up the backend mythtv runs mostly fine until I reboot.

The other small issue that I have is with the frontend, When i'm exiting live tv it exits the entire program.  Is it supposed to do that?  I'd rather it went back to the main menu.

Here is the output from running sudo mythfrontend (once the backend has been woken up)

mike@mike-desktop ~/Documents $ sudo mythfrontend
[sudo] password for mike: 
2009-08-10 23:09:45.599 Using runtime prefix = /usr
2009-08-10 23:09:46.168 XScreenSaver support enabled
2009-08-10 23:09:46.169 DPMS is disabled.
2009-08-10 23:09:46.169 Empty LocalHostName.
2009-08-10 23:09:46.169 Using localhost value of mike-desktop
2009-08-10 23:09:46.176 New DB connection, total: 1
2009-08-10 23:09:46.181 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:09:46.182 Closing DB connection named 'DBManager0'
2009-08-10 23:09:46.184 Total desktop dim: 2832x1050, over 2 screen[s].
2009-08-10 23:09:46.184 Screen 0 dim: 1680x1050.
2009-08-10 23:09:46.184 Screen 1 dim: 1152x864.
2009-08-10 23:09:46.184 Primary screen 0.
2009-08-10 23:09:46.184 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:09:46.185 Using screen 0, 1680x1050 at 1152,0
2009-08-10 23:09:46.192 New DB connection, total: 2
2009-08-10 23:09:46.192 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:09:46.194 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-10 23:09:46.194 Enabled verbose msgs:  important general
2009-08-10 23:09:46.543 No theme dir: /home/mike/.mythtv/themes/Mythbuntu-8.04-wide
2009-08-10 23:09:46.545 Total desktop dim: 2832x1050, over 2 screen[s].
2009-08-10 23:09:46.545 Screen 0 dim: 1680x1050.
2009-08-10 23:09:46.545 Screen 1 dim: 1152x864.
2009-08-10 23:09:46.545 Primary screen 0.
2009-08-10 23:09:46.545 Using screen 0, 1680x1050 at 1152,0
2009-08-10 23:09:46.546 No theme dir: /home/mike/.mythtv/themes/Mythbuntu-8.04-wide
2009-08-10 23:09:46.546 Switching to wide mode (Mythbuntu-8.04-wide)
2009-08-10 23:09:46.565 Using the Qt painter
2009-08-10 23:09:46.566 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mike/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-08-10 23:09:46.566 lirc_init failed for mythtv, see preceding messages
2009-08-10 23:09:48.305 Specified base font 'medium' does not exist for font clock
2009-08-10 23:09:48.306 Specified base font 'medium' does not exist for font small
2009-08-10 23:09:48.306 Specified base font 'medium' does not exist for font medium
2009-08-10 23:09:48.306 Specified base font 'medium' does not exist for font large
2009-08-10 23:09:48.307 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-08-10 23:09:48.387 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-10 23:09:48.417 Registering Internal as a media playback plugin.
2009-08-10 23:09:48.441 No theme dir: /home/mike/.mythtv/themes/Mythbuntu-8.04-wide
2009-08-10 23:09:51.944 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-10 23:09:51.945 Using protocol version 40
2009-08-10 23:09:51.949 TV: Attempting to change from None to WatchingLiveTV
2009-08-10 23:09:51.949 Using protocol version 40
2009-08-10 23:09:53.715 New DB connection, total: 3
2009-08-10 23:09:53.715 Connected to database 'mythconverg' at host: localhost
2009-08-10 23:09:54.503 AFD: Opened codec 0x830d920, id(MPEG2VIDEO) type(Video)
2009-08-10 23:09:54.504 AFD: codec MP2 has 2 channels
2009-08-10 23:09:54.504 AFD: Opened codec 0x830ba20, id(MP2) type(Audio)
2009-08-10 23:09:54.605 Opening audio device 'default'. ch 6(2) sr 32000
2009-08-10 23:09:54.605 Opening ALSA audio device 'default'.
E: core-util.c: Home directory /home/mike not ours.
2009-08-10 23:09:54.625 Mixer unable to find control PCM 2
2009-08-10 23:09:54.625 Mixer unable to find control PCM 3
2009-08-10 23:09:54.625 Mixer unable to find control PCM 4
2009-08-10 23:09:54.626 Mixer unable to find control PCM 5
2009-08-10 23:09:54.626 Mixer unable to find control PCM 2
2009-08-10 23:09:54.626 Mixer unable to find control PCM 3
2009-08-10 23:09:54.626 Mixer unable to find control PCM 4
2009-08-10 23:09:54.626 Mixer unable to find control PCM 5
2009-08-10 23:09:54.628 Mixer unable to find control PCM 2
2009-08-10 23:09:54.628 Mixer unable to find control PCM 3
2009-08-10 23:09:54.629 Mixer unable to find control PCM 4
2009-08-10 23:09:54.629 Mixer unable to find control PCM 5
2009-08-10 23:09:54.630 Mixer unable to find control PCM 2
2009-08-10 23:09:54.633 Mixer unable to find control PCM 3
2009-08-10 23:09:54.634 Mixer unable to find control PCM 4
2009-08-10 23:09:54.634 Mixer unable to find control PCM 5
2009-08-10 23:09:56.007 WriteAudio: buffer underrun
2009-08-10 23:09:56.021 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-10 23:09:56.054 OSD Theme Dimensions W: 640 H: 480
2009-08-10 23:09:56.075 WriteAudio: buffer underrun
2009-08-10 23:09:56.143 WriteAudio: buffer underrun
2009-08-10 23:09:56.211 WriteAudio: buffer underrun
2009-08-10 23:09:56.278 WriteAudio: buffer underrun
2009-08-10 23:09:56.345 WriteAudio: buffer underrun
2009-08-10 23:09:56.592 TV: Changing from None to WatchingLiveTV
2009-08-10 23:09:56.595 Using realtime priority.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 480 x 480
2009-08-10 23:09:56.700 OpenGLVideoSync()
2009-08-10 23:09:56.747 Video timing method: SGI OpenGL
2009-08-10 23:09:56.765 WriteAudio: buffer underrun
2009-08-10 23:10:01.076 WriteAudio: buffer underrun
2009-08-10 23:10:01.143 WriteAudio: buffer underrun
2009-08-10 23:10:01.211 WriteAudio: buffer underrun
2009-08-10 23:10:01.278 WriteAudio: buffer underrun
2009-08-10 23:10:01.345 WriteAudio: buffer underrun
2009-08-10 23:10:01.413 WriteAudio: buffer underrun
2009-08-10 23:10:01.482 WriteAudio: buffer underrun
2009-08-10 23:10:01.549 WriteAudio: buffer underrun
2009-08-10 23:10:01.617 WriteAudio: buffer underrun
2009-08-10 23:10:01.684 WriteAudio: buffer underrun
2009-08-10 23:10:01.752 WriteAudio: buffer underrun
2009-08-10 23:10:01.820 WriteAudio: buffer underrun
2009-08-10 23:10:01.889 WriteAudio: buffer underrun
2009-08-10 23:10:01.958 WriteAudio: buffer underrun
2009-08-10 23:10:02.026 WriteAudio: buffer underrun
2009-08-10 23:10:02.094 WriteAudio: buffer underrun
2009-08-10 23:10:02.162 WriteAudio: buffer underrun
2009-08-10 23:10:02.231 WriteAudio: buffer underrun
2009-08-10 23:10:02.299 WriteAudio: buffer underrun
2009-08-10 23:10:02.366 WriteAudio: buffer underrun
2009-08-10 23:10:02.434 WriteAudio: buffer underrun
2009-08-10 23:10:02.503 WriteAudio: buffer underrun
2009-08-10 23:10:02.572 WriteAudio: buffer underrun
2009-08-10 23:10:02.640 WriteAudio: buffer underrun
2009-08-10 23:10:02.708 WriteAudio: buffer underrun
2009-08-10 23:10:02.776 WriteAudio: buffer underrun
2009-08-10 23:10:05.752 WriteAudio: buffer underrun
2009-08-10 23:10:08.665 TV: Attempting to change from WatchingLiveTV to None
2009-08-10 23:10:08.668 ~OpenGLVideoSync() -- begin
2009-08-10 23:10:08.668 ~OpenGLVideoSync() -- middle
2009-08-10 23:10:08.669 ~OpenGLVideoSync() -- end
Segmentation fault

---

### Post by dazer26 on 2009-08-10
Ok I was thinking about this and the issue might be that i'm not part of the mythtv group.  when I try and start up mythfrontend (without the sudo command)  I get the error that I am not part of the mythtv group and would you like to be added, I click yes. (it never asks for sudo access to do this, whichI presume it should)  when I log out and back in and try and start mythfrontend again it still gives the same error.  Now I can start up mythtv by simply typing "mythtv" (no sudo) into the terminal and this goes straight to live tv bypassing the menu and such.

---

