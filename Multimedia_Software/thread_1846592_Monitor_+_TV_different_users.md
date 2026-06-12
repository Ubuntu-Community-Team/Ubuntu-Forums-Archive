---
title: "Monitor + TV different users"
date: 2011-09-19
forum: Multimedia Software
---

### Post by grouchomrx on 2011-09-19
Hi,

I've been reading and testing a lot, and I don't find the solution for what I want to do...

Situation:
Ubuntu Natty
nVidia 9800GT (2 dvi output)
Samsung 1600x1050 monitor 
1920x1080 TV with a DVI to HDMI adapter and internally connected spdif from motherboard to graphic card

Well, everything works properly when I select the TV as an extension of the monitor, I get the fullHD resolution, the sound... everything perfect.

But now, what I want to do is the next:

1. The login screen does not appear in both monitors, so I'd like it in both. In addition, login screen appears in the monitor it wants, and not in the main monitor (where main panel appears)... I don't know how to control it.

2. I'd to create 2 different users or hardware profiles. The first one should have only the monitor active (not the TV). The second one should have only the TV active.

In this situation, if I want to see a movie, I select the second user, so I've the full desktop in my TV. When I want to work with the PC, I select the first user and I see everything on my monitor.

I think in Windows this can be done using Hardware Profiles, so I guess there is a way to get that in Ubuntu.

Thank you in advance.
Best regards.

---

### Post by grouchomrx on 2011-09-19
I'm sorry, I forgot... 

Both profiles should have too different audio configuration. The only change needed is the audio output selection, the "monitor profile" should have analog audio, and the "tv profile" digital audio.

It's easy to change this selection from gnome-audio-settings, but I don't know how to select it automatically as the user login.

---

### Post by grouchomrx on 2011-09-21
No ideas?

---

### Post by aeiah on 2011-09-21
i achieve this in a different way. i have a monitor and hdtv permanently plugged into my machine, as you do. i have my machine set up just to use my normal monitor, and when i want to start up xbmc to watch videos on the hdtv, i run a script that creates a new X session on the hdtv and switches to it (activated by remote :cool: ). its a bit cleaner than switching users, although it does involve root privilages :|

its an nvidia 7800GT and i use ubuntu 10.04, but things should be similar.

basically i do this in a script:
```

# x server environment setup
X :1 -layout hdtv &
export DISPLAY=:1.0

# graphics sync settings
nvidia-settings -a :1.0/SyncToVBlank=1 &
nvidia-settings -a :1.0/AllowFlipping=1 &
nvidia-settings -a :1.0/XVideoTextureSyncToVBlank=1 &
nvidia-settings -a :1.0/XVideoBlitterSyncToVBlank=0 &

# launch xbmc
xbmc;

```

-layout hdtv is a layout specified in my xorg.conf. here's a post that talks about it: [http://ubuntuforums.org/showpost.php?p=8835078&postcount=2](http://ubuntuforums.org/showpost.php?p=8835078&postcount=2)

you might not have a xorg.conf, but should be able to generate one with nvidia-settings unless things have changed a lot.

---

### Post by aeiah on 2011-09-21
oh, and as for your audio stuff - i guess you'll have to find a way to do it on the command line. there'll be a way, either through pulse audio or alsa. you could add it to the launch script. like i said, i launch mine with a remote not a login screen, but there's no reason why you cant run the script at login.

---

### Post by jawilljr on 2011-09-21
> **aeiah said:**
> i achieve this in a different way. i have a monitor and hdtv permanently plugged into my machine, as you do. i have my machine set up just to use my normal monitor, and when i want to start up xbmc to watch videos on the hdtv, i run a script that creates a new X session on the hdtv and switches to it (activated by remote :cool: ). its a bit cleaner than switching users, although it does involve root privilages :|

its an nvidia 7800GT and i use ubuntu 10.04, but things should be similar.

basically i do this in a script:
```

# x server environment setup
X :1 -layout hdtv &
export DISPLAY=:1.0

# graphics sync settings
nvidia-settings -a :1.0/SyncToVBlank=1 &
nvidia-settings -a :1.0/AllowFlipping=1 &
nvidia-settings -a :1.0/XVideoTextureSyncToVBlank=1 &
nvidia-settings -a :1.0/XVideoBlitterSyncToVBlank=0 &

# launch xbmc
xbmc;

```

-layout hdtv is a layout specified in my xorg.conf. here's a post that talks about it: [http://ubuntuforums.org/showpost.php?p=8835078&postcount=2](http://ubuntuforums.org/showpost.php?p=8835078&postcount=2)

you might not have a xorg.conf, but should be able to generate one with nvidia-settings unless things have changed a lot.

There's another way to get XBMC on the second without needing root privileges.

I used [these instructions](http://blog.burlock.org/xbmc/77-fullscreen-xbmc-without-locking-the-mouse) and the script provided.

You need wmctrl installed:

```
sudo apt-get install wmctrl
```

Next using nvidia-settings set up using separate X servers...do not enable xinerama. Me I put the TV "Right Of" the main monitor.

Save the X configuration then reboot.

Set up XBMC so it in windowed mode and close it.

Use this script to run XBMC:

```
#! /bin/bash
# Launch XBMC in windowed mode, then use wmctrl to remove the titlebar
	 
# Select display 1
DISPLAY=:0.1
 
# Start XBMC without blocking this script
xbmc &
	 
# Wait for the XBMC window to appear
status=0
while [ $status -eq 0 ]
do
    sleep 1
    status=`wmctrl -x -l | grep "XBMC Media Center" | wc -l | awk '{print $1}'`
done
 
# Force XBMC window to fullscreen
wmctrl -x -r XBMC Media Center.XBMC Media Center -b toggle,fullscreen
```

---

