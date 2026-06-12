---
title: "So close to perfect... then crashes"
date: 2008-06-05
forum: Mythbuntu
---

### Post by RFinn on 2008-06-05
So after months of puttering with MythTV on weekends I am finally ready to integrate it into my home theatre setup.

Everything works great except that when i try to exit live TV back to the menu by hitting Esc, the front end crashes and exits back to the OS. This also happens occasionally when exiting Mythvideo and on other seemingly random occasions.


If anyone has any hints on this it would make my day. 


I'm running version 8.04 with a PIII 850 MHz system, a Radeon 9600 Pro, Hauppage PVR 150, and 512mb ram

---

### Post by larsolav on 2008-06-05
What do the frontend and backend logs say when this happens? Maybe they can point you in the right direction?

/var/log/mythtv/mythfrontend.log 
/var/log/mythtv/mythbackend.log

Cheers!

---

### Post by JugeHuge on 2008-06-10
Hello. I have same problem with my setup..

Here is the mythbackend.log
```
2008-06-10 17:53:35.328 Seem to be woken up by USER
2008-06-10 17:53:35.330 Reschedule requested for id -1.
2008-06-10 17:53:35.348 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2008-06-10 17:53:49.981 MainServer::HandleAnnounce Monitor
2008-06-10 17:53:49.987 adding: juge-desktop as a client (events: 0)
2008-06-10 17:53:49.988 MainServer::HandleAnnounce Monitor
2008-06-10 17:53:49.989 adding: juge-desktop as a client (events: 1)
2008-06-10 17:53:49.997 MainServer::HandleAnnounce Playback
2008-06-10 17:53:49.998 adding: juge-desktop as a client (events: 0)
2008-06-10 17:53:50.001 TVRec(1): Changing from None to WatchingLiveTV
2008-06-10 17:53:50.010 TVRec(1): HW Tuner: 1->1
2008-06-10 17:53:50.044 New DB connection, total: 4
2008-06-10 17:53:50.052 Connected to database 'mythconverg' at host: localhost
2008-06-10 17:53:51.143 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-06-10 17:53:51.436 Finished recording TV2: Pikku Kakkonen: channel 1002
2008-06-10 17:53:52.528 Finished recording TV2: Pikku Kakkonen: channel 1002
2008-06-10 17:53:52.619 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-06-10 17:53:52.841 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-10 17:53:52.848 Empty LocalHostName.
2008-06-10 17:53:52.848 Using localhost value of juge-desktop
2008-06-10 17:53:52.856 New DB connection, total: 1
2008-06-10 17:53:52.860 Connected to database 'mythconverg' at host: localhost
2008-06-10 17:53:52.861 Closing DB connection named 'DBManager0'
2008-06-10 17:53:52.863 Connected to database 'mythconverg' at host: localhost
2008-06-10 17:53:52.864 New DB connection, total: 2
2008-06-10 17:53:52.865 Connected to database 'mythconverg' at host: localhost
2008-06-10 17:53:52.868 Current Schema Version: 1214
2008-06-10 17:53:52.877 Preview Error: Previewer file '/var/lib/mythtv/recordings/1002_20080610175350.mpg' is not valid.
2008-06-10 17:53:52.879 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1002_20080610175350.mpg'
2008-06-10 17:53:52.885 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20080610175350.mpg.png) exists: 0 readable: 0 size: 0
2008-06-10 17:54:04.412 TVRec(1): Changing from WatchingLiveTV to None
2008-06-10 17:54:04.502 Finished recording TV2: Pikku Kakkonen: channel 1002
```

and here is mythfrontend.log
```

2008-06-10 17:54:02.869 WriteAudio: buffer underrun
2008-06-10 17:54:03.675 NVP: prebuffering pause
2008-06-10 17:54:04.088 NVP: prebuffering pause
2008-06-10 17:54:04.345 TV: Attempting to change from WatchingLiveTV to None
2008-06-10 17:54:04.555 TV: Changing from WatchingLiveTV to None
```

---

### Post by lhommemagique on 2008-06-15
I'm having the same issue here. Running mythfrontend in a terminal produces a seg fault when trying to switch from live tv back to the main menu. Here is the relevant bits of the output.
```

2008-06-15 22:42:53.327 TV: Changing from None to WatchingLiveTV
2008-06-15 22:42:53.381 Realtime priority would require SUID as root.
2008-06-15 22:42:53.479 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-06-15 22:42:53.481 Video timing method: USleep with busy wait
2008-06-15 22:42:57.462 TV: Attempting to change from WatchingLiveTV to None
2008-06-15 22:42:57.620 TV: Changing from WatchingLiveTV to None
Segmentation fault

```

right now I'm running mythfront end from mythwelcome that way at least when the front end crashes mythwelcome will let me relaunch it from the couch with my remote.  I did not have this bug until updating to 8.04 a few days ago.  

My pc has similar specs except a faster cpu because I use this as a back and frontend.  intel 2.4 ghz, 512 ram, ati 9700 all-in-wonder pro, hauppauge 150 (usb version)

---

### Post by misterspider on 2008-06-15
I had the same problem with exiting, and swapped to nvidia graphics card. Haven't seen the problem again.

---

### Post by lhommemagique on 2008-06-15
It seems myhwelcome doesn't always load after crash but it works most of the time. 

I would also like to suggest that the title of this thread be changed to something more descriptive of the problem, that might drive a little more traffic to it and help others with the same issue to search for a resolution.

---

### Post by Namain on 2008-06-28
I've got the same bug. No solutions as of yet?

I've got an ATI X1600 card.  Here's my xorg.conf entry:

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Option          "EnableMonitor" "crt2"
        # Allows for accelerated video on this card
        Option          "TexturedVideo" "true"
        Option          "TVOverlay"
        Busid           "PCI:1:0:0"
EndSection

```

---

