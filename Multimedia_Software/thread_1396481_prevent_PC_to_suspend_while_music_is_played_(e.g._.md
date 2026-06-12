---
title: "prevent PC to suspend while music is played (e.g. Songbird)"
date: 2010-02-02
forum: Multimedia Software
---

### Post by produnis on 2010-02-02
While Rhythmbox and Amarok are able to prevent suspend while music is played, this won't work with e.g. Songbird.

Here is my hack to prevent suspend while Songbird plays music.

1. Install Songbird-Add-On "Pause/Play/Stop" from [here]("http://www.mediafire.com/download.php?oejqzndwnad")  and find out how to install this Add-On on lates Songbird-Release by reading [the last comment of *stingray* here]("http://addons.songbirdnest.com/addon/48")

2. Install xmacro (sudo apt-get install xmacro)

3. Create a file called "myxmacro" and give it the following content:
```
MotionNotify 90 90 
MotionNotify 120 120
```4. Create a file "no.idle.sh" and make it executable:
```
touch no.idle.sh
chmod +x no.idle.sh
```Give it the following content:

```
#!/bin/bash
# No.idle.sh prevents GNOME to turn IDLE 
# if there is any sound sent to speakers
# This script requires the package "xmacro"
# (apt-get install xmacro)
###########################################
# This script requires a textfile called "myxmacro"
# with the following (dummy) content:
# ------------ myxmacro ------------
# MotionNotify 90 90 
# MotionNotify 120 120
# ----------------------------------
# You need to fix the path to "myxmacro" in line 31
#
#############################################

# set Log-File
LOG=/home/YOUR_USERNAME/noidle.log
sound=0
silence=0


while true; do
    sleep 1
    Datum=`date +%d.%m.%Y-%H:%M:%S`    
    
    # check if sound is sent to speaker    
    if pactl list | grep RUNNING > /dev/null; then
        echo "[$Datum] Sound (Ping: $sound)" >> $LOG
        sound=$((sound+1));
        xmacroplay :0 </path/to/myxmacro
        silence=0
    else
        echo "[$Datum] Silence (Ping: $silence)"    >> $LOG
        silence=$((silence+1));
        sound=0
    fi
    #----------------------------------------------------
done
```You need to:
- fix the path to the logfile in line 18
- fix the path to "myxmacro" in line 31


5. Add the script "no.idle.sh" to your GNOME-Startup-Items, so that no.idle.sh is running on every startup.

Done.


**What the script does:**
The script checks every second, if there is any sound sent to the speakers (using the terminal command *pactl list | grep RUNNING*).

If music is running, it simulates mouse-movement (using xmacroplay). This has the effect, that your GNOME-session won't run IDLE (and as a result your PC won't suspend).

If there is no music played, it does nothing (so your session IS ABLE to run IDLE and after that suspends)

You can watch the script checking for music by typing in a terminal:

```
tail -f /path/to/noidle.log
```(replace /path/to/noidle.log  with the actual path you edited in line 18 )


Unfortunately, Songbird will give a "NOT RUNNING" only, if the playlist has reached its end. If you just click "Pause",  *no.idle.sh*  will still think that there is music played. Therefore, you need to install the Songbird-Addon "Pause/Play/Stop" (see first step), which will add an original "Stop"-Button to Songbird's interface. So you need to click this "Stop"-Button in order to let no.idle.sh know, that music has stopped.

There won't be such a probem with other apps, e.g. Totem. If you click "Pause" in Totem, no.idle.sh will recognise this.

HAVE FUN:D

---

