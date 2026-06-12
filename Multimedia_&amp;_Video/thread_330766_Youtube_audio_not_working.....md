---
title: "Youtube audio not working...."
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by gmanr26 on 2007-01-03
I can see the videos but i can't hear the audio.... and I know the video has an audio track... my sound is working... i know cuz i have my mp3s playing fine.... any ideas?

---

### Post by pissedoffdude on 2007-01-03
> **gmanr26 said:**
> I can see the videos but i can't hear the audio.... and I know the video has an audio track... my sound is working... i know cuz i have my mp3s playing fine.... any ideas?

Are you using adobe flash 7 or 9 beta?  I used to have audio problems with flash 7 but I haven't had them since I switched to 9.

---

### Post by gmanr26 on 2007-01-03
I'm not sure..... I'm a real Linux noob.... running Ubuntu Edgy 6.10

how would i find out which package is adobe flash 7/9???

---

### Post by pissedoffdude on 2007-01-04
> **gmanr26 said:**
> I'm not sure..... I'm a real Linux noob.... running Ubuntu Edgy 6.10

how would i find out which package is adobe flash 7/9???

Open up a firefox and type about : plugins (no spacing between the : ) that should tell you which version you have.  If you want to install flash 9 the easy way use automatix to install swiftfox and swiftfox plugins

---

### Post by sirbalmung on 2007-10-22
I have the same problem and I upgraded to flash 9 beta and I still have no sound on firefox, however I also dont have sound on opera

---

### Post by Libertine on 2007-10-22
I have this same problem on Gutsy...flash audio worked for a while but then just suddenly stopped. I can see videos but I just can't hear them. I'm using a Creative Sound Blaster Live! 24-Bit if it means anything to anyone :(

---

### Post by cogadh on 2007-10-22
Having the same issue with Flash in Gutsy, Creative SB Audigy LS, which is essentially the same thing as the SB Live! 24-bit. I don't think it is sound card related though. It seems to me that if there were a problem with the sound card, sound wouldn't work at all, instead of just no sound in Flash apps.

---

### Post by Screaming Monkey on 2007-10-22
Just to add my $.02 I am having the same problem with my audigy card and both google video and youtube videos.  Like you cogadh, I don't have any problems with sound in any of the other apps I run, just with the Flash apps.

---

### Post by ntwrkguy on 2007-10-22
Same here (no audio in Flash 9), and it started happening with the upgrade from 7.04 to 7.10...

---

### Post by Libertine on 2007-10-22
That's weird, mine was working after the update but then randomly stopped working after about an hour or two.

---

### Post by Libertine on 2007-10-22
I found a solution for this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server)

Enjoy everyone :D

---

### Post by sirbalmung on 2007-10-23
It worked!!! woot thnx :) finally got sound back :D

---

### Post by cappii on 2007-10-23
Thanks, Libertine.  This fixed me!! ^5 all the way from Texas!!!:guitar:

---

### Post by cogadh on 2007-10-23
Damn, beat me to it! I just found the same doc and got sound working beautifully.

---

### Post by Screaming Monkey on 2007-10-23
Tried it all and still no sound for me.  Any clues?

I don't have an asound.conf file, I haven't needed one, is that an issue?  I created one for the operation as per the guide, but then nothing worked for me, not amarok or nothing.  I removed everything and at least got my sound back for my tunes and what not.

---

### Post by cogadh on 2007-10-23
Don't create an asound.conf file, create an .asoundrc file in your home folder, it does basically the same thing (asound.conf was global settings, .asoundrc is per-user settings).

---

### Post by Screaming Monkey on 2007-10-23
still doesn't work.  And when I reboot, and then try amarok, I get a couple of error messages, one being that the decopserver isn't running and then after that, it can't communicate with klaunch(er).  I'm uninstalling pulse (again) and have taken the lines out of my .asoundrc file.  

Any other ideas?

---

### Post by cogadh on 2007-10-23
Are you running Kubuntu/KDE? If so, that might be part of the problem, the instructions cover Ubuntu/Gnome. If I remember correctly, KDE still uses the aRts sound system by default, while these instructions are geared towards ALSA in combination with ESD (with PulseAudio replacing ESD as the sound mixer).

You might try looking at the Kubuntu version of the same site: [http://kubuntuguide.org/](http://kubuntuguide.org/)
I didn't find a PulseAudio how to when I quickly scanned through the TOC, but I might have just missed it.

---

### Post by Screaming Monkey on 2007-10-23
No, I'm using Gnome believe it or not.  I tried to follow the activating flash plug-in part of the [wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox").  But that didn't work either.  After that I uninstalled everything I installed, restarted my computer and now the sound doesn't come from my speakers at all, but from the case.

Man, this is getting frustrating.  Thanks though for your help so far.

edit**
Before all this, after I upgraded, I would have to reboot every once in a while in order to get the sound from the speakers and not the case.  Don't know if that's important but thought I'd add it just in case

---

### Post by Screaming Monkey on 2007-10-23
So, I got my sound back through my speakers for now.  I used this thread:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_sound_to_work_properly_in_GNOME]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_sound_to_work_properly_in_GNOME")
(howver instead of unchecking the "sound for events" button, I unchecked the "play system sounds" button)

But still no sound for flash videos.

---

### Post by wolux on 2007-10-24
Hi,

well i got the same problem. I was thinking it came after installing mpg321, PulseAudio, PulseAudo-esound-compat, libasounds2-plugins, all needed for previz of mp3 files in nautilus, but i'm not sure...
The way i solved the sound problem in flash is tying to follow the link from Libertine.
So :
```

sudo apt-get install "pulseaudio-*" paman padevchooser paprefs pavucontrol

```
The gstreamer plugin for pulseaudio can't be found so i went on next step
```

wget http://pulseaudio.vdbonline.net/libflashsupport/libflashsupport_1.0~2219-1_i386.deb

```
and made installation with Gdebi.

And no asound.conf file... neither asoundrc... in home

So i restart session, open firefox and test youtube -> it works.

---

### Post by cogadh on 2007-10-24
The GStreamer plugin package has a different name in the Gutsy repositories: libgstreamer-plugins-pulse0.10-0

There is no asound.conf file in Ubuntu, not sure why. The .asoundrc file has to be created in your home directory by you, it won't be there by default. The period on the beginning of the name is required and once created, it will be a hidden file (that's what the period does).

---

### Post by Screaming Monkey on 2007-10-25
Hey there.  Still not able to get sound working in flash.

I've tried all the different hints and everything.  Any other ideas?

---

### Post by orl on 2007-10-26
hi,
this worked for me. after reading some of the comments multiple applications can play sound on top of the flash sound output aswell...

[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

---

### Post by furieh on 2007-10-26
[quote=http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/"]


sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc
 

Replace FIREFOX_DSP="none"

for

FIREFOX_DSP=”aoss”[/quote]

:guitar:

---

### Post by Screaming Monkey on 2007-10-26
Still nothing folks.  Am I doing something wrong?  I have just removed alsa-oss because that was changing my default sound to the computers damn internal speakers and nothing would change it back - removing it did though.  

So, now I am stuck with a great system that won't do flash sound in firefox, and that has occassional hiccups and changes the default sound conf on me.

Do I need to create a new thread for this debacle?

---

### Post by Screaming Monkey on 2007-10-30
Anyone visiting this thread might also need to check out this thread here:
[http://ubuntuforums.org/showthread.php?p=3446685 (specifically post #5)]("http://ubuntuforums.org/showthread.php?p=3446685")
and this one here:
[http://ubuntuforums.org/showthread.php?t=590989&highlight=flash%2C+youtube]("http://ubuntuforums.org/showthread.php?t=590989&highlight=flash%2C+youtube")

I found that
```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```
solved my problems beautifully.

---

### Post by paulphillips on 2008-04-02
> **Screaming Monkey said:**
> Anyone visiting this thread might also need to check out this thread here:
[http://ubuntuforums.org/showthread.php?p=3446685 (specifically post #5)]("http://ubuntuforums.org/showthread.php?p=3446685")
and this one here:
[http://ubuntuforums.org/showthread.php?t=590989&highlight=flash%2C+youtube]("http://ubuntuforums.org/showthread.php?t=590989&highlight=flash%2C+youtube")

I found that
```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```
solved my problems beautifully.

I can concur!!  I happened upon this independently as in my case I could play audio, but my wife couldn't - so I concluded it must be a difference in environment.

I discovered I didn't have an ".asoundrc" or ".asoundrc.asoundconf" file in my home directory, so I deleted them from my wife's account, and voila!  It all works now!:guitar:

---

