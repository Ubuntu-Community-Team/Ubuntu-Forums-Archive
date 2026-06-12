---
title: "Slow frontend start - sometimes even aborting"
date: 2010-02-01
forum: Mythbuntu
---

### Post by jensk on 2010-02-01
I have a Karmic/0.22 installation consisting of a separate BE and several portables as FE's. 
My only stationary FE is the one under the TV-set. It's a Shuttle X27D with wired 100Mbit network connection. The Shuttle is a FE only setup connected to my TV via DVI/HDMI.

Since i upgraded from 8.10/0.21 i noticed that mythfrontend.real has become very slow to start - allmost 45 seconds on alle types of FE's. On my Shuttle FE it's set to start on boot with autologin. Every one in five times it doesn't start at all and must be started manually.

Is this a common experience that FE's start slower in 0.22 that it did on 0.21 and that it sometimes have to bestarted more than once to get running.

I shall note that before i start FE process the second time i check for running myth processes with:
```
ps -A | grep myth
```
/jens

---

### Post by azmyth on 2010-02-01
I notice this as well. It was much worse on 9.04 and it's been better on 9.10. With mine, the background comes up quickly but the text is slow. I compared logs from fast FE start to slow and I saw nothing different. I asked on IRC and no one had any comments.

---

### Post by ian dobson on 2010-02-01
Hi,

How large is your theme cache? I increased mine by afew mb in myth-fronted setup and that seemed to help (frontend process only seems to take 20seconds to start).

Regards
Ian Dobson

---

### Post by azmyth on 2010-02-01
Mine is set to 1 but it doesn't say MB it just says maximum number of prescaled themes to cache.

---

### Post by rodercot on 2010-02-02
I have built three Mini ITX Machines since christmas and all of them have the exact same problem and I have posted here in regards to it with no replies. I tried upping the cache as well with no difference, these are all with 9.10, Avenard Repos, and 190+ GLX drivers. I have even tried stripping the boot process a little I have disable xspalsh but it still takes nearly 1 minute to load the FE on all these atom machines from the time I see a desktop image.

 Last week I re-configured my Asus P5N7A-VM and C2D 7300 with a 9.10 clean install and the cache set to 1 and the FE loading is almost instant less than 10 seconds.

 So I am thinking this is hardware related somehow. I have not tried following with top on a remote connection to compare the two that may be another step to look into. 

 rgds,

 Dave

---

### Post by rodercot on 2010-02-05
OK Maybe I was wrong about it being hardware related. I finshed rebuilding my C2D system now it is a C2D 7400 at 2.8 (Stock) with 2Gb on an Asus P5N7A-VM and it is again very slow to load, but I know that it was not this slow when I first loaded 9.10. I think I will reload the system again from clean as now I have things the way I want them and have it documented.

 I will try the front end after every package install and see at which point it starts to be slow to load. I have tail'd top from boot up well as I quick as I can anyhow and I see the frontend hitting 120% cpu use for a split second but then down to almost nothing. 

 I can count to 50 between seeing the desktop and having a useable frontend, the other thing I find is it is reeking havoc on first boot use of mythlcd server and LCDproc, It catches the client and instantly goes to date and time, no data, I have to restart the FE to actually get data.

 Does anyone have any idea on diagnosing this issue, does no-one else see this problem?

 Regards,

 Dave

---

### Post by jensk on 2010-02-05
I have resintalled the frontend connected to the Tv set. I did this because it started to permanently not being able to autostart the frontend as part of the boot.

The reinstall didn't help. I still have to start the frontend manually (wife still asking why I don't fix this annoying fault)
/var/log/mythtv/mythfrontend.log just states that it is aborting:
```
Starting mythfrontend.real..
2010-02-05 17:36:58.970 mythfrontend version: branches/release-0-22-fixes [23323] www.mythtv.org
2010-02-05 17:36:58.971 Using runtime prefix = /usr
2010-02-05 17:36:58.971 Using configuration directory = /home/administrator/.mythtv
2010-02-05 17:36:59.838 Empty LocalHostName.
2010-02-05 17:36:59.838 Using localhost value of fe-stuen
2010-02-05 17:36:59.839 Testing network connectivity to '192.168.1.110'
2010-02-05 17:36:59.864 New DB connection, total: 1
2010-02-05 17:37:26.182 Connected to database 'mythconverg' at host: 192.168.1.110
2010-02-05 17:37:26.183 Closing DB connection named 'DBManager0'
2010-02-05 17:37:26.203 ScreenSaverX11Private: Gnome screen saver support enabled
2010-02-05 17:37:26.205 DPMS is active.
2010-02-05 17:37:26.210 Primary screen: 0.
2010-02-05 17:37:56.201 Connected to database 'mythconverg' at host: 192.168.1.110
2010-02-05 17:37:56.206 Using screen 0, 1280x768 at 0,0
2010-02-05 17:37:56.238 MythUI Image Cache size set to 20971520 bytes
2010-02-05 17:37:56.239 Enabled verbose msgs:  important general
2010-02-05 17:37:56.256 Primary screen: 0.
2010-02-05 17:37:56.258 Using screen 0, 1280x768 at 0,0
2010-02-05 17:37:56.260 Using theme base resolution of 1280x720
2010-02-05 17:37:56.283 LIRC: Successfully initialized '/dev/lircd' using '/home/administrator/.mythtv/lircrc' config
2010-02-05 17:37:56.283 JoystickMenuThread Error: Joystick disabled - Failed to read /home/administrator/.mythtv/joystickmenurc
2010-02-05 17:37:56.603 Using the Qt painter
2010-02-05 17:37:56.819 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-02-05 17:37:56.921 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-02-05 17:37:56.966 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-02-05 17:37:56.967 Unable to load window 'backgroundwindow' from base
2010-02-05 17:37:56.981 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-05 17:37:57.484 Desktop video mode: 1280x768 59.9952 Hz
2010-02-05 17:37:59.528 Registering Internal as a media playback plugin.
2010-02-05 17:37:59.897 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-02-05 17:37:59.902 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-02-05 17:37:59.912 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-02-05 17:37:59.917 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-02-05 17:37:59.929 Cannot load language da for module mythmovies
2010-02-05 17:38:00.075 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-02-05 17:38:00.231 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-02-05 17:38:00.368 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-02-05 17:38:00.639 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-02-05 17:38:00.764 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-02-05 17:38:00.772 Found mainmenu.xml for theme 'Mythbuntu'
ICE default IO error handler doing an exit(), pid = 1417, errno = 32

```
Since I have plenty of time during the autostart of the frontend I can do a ps aux and se that it is the mythfrontend.real process that gets the ICE default IO error

I have searched for ICE default IO error but haven't found the information that could help me solve the issue.
So i have to start the frontend manually after boot to desktop

When started manually the very slow start of the frontend is still there - approx 50 seconds from click on menu to the theme is loaded.

The frontend is a Shuttle X27D athlon 330 with a local 64Gb SSD disk so there should be anough muscle to start Mythfrontend within seconds.
/jens

---

### Post by 4dognight on 2010-02-05
It might be something related to your DB. From your logs, there is about a 26 sec pause , when it trys to connect to the DB.

---

### Post by gdownes on 2010-02-06
Yep, I am getting the same thing; the backend/frontend machine takes 1-2 mins to load the theme. All other frontend machines see the mythfrontend.real process load but never open up mythtv. When I load the backend setup app, it fails to load and skips to the mythfilldatabase prompt.

A less severe version of this happened several weeks back and it seemed to come good, but this time it has got to the point that no remote frontends can load mythtv.

Any ideas anyone?

---

### Post by jensk on 2010-02-06
I have noticed the 26 second delay on the connection to the backend DB. I will try to dig into that this weekend. The backend is a 3Ghz core duo 6400 machine. It is never pressed for CPU ressources so i don't know why this delay is there.

Any ideas as to why mythfrontend.real is aborting with
```
ICE default IO error handler doing an exit(), pid = 1417, errno = 32
```
The pid is mythfrontend.real.

One minute later I can start mythfrontend.real manually:confused:

---

### Post by jensk on 2010-02-06
Forgot to upload /var/log/mythfront.log part for when a start of mythfrontend.real is successfull - aka manual start in the menu:
```
Starting mythfrontend.real..
2010-02-06 09:35:57.299 mythfrontend version: branches/release-0-22-fixes [23323] www.mythtv.org
2010-02-06 09:35:57.300 Using runtime prefix = /usr
2010-02-06 09:35:57.300 Using configuration directory = /home/administrator/.mythtv
2010-02-06 09:35:58.157 Empty LocalHostName.
2010-02-06 09:35:58.158 Using localhost value of fe-stuen
2010-02-06 09:35:58.158 Testing network connectivity to '192.168.1.110'
2010-02-06 09:35:58.183 New DB connection, total: 1
2010-02-06 09:36:13.198 Connected to database 'mythconverg' at host: 192.168.1.110
2010-02-06 09:36:13.200 Closing DB connection named 'DBManager0'
2010-02-06 09:36:13.219 ScreenSaverX11Private: Gnome screen saver support enabled
2010-02-06 09:36:13.221 DPMS is active.
2010-02-06 09:36:13.224 Primary screen: 0.
2010-02-06 09:36:28.234 Connected to database 'mythconverg' at host: 192.168.1.110
2010-02-06 09:36:28.237 Using screen 0, 1280x768 at 0,0
2010-02-06 09:36:28.266 MythUI Image Cache size set to 20971520 bytes
2010-02-06 09:36:28.266 Enabled verbose msgs:  important general
2010-02-06 09:36:28.281 Primary screen: 0.
2010-02-06 09:36:28.282 Using screen 0, 1280x768 at 0,0
2010-02-06 09:36:28.284 Using theme base resolution of 1280x720
2010-02-06 09:36:28.304 LIRC: Successfully initialized '/dev/lircd' using '/home/administrator/.mythtv/lircrc' config
2010-02-06 09:36:28.305 JoystickMenuThread Error: Joystick disabled - Failed to read /home/administrator/.mythtv/joystickmenurc
2010-02-06 09:36:28.606 Using the Qt painter
2010-02-06 09:36:28.808 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-02-06 09:36:28.850 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-02-06 09:36:28.897 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-02-06 09:36:28.897 Unable to load window 'backgroundwindow' from base
2010-02-06 09:36:28.911 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-06 09:36:29.331 Desktop video mode: 1280x768 59.9952 Hz
2010-02-06 09:36:31.116 Registering Internal as a media playback plugin.
2010-02-06 09:36:31.255 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-02-06 09:36:31.263 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-02-06 09:36:31.271 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-02-06 09:36:31.279 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-02-06 09:36:31.287 Cannot load language da for module mythmovies
2010-02-06 09:36:31.338 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-02-06 09:36:31.436 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-02-06 09:36:31.469 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-02-06 09:36:31.596 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-02-06 09:36:31.698 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-02-06 09:36:31.702 Found mainmenu.xml for theme 'Mythbuntu'
2010-02-06 09:36:32.300 MythContext: Connecting to backend server: 192.168.1.110:6543 (try 1 of 1)
2010-02-06 09:36:32.301 Using protocol version 50

```

I have tried to delete the autologin'd mythusers .ICEauthority but i didn't help on the autostart of the frontend. it still crashes.

---

### Post by gdownes on 2010-02-06
I found [http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8.10-681312]("http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8.10-681312/") and this seems to have changed things back to a 10 second delay (I wasn't able to launch mythfrondend.real without it crashing).

Hope this helps; but please let us know if a fix for the delay in starting mythfrontend.real is found.

---

### Post by gdownes on 2010-02-06
Sorry, in addition, this is helpful as it explained the ICE error and gave me the thought to look for the code in my above posting link.

[http://www.linuxquestions.org/questions/linux-software-2/just-what-is-going-on-with-.iceauthority-ownership-325611/]("http://www.linuxquestions.org/questions/linux-software-2/just-what-is-going-on-with-.iceauthority-ownership-325611/")

---

### Post by jensk on 2010-02-06
I have tried to "play" with the rights of the .ICEauthority file.

I have deleted it and it was recreated on the next boot.

The owner has all the time ben the autologin'ed user
The rights of the /home/'user' dir is also correct
```
drwxr-xr-x 28 administrator administrator 4096 2010-02-06 18:43 administrator
```

I have changed the rights to 777 but efter every boot it is returned to the login'ed user that have rw and nothing else.
```
-rw------- 1 administrator administrator 1304 2010-02-06 18:43 .ICEauthority

```

My autostarted mythfrontend is still crashing with (from /var/log/mythtv/mythfrontend.log)
```
ICE default IO error handler doing an exit(), pid = 1400, errno = 32

```

After the crash I can start mythfrontend.real normally from the menu.

I completely lost on resolving this issue.

---

