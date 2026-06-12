---
title: "How do I make totem use something other than pulseaudio"
date: 2009-11-13
forum: Multimedia Software
---

### Post by Dthdealer on 2009-11-13
Pulseaudio has been a pain for me ever since I used Ubuntu.  Crackly sound and buffering ten seconds ahead of music players were just a few of my problems.  I even had a launcher in my gnome-bar to restart the server, as it liked to crash.

So I removed it.  Everything was fixed! No crackly audio, no need to restart the server (quite literally) every half hour and position bars while playing music syncronised with the actual output.  I had to change from gnome-volume-control to gnome-alsa-mixer however, but again (opinion) I believe that was an improvement.

But now one of my most used applications is broken - totem.  No-where in its settings (nor in its settings edited via gconf) is a way to select an alternative output device for audio.  Without the pulseaudio server it simply doesn't output audio, and the volume button is greyed out.

Mplayer, although awesome, doesn't suit (not as user-friendly) the other users of this computer.

Without having to edit the source code is there a way to configure Totem use something else other than pulseaudio?

---

### Post by alphacrucis2 on 2009-11-13
> **Dthdealer said:**
> Pulseaudio has been a pain for me ever since I used Ubuntu.  Crackly sound and buffering ten seconds ahead of music players were just a few of my problems.  I even had a launcher in my gnome-bar to restart the server, as it liked to crash.

So I removed it.  Everything was fixed! No crackly audio, no need to restart the server (quite literally) every half hour and position bars while playing music syncronised with the actual output.  I had to change from gnome-volume-control to gnome-alsa-mixer however, but again (opinion) I believe that was an improvement.

But now one of my most used applications is broken - totem.  No-where in its settings (nor in its settings edited via gconf) is a way to select an alternative output device for audio.  Without the pulseaudio server it simply doesn't output audio, and the volume button is greyed out.

Mplayer, although awesome, doesn't suit (not as user-friendly) the other users of this computer.

Without having to edit the source code is there a way to configure Totem use something else other than pulseaudio?

I can't help with your Totem issue but have you tried VLC player.

---

### Post by kerry_s on 2009-11-13
look in the repo for "asoundrc-gtk" it's the gui to set sound source, also make sure you change system->preferences->sound 
to all alsa

---

### Post by VertexPusher on 2009-11-13
> **Dthdealer said:**
> Without having to edit the source code is there a way to configure Totem use something else other than pulseaudio?
Yes.

First, make sure that the package **gstreamer0.10-alsa** is installed. Then enter the following command in a terminal:
```
gstreamer-properties
```
You will see a window with two tabs, video and audio. On the audio tab you can set the default audio source and sink for all GStreamer applications. Set both to ALSA.

The next time you start Totem, it will send audio through ALSA instead of PulseAudio.

---

### Post by Dthdealer on 2009-11-13
> **VertexPusher said:**
> Yes.

First, make sure that the package **gstreamer0.10-alsa** is installed. Then enter the following command in a terminal:
```
gstreamer-properties
```
You will see a window with two tabs, video and audio. On the audio tab you can set the default audio source and sink for all GStreamer applications. Set both to ALSA.

The next time you start Totem, it will send audio through ALSA instead of PulseAudio.


*gstreamer-properties* was already installed so I fired it up.  Both input and output are already set to ALSA.  Using the test button shows it works, with my speakers emitting a hum.

However Totem still refuses to do anything but give me a greyed out volume button and no sound.

> **kerry_s said:**
> look in the repo for "asoundrc-gtk" it's the gui to set sound source, also make sure you change system->preferences->sound 
to all alsa

Since the removal of pulseaudio the gnome-volume-control (sound preferences now in 9.10) utility fails to start, presenting me with a dialog box stating **Waiting for sound system to respond**.

*asoundrc-gtk* just tells me I don't have the *asound* daemon installed/running.  Nothing in the repos that seems to help me - *libasound2* is already installed.

```
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136114&stc=1&d=1258169687[/IMG]

---

### Post by kerry_s on 2009-11-13
have you tried installing esound to replace the pulse audio stuff?

i'm using lenny, so i didn't have the pulse mess to deal with, but i have mine setup for esound(esd).

1st pic is what i have installed.
2nd pic is my sound settings.

---

### Post by VertexPusher on 2009-11-14
> **Dthdealer said:**
> However Totem still refuses to do anything but give me a greyed out volume button and no sound.
I forgot to mention that you have to remove gstreamer0.10-pulseaudio as well.

> *asoundrc-gtk* just tells me I don't have the *asound* daemon installed/running.  Nothing in the repos that seems to help me - *libasound2* is already installed.
The asoundconf tool is missing in the package. This has already been reported as a bug and should be resolved soon. If you have only one soundcard, you should be fine. If you have more, there's still the option to edit the .asoundrc file manually.

---

### Post by aramyegenian on 2009-11-14
Hi,

I had the same issue, I removed gstreamer0.10-pulseaudio but still I got no sound from totem... until I noticed that totem's volume control was all the way down :p i turned it up and it now works.. thanks, hope this helps someone...

---

### Post by Dthdealer on 2009-11-14
I installed esd and rebooted however the server didn't start, so I followed the instructions at [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063).  No change - maybe it isn't in the rc.d scripts, but I don't know what commands I'd need to put in a shell script to start it.

Removing gstreamer0.10-pulseaudio has no effects as totem is still being pointed to a dead end.

---

### Post by Dthdealer on 2009-11-15
I forgot to restart after removing the pulseaudio gstreamer package.

Solved!  Thankyou

---

