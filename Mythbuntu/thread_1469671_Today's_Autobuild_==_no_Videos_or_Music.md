---
title: "Today's Autobuild == no Videos or Music"
date: 2010-05-02
forum: Mythbuntu
---

### Post by uncle hammy on 2010-05-02
I just did an upgrade today (to release-0-23-fixes (24334)) and now Watch Videos and Listen to Music do absolutely nothing.  Press it til the cows come home, and nothing happens.  MythGallery throws an actual error popup that says "The plugin mythgallery has failed to run for some reason", followed by another popup "Plugin mythgallery is not compatible with the installed MythTV libraries.  Please recompile the plugin after a make distclean.".  This is consistent across all 3 machines that I just upgraded this morning.

There were 4 packages updated mythtv-frontend, libmyth-0.23-0, mythtv-common, mythtv-transcode-utils

---

### Post by silvanet on 2010-05-02
Same here issue for me.  I upgraded to be able to play some ISO's.

---

### Post by Akriss on 2010-05-02
Seems like a package forgot to update and or remove some libraries.

frontend log shows:
```
Starting mythfrontend.real..
2010-05-02 14:30:21.426 mythfrontend version: branches/release-0-23-fixes [24334] www.mythtv.org
2010-05-02 14:30:21.427 Using runtime prefix = /usr
2010-05-02 14:30:21.427 Using configuration directory = /home/media-serv/.mythtv
2010-05-02 14:30:22.117 Empty LocalHostName.
2010-05-02 14:30:22.117 Using localhost value of media-serv-desktop
2010-05-02 14:30:22.121 New DB connection, total: 1
2010-05-02 14:30:22.123 Connected to database 'mythconverg' at host: localhost
2010-05-02 14:30:22.124 Closing DB connection named 'DBManager0'
2010-05-02 14:30:22.132 ScreenSaverX11Private: XScreenSaver support enabled
2010-05-02 14:30:22.133 DPMS is disabled.
2010-05-02 14:30:22.134 Primary screen: 0.
2010-05-02 14:30:22.134 Connected to database 'mythconverg' at host: localhost
2010-05-02 14:30:22.135 Using screen 0, 1920x1080 at 0,0
2010-05-02 14:30:22.141 Desktop video mode: 1920x1080 60.0024 Hz
2010-05-02 14:30:22.156 MythUI Image Cache size set to 20971520 bytes
2010-05-02 14:30:22.169 Enabled verbose msgs:  important general
2010-05-02 14:30:22.172 Primary screen: 0.
2010-05-02 14:30:22.172 Using screen 0, 1920x1080 at 0,0
2010-05-02 14:30:22.172 Using theme base resolution of 1280x720
2010-05-02 14:30:22.175 LIRC: Successfully initialized '/dev/lircd' using '/home/media-serv/.mythtv/lircrc' config
2010-05-02 14:30:22.175 JoystickMenuThread Error: Joystick disabled - Failed to read /home/media-serv/.mythtv/joystickmenurc
2010-05-02 14:30:22.196 Using Frameless Window
2010-05-02 14:30:22.196 Using Full Screen Window
2010-05-02 14:30:22.412 Using the Qt painter
2010-05-02 14:30:22.458 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-05-02 14:30:22.464 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-05-02 14:30:22.470 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-05-02 14:30:22.470 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-05-02 14:30:22.472 New DB connection, total: 2
2010-05-02 14:30:22.473 New DB connection, total: 3
2010-05-02 14:30:22.473 Connected to database 'mythconverg' at host: localhost
2010-05-02 14:30:22.474 Connected to database 'mythconverg' at host: localhost
2010-05-02 14:30:22.474 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-02 14:30:22.704 Registering Internal as a media playback plugin.
2010-05-02 14:30:22.707 Plugin mytharchive (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.707 Test Popup Version Failed 
2010-05-02 14:30:22.707 Unable to initialize plugin 'mytharchive'.
2010-05-02 14:30:22.708 Plugin mythbrowser (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.708 Unable to initialize plugin 'mythbrowser'.
2010-05-02 14:30:22.710 Plugin mythgallery (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.710 Unable to initialize plugin 'mythgallery'.
2010-05-02 14:30:22.711 Plugin mythmovies (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.711 libmythmovies.so/main.o: binary version mismatch
2010-05-02 14:30:22.712 Unable to initialize plugin 'mythmovies'.
2010-05-02 14:30:22.722 Plugin mythmusic (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.722 Unable to initialize plugin 'mythmusic'.
2010-05-02 14:30:22.724 Plugin mythnetvision (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.724 Unable to initialize plugin 'mythnetvision'.
2010-05-02 14:30:22.725 Plugin mythnews (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.725 Unable to initialize plugin 'mythnews'.
2010-05-02 14:30:22.728 Plugin mythvideo (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.728 Unable to initialize plugin 'mythvideo'.
2010-05-02 14:30:22.729 Plugin mythweather (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:22.729 Unable to initialize plugin 'mythweather'.
2010-05-02 14:30:22.733 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-02 14:30:22.733 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-02 14:30:22.733 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-02 14:30:22.734 NetworkControl: Listening for remote connections on port 6546
2010-05-02 14:30:22.735 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-05-02 14:30:22.763 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-05-02 14:30:22.764 Found mainmenu.xml for theme 'Mythbuntu'
2010-05-02 14:30:23.348 MythContext: Connecting to backend server: 192.168.1.129:6543 (try 1 of 1)
2010-05-02 14:30:23.356 Using protocol version 56
2010-05-02 14:30:25.426 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-05-02 14:30:47.929 Plugin mythgallery (0.23.20100314-1) binary version does not match libraries (0.23.20100429-1)
2010-05-02 14:30:47.932 Unable to initialize plugin 'mythgallery'.
2010-05-02 14:30:47.932 Unable to run plugin 'mythgallery': not initialized
2010-05-02 14:31:02.916 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```

I have tried removing all plug-ins and then re-enabling. It did not work though.

Ill try a complete removal of the frontend and reinstall later, it might work.

---

### Post by tgm4883 on 2010-05-02
Let me guess, you are both using Mythbuntu 64-bit?

---

### Post by Akriss on 2010-05-02
> **tgm4883 said:**
> Let me guess, you are both using Mythbuntu 64-bit?

Correct!

Well for me at least.

Oh and a complete removal of the frontend and reinstall did not remedy it.

---

### Post by uncle hammy on 2010-05-02
> **tgm4883 said:**
> Let me guess, you are both using Mythbuntu 64-bit?
Yes

---

### Post by tgm4883 on 2010-05-02
Ok, this is happening because of a combination of 2 reasons.

1) At release, Canonical pulls a bunch of servers off of building packages to help with the load of ISO downloads.

2) One package of MythTV is not architecture dependent. All but one package for 64-bit packages is built by the amd64 machines. One MythTV package for 64-bit machines is built by the i386 machines. (that is because that package works on any architecture). 

You will notice on [this page]("https://edge.launchpad.net/~mythbuntu/+archive/0.23/+packages") that the MythTV builds only have i386 listed. This is because the amd64 ones have already built and we are waiting on the i386 ones to be built (As of right now, they will start in 1 hour)

Once these get built (and mythplugins gets built as well to resolve the mythvideo part), you will need to do the updates again so it will upgrade everything to the right build. Alternatively, you may be able to fire up Synaptic and Force an older build number.

I'm currently seeing if there is a way to make sure this doesn't happen in the future.

---

### Post by uncle hammy on 2010-05-02
Gotcha, thanks for the clarification.  I have a 6 year old came into our room this morning complaining her tummy hurt, and proceeded to divided her day equally between her head in the toilet and lying on the couch watching videos.

I ended up enabling the JYA repos (which seemed to be completely up to date) in order to be able to provide her with Alivn and the Chipmunks :).

---

### Post by DemonBob on 2010-05-02
Same thing for me, but I am running 32bit ubuntu. 

```
demonbob@sys-mythtv:~$ uname -a
Linux sys-mythtv 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```

```
demonbob@sys-mythtv:~$ getconf LONG_BIT
32

```

---

### Post by kasulstyls on 2010-05-02
Same thing for me on 32bit!

---

### Post by tgm4883 on 2010-05-02
> **DemonBob said:**
> Same thing for me, but I am running 32bit ubuntu. 

```
demonbob@sys-mythtv:~$ uname -a
Linux sys-mythtv 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```

```
demonbob@sys-mythtv:~$ getconf LONG_BIT
32

```

> **kasulstyls said:**
> Same thing for me on 32bit!

Is it just mythvideo (and other plugins) that don't work? Does livetv/recorded tv work?

---

### Post by Akriss on 2010-05-02
> **tgm4883 said:**
> Is it just mythvideo (and other plugins) that don't work? Does livetv/recorded tv work?

If it helps at all. Live / recorded are the only working options. Thats on 64bit system.

---

### Post by kasulstyls on 2010-05-02
so far just the video and the music have the issue. when highlighting the video button and selecting it, I get no response. When i choose music, (i cant remember the exact error ) says the plugin needs to be built.

Livetv works and i have not recorded any yet. As my Livetv has been a little flaky.  
[http://ubuntuforums.org/showthread.php?t=1467656](http://ubuntuforums.org/showthread.php?t=1467656)

---

### Post by tgm4883 on 2010-05-02
Yea read my previous response as to why this happens. Take a look at the page and see if mythplugins has built yet.

---

### Post by Akriss on 2010-05-02
> **tgm4883 said:**
> 
Once these get built (and mythplugins gets built as well to resolve the mythvideo part), you will need to do the updates again so it will upgrade everything to the right build. Alternatively, you may be able to fire up Synaptic and Force an older build number.



Yup! just waiting for my BE to finish a recording.

---

### Post by Al_Vampyre on 2010-05-04
I got caught by this one last night, I note on the page that was mentioned that there are currently 5 pending builds, is checking the webpage the only way to avoid this?

---

### Post by williammanda on 2010-05-04
Just wanted to report I had the same issue on 32 bit. When I went to check for an upgrade the version for 32 bit was the same 24344 but the 64 bit was 24358. Both versions seem to be working now.

---

### Post by AndrewSJGrant on 2010-05-06
Hi

I think i'm having the same problem. I've upgraded both Backend and Remote Frontend to Ubuntu 10.04 and MythTV 0.23. I seem to have the backend working fine. The frontend is connecting all ok and can see the the recorded programmes and watch them.

The problem i'm having is that I can't get MythVideo to work. I can't install plugins through MythBuntu Control Center as it comes up with the error 'Requires installation of untrusted packages. The action would require the installation of packages from unauthenticated sources.'

To get around this I then installed the plugins through Terminal 'sudo apt-get install mythplugins.
These installed fine but when I tried running MythVideo (the only one I use) I get this: Plugin mythvideo is not compatible with the installed MythTV libraries. Please recompile the plugin after a make distclean.

Can anyone help me on this?

Thanks

Andrew

---

### Post by tgm4883 on 2010-05-06
Sounds like you enabled a different repo. what do you have listed in /etc/apt/sources.list file and in the /etc/apt/sources.list.d/ directory

---

### Post by continuous on 2010-05-10
> **tgm4883 said:**
> 
Once these get built (and mythplugins gets built as well to resolve the mythvideo part), you will need to do the updates again so it will upgrade everything to the right build. Alternatively, you may be able to fire up Synaptic and Force an older build number.

I'm currently seeing if there is a way to make sure this doesn't happen in the future.

OK, kind of get what you are saying, but now it's a few days later and updates haven't helped. How do I 'force an older build number' via synaptic, or should I wait a little longer?

---

### Post by tgm4883 on 2010-05-10
> **continuous said:**
> OK, kind of get what you are saying, but now it's a few days later and updates haven't helped. How do I 'force an older build number' via synaptic, or should I wait a little longer?

If you are still experiencing this issue then you likely either A) are experiencing a different issue, or B) don't have your updates done.

What is the output of the following commands 

```
dpkg -l mythtv-frontend
dpkg -l mythtv-backend
dpkg -l mythvideo
```

---

### Post by digiital on 2010-05-11
I'm having the same issue, none of my videos play. 

```

david@david-desktop:~$ dpkg -l mythtv-frontend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythtv-frontend                   0.23.0+fixes24509-0ubuntu0+mythbu A personal video recorder application (client)
david@david-desktop:~$ dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythtv-backend                    0.23.0+fixes24509-0ubuntu0+mythbu A personal video recorder application (server)
david@david-desktop:~$ dpkg -l mythvideo
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythvideo                         0.23.0+fixes24509-0ubuntu0+mythbu A generic video player frontend module for MythTV


```

> **tgm4883 said:**
> If you are still experiencing this issue then you likely either A) are experiencing a different issue, or B) don't have your updates done.

What is the output of the following commands 

```
dpkg -l mythtv-frontend
dpkg -l mythtv-backend
dpkg -l mythvideo
```

---

### Post by tgm4883 on 2010-05-11
> **digiital said:**
> I'm having the same issue, none of my videos play. 

```

david@david-desktop:~$ dpkg -l mythtv-frontend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythtv-frontend                   0.23.0+fixes24509-0ubuntu0+mythbu A personal video recorder application (client)
david@david-desktop:~$ dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythtv-backend                    0.23.0+fixes24509-0ubuntu0+mythbu A personal video recorder application (server)
david@david-desktop:~$ dpkg -l mythvideo
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythvideo                         0.23.0+fixes24509-0ubuntu0+mythbu A generic video player frontend module for MythTV


```

The good news is you have the same version across your installs packages. The bad news is that the issue you are facing is a different issue than this one. Please open a new thread and post the logs from your frontend there.

---

