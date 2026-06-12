---
title: "2 new Ion systems with 9.10 JYA slow to load mythfrontend"
date: 2010-01-11
forum: Mythbuntu
---

### Post by rodercot on 2010-01-11
Hey all,

 I bit the bullet and decided to upgrade my 8.10 frontends but I did this with new clean installs on Asrock ION330 and a Asus ION330 system I assembled.
 
 Both systems are pretty much identical. loaded with 9.10, 2.631.17 kernels, all updated with JYA's repos. running 190-glx, alsa 1.0.20 and finally xbmc. 

 both systems use mythbuntu (the old project grayhem theme) Is what I call it and both are vdpau HQ playback profile and they also both output over hdmi one in stereo to an lgtv and the other in 5.1 to a denon amp. They both resume and suspend just fine with custom /etc/pm/sleep.d scripts. 

 However the problem I am having is that it takes about 20-30 seconds to load up mythfronted from a cold boot or when switching from xbmc to mythfrontend. I use appswitch to do this so xbmc is kill all. 

 I was wondering if anyone could point me in a direction to start looking the log shows nothing abnormal and if I start mythfrontend from terminal there are no pauses or errors there either. 

 Thanks,

 Dave

---

### Post by ian dobson on 2010-01-11
Hi,

Maybe try increasing the size of your thema cache in the frontend setup. I increased the size of the cache on my Frontend that boots from a CF card, and it reduced the boot time by 10-15 seconds.

Regards
Ian Dobson

---

### Post by rodercot on 2010-01-12
> **ian dobson said:**
> Hi,

Maybe try increasing the size of your thema cache in the frontend setup. I increased the size of the cache on my Frontend that boots from a CF card, and it reduced the boot time by 10-15 seconds.

Regards
Ian Dobson


 Ian,

 Thanks for the suggestion, I upped the value to 5 on a couple of my machines, on my test machine I upgraded the video drivers and down-graded them as well to test but no difference. 

 My machines boot-up rather quickly but from the mythbuntu splash (like the first mouse cursor) to a useable front-end I can count 1..1000 up to almost 40..1000. 

 I am going to try and tail the logs on my machines and see if I can see anything happening while it is loading. 

 Thanks,

 Dave

---

### Post by rodercot on 2010-01-14
I am completely baffled by this. I load up the frontend on my 8.10 backend using .22 as well and it is instant no hesitation but on all three frontend only machines with 9.10 and .22 they take a minimal 30-40 seconds to a useable front end and this is after the system is booted and I have a mouse cursor.

 I have tried all the themes, I have tried with different profiles. The only pause I see when loading from the terminal is myth trying to resolve a display after display=0 and I am not sure why this happens twice in the log you can see it. once finding the display at 16x12 and the second resolving a res to use for myth at 1280x720. 

 This is a but annoying to me but I do not watch much live tv anyhow but the waf is into pressing buttons and hates to wait and of course I get the - Well it does not take this long with the bell reciever. -- UGGGH -- I have no comeback here - LOL.

 Log File

```
Starting mythfrontend.real..
2010-01-14 07:40:39.377 mythfrontend version: branches/release-0-22-fixes [23117] www.mythtv.org
2010-01-14 07:40:39.377 Using runtime prefix = /usr
2010-01-14 07:40:39.377 Using configuration directory = /home/xbmc/.mythtv
2010-01-14 07:40:40.232 Empty LocalHostName.
2010-01-14 07:40:40.232 Using localhost value of xbmcmyth-test
2010-01-14 07:40:40.232 Testing network connectivity to '192.168.1.199'
2010-01-14 07:40:40.241 New DB connection, total: 1
2010-01-14 07:40:45.304 Connected to database 'mythconverg' at host: 192.168.1.199
2010-01-14 07:40:45.305 Closing DB connection named 'DBManager0'
2010-01-14 07:40:45.314 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-14 07:40:45.315 DPMS is active.
2010-01-14 07:40:45.316 Primary screen: 0.
2010-01-14 07:40:50.388 Connected to database 'mythconverg' at host: 192.168.1.199
2010-01-14 07:40:50.389 Using screen 0, 1600x1200 at 0,0
2010-01-14 07:40:50.401 MythUI Image Cache size set to 20971520 bytes
2010-01-14 07:40:50.401 Enabled verbose msgs:  important general
2010-01-14 07:40:50.406 Primary screen: 0.
2010-01-14 07:40:50.407 Using screen 0, 1600x1200 at 0,0
2010-01-14 07:40:50.407 Using theme base resolution of 800x600
2010-01-14 07:40:50.418 LIRC: Successfully initialized '/dev/lircd' using '/home/xbmc/.mythtv/lircrc' config
2010-01-14 07:40:50.418 JoystickMenuThread Error: Joystick disabled - Failed to read /home/xbmc/.mythtv/joystickmenurc
2010-01-14 07:40:50.599 Using the Qt painter
2010-01-14 07:40:50.721 Loaded base theme from /usr/share/mythtv/themes/MythCenter/base.xml
2010-01-14 07:40:50.878 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-14 07:40:50.942 New DB connection, total: 2
2010-01-14 07:40:50.944 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-14 07:40:51.560 Desktop video mode: 1600x1200 75.0019 Hz
2010-01-14 07:40:51.720 Registering Internal as a media playback plugin.
2010-01-14 07:40:51.746 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-01-14 07:40:51.869 MMUnix::AddDevice() Error: failed to stat /dev/bdi,
                        eno: No such file or directory (2)
2010-01-14 07:40:51.872 MMUnix::AddDevice() Error: failed to stat /dev/power,
                        eno: No such file or directory (2)
2010-01-14 07:40:51.875 MMUnix::AddDevice() Error: failed to stat /dev/trace,
                        eno: No such file or directory (2)
2010-01-14 07:40:51.882 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-01-14 07:40:51.931 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-01-14 07:40:51.933 Found mainmenu.xml for theme 'MythCenter'
2010-01-14 07:40:56.001 Connected to database 'mythconverg' at host: 192.168.1.199
2010-01-14 07:40:57.031 MythContext: Connecting to backend server: 192.168.1.199:6543 (try 1 of 1)
2010-01-14 07:40:57.031 Using protocol version 50
```

 
 
 Stumped :(

 Regards,

 Dave

---

### Post by byronmyth on 2010-10-18
Did you ever get to the bottom of this issue? I'm seeing exactly the same with my new ION HD ID-11 setup now I have separated the frontend and backend, takes a good 30 seconds for the frontend to load, is then pretty quick...

---

### Post by ian dobson on 2010-10-18
Hi,

Just have a look in your frontend log file, looking for pauses/long delays between the logged times for each message.

Regards
Ian Dobson

---

### Post by byronmyth on 2010-10-23
Hi Ian.

Looks like this section is where most of the time is going, no errors that I can see, just two chunks of 10 seconds sitting doing nothing, any ideas?:


2010-10-23 09:37:20.675 UPnPautoconf() - Found one UPnP backend
2010-10-23 09:37:20.786 Testing network connectivity to '192.168.2.222'
2010-10-23 09:37:20.793 Closing DB connection named 'DBManager0'
2010-10-23 09:37:29.150 Connected to database 'mythconverg' at host: 192.168.2.222
2010-10-23 09:37:29.152 Closing DB connection named 'DBManager0'
2010-10-23 09:37:29.165 DPMS is active.
2010-10-23 09:37:29.169 Primary screen: 0.
2010-10-23 09:37:39.256 Connected to database 'mythconverg' at host: 192.168.2.222
2010-10-23 09:37:39.263 Using screen 0, 1920x1080 at 0,0
2010-10-23 09:37:39.299 Desktop video mode: 1920x1080 60.0565 Hz
2010-10-23 09:37:39.360 MythUI Image Cache size set to 20971520 bytes
2010-10-23 09:37:39.399 Enabled verbose msgs:  important general
2010-10-23 09:37:39.415 Primary screen: 0.
2010-10-23 09:37:39.416 Using screen 0, 1920x1080 at 0,0
2010-10-23 09:37:39.418 Using theme base resolution of 1280x720
2010-10-23 09:37:39.444 LIRC: Successfully initialized '/dev/lircd' using '/home/pirate/.mythtv/lircrc' $
2010-10-23 09:37:39.444 JoystickMenuThread Error: Joystick disabled - Failed to read /home/pirate/.mytht$
2010-10-23 09:37:39.549 Using Frameless Window
2010-10-23 09:37:39.549 Using Full Screen Window
2010-10-23 09:37:40.421 Using the OpenGL painter

---

### Post by ian dobson on 2010-10-23
Hi,

Do you use UPNP? if not disable it on the backend and try again. I think the enable/disable upnp is a command line parameter for the backend process, so you'll need to edit the startup script/config files for mythtv-backend.

I have in my /etc/init/mythtv-backend.conf the following:-
exec /bin/su -c "/usr/bin/mythbackend --noupnp --logfile /var/log/mythtv/mythbackend.log --user mythtv -v eit" mythtv

I also see your running 0-22-fixes, this is quite old. I would recommend updating to 23.1-fixes. Note you'll need to update all machines to the same version.


Regards
Ian Dobson

---

### Post by byronmyth on 2010-11-01
Hi Ian.
 
It was the OP that had the older version, here is a newer log, no UPNP this time, just as slow:
 
2010-11-01 12:53:57.644 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-11-01 12:53:57.646 Using runtime prefix = /usr
2010-11-01 12:53:57.646 Using configuration directory = /home/pirate-maintv/.mythtv
2010-11-01 12:53:58.341 Empty LocalHostName.
2010-11-01 12:53:58.342 Using localhost value of pirate-maintv-desktop
[I]2010-11-01 12:53:58.362 New DB connection, total: 1
2010-11-01 12:54:03.421 Connected to database 'mythconverg' at host: 192.168.2.222
2010-11-01 12:54:03.423 Closing DB connection named 'DBManager0'
2010-11-01 12:54:03.447 DPMS is active.
2010-11-01 12:54:03.451 Primary screen: 0.
2010-11-01 12:54:08.522 Connected to database 'mythconverg' at host: 192.168.2.222
[/I]2010-11-01 12:54:08.542 Using screen 0, 1920x1080 at 0,0
2010-11-01 12:54:08.585 Desktop video mode: 1920x1080 50.045 Hz

On all my other PC's the frontend loads quickly so it doesn't appear to be a backend issue.
 
If I connect to the database directly using the following, I get the same delay 10-15 second delay:
 
/etc$ mysql -umythtv -pmypassword -Dmythconverg -h192.168.2.222 
 
Pings to the server are good:
 
PING 192.168.2.222 (192.168.2.222) 56(84) bytes of data.
64 bytes from 192.168.2.222: icmp_seq=1 ttl=64 time=0.144 ms
64 bytes from 192.168.2.222: icmp_seq=2 ttl=64 time=0.126 ms
64 bytes from 192.168.2.222: icmp_seq=3 ttl=64 time=0.127 ms
64 bytes from 192.168.2.222: icmp_seq=4 ttl=64 time=0.128 ms

I completely re-installed the frontend (ION HD-ID11) from scratch on the weekend as originally I had copied the install across from a memory card, still the same delay. With a SSD I'd expected this machine to fly along! Although to be fair, once the Frontend is loaded and the menu's entered once it works pretty much flawlessly.
 
Run out of ideas, anyone?

---

### Post by ian dobson on 2010-11-01
Hi,

Maybe have a look here [http://forums.mysql.com/read.php?24,23390,23390](http://forums.mysql.com/read.php?24,23390,23390)

Although only mysql related their having a 5 second delay on connecting to the mysql database.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-11-01
Hi,

Or maybe add all your hists/ip addresses to the /etc/hosts file.

Playing with one of my test boxes, I could repeat this if the ip address/host wasn't resolvable on the sql server box.

Regards
Ian Dobson

---

### Post by byronmyth on 2010-11-03
Yep, that sorted it! Added the hostname/IP to the backend's host file and now it connects perfectly, wierd that is the only frontend (out of 4) that needs that though! Many thanks.
 
2010-11-03 08:08:42.597 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-11-03 08:08:42.599 Using runtime prefix = /usr
2010-11-03 08:08:42.599 Using configuration directory = /home/pirate-maintv/.mythtv
2010-11-03 08:08:43.299 Using localhost value of pirate-maintv-desktop
2010-11-03 08:08:43.316 New DB connection, total: 1
2010-11-03 08:08:43.322 Connected to database 'mythconverg' at host: 192.168.2.222
2010-11-03 08:08:43.323 Closing DB connection named 'DBManager0'
2010-11-03 08:08:43.339 DPMS is active.
2010-11-03 08:08:43.351 Primary screen: 0.
2010-11-03 08:08:43.355 Connected to database 'mythconverg' at host: 192.168.2.222
2010-11-03 08:08:43.365 Using screen 0, 1920x1080 at 0,0
2010-11-03 08:08:43.405 Desktop video mode: 1920x1080 50.045 Hz
2010-11-03 08:08:43.472 MythUI Image Cache size set to 20971520 bytes
2010-11-03 08:08:43.510 Enabled verbose msgs:  important general
2010-11-03 08:08:43.527 Primary screen: 0.

---

### Post by ian dobson on 2010-11-03
Hi,

I always add the hostname/ip address to all my boxes when they have a fixed IP address. Glad to hear the problem is solved.

Now you need to reboot the box 1000 times to recover the time that was spent trying to solve this problem.

Regards
Ian Dobson

---

### Post by byronmyth on 2010-11-03
LOL, yes how true, thanks all the same, I hate having things not "just so".
 
I'm just about to put in a second ION PC to replace an old machine so at least now I have a squeeky clean installation script to follow as I've managed to solve all but one issue: 
 
I've been trying to find an option to re-direct the sound output when using the built in web browser (to my stereo rather than TV). With the music player I use [COLOR=red][FONT=Calibri]ALSA:plughw:1,1 [/FONT][/COLOR]I can't find anywhere to use this option with mythbrowser though. Any ideas?
 
Brian

---

### Post by ian dobson on 2010-11-03
Hi,

Looking the the settings table I can see a setting "MusicAudioDevice" for my frontend. I imagine you can edit this somewhere in the user interface but don't ask me where.

If the worst commes to the worst just use MyPHPAdmin to manually edit the table.

Regards
Ian Dobson

ps. Thats another 20 reboots.

---

### Post by byronmyth on 2010-11-04
Sadly that setting appears to be for the music player rather than Mythbrowser. My other half likes to listen to German radio (ex pat) which currently I get via their satellite channel (Antenne Bayern), but they also stream via the internet, so I'd like to output the audio via our stereo rather than the TV (already sorted for music player). If there is a setting within the MythFrontend I can't find it! Thanks for your help though...

---

### Post by ian dobson on 2010-11-04
Hi,

I don't use Mythbrowser myself, but thinking about it in a logical/ilogical fashion, I'd imagine that it doesn't support changing the default audio output. 

BUT:
1) You could try setting the default audio output to your stereo output (In the X server) and just try changing all MythTV parts that should go though the TV to use the other port.

2) Mythbrowser is based on the QtWebKit, there might be a configuration option you can set in some config file.

Wow, Your better half in German, not bad. I'm English but live and work in Switzerland only afew km from the German Border.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-11-04
Hi,

I've just though of a 3rd way to do this. If the link to the internet radio is always the same, why not just create 2 links in the MythTV menu. One that starts vlc or mplayer with the correct command line parameters (http link/audio output) and the second that just kills vlc/mplayer.

Regards
Ian Dobson

---

