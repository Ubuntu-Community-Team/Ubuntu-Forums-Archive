---
title: "Can't watch recordings or &quot;watch tv&quot;"
date: 2009-10-26
forum: Mythbuntu
---

### Post by fritz3000g on 2009-10-26
[SIZE="2"]I ran into a problem with mythtv today, which I am baffled by.**

When I click "watch tv", it goes black for a few seconds and then goes back to the main menu.**The other symptom is that all my recordings are shown as grey and say that the can not be accessed.**

I was thinking that it might be a permissions problem, but my whole user directory is 777 permissions with mythtv as a group.**Also, var/lib/myth**is the same.**Any ideas?

Here's the log output.  I've made the lines with errors bold.  Any help would be great.  [/SIZE]

2009-10-26 20:48:24.799 Using runtime prefix = /usr
2009-10-26 20:48:25.106 XScreenSaver support enabled
2009-10-26 20:48:25.107 DPMS is active.
2009-10-26 20:48:25.107 Empty LocalHostName.
2009-10-26 20:48:25.107 Using localhost value of server
2009-10-26 20:48:25.112 New DB connection, total: 1
2009-10-26 20:48:25.115 Connected to database 'mythconverg' at host: localhost
2009-10-26 20:48:25.125 Closing DB connection named 'DBManager0'
2009-10-26 20:48:25.126 Primary screen 0.
2009-10-26 20:48:25.126 Connected to database 'mythconverg' at host: localhost
2009-10-26 20:48:25.127 Using screen 0, 1280x1024 at 0,0
2009-10-26 20:48:25.132 New DB connection, total: 2
2009-10-26 20:48:25.144 Connected to database 'mythconverg' at host: localhost
2009-10-26 20:48:25.145 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-26 20:48:25.145 Enabled verbose msgs:  important general
2009-10-26 20:48:25.423 No theme dir: /home/fritz3000g/.mythtv/themes/G.A.N.T
2009-10-26 20:48:25.424 Primary screen 0.
2009-10-26 20:48:25.424 Using screen 0, 1280x1024 at 0,0
2009-10-26 20:48:25.424 No theme dir: /home/fritz3000g/.mythtv/themes/G.A.N.T
2009-10-26 20:48:25.424 Switching to square mode (G.A.N.T)
2009-10-26 20:48:25.443 Using the Qt painter
2009-10-26 20:48:25.444 JoystickMenuClient Error: Joystick disabled - Failed to read /home/fritz3000g/.mythtv/joystickmenurc
2009-10-26 20:48:25.445 lirc init success using configuration file: /home/fritz3000g/.mythtv/lircrc
2009-10-26 20:48:25.995 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-10-26 20:48:26.072 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-26 20:48:26.095 Registering Internal as a media playback plugin.
2009-10-26 20:48:26.154 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-26 20:48:26.216 MythMusic adding CD-Writer: 0,0,0 -- iHDP118   4     
2009-10-26 20:48:26.216 MythMusic adding CD-Writer: 2,1,0 -- CDDVDW SH-S203N 
2009-10-26 20:48:26.255 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-26 20:48:26.291 No theme dir: /home/fritz3000g/.mythtv/themes/G.A.N.T
2009-10-26 20:48:27.625 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-26 20:48:27.625 Using protocol version 40
2009-10-26 20:48:27.641 TV: Attempting to change from None to WatchingLiveTV
2009-10-26 20:48:27.641 Using protocol version 40
2009-10-26 20:48:29.069 GetEntryAt(-1) failed.
2009-10-26 20:48:29.069 EntryToProgram(0@Wed Dec 31 [B]18:00:00 1969) failed to get pginfo
2009-10-26 20:48:29.069 TV Error: LiveTV not successfully started
2009-10-26 20:48:29.070 TV Error: LiveTV not successfully started[/B]
2009-10-26 20:48:29.149 TV: Deleting TV Chain in destructor
2009-10-26 20:48:29.151 DPMS Deactivated 
2009-10-26 20:48:29.151 DPMS Reactivated.
2009-10-26 20:48:31.104 Deleting UPnP client...

---

### Post by nasha on 2009-10-26
That error is definitely permissions related, it's come up plenty.
I don't know what more to say, just make sure your using the default storage location for mythtv is set to /var/lib/mythtv/recordings in Storage Groups.

I recently had a user who sent me round on a wild goose chase attempting to solve this same issue, and all permissions were correct, except the user had changed the default storage location, and not told me. Once rectified, the issue was resolved.

---

### Post by maddojf on 2009-11-07
Did you ever figure this out?  I am having the same problem on a my remote frontend.  I can watch 'Videos' that are stored on the backend, but I cant watch 'Live TV' or 'Recordings' even they show up in the menu.  When I click on a recording I get a 'file not found' dialog.  

I originally tried to using the storage groups option but I couldn't get anything to play, so now I am now mounting the directories with NFS.  This allows me to play videos but I still can't view recordings. 

Sidenote: The frontend on the same machine as the backend plays all the recordings fine and plays live-tv.  It is only the remote frontend that is giving me problems.

Been working on this for a week so any suggestions would be appreciated.  Thanks.

---

### Post by maddojf on 2009-11-15
I found directions in another thread that solved this problem for me.
[http://ubuntuforums.org/showthread.php?p=8319790#post8319790](http://ubuntuforums.org/showthread.php?p=8319790#post8319790)

---

### Post by Jim_Rogers on 2009-11-16
I'm having this problem and the fixes on the other thread aren't helping.

The frontend on my backend works fine. My remote frontend can get to the backend, but it won't watch live tv or recordings.

When I try to view recordings, it shows the list and it even plays the little preview window below. But if I try to actually select and watch the recording it says file not found. Live tv just goes blank for a few seconds and it goes back to menu.

I tried setting the default storage directory (in the mythbackend setup) to /var/lib/mythtv/recordings and it didn't work. I chown'ed that folder to mythtv:mythtv and made the permissions 777 and it didn't help.

I saw a suggestion that you need that folder out of the home directory. I created one, set the ownership and permission, and put it in the backend setup, but still no soap (although the new storage directories do work on the frontend on the backend).

I'm trying to set up 8.04, BTW.

The log just says things indicating it can't find the files (something like "RingBuf: /CAN'T/FIND/FILE/blah, blah, blah)

I must have some permission wrong or something. I don't understand how it can read the file to play it in the preview window, but then not be able to play it.

I must confess also that I don't really understand the storage directory stuff-- read the wiki but I don't think I get it.

Any help appreciated!

--Jim

---

### Post by nickrout on 2009-11-16
> **Jim_Rogers said:**
> 

I'm trying to set up 8.04, BTW.

--Jim

really? why? 8.04 is REALLY old.

---

### Post by Jim_Rogers on 2009-11-17
> **nickrout said:**
> really? why? 8.04 is REALLY old.

I tried to use 9.10 but I couldn't get it to scan the channels. A quick check on the internet seemed to indicate that others were having this problem as well, so rather than mess with it, I figured I'd just try the previous version in the hope that it would install easily.

So I went to the mythbuntu site and 8.04.1 was the next oldest on the list, so I took it in the hope that, while I might not have the most cutting edge release, I would have something that would install and give me what I need. It did (at least on the backend).

The reason I don't care about which release I use is because my mythtv needs are very simple-- all I want is to record shows, watch live tv, and burn shows to dvd's. I don't even know (or care) about any of the other features (mythweb, videos, etc.). I just want those three core functions to work rock-solid (and to not have any install hassles). 9.10 is relatively new, and I get the feeling that the new mythtv releases (0.22 or whatever) has some glitches as well.

I don't even know if 9.10 has the new mythtv release or release candidate or whatever; I didn't even want to take the time to find out, so I was hoping to just skip all potential new software glitches by just using an older version.

If 9.10 will install and work, however, I'm happy to use it (after I figure out how to scan the channels). But my 8.04 install is 99% done, so if I could fix my frontend problem (and it works reliably), I'm happy to use it as well.

I don't care what I use-- I just want a reliable mythtv system!

Do you think it best that I stop trying to solve my frontend problem with 8.04 and try to solve the channel scan problem in 9.10?

---

### Post by Jim_Rogers on 2009-11-17
OK-- I got 9.10 going. The channel scan page doesn't seem to scan, but apparently it doesn't have to. I hit the "fetch channels" button and nothing happened and the scan didn't scan. However, all the channels were there anyway and it works.

So I have a functional backend with a frontend running on it perfectly fine. But I still can't watch livetv or view recordings on my remote frontend.

Just as before, I can see the recordings, but if I select one, it says "file not found." I thought it was strange before that I could see the files that supposedly couldn't be found, but now I can actually delete them from the frontend!

I have no idea why I can see and delete recordings from my remote frontend but the frontend can't "find" them to watch.

The fact that I'm able to successfully get into the database from the frontend makes me think the solution on the other thread cited above is not for me.

Any ideas?

---

### Post by nickrout on 2009-11-17
> **Jim_Rogers said:**
> OK-- I got 9.10 going. The channel scan page doesn't seem to scan, but apparently it doesn't have to. I hit the "fetch channels" button and nothing happened and the scan didn't scan. However, all the channels were there anyway and it works.

So I have a functional backend with a frontend running on it perfectly fine. But I still can't watch livetv or view recordings on my remote frontend.

Just as before, I can see the recordings, but if I select one, it says "file not found." I thought it was strange before that I could see the files that supposedly couldn't be found, but now I can actually delete them from the frontend!

I have no idea why I can see and delete recordings from my remote frontend but the frontend can't "find" them to watch.

The fact that I'm able to successfully get into the database from the frontend makes me think the solution on the other thread cited above is not for me.

Any ideas?

Excellent progress :)

I suggest that you post the frontend logs surrounding trying to play a recording and we'll see what can be done...

---

### Post by Jim_Rogers on 2009-11-17
> **nickrout said:**
> Excellent progress :)

I suggest that you post the frontend logs surrounding trying to play a recording and we'll see what can be done...

I'm looking at the log right now (I think-- it's in /tmp right? There are two; one labeled mythfronted.1602.log and the other with a different number. That's not what they looked like in the old days!)

Anyway, one of the logs is huge! Takes nano nearly two minutes just to load it. It just says over and over RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv101-desktop/<file>.

Near the top is says its looking for a file that should be local but it's not there.

I found a mythtv wiki that said you can get this confusion if the front and back have the same hostname-- but in those name settings you have to use the ip of the backend, don't you?

[http://www.mythtv.org/wiki/Frequently_Asked_Questions](http://www.mythtv.org/wiki/Frequently_Asked_Questions)

This log is huge (waiting for several minutes now for gedit to scroll to the bottom). I assume you don't want all that posted, is what I've said enough? Or do you need the gory details?

If so I'll attempt to post some relevant parts of it.

Thanks,

Jim

---

### Post by Jim_Rogers on 2009-11-17
Here's the end of it (it finally scrolled to the bottom):

> Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Waited 16 seconds for data, aborting.
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2009-11-17 17:58:32.213 NVP::OpenFile(): Error, couldn't read file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg
2009-11-17 17:58:32.213 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2009-11-17 17:58:32.214 TV Error: LiveTV not successfully started
2009-11-17 17:58:32.215 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-17 17:58:32.215 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-17 17:58:32.213 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1010_20091117175809.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-17 17:58:37.917 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-11-17 17:58:38.550 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-17 17:58:38.814 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:38.821 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:38.895 MythContext: Connecting to backend server: 192.168.11.100:6543 (try 1 of 1)
2009-11-17 17:58:38.898 Using protocol version 50
2009-11-17 17:58:38.910 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:39.706 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:39.728 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:39.883 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:41.003 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:41.003 PlaybackBox::play(): Error, /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1008_20091117160600.mpg file not found
2009-11-17 17:58:41.284 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:43.696 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:43.722 ProgramInfo, Error: GetPlaybackURL: '1008_20091117160600.mpg' should be local, but it can not be found.
2009-11-17 17:58:47.033 PlaybackBox::showActions(): Error, /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1008_20091117160600.mpg file not found
2009-11-17 17:59:05.370 Deleting UPnP client...

---

### Post by nickrout on 2009-11-17
> **Jim_Rogers said:**
> I'm looking at the log right now (I think-- it's in /tmp right? There are two; one labeled mythfronted.1602.log and the other with a different number. That's not what they looked like in the old days!)

Anyway, one of the logs is huge! Takes nano nearly two minutes just to load it. It just says over and over RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv101-desktop/<file>.

Near the top is says its looking for a file that should be local but it's not there.

I found a mythtv wiki that said you can get this confusion if the front and back have the same hostname-- but in those name settings you have to use the ip of the backend, don't you?

[http://www.mythtv.org/wiki/Frequently_Asked_Questions](http://www.mythtv.org/wiki/Frequently_Asked_Questions)

This log is huge (waiting for several minutes now for gedit to scroll to the bottom). I assume you don't want all that posted, is what I've said enough? Or do you need the gory details?

If so I'll attempt to post some relevant parts of it.

Thanks,

Jim


The log is in /var/log/mythtv/mythfrontend.log (or something close to that, I am not in front of a myth machine now).

Not sure what you have found in /tmp

---

### Post by nickrout on 2009-11-17
OK you posted your log before I hit send on my reply. The dates look right so  I assume it is the right log...

Seems to be a number of reasons could cause this.

On the backend does the file 1008_20091117160600.mpg exist and if so how big is it? It should be in /var/lib/mythtv/recordings unless you have set another location.

---

### Post by Jim_Rogers on 2009-11-17
> **nickrout said:**
> OK you posted your log before I hit send on my reply. The dates look right so  I assume it is the right log...

Seems to be a number of reasons could cause this.

On the backend does the file 1008_20091117160600.mpg exist and if so how big is it? It should be in /var/lib/mythtv/recordings unless you have set another location.

There is no mythtv subdirectory in my /var/log. I found this log by doing find / -name '*.log' The two I mention are the only ones with the word mythtv in them. I figured it was just something different in 9.10.

Looking on the backend, that file 1008_20091117160600.mpg is not in recordings. 

--Jim

EDIT: I may have deleted that file. I just tried to watch another recording, it said it wasn't there, the log gave the same error, but both files (1042_20091117180000.mpg and 1042_20091117183300.mpg) *are* in the backend recordings folder. Here is the entire log (it's small):

> Starting mythfrontend.real..
2009-11-17 19:45:14.745 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-17 19:45:14.746 Using runtime prefix = /usr
2009-11-17 19:45:14.746 Using configuration directory = /home/mythtv10/.mythtv
2009-11-17 19:45:15.624 Empty LocalHostName.
2009-11-17 19:45:15.624 Using localhost value of mythtv10-desktop
2009-11-17 19:45:15.624 Testing network connectivity to '192.168.11.100'
2009-11-17 19:45:15.710 New DB connection, total: 1
2009-11-17 19:45:15.843 Connected to database 'mythconverg' at host: 192.168.11.100
2009-11-17 19:45:15.844 Closing DB connection named 'DBManager0'
2009-11-17 19:45:15.864 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-17 19:45:15.865 DPMS is active.
2009-11-17 19:45:15.880 Primary screen: 0.
2009-11-17 19:45:15.885 Connected to database 'mythconverg' at host: 192.168.11.100
2009-11-17 19:45:15.904 Using screen 0, 1024x768 at 0,0
2009-11-17 19:45:15.941 MythUI Image Cache size set to 20971520 bytes
2009-11-17 19:45:15.942 Enabled verbose msgs:  important general
2009-11-17 19:45:15.993 Primary screen: 0.
2009-11-17 19:45:15.995 Using screen 0, 1024x768 at 0,0
2009-11-17 19:45:16.020 Using theme base resolution of 1280x720
2009-11-17 19:45:16.056 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2009-11-17 19:45:16.056 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mythtv10/.mythtv/joystickmenurc
2009-11-17 19:45:16.429 Using the Qt painter
2009-11-17 19:45:16.564 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-17 19:45:16.627 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-17 19:45:16.641 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-17 19:45:16.641 Unable to load window 'backgroundwindow' from base
2009-11-17 19:45:16.706 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-17 19:45:17.538 Desktop video mode: 1024x768 60.006 Hz
2009-11-17 19:45:18.522 Registering Internal as a media playback plugin.
2009-11-17 19:45:18.813 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-17 19:45:18.815 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-17 19:45:18.817 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-17 19:45:18.820 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-17 19:45:19.087 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-17 19:45:19.310 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-17 19:45:19.370 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-17 19:45:19.679 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-17 19:45:19.735 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-17 19:45:19.766 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-17 19:45:20.539 MythContext: Connecting to backend server: 192.168.11.100:6543 (try 1 of 1)
2009-11-17 19:45:20.581 Using protocol version 50
2009-11-17 19:45:26.336 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-11-17 19:45:27.063 New DB connection, total: 2
2009-11-17 19:45:27.067 Connected to database 'mythconverg' at host: 192.168.11.100
2009-11-17 19:45:27.074 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-17 19:45:27.361 ProgramInfo, Error: GetPlaybackURL: '1042_20091117183300.mpg' should be local, but it can not be found.
2009-11-17 19:45:27.371 ProgramInfo, Error: GetPlaybackURL: '1042_20091117183300.mpg' should be local, but it can not be found.
2009-11-17 19:45:27.387 MythContext: Connecting to backend server: 192.168.11.100:6543 (try 1 of 1)
2009-11-17 19:45:27.409 Using protocol version 50
2009-11-17 19:45:27.469 ProgramInfo, Error: GetPlaybackURL: '1042_20091117183300.mpg' should be local, but it can not be found.
2009-11-17 19:45:27.483 ProgramInfo, Error: GetPlaybackURL: '1042_20091117180000.mpg' should be local, but it can not be found.
2009-11-17 19:45:27.490 ProgramInfo, Error: GetPlaybackURL: '1042_20091117180000.mpg' should be local, but it can not be found.
2009-11-17 19:45:27.559 MythContext: Connecting to backend server: 192.168.11.100:6543 (try 1 of 1)
2009-11-17 19:45:27.569 Using protocol version 50
2009-11-17 19:45:29.252 ProgramInfo, Error: GetPlaybackURL: '1042_20091117183300.mpg' should be local, but it can not be found.
2009-11-17 19:45:30.315 ProgramInfo, Error: GetPlaybackURL: '1042_20091117183300.mpg' should be local, but it can not be found.
2009-11-17 19:45:30.928 ProgramInfo, Error: GetPlaybackURL: '1042_20091117180000.mpg' should be local, but it can not be found.
2009-11-17 19:45:31.923 ProgramInfo, Error: GetPlaybackURL: '1042_20091117183300.mpg' should be local, but it can not be found.
2009-11-17 19:45:31.923 PlaybackBox::play(): Error, /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv10-desktop/1042_20091117183300.mpg file not found
2009-11-17 19:45:42.722 Deleting UPnP client...

---

### Post by maddojf on 2009-11-17
A few possibities.

1.  You are probably right that accessing the database isn't the problem, but its worth making sure.  I was able to see the recordings and previews on my remote frontend even though I wasn't getting proper access to the database on the backend.  To make sure, try logging into the database from the command line on your frontend with the following command (I assume from the log you posted that the backend ip is 192.168.11.100, if not then replace the ip address with the address of your backend).```
mysql -h 192.168.11.100 -u mythtv -p mythconverg
```
It will then prompt you for the password to the database.  If you then get a ">" prompt then the database access is not the problem and you can just type "exit" and move on.  If this returns an error, then follow the directions in the other thread.

2.  Make sure that on the backend you have entered an ip address (e.g. 192.168.11.100, not localhost) for both of the "Local Backend" and "Master Backend" entries in "Mythtv Backend Setup" on the first screen of the "General" option.  If localhost is entered in either of these then I think file paths will be messed up.

3.  Make sure that you are using the same time zones on both machines.  I have read other people reporting that differing time zones can mess up file paths in the database.

---

### Post by Jim_Rogers on 2009-11-17
1. Yes-- that works fine (been trying that since I saw it on the other thread that got you your answers).

2. Yep-- all correct.

3. Both showing the exact same time.

I think the fact that I can use the frontend to delete recordings from the backend means that I'm not having any trouble connecting (although you're right to check-- I can seriously be an idiot with these things!).

I have had connection problems in the past and worked through them. However, I've never had a situation where I could delete but not watch with the frontend.

It's like some permission or ownership is wrong-- but it all looks right to me. The storage files are owned by mythtv and the permissions are all 755, which is my understanding of what they should be (and I didn't change anything about the storage directories from the install).

--Jim

---

### Post by Jim_Rogers on 2009-11-19
Well, I had to give up.

Yesterday I burned a new disk and used an external cd/dvd drive (kind of grasping at straws, but the internal drive had had a fairly high number of fails while burning so I gave it a shot).

Did an install and got an "Error: No tuners are available but no active recordings?" (or something like that). After just going into the backend setup (not changing anything) and running mythfilldatabase again, it all just worked. I could watch live tv and recordings on my remote, wireless frontend.

It worked for about half an hour, and then it was right back to the same thing-- can't watch recordings or live tv. I can see recordings, the preview window plays, I can delete recordings, I can schedule recordings and they record, I just can't watch recordings or live tv. The logs just keep saying the file can't be found (same as before). 

The fact that it worked for awhile indicates that I did have it set up right.

Anyway, I went back to mythdora (I was previously using mythdora 10 when my hard drive went out-- that's what started all this). However, after installing and updating (and getting 0.22), I had the exact same problem as with mythbuntu 9.10.

So I installed mythdora 10 and did not update it, and everything works fine. So, I'm concluding that there's something wrong with 0.22.

I know this doesn't resolve anything, but I thought I'd just close out this thread (at least my part of it) by explaining how it turned out.

I may try again next year when more of the bugs are worked out.

Thanks for the help offered,

--Jim

---

### Post by endemoniada on 2009-11-30
I`m getting the exact same issues, has anyone discovered a solution yet

Frontend log when trying to watch recording from remote backend

> Starting mythfrontend.real..
2009-12-01 00:05:38.639 mythfrontend version: branches/release-0-22-fixes [22924] [www.mythtv.org](www.mythtv.org)
2009-12-01 00:05:38.640 Using runtime prefix = /usr
2009-12-01 00:05:38.640 Using configuration directory = /home/ade/.mythtv
2009-12-01 00:05:39.082 Empty LocalHostName.
2009-12-01 00:05:39.083 Using localhost value of ubuntu
2009-12-01 00:05:39.083 Testing network connectivity to '192.168.0.2'
2009-12-01 00:05:39.094 New DB connection, total: 1
2009-12-01 00:05:39.104 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 00:05:39.106 Closing DB connection named 'DBManager0'
2009-12-01 00:05:39.123 ScreenSaverX11Private: Gnome screen saver support enabled
2009-12-01 00:05:39.125 DPMS is active.
2009-12-01 00:05:39.127 Primary screen: 0.
2009-12-01 00:05:39.140 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 00:05:39.148 Using screen 0, 1280x800 at 0,0
2009-12-01 00:05:39.332 MythUI Image Cache size set to 20971520 bytes
2009-12-01 00:05:39.333 Enabled verbose msgs:  important general
2009-12-01 00:05:39.453 Primary screen: 0.
2009-12-01 00:05:39.468 Using screen 0, 1280x800 at 0,0
2009-12-01 00:05:39.469 Using theme base resolution of 1280x720
2009-12-01 00:05:39.702 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2009-12-01 00:05:39.702 JoystickMenuThread Error: Joystick disabled - Failed to read /home/ade/.mythtv/joystickmenurc
2009-12-01 00:05:40.942 Using the Qt painter
2009-12-01 00:05:41.233 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-12-01 00:05:41.291 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-12-01 00:05:41.328 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-12-01 00:05:41.329 Unable to load window 'backgroundwindow' from base
2009-12-01 00:05:41.486 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-01 00:05:44.421 Desktop video mode: 1280x800 59.9125 Hz
2009-12-01 00:05:49.021 Registering Internal as a media playback plugin.
2009-12-01 00:05:49.042 No plugins directory /usr/lib/mythtv/plugins
2009-12-01 00:05:49.283 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-12-01 00:05:49.289 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-12-01 00:05:49.317 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-12-01 00:05:49.323 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-12-01 00:05:49.423 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-12-01 00:05:49.751 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-01 00:05:49.786 Found mainmenu.xml for theme 'Mythbuntu'
2009-12-01 00:05:51.956 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 00:05:51.964 Using protocol version 50
2009-12-01 00:05:54.107 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-12-01 00:05:55.226 New DB connection, total: 2
2009-12-01 00:05:55.233 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 00:05:55.275 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-12-01 00:05:55.764 ProgramInfo, Error: GetPlaybackURL: '1007_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:55.773 ProgramInfo, Error: GetPlaybackURL: '1007_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:55.786 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 00:05:55.788 Using protocol version 50
2009-12-01 00:05:56.059 ProgramInfo, Error: GetPlaybackURL: '1007_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.167 ProgramInfo, Error: GetPlaybackURL: '1002_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.214 ProgramInfo, Error: GetPlaybackURL: '1002_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.231 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 00:05:56.239 Using protocol version 50
2009-12-01 00:05:56.252 ProgramInfo, Error: GetPlaybackURL: '1001_20091130205900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.254 ProgramInfo, Error: GetPlaybackURL: '1001_20091130205900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.394 ProgramInfo, Error: GetPlaybackURL: '1001_20091130195900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.397 ProgramInfo, Error: GetPlaybackURL: '1001_20091130195900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.432 ProgramInfo, Error: GetPlaybackURL: '1010_20091130195400.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.438 ProgramInfo, Error: GetPlaybackURL: '1010_20091130195400.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.491 ProgramInfo, Error: GetPlaybackURL: '1007_20091130185900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.494 ProgramInfo, Error: GetPlaybackURL: '1007_20091130185900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.499 ProgramInfo, Error: GetPlaybackURL: '1020_20091130145900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.540 ProgramInfo, Error: GetPlaybackURL: '1020_20091130145900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.633 ProgramInfo, Error: GetPlaybackURL: '1002_20091129223400.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.678 ProgramInfo, Error: GetPlaybackURL: '1002_20091129223400.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.737 ProgramInfo, Error: GetPlaybackURL: '1002_20091129205900.mpg' should be local, but it can not be found.
2009-12-01 00:05:56.779 ProgramInfo, Error: GetPlaybackURL: '1002_20091129205900.mpg' should be local, but it can not be found.
2009-12-01 00:05:57.321 ProgramInfo, Error: GetPlaybackURL: '1007_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:59.056 ProgramInfo, Error: GetPlaybackURL: '1007_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:05:59.057 PlaybackBox::play(): Error, /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1007_20091130215900.mpg file not found
2009-12-01 00:06:01.293 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 00:06:01.301 Using protocol version 50
2009-12-01 00:06:01.335 ProgramInfo, Error: GetPlaybackURL: '1002_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:06:01.467 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 00:06:01.469 Using protocol version 50
2009-12-01 00:06:01.527 ProgramInfo, Error: GetPlaybackURL: '1007_20091130215900.mpg' should be local, but it can not be found.
2009-12-01 00:06:08.052 Deleting UPnP client...


Frontend log when trying to watch LiveTv from remote backend

> Starting mythfrontend.real..
2009-12-01 01:42:31.545 mythfrontend version: branches/release-0-22-fixes [22936] [www.mythtv.org](www.mythtv.org)
2009-12-01 01:42:31.603 Using runtime prefix = /usr
2009-12-01 01:42:31.603 Using configuration directory = /home/ade/.mythtv
2009-12-01 01:42:32.438 Empty LocalHostName.
2009-12-01 01:42:32.438 Using localhost value of ubuntu
2009-12-01 01:42:32.453 New DB connection, total: 1
2009-12-01 01:42:32.466 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 01:42:32.490 Closing DB connection named 'DBManager0'
2009-12-01 01:42:32.533 ScreenSaverX11Private: Gnome screen saver support enabled
2009-12-01 01:42:32.536 DPMS is active.
2009-12-01 01:42:32.540 Primary screen: 0.
2009-12-01 01:42:32.552 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 01:42:32.580 Using screen 0, 1280x800 at 0,0
2009-12-01 01:42:32.661 MythUI Image Cache size set to 20971520 bytes
2009-12-01 01:42:32.661 user: 1000 effective user: 1000 before privileged thread
2009-12-01 01:42:32.662 user: 1000 effective user: 1000 run_priv_thread
2009-12-01 01:42:32.662 user: 1000 effective user: 1000 after privileged thread
2009-12-01 01:42:32.664 Enabled verbose msgs:  important general playback
2009-12-01 01:42:32.748 Primary screen: 0.
2009-12-01 01:42:32.753 Using screen 0, 1280x800 at 0,0
2009-12-01 01:42:32.755 Using theme base resolution of 1280x720
2009-12-01 01:42:32.837 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2009-12-01 01:42:32.838 JoystickMenuThread Error: Joystick disabled - Failed to read /home/ade/.mythtv/joystickmenurc
2009-12-01 01:42:33.506 Using the Qt painter
2009-12-01 01:42:33.900 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-12-01 01:42:33.920 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-12-01 01:42:33.941 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-12-01 01:42:33.942 Unable to load window 'backgroundwindow' from base
2009-12-01 01:42:34.024 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-01 01:42:34.977 Desktop video mode: 1280x800 60.0565 Hz
2009-12-01 01:42:35.107 max_width: 1280 max_height: 800
2009-12-01 01:42:36.702 Registering Internal as a media playback plugin.
2009-12-01 01:42:36.709 No plugins directory /usr/lib/mythtv/plugins
2009-12-01 01:42:36.911 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-12-01 01:42:36.919 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-12-01 01:42:36.963 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-12-01 01:42:37.167 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-01 01:42:37.190 Found mainmenu.xml for theme 'Mythbuntu'
2009-12-01 01:42:38.634 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 01:42:38.638 Using protocol version 50
2009-12-01 01:42:41.371 TV: StartTV() -- begin
2009-12-01 01:42:41.372 TV: ctor
2009-12-01 01:42:41.611 New DB connection, total: 2
2009-12-01 01:42:41.619 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 01:42:41.893 TV: DrawUnusedRects() -- begin
2009-12-01 01:42:41.893 TV: DrawUnusedRects() -- end
2009-12-01 01:42:41.894 TV: DrawUnusedRects() -- begin
2009-12-01 01:42:41.894 TV: DrawUnusedRects() -- end
2009-12-01 01:42:42.105 TV: tv->LiveTV() -- begin
2009-12-01 01:42:42.154 TV: tv->LiveTV() -- end
2009-12-01 01:42:42.154 TV: StartTV -- process events begin
2009-12-01 01:42:42.175 TV: HandleStateChange(0) -- begin
2009-12-01 01:42:42.175 TV: Attempting to change from None to Watching WatchingLiveTV
2009-12-01 01:42:42.186 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 01:42:42.190 Using protocol version 50
2009-12-01 01:42:42.265 Spawning LiveTV Recorder -- begin
2009-12-01 01:42:42.573 Spawning LiveTV Recorder -- end
2009-12-01 01:42:42.581 LiveTVChain(live-ubuntu-2009-12-01T01:42:42): ReloadAll(): Added new recording
2009-12-01 01:42:42.642 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014230.mpg' should be local, but it can not be found.
2009-12-01 01:42:42.674 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014230.mpg' should be local, but it can not be found.
2009-12-01 01:42:42.675 We have a playbackURL(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014230.mpg) & cardtype(DUMMY)
2009-12-01 01:42:42.675 We have a RingBuffer
2009-12-01 01:42:42.728 TV: StartRecorder(): took 3 ms to start recorder.
2009-12-01 01:42:42.730 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-12-01 01:42:42.860 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-12-01 01:42:42.874 NVP(0): Disabling Audio, params(-1,2,44100)
2009-12-01 01:42:42.878 VideoOutput: Allowed renderers: xv-blit,xshm,xlib,opengl,vdpau
2009-12-01 01:42:42.878 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,xv-blit,opengl,vdpau
2009-12-01 01:42:42.909 VDP: Accepting: cmp(<= 720 576,> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2009-12-01 01:42:42.909 VDP: Rejecting: cmp(<= 1280 720,> 720 576) dec(xvmc) cpus(1) rend(xvmc-blit) osd(opengl) osdfade(enabled) deint(bobdeint,onefield) filt()
			OSD Renderer opengl is not supported w/renderer xvmc-blit (supported: chromakey,chromakey,ia44blend)
2009-12-01 01:42:42.909 VDP: Accepting: cmp(<= 1280 720,> 720 576) dec(libmpeg2) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:42.909 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(1) rend(xvmc-blit) osd(ia44blend) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:42.910 VDP: Accepting: cmp(> 0 0) dec(libmpeg2) cpus(1) rend(xv-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:42.910 VDP: LoadBestPreferences(2048x2048, 0)
2009-12-01 01:42:42.910 VDP: LoadBestPreferences(2048x2048, 60)
2009-12-01 01:42:42.910 VDP: LoadBestPreferences(720x576, 60)
2009-12-01 01:42:42.910 VideoOutput: Preferred renderer: xv-blit
2009-12-01 01:42:42.910 VideoOutput: Trying video renderer: 'xv-blit'
2009-12-01 01:42:42.945 New DB connection, total: 3
2009-12-01 01:42:42.954 Connected to database 'mythconverg' at host: 192.168.0.2
2009-12-01 01:42:46.077 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014230.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.093 VDP: Accepting: cmp(<= 720 576,> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2009-12-01 01:42:46.093 VDP: Rejecting: cmp(<= 1280 720,> 720 576) dec(xvmc) cpus(1) rend(xvmc-blit) osd(opengl) osdfade(enabled) deint(bobdeint,onefield) filt()
			OSD Renderer opengl is not supported w/renderer xvmc-blit (supported: chromakey,chromakey,ia44blend)
2009-12-01 01:42:46.094 VDP: Accepting: cmp(<= 1280 720,> 720 576) dec(libmpeg2) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:46.094 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(1) rend(xvmc-blit) osd(ia44blend) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:46.094 VDP: Accepting: cmp(> 0 0) dec(libmpeg2) cpus(1) rend(xv-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:46.094 VDP: LoadBestPreferences(2048x2048, 0)
2009-12-01 01:42:46.094 VDP: LoadBestPreferences(2048x2048, 60)
2009-12-01 01:42:46.137 VideoOutputXv: ctor
2009-12-01 01:42:46.138 VideoOutWindow::SetPIPState. pip_state: 0]
2009-12-01 01:42:46.140 VideoOutputXv: Creating gc
2009-12-01 01:42:46.140 VideoOutputXv: XJ_screen_num: '0'
2009-12-01 01:42:46.141 VideoOutputXv: XJ_curwin:     '58720262'
2009-12-01 01:42:46.141 VideoOutputXv: XJ_win:        '58720262'
2009-12-01 01:42:46.141 VideoOutputXv: XJ_root:       '423'
2009-12-01 01:42:46.141 VideoOutputXv: XJ_gc:         '0x9b2d060'
2009-12-01 01:42:46.142 Display Rect  left: 0, top: 0, width: 1280, height: 800, aspect: 1.33333
2009-12-01 01:42:46.142 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.3333
2009-12-01 01:42:46.142 VDP: LoadBestPreferences(720x576, 60)
2009-12-01 01:42:46.142 Display Rect  left: 0, top: 0, width: 1280, height: 800, aspect: 1.33333
2009-12-01 01:42:46.143 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.3333
2009-12-01 01:42:46.143 LiveTVChain(live-ubuntu-2009-12-01T01:42:42): ReloadAll(): Added new recording
2009-12-01 01:42:46.145 VideoOutput: Pixel dimensions: Screen 1280x800, window 1280x800
2009-12-01 01:42:46.145 VideoOutput: Actual display dimensions: 325x203 mm  Aspect: 1.60099
2009-12-01 01:42:46.145 VideoOutput: Estimated window dimensions: 325x203 mm  Aspect: 1.60099
2009-12-01 01:42:46.147 VideoOutputXv: InitSetupBuffers() render: xv-blit, allowed: xv-blit,xshm,xlib
2009-12-01 01:42:46.171 VDP: Accepting: cmp(<= 720 576,> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2009-12-01 01:42:46.171 VDP: Rejecting: cmp(<= 1280 720,> 720 576) dec(xvmc) cpus(1) rend(xvmc-blit) osd(opengl) osdfade(enabled) deint(bobdeint,onefield) filt()
			OSD Renderer opengl is not supported w/renderer xvmc-blit (supported: chromakey,chromakey,ia44blend)
2009-12-01 01:42:46.172 VDP: Accepting: cmp(<= 1280 720,> 720 576) dec(libmpeg2) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:46.172 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(1) rend(xvmc-blit) osd(ia44blend) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:46.172 VDP: Accepting: cmp(> 0 0) dec(libmpeg2) cpus(1) rend(xv-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-12-01 01:42:46.172 VDP: LoadBestPreferences(2048x2048, 0)
2009-12-01 01:42:46.172 VDP: LoadBestPreferences(2048x2048, 60)
2009-12-01 01:42:46.172 VDP: LoadBestPreferences(720x576, 60)
2009-12-01 01:42:46.214 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.232 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2009-12-01 01:42:46.232 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-12-01 01:42:46.232 VideoOutputXv: Has XVideo flags...
2009-12-01 01:42:46.233 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-12-01 01:42:46.233 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-12-01 01:42:46.233 VideoOutputXv: Has XVideo flags...
2009-12-01 01:42:46.233 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-12-01 01:42:46.233 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  0
2009-12-01 01:42:46.234 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-12-01 01:42:46.234 VideoOutputXv: Has XVideo flags...
2009-12-01 01:42:46.234 VideoOutputXv: Here...
2009-12-01 01:42:46.234 VideoOutputXv: Grabbed xv port 355
2009-12-01 01:42:46.234 VideoOutputXv: XVideo surface found on port 355
2009-12-01 01:42:46.234 VideoOutputXv: XV_SET_DEFAULTS is supported on this port
2009-12-01 01:42:46.235 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-12-01 01:42:46.235 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-12-01 01:42:46.235 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-12-01 01:42:46.235 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-12-01 01:42:46.235 VideoOutputXv: XVideo Format #3 is 'I420'
2009-12-01 01:42:46.235 VideoOutputXv: Using XVideo Format 'YV12'
2009-12-01 01:42:46.236 VideoOutputXv: CreateShmImages(32): video_dim: 720x576
2009-12-01 01:42:46.334 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.454 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.469 VDP: SetVideoRenderer(xv-blit)
2009-12-01 01:42:46.470 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-12-01 01:42:46.487 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-12-01 01:42:46.487 Display Rect  left: 107, top: 0, width: 1066, height: 800, aspect: 1.60099
2009-12-01 01:42:46.487 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.3333
2009-12-01 01:42:46.501 Over/underscan. V: 0, H: 0
2009-12-01 01:42:46.501 Display Rect  left: 107, top: 0, width: 1066, height: 800, aspect: 1.60099
2009-12-01 01:42:46.502 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.3333
2009-12-01 01:42:46.502 VDP: LoadBestPreferences(720x576, 25)
2009-12-01 01:42:46.507 NVP(0): LoadFilters(''..) -> 0x0
2009-12-01 01:42:46.517 OSD Theme Dimensions W: 1280 H: 720
2009-12-01 01:42:46.593 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.719 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.843 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:46.960 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.090 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.206 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.321 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.444 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.561 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.681 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.797 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:47.908 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:48.016 NVP(0): ClearAfterSeek(1)
2009-12-01 01:42:48.016 VideoOutputXv: ClearAfterSeek()
2009-12-01 01:42:48.017 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:48.017 VideoOutputXv: DiscardFrames(0)
2009-12-01 01:42:48.017 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-01 01:42:48.017 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-12-01 01:42:48.017 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-12-01 01:42:48.026 playCtx: StartDecoderThread(): took 5147 ms to start player.
2009-12-01 01:42:48.026 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-12-01 01:42:48.026 TV: Changing from None to Watching WatchingLiveTV
2009-12-01 01:42:48.026 TV: State is LiveTV & mctx == ctx
2009-12-01 01:42:48.027 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2009-12-01 01:42:48.029 FilterManager: GetFilterInfo(convert) returning: 0x0
2009-12-01 01:42:48.029 FilterManager: GetFilterInfo(bobdeint) returning: 0x9f0f038
2009-12-01 01:42:48.029 Using deinterlace method bobdeint
2009-12-01 01:42:48.029 Realtime priority would require SUID as root.
2009-12-01 01:42:48.050 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-12-01 01:42:48.050 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2009-12-01 01:42:48.050 Set video sync frame interval to 40000
2009-12-01 01:42:48.052 Using audio as timebase
2009-12-01 01:42:48.052 Video timing method: USleep with busy wait
2009-12-01 01:42:48.052 Refresh rate: 16651, frame interval: 40000
2009-12-01 01:42:48.058 TV: UpdateOSDInput done
2009-12-01 01:42:48.058 TV: UpdateLCD done
2009-12-01 01:42:48.062 NVP(0): DoPause() -- begin
2009-12-01 01:42:48.063 rate: 25 speed: 1 skip: 1 = interval 40000
2009-12-01 01:42:48.063 Set video sync frame interval to 40000
2009-12-01 01:42:48.063 NVP(0): DoPause() -- setting paused
2009-12-01 01:42:48.063 LiveTVChain(live-ubuntu-2009-12-01T01:42:42): SwitchTo(1)
2009-12-01 01:42:48.063 LiveTVChain(live-ubuntu-2009-12-01T01:42:42): Entry@1: '1001_20091201014231'
2009-12-01 01:42:48.063 JumpToProgram(void)
2009-12-01 01:42:48.064 TV: ITVRestart done
2009-12-01 01:42:48.069 TV: HandleStateChange(0) -- end
2009-12-01 01:42:48.093 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-01 01:42:48.128 ScreenSaverX11Private: DPMS Deactivated 1
2009-12-01 01:42:48.129 ScreenSaverX11Private: ResetTimer -- begin
2009-12-01 01:42:48.129 ScreenSaverX11Private: StopTimer
2009-12-01 01:42:48.154 ScreenSaverX11Private: StartTimer
2009-12-01 01:42:48.154 ScreenSaverX11Private: ResetTimer -- end
2009-12-01 01:42:48.171 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:48.178 NVP(0): LoadFilters(''..) -> 0x0
2009-12-01 01:42:48.201 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014231.mpg' should be local, but it can not be found.
2009-12-01 01:42:48.201 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014230.mpg): OpenFile(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014231.mpg, 12)
2009-12-01 01:42:54.701 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014231.mpg): Could not open /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014231.mpg.
2009-12-01 01:42:54.702 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014231.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-12-01 01:42:54.702 NVP(0), Error: JumpToProgram's OpenFile failed.
2009-12-01 01:42:54.702 NVP(0), Error: Unknown recorder error, exiting decoder
2009-12-01 01:42:54.702 NVP(0): Exited decoder loop.
2009-12-01 01:42:54.756 VideoOutputXv: dtor
2009-12-01 01:42:54.756 VideoOutputXv: DiscardFrames(1)
2009-12-01 01:42:54.756 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-01 01:42:54.756 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-12-01 01:42:54.757 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-12-01 01:42:54.757 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-12-01 01:42:54.757 VideoOutputXv: DiscardFrames(1)
2009-12-01 01:42:54.757 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-01 01:42:54.757 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-12-01 01:42:54.757 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-12-01 01:42:54.757 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-12-01 01:42:54.760 VideoOutputXv: Closing XVideo port 355
2009-12-01 01:42:54.962 TV: HandleStateChange(0) -- begin
2009-12-01 01:42:54.963 TV: Attempting to change from Watching WatchingLiveTV to None
2009-12-01 01:42:54.963 TV: StopStuff() for player ctx 0 -- begin
2009-12-01 01:42:54.963 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2009-12-01 01:42:54.963 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2009-12-01 01:42:54.963 TV: StopStuff(): stopping ring buffer
2009-12-01 01:42:54.963 TV: StopStuff(): stopping player
2009-12-01 01:42:54.963 TV: StopStuff(): stopping recorder
2009-12-01 01:42:55.159 TV: StopStuff() -- end
2009-12-01 01:42:55.159 TV: Changing from Watching WatchingLiveTV to None
2009-12-01 01:42:55.161 TV: HandleStateChange(0) -- end
2009-12-01 01:42:55.182 ScreenSaverX11Private: DPMS Reactivated 1
2009-12-01 01:42:55.183 ScreenSaverX11Private: StopTimer
2009-12-01 01:42:55.183 TV: HandleStateChange(0) -- begin
2009-12-01 01:42:55.183 TV: Attempting to change from None to None
2009-12-01 01:42:55.186 TV: HandleStateChange(0) -- end
2009-12-01 01:42:55.215 TV: HandleStateChange(0) -- begin
2009-12-01 01:42:55.215 TV: Attempting to change from None to None
2009-12-01 01:42:55.219 TV: HandleStateChange(0) -- end
2009-12-01 01:42:55.240 TV: HandleStateChange(0) -- begin
2009-12-01 01:42:55.240 TV: Attempting to change from None to None
2009-12-01 01:42:55.243 TV: HandleStateChange(0) -- end
2009-12-01 01:42:55.244 TV: StartTV -- process events end
2009-12-01 01:42:55.267 TV: tv->LiveTV() -- begin
2009-12-01 01:42:55.317 TV: tv->LiveTV() -- end
2009-12-01 01:42:55.317 TV: StartTV -- process events begin
2009-12-01 01:42:55.337 TV: HandleStateChange(0) -- begin
2009-12-01 01:42:55.338 TV: Attempting to change from None to Watching WatchingLiveTV
2009-12-01 01:42:55.350 MythContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2009-12-01 01:42:55.354 Using protocol version 50
2009-12-01 01:42:55.439 Spawning LiveTV Recorder -- begin
2009-12-01 01:42:55.589 Spawning LiveTV Recorder -- end
2009-12-01 01:42:55.597 LiveTVChain(live-ubuntu-2009-12-01T01:42:55): ReloadAll(): Added new recording
2009-12-01 01:42:55.657 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014243.mpg' should be local, but it can not be found.
2009-12-01 01:42:55.686 ProgramInfo, Error: GetPlaybackURL: '1001_20091201014243.mpg' should be local, but it can not be found.
2009-12-01 01:42:55.686 We have a playbackURL(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1001_20091201014243.mpg) & cardtype(DUMMY)
2009-12-01 01:42:55.687 We have a RingBuffer
2009-12-01 01:42:55.739 TV: StartRecorder(): took 2 ms to start recorder.
2009-12-01 01:42:55.741 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-12-01 01:42:55.741 playCtx, Error: Attempting to setup a player, but it already exists.
2009-12-01 01:42:55.741 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2009-12-01 01:42:55.741 TV Error: LiveTV not successfully started
2009-12-01 01:42:55.741 TV: HandleStateChange(0) -- end
2009-12-01 01:42:55.780 ScreenSaverX11Private: DPMS Deactivated 1
2009-12-01 01:42:55.780 ScreenSaverX11Private: ResetTimer -- begin
2009-12-01 01:42:55.780 ScreenSaverX11Private: StopTimer
2009-12-01 01:42:55.780 ScreenSaverX11Private: StartTimer
2009-12-01 01:42:55.780 ScreenSaverX11Private: ResetTimer -- end
2009-12-01 01:42:55.781 ScreenSaverX11Private: DPMS Reactivated 1
2009-12-01 01:42:55.781 ScreenSaverX11Private: StopTimer
2009-12-01 01:43:00.318 TV: StartTV -- process events end
2009-12-01 01:43:00.318 TV: StartTV -- process events 2 begin
2009-12-01 01:43:00.318 TV: StartTV -- process events 2 end
2009-12-01 01:43:00.325 TV::~TV() -- begin
2009-12-01 01:43:00.377 TV::~TV() -- lock
2009-12-01 01:43:00.458 TV::~TV() -- end
2009-12-01 01:43:00.462 TV: StartTV -- end
2009-12-01 01:43:06.216 Deleting UPnP client...

---

### Post by nickrout on 2009-11-30
does the file 1001_20091201014243.mpg exist in your storage group on the backend?

---

### Post by endemoniada on 2009-12-01
> **nickrout said:**
> does the file 1001_20091201014243.mpg exist in your storage group on the backend?

yes it does exist, but it is 0mb  in size & doesn`t increase in size, it was created when i clicked watch TV on my remote frontend, after about 30 seconds of trying the remote frontend skips back to the menuscreen with a pop up window saying "Error opening jump programme file buffer".

Watching live tv & recordings work fine in the frontend on my backend machine, but not when trying to watch them on my remote frontend

---

### Post by endemoniada on 2009-12-01
Have solved my issues. On closer inspection I noticed that backend & remote frontend machines both had the same hostname, I did > gksudo gedit /etc/hosts /etc/hostname on the frontend machine and gave it a different hostname to the backend machine and it fixed the issue for me.

  I don`t know whether other users in this thread have checked to see if their machines are using the same hostname, but if they`re the same then you should change the hostname on the frontend machine.

easiest way to check would be to open a terminal window on both machines to check, if they both have the same hostname like mine did both machines had> ade@ubuntu showing in the terminal window then you should try changing the hostname on your remote frontend machine. My backend machine is still > ade@ubuntu but my remote frontend is now > ade@laptopand i am again able to watch recordings & livetv on my remote frontend :D

sincerly hope this helps other people in this thread

---

### Post by nickrout on 2009-12-01
hmmm - so like it said in post #10 on this thread :)

Glad you got it fixed.

---

