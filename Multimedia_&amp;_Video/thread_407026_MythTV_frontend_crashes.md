---
title: "MythTV frontend crashes"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by tuco penguin on 2007-04-11
Any help here appreciated...

I was "trying out" MythTV on my main desktop, running Ubuntu Edgy with MythTV backend and frontend.  Mostly happy with the results, I decided to buy an old used Dell to serve as a dedicated MythTV backend, slimserver, and cups print server.  I believe I got mythtv backend installed and running on the backend, and I'm ready to see TV pictures to confirm my optimism.  Having uninstalled my tuner card (Hauppauge PVR-500) from my desktop machine during the migration, I also uninstalled all IVTV and mythtv backend software using Synaptic.  Then I tried to run mythtv setup to point it to the new backend.  Instead of running, my X session restarted and I found myself at a fresh Ubuntu login screen.  Tried running myth frontend.  Same result.  Tried complete uninstall of all mythtv software, then reinstall.  Same result.  I'm not sure how to connect to my new backend and see it working now.](*,) 

Is there some lower level test I can do to scout out the source of the problem.  A useful log file to look at?  Or maybe my story raises a red flag and there is an easy fix at hand?

Thanks in advance for any help.

---

### Post by majoridiot on 2007-04-12
install ssh on the backend:

```
sudo apt-get install openssh-server
```

once it is installed, connect to the backend from the frontend machine via ssh:

```
ssh user@your.backend.network.address
```

then run the backend from the terminal... 

```
sudo /etc/init.d/mythtv-backend restart
```

you will get a good idea of what might be happening by watching the output.


the backend error log is located at /var/log/mythtv/mythbackend.log and will also show what might be
going on.

you can also try a remote ssh running of the frontend by forwarding an X session to your frontend-

```
ssh -X -Y user@your.backend.network.address
```

and then run mythfrontend from the terminal to see what sorts of errors it generates.

you might try following the official Ubuntu install guides, as well:  [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by tommyp on 2007-04-12
I, too, have this problem, though I am running on a desktop, combined back/front.  This problem just started within the last couple of days (after some of the latest ubuntu auto updates - maybe this had something to do with it)

Has anyone found a cause / solution?

---

### Post by tuco penguin on 2007-04-12
Well, the only message generated when restarting mythtv backend is "." which I take as a good sign.  The log file is nonexistent (at least in that directory.)  Does that mean no errors?  (And yes, ssh and networking are all working OK.)

When I originally followed the mythtv backend only setup at help.ubuntu.com there is a section near the end that says:
> 
Check that the backend successfully started:

```
$ ps -p `cat /var/run/mythtv/mythbackend.pid`
```

If you don't see output like:

```
    
        PID TTY          TIME CMD
      30711 ?        00:00:00 mythbackend
```

then there was an error. Check the backend log file for obvious errors:


After a couple of false starts, I finally got the output as described, so I figured the backend was OK.  I never checked the log because my error was fairly easy to track down (although right now I don't recall what it was.)  I really have the sense that this is a frontend error.  On execution the screen goes black almost immediately and never makes any indication that it has even connected to the backend.  Come to think of it, it couldn't connect to the back end because I have yet to configure it with the correct IP address for the backend... unless there is some sort of autodetection built in.  My recollection was that my first time around I had to point the frontend to the backend IP address.  I was expecting to do that step next but just can't get there.  My worry is that somehow, despite a "complete" uninstallation and reinstallation, mythtv frontend is still starting up and trying to find the nonexistent backend server on the desktop machine.

One other thought:  I uninstalled my tuner card from my desktop machine before uninstalling any software (IVTV or mythtv backend.)  Also, I uninstalled the software without explicitly stopping the backend server running on the desktop--although I would hope Synaptic is smart enough to handle that, maybe mythtv frontend is not...

Anyone else had problems since recent Ubuntu updates?  Maybe all this migrating backend stuff is just a red herring?

My apologies if I can not follow this thread until next week.  I leave tomorrow morning on vacation (away from the computers) and won't be back until Sun. night.  Any posts with ideas in the meantime are still greatly appreciated.

Cheers!

---

### Post by majoridiot on 2007-04-12
sorry for the typo- the backend log is in /var/log/mythtv/mythbackend.log on the backend machine

see if you have the hidden folder .mythtv in your home directory on the frontend machine-

```
$ ls -a ~
```

if it is not there, then make one:

```
$ mkdir ~/.mythtv
```

then, copy /etc/mythtv/mysql.txt from your backend machine to the hidden .mythtv folder on your frontend

next, run the frontend from a terminal with:

```
$ mythfrontend
```

even if the screen blacks out, you should still be able to see what errors it generates in the terminal
after you exit.  depending on the speed of your machines, it may take awhile to get things started,
so be patient.

---

### Post by tuco penguin on 2007-04-12
Thanks for the quick reply.  Because the GUI completely restarts when this happens, I am not able to see the contents of the terminal after the "crash."  However, some error messages do roll by before the screen blanks, so on one instance I have CTRL+C'd before the screen went blank and found these very telling error messages right off (no text omitted from beginning of output):
```
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
2007-04-12 23:07:40.970 Using runtime prefix = /usr
2007-04-12 23:07:41.027 Gnome-Screensaver support enabled
2007-04-12 23:07:41.027 DPMS is active.
2007-04-12 23:07:41.226 New DB connection, total: 1
2007-04-12 23:07:41.322 Connected to database 'mythconverg' at host: 192.168.0.10
2007-04-12 23:07:41.372 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-12 23:07:41.403 Using screen 0, 1440x900 at 0,0
2007-04-12 23:07:41.497 Current Schema Version: 1160
2007-04-12 23:07:41.498 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-04-12 23:07:41.502 Enabled verbose msgs:  important general


```
I notice that it is in fact now connected to the correct backend server (after I edited mysql.txt, thanks for that tip!)  But those X errors... still looking for the tuner card in the wrong box perhaps?

---

### Post by majoridiot on 2007-04-12
> **tuco penguin said:**
> I notice that it is in fact now connected to the correct backend server (after I edited mysql.txt, thanks for that tip!)  But those X errors... still looking for the tuner card in the wrong box perhaps?

ignore those errors... they are "standard" as it were.  press on and see where you stand with things-
you are obviously connecting to the DB now.  i'd start with deleting ALL tuners AND sources and 
setting up from scratch.

if you think the frontend is still having probs, launch it with this command to log all output so you can 
take a look:

```
$ mythfrontend 2>&1 >> frontend.log
```

---

### Post by Erlander on 2007-04-12
I get the same X errors on a working install of Mythtv and have presumed all along that they are from my remote that is not correctly setup with lirc.

```
rob@Ubuntu:~$ mythfrontend
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
2007-04-13 13:26:13.833 Using runtime prefix = /usr
2007-04-13 13:26:13.867 Gnome-Screensaver support enabled
2007-04-13 13:26:13.867 DPMS is active.
2007-04-13 13:26:14.081 New DB connection, total: 1
2007-04-13 13:26:14.154 Connected to database 'mythconverg' at host: 192.168.2.3
2007-04-13 13:26:14.155 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-13 13:26:14.158 Running in a window
2007-04-13 13:26:14.158 Using screen 0, 1024x718 at 0,25
2007-04-13 13:26:14.177 Current Schema Version: 1160
2007-04-13 13:26:14.177 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-04-13 13:26:14.177 Enabled verbose msgs:  important general
2007-04-13 13:26:14.627 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-13 13:26:14.629 Running in a window
2007-04-13 13:26:14.629 Using screen 0, 1024x718 at 0,25
2007-04-13 13:26:14.629 Switching to square mode (G.A.N.T.)
2007-04-13 13:26:14.672 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-04-13 13:26:15.150 Joystick disabled.
2007-04-13 13:26:15.602 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-04-13 13:26:15.705 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-13 13:26:15.787 Registering Internal as a media playback plugin.
2007-04-13 13:26:23.569 New DB connection, total: 2
2007-04-13 13:26:23.570 Connected to database 'mythconverg' at host: 192.168.2.3
2007-04-13 13:26:23.604 Connecting to backend server: 192.168.2.3:6543 (try 1 of 5)
2007-04-13 13:26:23.620 Using protocol version 31
2007-04-13 13:26:23.628 TV: Attempting to change from None to WatchingLiveTV
2007-04-13 13:26:23.629 Using protocol version 31
2007-04-13 13:26:23.742 DPMS Deactivated 
2007-04-13 13:26:23.763 NVP: Disabling Audio, params(-1,2,44100)
2007-04-13 13:26:23.784 VideoOutputXv: XvMCTex: Init failed
2007-04-13 13:26:23.785 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x1b4
2007-04-13 13:26:24.490 TV: Changing from None to WatchingLiveTV
2007-04-13 13:26:24.491 New DB connection, total: 3
2007-04-13 13:26:24.492 Connected to database 'mythconverg' at host: 192.168.2.3
2007-04-13 13:26:24.516 Realtime priority would require SUID as root.
[mpegts @ 0xb72a6ec0]Parser not found for Codec Id: 94211 !
2007-04-13 13:26:24.810 Video timing method: SGI OpenGL
2007-04-13 13:26:27.094 NVP: Prebuffer wait timed out 10 times.
2007-04-13 13:26:28.042 VideoOutputXv: XvMCTex: Init failed
2007-04-13 13:26:28.043 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x1b4
2007-04-13 13:26:28.296 AFD: Opened codec 0x9dd6fd0, id(MPEG2VIDEO) type(Video)
2007-04-13 13:26:28.313 AFD: Opened codec 0x9dd5f70, id(MP3) type(Audio)
2007-04-13 13:26:28.314 AFD: Opened codec 0x9dd6570, id(AC3) type(Audio)
2007-04-13 13:26:28.315 AFD: Opened codec 0x9deae00, id(MPEG2VIDEO) type(Video)
2007-04-13 13:26:28.370 Opening OSS audio device '/dev/dsp'.
2007-04-13 13:26:28.378 NVP: Enabling Audio
2007-04-13 13:26:31.417 NVP: prebuffering pause
2007-04-13 13:26:43.943 TV: Attempting to change from WatchingLiveTV to None
2007-04-13 13:26:44.635 TV: Changing from WatchingLiveTV to None
2007-04-13 13:26:44.638 DPMS Reactivated.
rob@Ubuntu:~$ 
```

Yes, I'm getting other errors too.

Rob

---

### Post by tuco penguin on 2007-04-12
frontend.log contains only:

```
2007-04-12 23:43:34.952 Using runtime prefix = /usr
2007-04-12 23:43:34.984 Gnome-Screensaver support enabled
2007-04-12 23:43:34.985 DPMS is active.
2007-04-12 23:43:35.432 New DB connection, total: 1
2007-04-12 23:43:35.469 Connected to database 'mythconverg' at host: 192.168.0.$
2007-04-12 23:43:35.473 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-12 23:43:35.478 Using screen 0, 1440x900 at 0,0
2007-04-12 23:43:35.498 Current Schema Version: 1160
2007-04-12 23:43:35.498 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 23:43:35.499 Enabled verbose msgs:  important general
2007-04-12 23:43:36.971 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-12 23:43:36.973 Using screen 0, 1440x900 at 0,0
2007-04-12 23:43:36.974 Switching to square mode (G.A.N.T.)
```

I will ssh back to the backend again and step through all the setup steps again, deleting all tuners and sources.  If time permits I will post results before turning in for the night, otherwise I'll return to this next week.  Thanks for the kind help, majoridiot :)

---

### Post by majoridiot on 2007-04-13
yeah... it looks like the frontend is starting up fine.

deleting the cards and tuners and re-configuring them is definitely the next step to take.

if it's a fairly new install and you don't have a lot of recorded videos and db data, you can always just
drop the database and start with a fresh one if you reach that point of frustration. ;)

EDIT: it's late and i'm tired... just noticed this:

> 2007-04-12 23:43:35.469 Connected to database 'mythconverg' at host: 192.168.0.$

and if that was all that was in the logfile, then there is a problem- it should have gotten farther than that.
the next step is to paint the screen, which is where you are crashing and there is no indication it is even
trying.

check your ~/.mythtv/mysql.txt and make sure it contains the correct address of the backend on your
network.

if you got a kernel update, it could have possibly broken your video driver. if you a running the proprietary
nvidia or ati drivers, reinstalling might fix it if it is trying to paint with opengl.

---

### Post by tuco penguin on 2007-04-13
On remote server, I stopped mythbackend, ran mythbackend setup, deleted all tuners, deleted all sources, set up tuners and sources again, ran /etc/cron.daily/mythtv-backend, started mythbackend.  Then on local frontend, ran mythfrontend again.  Same result--Gnome shuts down completely and I find myself at a fresh login screen.

FWIW, when I exit the myth setup, I get an error message to the effect "Card 0 is set to channel 2 which does not exist.  Do you want to continue?"  (not verbatim)  In fact, I set my tuners to channel 5 and 7 which do exist--card 0 is some other ghost beast.  I tried to fix the problem before exiting and could not locate the "card" referred to in the error message.  I definitely had this message the first time I setup the backend in the new box a couple days ago (and possibly when I set it up in the old desktop box a couple months ago, too.)  Am I getting closer...

The output to frontend.log this time (no errors that I can see)

```
                 
2007-04-12 23:43:34.952 Using runtime prefix = /usr
2007-04-12 23:43:34.984 Gnome-Screensaver support enabled
2007-04-12 23:43:34.985 DPMS is active.
2007-04-12 23:43:35.432 New DB connection, total: 1
2007-04-12 23:43:35.469 Connected to database 'mythconverg' at host: 192.168.0.10
2007-04-12 23:43:35.473 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-12 23:43:35.478 Using screen 0, 1440x900 at 0,0
2007-04-12 23:43:35.498 Current Schema Version: 1160
2007-04-12 23:43:35.498 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-04-12 23:43:35.499 Enabled verbose msgs:  important general
2007-04-12 23:43:36.971 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-12 23:43:36.973 Using screen 0, 1440x900 at 0,0
2007-04-12 23:43:36.974 Switching to square mode (G.A.N.T.)
2007-04-13 00:25:07.564 Using runtime prefix = /usr
2007-04-13 00:25:08.180 Gnome-Screensaver support enabled
2007-04-13 00:25:08.180 DPMS is active.
2007-04-13 00:25:09.051 New DB connection, total: 1
2007-04-13 00:25:09.124 Connected to database 'mythconverg' at host: 192.168.0.10
2007-04-13 00:25:09.128 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-13 00:25:09.134 Using screen 0, 1440x900 at 0,0
2007-04-13 00:25:09.157 Current Schema Version: 1160
2007-04-13 00:25:09.158 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-04-13 00:25:09.158 Enabled verbose msgs:  important general
2007-04-13 00:25:10.349 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-13 00:25:10.351 Using screen 0, 1440x900 at 0,0
2007-04-13 00:25:10.352 Switching to square mode (G.A.N.T.)

```

Don't think I can finish this tonight, as much as I want to... zzzzzzz....

---

### Post by majoridiot on 2007-04-13
i was editing when you were posting LOL-

EDIT: it's late and i'm tired... just noticed this:

> 2007-04-12 23:43:35.469 Connected to database 'mythconverg' at host: 192.168.0.$

and if that was all that was in the logfile, then there is a problem- it should have gotten farther than that.
the next step is to paint the screen, which is where you are crashing and there is no indication in the log
it is even trying.

check your ~/.mythtv/mysql.txt and make sure it contains the correct address of the backend on your
network.

if you got a kernel update, it could have possibly broken your video driver. if you a running the proprietary
nvidia or ati drivers, reinstalling might fix it if it is trying to paint with opengl.

---

### Post by majoridiot on 2007-04-13
also- that tuner error is very common when the db has issues.  i have  fought it myself many times.

one step at a time- get the frontend to connect then fix the database or just drop it and start again.

---

### Post by tuco penguin on 2007-04-13
Front end is connecting, as you can see from the log posted above... "$" was just my sloppy cut and paste from a nano window that was not wide enough for all the text.  Sorry bout that.

This video driver thing actually sounds like a possibility.  From time to time I have noticed my machine having some video issues--screen going blank for one or two seconds every minute or so.  It usually doesn't last and I never traced it to any updates (is not happening right now), but it certainly could correlate to updates and I never noticed it.  I do recall having this pop up about a week ago and I never re-ran myth in the all-in-one configuration between that incident and the hardware migration to the new box so it could be related to the video driver and not the tuner card move.

Now I will have to hunt down how to install that video driver (XFX 5200, nvidea, but I don't recall where I got them.)  Thanks again.  Signing out.  'nite.

---

### Post by majoridiot on 2007-04-13
you should have more in the frontend log... where it selects the painter and then connects to the db.
here's a copy from a fresh connect on my frontend:

> 2007-04-12 22:21:59.865 Using runtime prefix = /usr
2007-04-12 22:21:59.888 Gnome-Screensaver support enabled
2007-04-12 22:21:59.888 DPMS is active.
2007-04-12 22:21:59.906 New DB connection, total: 1
2007-04-12 22:21:59.922 Connected to database 'mythconverg' at host: 192.168.1.100
2007-04-12 22:21:59.923 Total desktop dim: 1280x1024, with 2 screen[s].
2007-04-12 22:21:59.926 Using screen 1, 1280x1024 at 0,0
2007-04-12 22:21:59.941 Current Schema Version: 1160
2007-04-12 22:21:59.941 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 22:21:59.941 Enabled verbose msgs:  important general
2007-04-12 22:22:00.231 Total desktop dim: 1280x1024, with 2 screen[s].
2007-04-12 22:22:00.232 Using screen 1, 1280x1024 at 0,0
2007-04-12 22:22:00.233 Switching to square mode (Titivillus)
2007-04-12 22:22:00.247 Using the OpenGL painter <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
2007-04-12 22:22:00.543 Joystick disabled.
2007-04-12 22:22:00.544 New DB connection, total: 2
2007-04-12 22:22:00.559 Connected to database 'mythconverg' at host: 192.168.1.100
2007-04-12 22:22:00.973 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 22:22:01.249 Registering Internal as a media playback plugin.
2007-04-12 22:22:01.407 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2007-04-12 22:22:01.408 Using protocol version 31
2007-04-12 22:22:04.333 Using NV NPOT texture extension

as you can see, you aren't making it past the paint method.

envy is a very good way to install the latest nvidia drivers: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jduckles on 2007-04-14
I was having the same problem.  A reinstall of the NVIDIA binary drivers fixed it.

---

### Post by OldGaf on 2007-04-14
I got this before and had to reinstall my nVidia drivers...... I got some messsage during the reinstall about a symbolic link problem it had to fix. Anyway, I got it a few times after installing myth. Reinstalling my nVidia always fixes it for me.

Now I have a problem with the whole thing locking up when using the program guide:

[http://ubuntuforums.org/showthread.php?t=409233]("http://ubuntuforums.org/showthread.php?t=409233")

---

### Post by tuco penguin on 2007-04-17
Thanks everyone for the input, esp. majoridiot.

I used Envy to re-install my nvidea drivers and the crash has gone away.  I am now connecting to my backend master server and running mythtv!  (It's a little slow... maybe another post, another day.)

One interesting side note FWIW:  Once I suspected the video driver, I started poking around my nvidea display setup utility.  When I clicked on OpenGl settings to see what it said, the screen blanked and I lost my X session--just like my original MythTV crash.  Next thing I did was download and install envy, then run it.  All was good.

Ciao!

---

### Post by majoridiot on 2007-04-17
glad you got it working! :)

you can check for errors in a couple of places to try and root out your "slowness"

```
 nano /var/log/mythtv/mythbackend.log
```

is the backend log and will show you what's going on with the backend; also look at 

```
$ dmesg
```

to see if there are any obvious errors there.

---

