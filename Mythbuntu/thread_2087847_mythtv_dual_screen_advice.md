---
title: "mythtv dual screen advice"
date: 2012-11-24
forum: Mythbuntu
---

### Post by milesnorth on 2012-11-24
I've been running mythtv under Kubuntu for about 3-years plus now with much thanks in the past to this forum.  My son recently handed down an iZ monitor for the home theatre so we don't have to run the Epson projector all the time.

I noticed under the nvidia x server settings that there are separate x screen, twinview, and xinerama settings.  I recall reading that xinerama requires monitors with the same bit depth, so I guess that option is out.   Do forum members have preferred ways of setting up two monitors for home theatre usage?  Are there ways to configure mythtv to run on the projector screen?  To setup desktops for each monitor?  

I know I'm a bit vague, but any insights to this process would be appreciated.  I have Kubuntu 12.04, Mythtv 0.25, an Epson 8500UB 12-bit color depth projector, and an iZ 3d 8-bit LCD monitor.   I'm slightly competent in linux.

Thanks,
Kurt

---

### Post by BicyclerBoy on 2012-11-24
My preference is separate X screens.
Twinview requires all screens to have same refresh rate & it confuses most full screen apps.
The Xorg xinerama is (was) not recommended as it limits nvidia driver performance. (the internal xinerama extension is something else)..

It is easy enough to concoct a launching script to start mythtv on either screen & move mouse to it:
mythfrontend -display :0.1  --geometry XxY --etc.
I can post one if you are interested..

The display option keyword seems to break the "-w" == "--word" rule..

The composite effects manager in kde may or may not mess up full screen redirection & cause VDPAU to use blitter (possible tearing) instead of video overlay.
You may need to find/set "un-redirect full screen".

---

### Post by milesnorth on 2012-11-26
> **BicyclerBoy said:**
> My preference is separate X screens.
Twinview requires all screens to have same refresh rate & it confuses most full screen apps.
The Xorg xinerama is (was) not recommended as it limits nvidia driver performance. (the internal xinerama extension is something else)..

It is easy enough to concoct a launching script to start mythtv on either screen & move mouse to it:
mythfrontend -display :0.1  --geometry XxY --etc.
I can post one if you are interested..

The display option keyword seems to break the "-w" == "--word" rule..

The composite effects manager in kde may or may not mess up full screen redirection & cause VDPAU to use blitter (possible tearing) instead of video overlay.
You may need to find/set "un-redirect full screen".

Appreciate the feedback.  I did try separate X screens and a little script from the Mythtv Howto pages.
```
#!/bin/sh
# Run MythTV front end on display 1
export DISPLAY=:0.1
mythfrontend
```Did a similar script for display 0 and managed to get two sessions of mythtv running and not being able to shift the focus with the mouse back to display 1.  

I haven't really scripted in linux before but I'll take a look at your script snippet.  I may not be a cook but I can usually follow a recipe, so any further examples would be helpful. 

Additionally, is it hard to check if a mythtv process is already running and kill it when you want to restart mythtv back in the other X session?  Should I try to get a menu toolbar running on display 1 to fire up a couple of other programs like Dolphin, SMPlayer, and a browser?

Thanks,
Kurt

---

### Post by BicyclerBoy on 2012-11-26
Here's my start script.
```

#!/bin/sh
# Run MythTV front end on display :0.1
export HOME=/home/user_xx

# EXTRA_ARGS="--logpath /var/log/mythtvfrontend/"                 # Note 3. (choose 1)
EXTRA_ARGS="--syslog local7"                           #
# note 3. --logfile is used prior to 0.25, use --logpath or --syslog with 0.25 and above. See Logging. 

ARGS="-display :0.1"

RUNNING=0
message="Already running"

for x in `ps -C mythfrontend | grep -v PID` end; do
    test $x != 'mythfrontend' && continue
    RUNNING=1;
done

# put the mouse back.
`xwit $ARGS -root -warp 520 1080`

if [ $RUNNING = 1 ]; then
    `/usr/local/bin/mythutil --message --message_text "$message" --timeout 5 --syslog local7 --bcastaddr 192.168.1.xx`
else
    export MYTHTV_AIRPLAY="1"
    `mythfrontend $ARGS $EXTRA_ARGS`
fi
exit 0

```

You can run multiple frontends on same X server but there is some trick to allow unique identification (some control file or env var MYTHCONFDIR).
If you use IR remote then the screen focus does not matter..

---

### Post by milesnorth on 2012-11-27
> **BicyclerBoy said:**
> Here my start script.

Got it.  Changed the user, ip addr., mythutil subdirectory, and installed xwit.  It works fine and dandy.

Much appreciated

---

