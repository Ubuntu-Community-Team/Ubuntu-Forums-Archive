---
title: "Audio stuttering"
date: 2009-03-30
forum: Multimedia Software
---

### Post by lvu on 2009-03-30
When I try to listen audio with mplayer (mplayer -vo null -ao pulse /some/mp3) from command-line, audio stutters. Also it stutters when playing with console mpg123, and with Rhythmbox. Strangely, stuttering disappears when playing the same file with SMPlayer. I've tried to get the command-line it uses for mplayer with ps -Af | grep mplayer and got the following:
```
/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 54525964 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -aid 0 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -ss 125 -osdlevel 0 -vf-add screenshot -channels 2 -softvol -softvol-max 110 /some/mp3
```
But when I run this very same command from console, audio stutters again.

It all began about a couple of weeks ago, before that everything was fine. Unfortunately I don't know if it was some update or some piece of software I've installed.

I've tried to do it like this:
```
pulseaudio --kill
pasuspender -- mplayer -vo null -ao alsa /some/mp3
```
, no difference. This time pulseaudio definitely wasn't running, so I think it is not the reason.

Also tried to change default-fragments and default-fragment-size-msec in /etc/pulse/daemon.conf and to boot to 2.6.27-7-generic (my current is 2.6.27-11-generic) - everything the same.

My system is Ubuntu 8.10, AMD Athlon64 X2 4200+, lspci | grep Audio gives 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

---

### Post by lvu on 2009-04-01
One more check. I've logged out from gnome session, switched to console #1, and stopped gdm service. So, I had a clean console, without any pulse. Then tried to play wav file with aplay, using different PCM devices. Effect is the same. Seems that I need to compile ALSA myself?..

---

### Post by njh on 2009-04-25
Yes, I've noticed the same thing with rhythmbox when compiling.  Used to be fine, recently has become so bad that I turn music off to compile.

---

