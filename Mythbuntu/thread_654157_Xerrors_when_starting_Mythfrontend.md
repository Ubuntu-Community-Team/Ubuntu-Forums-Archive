---
title: "Xerrors when starting Mythfrontend"
date: 2007-12-30
forum: Mythbuntu
---

### Post by jonno on 2007-12-30
I recently purchased an hd-5500 card which I'm planning on using in a
new HTPC. I thought it made sense to check it out first by putting it
in my existing Ubuntu desktop and installing Mythbunu over the top.
However I'm really struggling to get anything working and I'm not sure
if my problem is the Myth configuration or the tuner card.

There is more detail over here,
[http://pchdtv.com/forum/viewtopic.php?p=19432#19432](http://pchdtv.com/forum/viewtopic.php?p=19432#19432)

I think the backend sets up ok and I can scan and find 5 or 6 channels
ok however when I start the frontend I can never see any channels. I
don't think the quide is picking up any info (I'm scanning OTA ATSC
broadcasts) but I don't really know how that works.

Anyway, when I run mythfrontend in a terminal I noticed the following:
X Error: BadDevice, invalid or uninitialized input device 158
Major opcode: 146
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
Major opcode: 146
Minor opcode: 3
Resource id: 0x0
Failed to open device

Anyone have any idea what that might mean? The frontend continues to start but I can't watch any of the channels. I'm stumped.

---

### Post by newlinux on 2007-12-30
You can ignore those errors. They are bug with Xorg and wacom:

[https://launchpad.net/ubuntu/+source/xorg/+bug/42553](https://launchpad.net/ubuntu/+source/xorg/+bug/42553)

What happens when you try to watch liveTV? Have you look at your frontend and backend logs in /var/log/mythtv/

---

### Post by jonno on 2007-12-30
When I run mythbackend from a terminal I see:
2007-12-30 21:29:21.559 Using runtime prefix = /usr
2007-12-30 21:29:21.580 New DB connection, total: 1
2007-12-30 21:29:21.586 Connected to database 'mythconverg' at host: localhost
2007-12-30 21:29:21.592 Current Schema Version: 1160
Starting up as the master server.
2007-12-30 21:29:21.601 New DB connection, total: 2
2007-12-30 21:29:21.602 Connected to database 'mythconverg' at host: localhost
2007-12-30 21:29:21.604 EITHelper: localtime offset -6:00:00 
2007-12-30 21:29:21.608 TVRec(1) Error: Start channel invalid, setting to '18' on input Television instead.
2007-12-30 21:29:21.613 New DB connection, total: 3
2007-12-30 21:29:21.613 Connected to database 'mythconverg' at host: localhost
2007-12-30 21:29:21.617 TVRec(1) Error: Setting start channel '18' failed, 
                        and backup '7' failed as well.
2007-12-30 21:29:21.639 New DB scheduler connection
2007-12-30 21:29:21.640 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2007-12-30 21:29:21.648 MediaServer::HttpServer Create Error
2007-12-30 21:29:21.648 Main::Registering HttpStatus Extension
2007-12-30 21:29:21.650 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-30 21:29:21.659 Enabled verbose msgs:  important general
/var/lib/mythtv/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv' exists and that both 
the directory and that file are writeable by this user.

And then in the backend logfile (thanks for letting me know about them) I get lots of this stuff:
2007-12-30 21:28:38.115 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144250.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:28:38.116 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144451.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:28:38.117 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230170541.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:30:38.128 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144250.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:30:38.289 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144451.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:30:38.290 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230170541.mpg. File doesn't exist.  Database metadata will not be removed.

I admit I don't really understand the permissions and users setup for Myth. I tried to follow this:
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4)
but either I'm not doing something right or it's not working.

---

### Post by superm1 on 2007-12-31
> **jonno said:**
> When I run mythbackend from a terminal I see:
2007-12-30 21:29:21.559 Using runtime prefix = /usr
2007-12-30 21:29:21.580 New DB connection, total: 1
2007-12-30 21:29:21.586 Connected to database 'mythconverg' at host: localhost
2007-12-30 21:29:21.592 Current Schema Version: 1160
Starting up as the master server.
2007-12-30 21:29:21.601 New DB connection, total: 2
2007-12-30 21:29:21.602 Connected to database 'mythconverg' at host: localhost
2007-12-30 21:29:21.604 EITHelper: localtime offset -6:00:00 
2007-12-30 21:29:21.608 TVRec(1) Error: Start channel invalid, setting to '18' on input Television instead.
2007-12-30 21:29:21.613 New DB connection, total: 3
2007-12-30 21:29:21.613 Connected to database 'mythconverg' at host: localhost
2007-12-30 21:29:21.617 TVRec(1) Error: Setting start channel '18' failed, 
                        and backup '7' failed as well.
2007-12-30 21:29:21.639 New DB scheduler connection
2007-12-30 21:29:21.640 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2007-12-30 21:29:21.648 MediaServer::HttpServer Create Error
2007-12-30 21:29:21.648 Main::Registering HttpStatus Extension
2007-12-30 21:29:21.650 mythbackend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2007-12-30 21:29:21.659 Enabled verbose msgs:  important general
/var/lib/mythtv/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv' exists and that both 
the directory and that file are writeable by this user.

And then in the backend logfile (thanks for letting me know about them) I get lots of this stuff:
2007-12-30 21:28:38.115 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144250.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:28:38.116 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144451.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:28:38.117 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230170541.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:30:38.128 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144250.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:30:38.289 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230144451.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-30 21:30:38.290 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/4294967295_20071230170541.mpg. File doesn't exist.  Database metadata will not be removed.

I admit I don't really understand the permissions and users setup for Myth. I tried to follow this:
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4)
but either I'm not doing something right or it's not working.
You **can't** launch mythbackend that way.
It expects to run as the mythtv user.  

launch it like this:

```
sudo /etc/init.d/mythtv-backend restart
```

When you do so, then look at the log in /var/log/mythtv/mythbackend.log for information.

---

### Post by jonno on 2007-12-31
Ok thanks. Now mythbackend doesn't show up in System Monitor. How can I check it is actually running?
Anyway I followed the instructions and here is the backend log:

2007-12-31 09:31:50.883 Using runtime prefix = /usr
2007-12-31 09:31:50.915 New DB connection, total: 1
2007-12-31 09:31:50.924 Connected to database 'mythconverg' at host: localhost
2007-12-31 09:31:50.930 Current Schema Version: 1160
Starting up as the master server.
2007-12-31 09:31:50.945 New DB connection, total: 2
2007-12-31 09:31:50.951 Connected to database 'mythconverg' at host: localhost
2007-12-31 09:31:50.955 EITHelper: localtime offset -6:00:00 
2007-12-31 09:31:50.959 TVRec(1) Error: Start channel invalid, setting to '18' on input Television instead.
2007-12-31 09:31:50.964 New DB connection, total: 3
2007-12-31 09:31:50.966 Connected to database 'mythconverg' at host: localhost
2007-12-31 09:31:50.970 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '7' failed as well.
2007-12-31 09:31:50.990 New DB scheduler connection
2007-12-31 09:31:50.992 Connected to database 'mythconverg' at host: localhost
2007-12-31 09:31:52.348 Main::Registering HttpStatus Extension
2007-12-31 09:31:52.350 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-31 09:31:52.351 Enabled verbose msgs:  important general
/home/jonno/Videos//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/jonno/Videos/' exists and that both 
the directory and that file are writeable by this user.

As you can see I tried moving the recording location to my home directory but it still won't work.

---

### Post by jonno on 2007-12-31
Ok then I tried putting the recordings in a different folder:
> sudo mkdir /video
> sudo chmod 777 /video

then I changed to this folder in Mythbackend Setup

Then I restarted mythbackend with:
sudo /etc/init.d/mythtv-backend restart

Immediately in my backendlog I got:
2007-12-31 10:06:10.780 Using runtime prefix = /usr
2007-12-31 10:06:10.806 New DB connection, total: 1
2007-12-31 10:06:10.815 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:10.820 Current Schema Version: 1160
Starting up as the master server.
2007-12-31 10:06:10.837 New DB connection, total: 2
2007-12-31 10:06:10.840 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:10.844 EITHelper: localtime offset -6:00:00 
2007-12-31 10:06:10.848 TVRec(1) Error: Start channel invalid, setting to '18' on input Television instead.
2007-12-31 10:06:10.855 New DB connection, total: 3
2007-12-31 10:06:10.856 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:10.860 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '7' failed as well.
2007-12-31 10:06:10.881 New DB scheduler connection
2007-12-31 10:06:10.883 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:12.234 Main::Registering HttpStatus Extension
2007-12-31 10:06:12.236 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-31 10:06:12.237 Enabled verbose msgs:  important general
2007-12-31 10:06:12.238 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2007-12-31 10:06:12.241 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2007-12-31 10:06:12.902 Reschedule requested for id -1.
2007-12-31 10:06:12.944 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2007-12-31 10:06:12.949 Seem to be woken up by USER

And then it keeps updating with this stuff:
2007-12-31 10:06:30.895 AutoExpire: ERROR when trying to autoexpire file: /video/4294967295_20071230144250.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-31 10:06:30.900 AutoExpire: ERROR when trying to autoexpire file: /video/4294967295_20071230144451.mpg. File doesn't exist.  Database metadata will not be removed.

Note that I haven't started the frontend at all yet

---

### Post by superm1 on 2008-01-01
> **jonno said:**
> Ok then I tried putting the recordings in a different folder:
> sudo mkdir /video
> sudo chmod 777 /video

then I changed to this folder in Mythbackend Setup

Then I restarted mythbackend with:
sudo /etc/init.d/mythtv-backend restart

Immediately in my backendlog I got:
2007-12-31 10:06:10.780 Using runtime prefix = /usr
2007-12-31 10:06:10.806 New DB connection, total: 1
2007-12-31 10:06:10.815 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:10.820 Current Schema Version: 1160
Starting up as the master server.
2007-12-31 10:06:10.837 New DB connection, total: 2
2007-12-31 10:06:10.840 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:10.844 EITHelper: localtime offset -6:00:00 
2007-12-31 10:06:10.848 TVRec(1) Error: Start channel invalid, setting to '18' on input Television instead.
2007-12-31 10:06:10.855 New DB connection, total: 3
2007-12-31 10:06:10.856 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:10.860 TVRec(1) Error: Setting start channel '18' failed, 
            and backup '7' failed as well.
2007-12-31 10:06:10.881 New DB scheduler connection
2007-12-31 10:06:10.883 Connected to database 'mythconverg' at host: localhost
2007-12-31 10:06:12.234 Main::Registering HttpStatus Extension
2007-12-31 10:06:12.236 mythbackend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2007-12-31 10:06:12.237 Enabled verbose msgs:  important general
2007-12-31 10:06:12.238 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2007-12-31 10:06:12.241 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2007-12-31 10:06:12.902 Reschedule requested for id -1.
2007-12-31 10:06:12.944 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2007-12-31 10:06:12.949 Seem to be woken up by USER

And then it keeps updating with this stuff:
2007-12-31 10:06:30.895 AutoExpire: ERROR when trying to autoexpire file: /video/4294967295_20071230144250.mpg. File doesn't exist.  Database metadata will not be removed.
2007-12-31 10:06:30.900 AutoExpire: ERROR when trying to autoexpire file: /video/4294967295_20071230144451.mpg. File doesn't exist.  Database metadata will not be removed.

Note that I haven't started the frontend at all yet
A lot of the other areas of mythbuntu will be preconfigured to have your recordings to go to /var/lib/mythtv/recordings.  You should keep it there if you can.  Additionally, the directory has to be owned by mythtv:mythtv, not 777 permissions on it.

You can keep them where they are at right now, but that's up to you.  Just start the frontend now.

---

### Post by jonno on 2008-01-01
Well it turns out the majority of my problems came from me aborting the ATSC scan early.
Here is where I'm at now. I have 5 or 6 channels with good reception. Unfortunately I now get a blue screen when I try to play live tv. I do get audio and when I manage to record something I can see the video in a small window in the recording management window. My guess is this is due to my crummy on-board Intel 82845G chipset. I will make sure and get nVidia on my HTPC system. In the meantime if anyone has any suggestions how to fix this let me know.

---

### Post by superm1 on 2008-01-01
> **jonno said:**
> Well it turns out the majority of my problems came from me aborting the ATSC scan early.
Here is where I'm at now. I have 5 or 6 channels with good reception. Unfortunately I now get a blue screen when I try to play live tv. I do get audio and when I manage to record something I can see the video in a small window in the recording management window. My guess is this is due to my crummy on-board Intel 82845G chipset. I will make sure and get nVidia on my HTPC system. In the meantime if anyone has any suggestions how to fix this let me know.
This is probably because your onboard can't handle the resolution of the video.  You can see if its possible to allocate more ram to video, either in the BIOS or possibly with an xorg setting.

If you can't, then your only option is going to be a new card.

---

