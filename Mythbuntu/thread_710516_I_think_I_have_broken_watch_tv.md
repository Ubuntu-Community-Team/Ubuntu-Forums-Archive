---
title: "I think I have broken watch tv"
date: 2008-02-28
forum: Mythbuntu
---

### Post by Chewiesw on 2008-02-28
Hi

I seem to have broken the **watch tv ** part of mythtv.  Whenever I select Watch TV from the main menu, the screen blanks for a bit then returns to the main menu. Everything else seems to work fine. 

Watch TV did work and the only thing that I know I did wrong was to hard reset ( pulled the plug out) the box a couple of times. Is there any I can repair this? with having to re-install from scratch?

---

### Post by ajgreeny on 2008-02-28
Linux generally manages to deal with dirty reboots or shutdowns much better than windows, so I suspect there is no need to reinstall the whole system.  I have no experience of mythTV, however, so can't comment on that.

---

### Post by Nikas on 2008-02-28
Check your logs.

/var/log/mythtv/mythfrontend.log

You can monitor the log file with tail -f /var/log/mythtv/mythfrontend.log

In that way you can see in almost real time what happens when you are trying to watch live TV.

Post your findings here. :)

In a frontend only machine you will have your log in /tmp

---

### Post by newlinux on 2008-02-28
also check your backend log and your system status in mythfrontend to make sure a tuner isn't malfunctioning. If you did a hard reset while recording, it may think the tuner is still in use.

/var/log/mythtv/mythbackend.log

---

### Post by Levander on 2008-02-28
A common thing that causes that is incorrect file permissions.  I believe the common directory that the permission are wrong on is /var/lib/mythtv/recordings.  

The permissions on my machine (where it's working fine) are:

```

drwxrwsr-x 2 mythtv mythtv 4096 2008-02-28 21:21 /var/lib/mythtv/recordings

```

---

### Post by Chewiesw on 2008-03-06
Hi

Thank you for the  responses. I have attched my Front end log file. Please accept my apologies as I can't seem to work out how to post the log file so it looks neat. If there is nothing wronfg in here I will post my backend file.

```
Starting mythfrontend.real..
2008-03-06 20:52:54.867 Current Schema Version: 1160
2008-03-06 20:52:54.868 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-03-06 20:52:54.868 Enabled verbose msgs:  important general
2008-03-06 20:52:58.447 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-06 20:52:58.449 Using screen 0, 1280x1024 at 0,0
2008-03-06 20:52:58.450 Switching to square mode (Mythbuntu)
2008-03-06 20:52:58.479 Using the Qt painter
2008-03-06 20:52:59.015 New DB connection, total: 2
2008-03-06 20:52:59.015 Connected to database 'mythconverg' at host: localhost
2008-03-06 20:52:59.017 Joystick disabled.
2008-03-06 20:53:01.821 Loading from:
/usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-06 20:53:01.898 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-06 20:53:02.036 Registering Internal as a media playback plugin.
2008-03-06 20:53:02.138 Registering MythDVD DVD Media Handler as a media handler
ext()
2008-03-06 20:53:02.140 Registering MythDVD VCD Media Handler as a media handler
ext()
2008-03-06 20:53:02.280 Registering MythGallery Media Handler 1/2 as a media
handler ext()
2008-03-06 20:53:02.281 Registering MythGallery Media Handler 2/2 as a media
handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2008-03-06 20:53:02.780 Registering MythMusic Media Handler 1/2 as a media
handler ext()
2008-03-06 20:53:02.781 Registering MythMusic Media Handler 2/2 as a media
handler ext(ogg,mp3,aac,flac)
2008-03-06 20:53:08.154 Connecting to backend server: 127.0.0.1:6543 (try 1 of
5)
2008-03-06 20:53:08.166 Using protocol version 31
2008-03-06 20:53:08.286 TV: Attempting to change from None to WatchingLiveTV
2008-03-06 20:53:08.292 Using protocol version 31
2008-03-06 20:53:10.648 GetEntryAt(-1) failed.
2008-03-06 20:53:10.650 EntryToProgram(0@Thu Jan 1 02:00:00 1970) failed to get
pginfo
2008-03-06 20:53:10.650 TV Error: LiveTV not successfully started
2008-03-06 20:53:10.650 TV Error: LiveTV not successfully started
2008-03-06 20:53:10.651 TV: Deleting TV Chain in destructor
2008-03-06 20:53:10.661 DPMS Deactivated
2008-03-06 20:53:10.665 DPMS Reactivated.
Starting mythfrontend.real..
2008-03-06 20:55:42.761 Current Schema Version: 1160
2008-03-06 20:55:42.762 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-03-06 20:55:42.762 Enabled verbose msgs:  important general
2008-03-06 20:55:43.158 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-06 20:55:43.160 Using screen 0, 1280x1024 at 0,0
2008-03-06 20:55:43.161 Switching to square mode (Mythbuntu)
2008-03-06 20:55:43.178 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
lirc_init failed for mythtv, see preceding messages
2008-03-06 20:55:43.692 Joystick disabled.
2008-03-06 20:55:44.978 Loading from:
/usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-06 20:55:44.998 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-06 20:55:45.064 Registering Internal as a media playback plugin.
2008-03-06 20:55:45.091 Registering MythDVD DVD Media Handler as a media handler
ext()
2008-03-06 20:55:45.092 Registering MythDVD VCD Media Handler as a media handler
ext()
2008-03-06 20:55:45.121 Registering MythGallery Media Handler 1/2 as a media
handler ext()
2008-03-06 20:55:45.122 Registering MythGallery Media Handler 2/2 as a media
handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2008-03-06 20:55:45.215 Registering MythMusic Media Handler 1/2 as a media
handler ext()
2008-03-06 20:55:45.216 Registering MythMusic Media Handler 2/2 as a media
handler ext(ogg,mp3,aac,flac)
2008-03-06 20:55:48.705 New DB connection, total: 2
2008-03-06 20:55:48.706 Connected to database 'mythconverg' at host: localhost
2008-03-06 20:55:48.755 Connecting to backend server: 127.0.0.1:6543 (try 1 of
5)
2008-03-06 20:55:48.756 Using protocol version 31
2008-03-06 20:55:48.899 TV: Attempting to change from None to WatchingLiveTV
2008-03-06 20:55:48.901 Using protocol version 31
2008-03-06 20:55:51.652 GetEntryAt(-1) failed.
2008-03-06 20:55:51.653 EntryToProgram(0@Thu Jan 1 02:00:00 1970) failed to get
pginfo
2008-03-06 20:55:51.654 TV Error: LiveTV not successfully started
2008-03-06 20:55:51.654 TV Error: LiveTV not successfully started
2008-03-06 20:55:51.655 TV: Deleting TV Chain in destructor
2008-03-06 20:55:51.665 DPMS Deactivated
2008-03-06 20:55:51.669 DPMS Reactivated.
```

---

### Post by newlinux on 2008-03-06
Please post your backend logs too, especially right after a backend restart and when trying to watch livetv. Can you watch recordings?. And did you check the system status? More info about your system might be helpful (e.g. tuner card type) etc.

A couple of things to check based on your frontend log:

1. Is your start channel for that tuner a valid channel with program info (check the start channel in mythtv-setup and check program info with your program guide)

2. Is your program guide information correct in general? If not, try running:
```

mythfilldatabase --refresh-all

```
3. Could be your mysql db was corrupted. You might want to try repairing your database... Make sure frontends and backends are stopped then...
```

mysqlcheck -r -umythtv -p<your_mythtv_password> mythconverg

```

Without more info, I cannot give you a more targeted response, but hopefully you now know some more things to look at.

---

### Post by Tteddo on 2008-03-07
Have you verified that your capture cards are still setup in the backend setup? I reset mine one time and got the same error as you until I went in and set them up again.

---

### Post by Chewiesw on 2008-03-31
Hi Guys

I have solved the problem, I followed all the the advise in the above posts. I think the repair to the mysql databse did the trick. I then went and upgraded to 7.10 and broke everything again. I have managed to fix everything again and I am up and running.

Thanks for all your help.

---

