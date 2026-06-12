---
title: "Tutorial: How to record, pause and resume TV on-the-fly!"
date: 2008-09-18
forum: Multimedia Software
---

### Post by lovinglinux on 2008-09-18
This is a byproduct of my tutorial "[[COLOR="Dark_Red"]**Firefox Media Center**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=913671")". I decided to create a new thread because some people might not be interested in the other stuff from the Firefox tutorial, so here you will just learn how to create a simple PVR, so you can watch, pause and resume your TV like any Media Center out there.

[COLOR="Red"]**Requirements:**[/COLOR] You need a tv card already working with TVTime.

To create our PVR we first need to install transcode, ffmpeg and zenity. Type the following command on a terminal:

```
sudo apt-get install transcode ffmpeg zenity
```


After installing the required applications, we need to create a shell script for starting the PVR.

Open the text editor and add the following text 

For NTSC cards:

```
#!/bin/bash

killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 0% mute

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

 transcode -x v4l2,v4l2 \
           -M 2 \
           -i [COLOR="Red"]**/dev/video0**[/COLOR] \
           -p [COLOR="Red"]**/dev/dsp2**[/COLOR] \
           -y ffmpeg \
           -F mpeg4 \
           -g 720x480 \
           -f 0,4 \
           -I 1 \
           -u 100 \
           -Q 3 \
           -Z 360x240,fast \
           -E 48000,16,2 \
           --lame_preset medium \
           -o ~/[COLOR="Red"]**Desktop**[/COLOR]/${TODAY}-${NOW}.avi  &

(for a in `seq 1 100` ;
do
echo $a;
sleep 0.1;
done) | zenity --auto-close --progress \
--text="Buffering" \
--title="TV Feed" && [COLOR="Red"]**smplayer**[/COLOR] ~/[COLOR="Red"]**Desktop**[/COLOR]/${TODAY}-${NOW}.avi

killall transcode 
amixer -q set "Line" 0% mute
```

You will probably have to tweak this code and replace devices/player (in red) with your own. You can also choose another directory for saving the files. 

If you have a PAL-M TV card then use this code instead:


```
#!/bin/bash

killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 0% mute

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

transcode -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
        -g 640x480 \
        -i [COLOR="Red"]**/dev/video0**[/COLOR] \
        -p [COLOR="Red"]**/dev/dsp2**[/COLOR] \
        -e 32000,16,2 \
        -N 0x1 \
        -J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
        -o ~/[COLOR="Red"]**Desktop**[/COLOR]/${TODAY}-${NOW}.avi &

(for a in `seq 1 100` ;
do
echo $a;
sleep 0.1;
done) | zenity --auto-close --progress \
--text="Buffering" \
--title="TV Feed" && [COLOR="Red"]**smplayer**[/COLOR] ~/[COLOR="Red"]**Desktop**[/COLOR]/${TODAY}-${NOW}.avi

killall transcode 
amixer -q set "Line" 0% mute
```

For more command options visit [[COLOR="DarkRed"]**Transcode**[/COLOR]]("http://www.transcoding.org/cgi-bin/transcode?Transcode_Command_Line_Options") web site.

If you want to automatically move the recorded file to another directory after recording it, add the following command in the end of the previous code:

```
mv ~/[COLOR="Red"]**Desktop**[/COLOR]/${TODAY}-${NOW}.avi ~/[COLOR="Red"]**NewDirectory**[/COLOR]/${TODAY}-${NOW}.avi
```

Now save this file as /home/[COLOR="Red"]**you**[/COLOR]/bin/startpvr  (don't forget to replace you with your user name). 

Go to /home/[COLOR="Red"]**you**[/COLOR]/bin/, select the file and open it's properties. In the Permissions tab, make sure you tick "Allow executing file as program".

Now we need to create a button to start the PVR. You can right-click in the Desktop and select "Create launcher" or you can add a "Custom Application Launcher" to the gnome panel. Either way, you are going to use the following settings:

**Type:** Application
**Name:** PVR
**Command:** /home/[COLOR="Red"]**you**[/COLOR]/bin/startpvr

When you hit the new PVR button, TVTime will be launched, so you can choose the channel. Then you need to close the TVTime window, to start recording. The player will be launched 10 seconds later, so you can watch, pause and resume the TV channel being recorded. If you close the player, the recording will stop.

[COLOR="Red"]**Don't forget to replace things in red, including the player if you don't have smplayer.**[/COLOR]

You can also create buttons just to start TVTime, to record and stop recording as explained in [COLOR="Red"]**[Cresho's tutorial]("http://ubuntuforums.org/showthread.php?t=921233")**[/COLOR], from where I took some valuable information to create this tutorial myself.

---

### Post by someitalian123 on 2012-02-26
what do you list under -p if your using alsa instead of oss. I haven't been able to get this to work. I keep getting this on the output. 

```
tvtime: no process found
transcode: no process found
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/gaetano/.tvtime/tvtime.xml
Thank you for using tvtime.
[transcode] critical: Invalid filename "/dev/dsp": No such file or directory

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:102:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:117:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:134:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:153:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:165:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:175:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:186:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:198:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:208:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:218:16: Themeing engine 'adwaita' not found

(zenity:3036): Gtk-WARNING **: Theme parsing error: gtk-bars.css:223:16: Themeing engine 'adwaita' not found
in media state change with state = 0
transcode: no process found
```

---

