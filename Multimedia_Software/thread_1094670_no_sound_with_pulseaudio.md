---
title: "no sound with pulseaudio"
date: 2009-03-12
forum: Multimedia Software
---

### Post by arbosis on 2009-03-12
Hello, I'm using kubuntu 9.04 and all apps that use pulseaudio (like firefox) have no sound. When I try to use pulseaudio I can oly hear noise like static. I know my hardware is ok because I can play music with amarok and also use other operating systems with sound.

This is what the logs says:
user.log:
```
Mar  8 15:00:19 mercurius pulseaudio[4177]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Mar  8 15:00:20 mercurius pulseaudio[4177]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges andwe have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Mar  8 15:00:20 mercurius pulseaudio[4177]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Mar  8 15:00:20 mercurius pulseaudio[4179]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Mar  8 15:00:20 mercurius pulseaudio[4179]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges andwe have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Mar  8 15:00:20 mercurius pulseaudio[4179]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Mar  8 15:00:20 mercurius pulseaudio[4178]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Mar  8 15:00:20 mercurius pulseaudio[4178]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges andwe have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Mar  8 15:00:20 mercurius pulseaudio[4178]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Mar  8 15:00:22 mercurius pulseaudio[4189]: pid.c: Daemon already running.
Mar  8 15:00:22 mercurius pulseaudio[4190]: pid.c: Daemon already running.
Mar  8 15:54:56 mercurius pulseaudio[4183]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
```
also from user.log (there are like hundreds of lines like these):
```
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879337612 bytes (10653841 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879323276 bytes (10653760 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879308940 bytes (10653678 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879294604 bytes (10653597 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879280268 bytes (10653516 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879265932 bytes (10653434 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 11 21:48:32 mercurius pulseaudio[4588]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1879251596 bytes (10653353 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
```

I don't know if this info may help:
```
[arbosis@mercurius ~] aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0                                        
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]    
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0  
```

```
[arbosis@mercurius ~] lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia
       description: Audio device
       product: MCP67 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
```

My user is in all groups which says pulse

Please help. :(
Thanks :)

---

### Post by markbuntu on 2009-03-13
You can read this thread here, it is about KDE4, phonon and pulseaudio (look in post #9 if you are using KDE4.2). This was not written for jaunty but should help you get things figured out anyway.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by arbosis on 2009-03-13
> **markbuntu said:**
> You can read this thread here, it is about KDE4, phonon and pulseaudio (look in post #9 if you are using KDE4.2). This was not written for jaunty but should help you get things figured out anyway.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

I saw that post, but it doesn't fix my problem. I can only hear now noise when something tries to make a sound and when that occurrs these lines appear in the user.log
```
Mar 13 20:13:10 mercurius pulseaudio[10086]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 1527858640 bytes (8661330 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
```

Also, when I press Ctrl+Alt+F8 I can see some daemons or services that start, there is a line which says:
*Pulseaudio configured per-user session
and the '*' is in red, and there is no [ ok ] at the end of the line.

I'm still looking for the solution

ps: thanks for the reply markbuntu :)

---

### Post by danns on 2009-03-13
I am having this same problem too.  I just upgraded from intrepid to jaunty.  I know sound works properly because I have no problems with the sound in gnome.  I tried the information in the other page to no success.  

Amarok works but when I started it up it said the default sound output did not work and it switched to the second choice - hda-intel.  Something must be blocking pulseaudio in kde.

---

### Post by 3togo on 2009-03-14
Though I am not using KDE, I got the sampe problem in gnome.
 jc@ubuntu-hp:~$ gdm --version
GDM 2.20.9
jc@ubuntu-hp:~$ tail /var/log/syslog
Mar 14 13:10:05 ubuntu-hp pulseaudio[4296]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058054509616876 bytes (418289136893 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.

---

### Post by frosty.ptz on 2009-03-14
I confirm this problem on jaunty alpha 6 on amd64, gnome.

---

### Post by arbosis on 2009-03-16
**Does anyone have found a solution? :(**

---

### Post by markbuntu on 2009-03-16
There is some problems with implementing pulseaudio 0.9.14 in Jaunty. crimsun is working on them. There are some threads in the development and testing forum.

If you are using kubuntu or amarok2 then you are using Phonon which uses the xine backend. You need to go to system settings sound in kubuntu to set that up. Pulseaudio does not come by default in kubuntu nor does it start up automatically unless you make a launcher for it as in the link I gave. Post #9 in that link has an alternate method for getting pulse to start up with KDE4.2 which also works for kde4.1 and starts pulse up sooner.

You need to go here to set up alsa and pulseaudio 

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

so there is a default that phonon can use.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

You also need to have ALL the updates.

Once jaunty gets a little more stabilized I will be writing a guide for it and for KDE4 since many things are different. It will probably come out around the release date.

---

### Post by danns on 2009-03-16
Odd, but I got it working.  I updated to the latest packages today and logged into KDE to see if things had changed, but they had not.  I started messing around with some settings, testing gstreamer-properties and the multi-media settings in the KDE system configuration tool.  Nothing seemed to work. 

I tried Mplayer and gxine, but they would not play any audio.  I installed the phonon-xine backend and switched over to using that but I still had problems.  

When I switched back the phonon backend to gstreamer everything started working again.  Not sure why this is, but hey, at least it kicked something into gear!

This does not persist between session though and it seems I have to go back into the KDE multi-media settings and toggle xine as the preferred backend and then set gstreamer as the preferred backend.

---

### Post by arbosis on 2009-03-21
> **markbuntu said:**
> There is some problems with implementing pulseaudio 0.9.14 in Jaunty. crimsun is working on them. There are some threads in the development and testing forum.

If you are using kubuntu or amarok2 then you are using Phonon which uses the xine backend. You need to go to system settings sound in kubuntu to set that up. Pulseaudio does not come by default in kubuntu nor does it start up automatically unless you make a launcher for it as in the link I gave. Post #9 in that link has an alternate method for getting pulse to start up with KDE4.2 which also works for kde4.1 and starts pulse up sooner.

You need to go here to set up alsa and pulseaudio 

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

so there is a default that phonon can use.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

You also need to have ALL the updates.

Once jaunty gets a little more stabilized I will be writing a guide for it and for KDE4 since many things are different. It will probably come out around the release date.
I've already done that, but I still have no sound


> **danns said:**
> Odd, but I got it working.  I updated to the latest packages today and logged into KDE to see if things had changed, but they had not.  I started messing around with some settings, testing gstreamer-properties and the multi-media settings in the KDE system configuration tool.  Nothing seemed to work. 

I tried Mplayer and gxine, but they would not play any audio.  I installed the phonon-xine backend and switched over to using that but I still had problems.  

When I switched back the phonon backend to gstreamer everything started working again.  Not sure why this is, but hey, at least it kicked something into gear!

This does not persist between session though and it seems I have to go back into the KDE multi-media settings and toggle xine as the preferred backend and then set gstreamer as the preferred backend.
I have complete silence with gstreamer, with xine I can at least listen music with amarok

---

### Post by markbuntu on 2009-03-21
As far as I know the gstreamer backend has not yet been implemented for phonon so perhaps danns is resetting phonon by choosing the gstreamer backend. Phonon is still very much a work in progress. Please keep this on mind.

---

### Post by arbosis on 2009-03-26
It must have been an update or something ( I update every day) , because I have sound now, but if I try to use amarok and play a movie with dragoon player or play a youtube video sound fails...

---

### Post by danns on 2009-03-28
The update for me this morning killed sound permanently.  For gnome and kde.  Gstreamer is completely borked, all I get is static.  I still get sound through also in kde4 and using amarok, but most of the other applications like flash, vlc, mplayer, etc are no longer working.  I believe they must be using gstreamer. 

When I toggle the backends I still get the error about pulse failing and it drops to hw device using alsa for xine.  Gstreamer backend does not do this but like I said, it is all borked up.

---

### Post by danns on 2009-03-29
I've noticed another problem with this.  When testing the sound in the KDE4.2 multi-media settings it has a tendency to lock the application.  I notice the same thing with trying to play a file using mplayer on a terminal.  Both of those instances I can easily get out of but the problem is worse in flash.  Flash locks firefox and it becomes useless until I kill it and restart the application again.

**********

Ok, I got it working again.  I went in under gnome and using the gnome audio settings forced everything to pulse audio.  I also killed pulseaudio, deleted all the .pulse files/directories in my home directory and followed the directions on this site [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/334319](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/334319) to use that version of pulse and alsa.  

Everything seems back to where it was before the upgrade yesterday.

---

