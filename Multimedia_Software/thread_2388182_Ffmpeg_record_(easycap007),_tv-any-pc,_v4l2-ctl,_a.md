---
title: "Ffmpeg record (easycap007), tv-any-pc, v4l2-ctl, avidemux"
date: 2018-03-29
forum: Multimedia Software
---

### Post by xinuzi on 2018-03-29
I'm sorry, but an earlier post around this subject didn't display well.

(Tested on different older and newer laps with at least 4 GiB ram and at least usb2. All of them with Lubuntu LXDE X64.)

The subject contained these things:

**1) Reduce swappiness** of your system if you want to record from an input device.

```
sudo gedit /etc/sysctl.conf
```

('gedit' or some other text editor)

add to or change at bottom of file:

```
# Swappiness (originally 60)
vm.swappiness=10

```

**2) This FFmpeg bash recording script** to record/capture tv(PAL)-scart_OUT_plug-composite-EasyCap007-usb-pc:

Name: 'VID_FFmpeg_Record_x264-aac.sh'

```

#!/bin/bash

clear # Fresh terminal start

echo "FFMPEG RECORD X264 AAC"

echo

ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video1 -f alsa -thread_queue_size 1024 -i hw:2,0 -vcodec libx264 -preset superfast -tune film,zerolatency -crf 23 -s 640x360 -r 25 -aspect 16:9 -g 12 -acodec libvo_aacenc -b:a 128k -channels 2 -ar 48000 vid_$(date "+%Y%m%d_%H%M%S").mkv
```

Make it executable (everyone).

PAL, possibly NTSC or SECAM.

Check available FFmpeg version and codecs with:

```
ffmpeg -codecs
``` and with

```
ffmpeg -version
```

Set the right video input (/dev/video0; /dev/video1 etc) and audio device (hw:0,0; hw:1,0 etc) for your system. If unsure, possibly check in VLC Mediaplayer. Audio can easily be verified with code 'arecord -l' in terminal.

The very first time the ffmpeg code (script) will give you nothing (zeros) in the terminal window.

If the terminal window automatically closes on you the second time, it will probably be because you've put more than one space somewhere or you forgot a dash ('-') somewhere or you're using a '/dev/video*' input device with wrong number, and or audio device with wrong hw-settings and or an audio codec that isn't available in the ffmpeg-version you're using. The 'libvo_aacenc' audio codec in my ffmpeg recording code could very well be just 'aac' when you are using another ffmpeg version.
Audio codec 'libmp3lame' will work with as good as any ffmpeg version. AAC is supposed to be thé audio codec for video codec x264/h264, but mp3 has the advantage of as-good-as-aac quality and better-than-aac compatibility. 

Keep fps (Frames per Second) of output the same as of input to maintain a good video - audio synchronization. You can check these things with v4l2-ctl and in other ways, but, for PAL it's usually fps 25 ('-r 25') and for NTSC fps 30 ('-r 30').

'-g 12' = gop (key Iframe interval). Default 250. It is said that 15 is better for NTSC and 12 for PAL. Settings lower than 250 make aftercutting on keyframes in e.g. Avidemux more precise.
Alternatively you could set gop to the fps you're using '25' or '30'.

Other settings: see FFmpeg, V4L2 and x264 Documentation.

[B]3) Info on v4l2-ctl
[/B]
```

sudo apt-get install v4l2-utils

```

```
v4l2-ctl -d /dev/video1 -l 
```

to get the controls possibilities (of that specific '/dev/video1' device, in this case the location of the EasyCap007 'USBTV' input).

Controlling the controls can be bothersome, can be done with a bash script or with 'Qt V4L2 test Utility'

```
sudo apt-get install qv4l2
```

and this AFTER the ffmpeg recording starts running.

The effect can be viewed (with a certain delay) when you click the recording file and watch it in e.g. GNOME MPlayer.

Every ffmpeg recording will reset the controls settings to their defaults (or to sth unexpected).
(Actually the controls are resetting themselves.)

Under- and overexposure will often occur with the EasyCap007 (and with many other input devices). There's always a Close to Perfect View somewhere inbetween. Toggle (q)v4l2-ctl to find it in the given circumstances.

The default settings of my EasyCap007 (ID 1b71:3002 Fushicai USBTV007 Video Grabber [EasyCAP] ) are: 'brightness=448,contrast=464,saturation=512,hue=0' (and sometimes, depending on pc: 'sharpness=96').

You can run/Execute in Terminal ffmpeg recording script, open and fix on top the recording file in GNOME Mplayer and Execute in Terminal this  EasyCap007 (or possibly other input device) bash script (all in the same dir of course):

Name: 'VID_V4L2-ctl_Toggle_Settings.sh'

```

#!/bin/bash

clear

# Variables

control="v4l2-ctl -d /dev/video1 -c" # Set correct input device here; could be video0 according to device signal that comes in.
nexttext="[Enter] for next setting. If OK, Exit"

setting0="brightness=448,contrast=464,saturation=512,hue=0"
setting1="brightness=449,contrast=464,saturation=512,hue=0"
setting2="brightness=449,contrast=464,saturation=511,hue=0"
setting3="brightness=447,contrast=464,saturation=512,hue=0"
setting4="brightness=632,contrast=464,saturation=800,hue=0"
setting5="brightness=610,contrast=464,saturation=330,hue=0"
setting6="brightness=610,contrast=464,saturation=300,hue=0"
setting7="brightness=499,contrast=464,saturation=474,hue=0"
setting8="brightness=449,contrast=464,saturation=800,hue=0"
setting9="brightness=449,contrast=464,saturation=711,hue=0"

echo "V4L2-CTL TOGGLE"

echo

echo "Run this script after running FFmpeg Recording Script."
echo "Open the FFmpeg recording file with e.g. GNOME MPlayer (gnome-mplayer, gnome-mpv)."
echo "If image brightness and saturation okay in mplayer,"
echo "Exit this with Ctrl+c or with window X."

echo

echo "Start..."

echo

echo "Setting 0 (Defaults)"

echo $setting0

$control $setting0 2>/dev/null # hide errors

read -p "$nexttext" # Requires the double quotes

echo

echo "Setting 1"

echo $setting1

$control $setting1 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 2"

echo $setting2

$control $setting2 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 3"

echo $setting3

$control $setting3 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 4"

echo $setting4

$control $setting4 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 5"

echo $setting5

$control $setting5 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 6"

echo $setting6

$control $setting6 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 7"

echo $setting7

$control $setting7 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 8"

echo $setting8

$control $setting8 2>/dev/null # hide errors

read -p "$nexttext"

echo

echo "Setting 9"

echo $setting9

$control $setting9 2>/dev/null # hide errors

echo

echo "Reload script..."

echo

. ./VID_V4L2-ctl_Toggle_Settings.sh # File name has to be correct!


```

The script contains some of the best working settings for the EasyCap007 (but could work as well with any video input device).
Make executable (everyone).
First it sets the defaults.
Thereafter you manually toggle through the settings by entering and viewing the result in your player.
Give it some time each time. The signal needs to get sent back and forth.

At the end the whole script is reloaded in case the settings stay stubborn after going through all of them.

The '2>/dev/null' to deal with error message 'Invalid argument'. This error message doesn't prevent the script from interacting with the ffmpeg recording script.

[B][COLOR=#ff0000]4) Everything together in 1 launch script[/COLOR]

[/B]All of the above can be joined in 1 launch script that launches the FFmpeg recording, opens the recording file in GNOME MPlayer and launches the V4L2-ctl script to go through v4l2-ctl settings whilst viewing in the player:

Name: 'VID_START_FFmpeg_Record_x264_aac_MPlayer_V4L2-ctl.sh'

```

#!/bin/bash

clear

# Variables

outputfile="vid_$(date '+%Y%m%d_%H%M%S').mkv"

echo "START FFMPEG RECORD X264 AAC, GNOME MPLAYER VIEW, V4L2-CTL"

echo

echo "This script launches FFmpeg Record x264-aac code and"
echo "displays the resulting file in GNOME Mplayer and"
echo "opens V4L2-ctl Toggle script to tweak video image."
echo "Close any of the opened windows with Ctrl+c or with window X"

echo

ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video1 -f alsa -thread_queue_size 1024 -i hw:2,0 -vcodec libx264 -preset superfast -tune film,zerolatency -crf 23 -s 640x360 -r 25 -aspect 16:9 -g 12 -acodec libvo_aacenc -b:a 128k -channels 2 -ar 48000 $outputfile &

sleep 1

gnome-mplayer $outputfile &
# If not working, try 'gnome-mpv' or install it

sleep 1

x-terminal-emulator -e "./VID_V4L2-ctl_Toggle_Settings.sh"
# This should open Toggle script in new terminal window.
# Alternative code: gnome-terminal -e "bash ./VID_V4L2-ctl_Toggle_Settings.sh".
# 'sudo apt-get install gnome-terminal' on system if not present & if desired.

wait # let the original ffmpeg encoding continue

```

-> Everyone Executable.
-> Toggle script in same dir as this launch script of course.
[B]
5) Avidemux[/B]

Downloadable from the repositories, but the appImage at 

[http://fixounet.free.fr/avidemux/download.html](http://fixounet.free.fr/avidemux/download.html)

probably gives you the most recent, complete version.

Set executable rights of it.

Possibly shortcut to Desktop.

If Avidemux doesn't accept the recorderd matroska video, run this script in the recorded videos dir:

Name (e.g.): VID_SCRIPTS_FFMPEG_Convert_MKV_to_MKV_for_Avidemux.sh

```

#!/bin/bash

clear

echo "FFMPEG CONVERT STREAMCOPY MKV TO MKV FOR AVIDEMUX"

echo

for i in *.mkv; do ffmpeg -i "$i" -c copy "${i%.*}_reconverted_for_avidemux.mkv"; done

exit

```

- THE END -

---

### Post by xinuzi on 2018-03-29
O.M.G.
One of the reasons we should be able to easily remove our own posts.

---

### Post by QIII on 2018-03-29
If you could remove your own posts, think how messed up threads would get.

You can, however, edit all the html/php/whathaveyou tags and use bb tags.

Or, you could report the post and ask the staff to remove it.

---

### Post by xinuzi on 2018-03-31
*Reedited and simplified (although...) The Thing.*

---

### Post by xinuzi on 2018-04-12
Refined my **v4l2-ctl Toggle Script** (for 'James Bond' EasyCap007 USB videostick)  in the meantime.

See: first post.

Works well on Lubuntu X64, LXterminal.

Other input device -> probably other /dev/video* and other video image settings.

---

### Post by slickymaster on 2018-04-12
@xinuzi:

Please don't use 'Quote' tags to post output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of 'Code' tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by xinuzi on 2018-04-12
> **slickymaster said:**
> @xinuzi:

Please don't use 'Quote' tags to post output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of 'Code' tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

No problem.

Where do you see the problem exactly?

Could you 'quote' it? ;-)

I've put the coding in code tags as much as possible.

---

### Post by slickymaster on 2018-04-12
> **xinuzi said:**
> No problem.

Where do you see the problem exactly?

Could you 'quote' it? ;-)

I've put the coding in code tags as much as possible.

I just edited your entire first post, replacing your quote tags for code ones

---

### Post by xinuzi on 2018-04-12
You must be exhausted ;-P

I thought I had put ```
CODE
``` tags instead of > QUOTE ones.

Of course the > QUOTE tags were not meant to be where the ```
CODE
``` tags were intended.

Thanks for rectifying!

(Restored a few paragraphs in the meantime. The view should be fine now. The very first time this post didn't display well for other reasons.)

---

### Post by xinuzi on 2018-04-15
Made a few minor changes to my scripts.

So if you've saved them, replace them.

---

### Post by xinuzi on 2018-04-16
Replaced 'gnome-terminal -e' with '[COLOR=#000000][FONT=&quot]x-terminal-emulator -e' under'[/FONT][/COLOR][COLOR=#ff0000][FONT=&quot]**4) Everything together in 1 launch script**[/FONT][/COLOR][COLOR=#000000][FONT=&quot]' -> START script.
[/FONT][/COLOR][B][COLOR=#ff0000]
[/COLOR][/B]'x-terminal-emulator' will probably be more compatible on more systems..

Some video input devices will give excellent video image settings by default.
In that case it won't be necessary to launch a Toggle script and the 'x-terminal-emulator' line can be left out of the START script.
Just record with ffmpeg and view with GNOME MPlayer to your taste.

Hope my forum stalking ends here ;-)

---

### Post by xinuzi on 2018-04-17
Added 'clear' and renamed script file names.

I am sorry!

---

### Post by xinuzi on 2018-05-07
(Added script for better Avidemux compatibility to original post.)

---

