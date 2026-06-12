---
title: "No System Sound"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by rugbeeprop on 2007-10-20
Hi,  I have just installed fresh Ubuntu 7.10. I choose to clean install everything.  Everything works great except the System Sound. The sound seems to work in general, i.e. when there is sound when Ubuntu first boot up, I can play music and video.  The only thing that doesn't seem to work is the system sounds. On the Sound Preference, I click on Play, and I can hear it. I set the sounds to the default sounds that comes with Ubuntu (beep, siren, login, logout, etc). However, the sounds doesn't seem to sound when the events occur.  Any suggestion?

---

### Post by shayke on 2007-10-22
same thing, but I can't hear system sounds even when I test them (video and music works just fine)

---

### Post by coolbrook on 2007-10-26
:-#

(bump for no system sound, cd works in gxine, no sound on dvd in vlc)

---

### Post by coolbrook on 2007-10-26
Success

Did some tinkering with the output module in VLC's settings

Lights, Camera, Action.

:popcorn:

---

### Post by basic0 on 2007-10-31
Bump. Sound works fine with Audacity, Audacious, VLC, etc. The login sound still plays, but no other events play the sounds I have set for them. This worked fine in 7.04 and broke as soon as I started using Gutsy development (now using 7.10 stable).

Does anyone know what the problem is?

---

### Post by tvphil on 2007-10-31
I have read several forums on this subject in general and my problem in particular, no sound from Flash videos in Firefox without jumping through several hoops. One thing that seems to help Gutsy sound problems in general, is installing all Pulse Audio offerings in Synaptic. Pulse replaces most of the functions that use to be handled by ESD (Enlightened Sound Daemon) server that is no longer supported in Gutsy. Unfortunately, the one thing Pulse Audio hasn't corrected is the lack of audio in Flash video using Firefox. The hoops I jump through to get audio for flash involve using the following command as user, not root in a terminal....
 ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
 mkdir -p /tmp/.esd/
 touch /tmp/.esd/socket

Then restart the computer.
The problem with doing this is, if you shut down your computer, you have to do this all over again, since it's a temporary command. There doesn't seem to be a permanent solution to this vexing problem, that is an obvious oversight on the part of Gutsy's developers. Who know's if there is a fix coming from Ubuntu? The ball is in their court, I hope they come through.

---

### Post by rugbeeprop on 2007-10-31
> **coolbrook said:**
> Success

Did some tinkering with the output module in VLC's settings

Lights, Camera, Action.

:popcorn:

What did you do? Care to share?

---

### Post by magli on 2007-11-04
I am having the same problem as rugbeeprop.

Coolbrook was having an additional problem with sound in VLC, which is what I think he resolved. Is this the case, coolbrook? Or did you also manage to fix the system sounds problem?

I found this bug report, which reports the exact same issue:
[https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/139144](https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/139144)
but it dates back quite a while, and does not offer any help on how to fix it.

The bug was also brought up in this "absolute beginner talk" thread,:
[http://ubuntuforums.org/showthread.php?t=583757](http://ubuntuforums.org/showthread.php?t=583757)
But was not resolved either.

Anybody out there having this issue? It seems it is only affecting some of us, as I cannot find that many threads on it.

---

### Post by magli on 2007-11-04
Well, I found another bug report concerning this problem:
[https://bugs.launchpad.net/gnome-session/+bug/129029](https://bugs.launchpad.net/gnome-session/+bug/129029)
In this bug they focus on the fact that the logout sound does not play. I think that the logout sound is tied to the other gnome system sounds...at the end of that  very long page, it is concluded that the issue is *not* resolved in the final release of gutsy.

I do not know what is happening now, but would be nice to have this sorted soon with an update.

---

### Post by leovalles on 2007-11-07
Hey, there are two solutions that worked fine for me:

First one was installing esound in synaptic, then re-log in and **all** sounds were working for me, just a few complains: i connected a pair of USB speakers to my laptop and had to change all settings in sound preferences and most of the applications to make them work; and didn't find a way to make youtube videos sound through the USB speakers. Besides that, all perfect.
But i wanted more so i installed pulseaudio and works perfect with all sounds, i just followed this instruccions [http://www.pulseaudio.org/wiki/FlashPlayer9Solution](http://www.pulseaudio.org/wiki/FlashPlayer9Solution) to enable firefox sounds (youtube..). The **only** application stil not working for me is last.fm but i still can use it&#347; plugin through rhythmbox so not a big issue.  It has many features, i can connect my usb speakers and select which streams will play through them and which others to the intenal ones realtime (including firefox), it's really great.

So i think for any of you who still have problem with sounds in gutsy probably one of these solutions will help.

---

### Post by ridetheteapot on 2007-11-07
if you are planning to use alsa & dmix for sound then i think you'll have to make an /etc/asound.conf file.
I know at least in my install there was none (and no sound for that matter)

there is a lot of good info on the web about how to set the asound file up nice.
once that is set up and alsa is running (by default it is)
then just make sure that xmms or mpd or mplayer or whatever is using the alsa plugin and that the device is set to whatever you named the function ie. pcm.dmix would be dmix, or easier use pcm.!default and you probably won't need to change the device.

---

### Post by magli on 2007-11-08
Installing esound solved the problem for me.

Cheers everyone.

---

### Post by Ocean Machine on 2007-11-08
> **magli said:**
> Installing esound solved the problem for me.

Cheers everyone.

As it did for me, thanks for the tip.

---

### Post by rugbeeprop on 2007-11-14
[quote=leovalles;3727927]Hey, there are two solutions that worked fine for me:

First one was installing esound in synaptic, then re-log in and **all** sounds were working for me, just a few complains: /quote]

Hi Leovales,

Did your System Sound work before?

I installed esound, but nothing change. Perhaps I missed one of the steps after installing it.

---

