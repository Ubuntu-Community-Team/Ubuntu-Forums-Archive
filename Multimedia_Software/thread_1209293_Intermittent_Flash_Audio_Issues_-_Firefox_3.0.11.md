---
title: "Intermittent Flash Audio Issues - Firefox 3.0.11"
date: 2009-07-10
forum: Multimedia Software
---

### Post by PureLoneWolf on 2009-07-10
Hi all

I started noticing some strange behaviour yesterday when viewing Flash videos.  I tried to watch something on Facebook and the sound was incredibly stuttery..after a few seconds, so was the video.

Stopping playback didn't stop the stuttering until I brought another application into focus.  To fix the issue I had to close FF and restart it.

Then it was fine for a while.

I have tried to recreate it today, but can't.  I have been playing a lot of Team Fortress 2 through Wine and thought it could be that...but I was connected to a server and played a youtube video through facebook without any issue even with Amarok streaming an internet radio station.

Then I thought it could be skype - but being in a call didn't change it.  It seems to be an "over time" thing.  

Sound/Video is working exactly as it should generally.  As I type this I am (for testing purposes obviously):

Talking to a friend in skype
Listening to Amarok 1.4 internet radio stream
Spectating a TF2 game through Wine
Watching a film in XBMC
Watching a Youtube video in Firefox on Virtualbox 3 (XP)
Watching a Youtube video in Firefox on my PC

Everything is perfect.  Yet I know this thing will come back later and it frustrates me that I can't figure it out...

My specs:

**Hardware:**
Gigabyte EP35-DS3R Motherboard (Bios F2)
Intel Core 2 Duo E8400 (3ghz)
4gb installed RAM (3613mb available in Ubuntu - 1720mb in use)
Nvidia 9600GT 1024mb (Nvidia Driver 180.44)
Integrated Realtek ALC889A Audio Device (sna-hda-intel module)

**Software:**
Ubuntu 9.04 32bit(2.6.28-13) running Gnome 2.26.1 (Compiz enabled)
ALSA Mixer (System wide default)
Realtek ALC889A (OSS Mixer) - Only used as a wrapper for VMware (rarely used)
Firefox 3.0.11 (Shockwave Flash Plugin 10.0 r22)
XBMC 9.04
Amarok 1.4
Skype 2.0.0.72
Wine 1.0.1

Additionally, Pulseaudio was apt-get purged from my system on the 2nd day of running Ubuntu, so that is not in use or even available on the system.

I can't think of anything else that could be useful right now, so let me know if any other info would be useful.  This is an annoyance, with FF session saving, it is literally 5 seconds to get rid of the issue when it occurs, but still - I would rather not have it :)

Any help is gratefully recieved.

Thanks

---

### Post by wojox on 2009-07-10
PureLoneWolf

It appears to be a bug that has been reported. Check this out:

[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

---

### Post by PureLoneWolf on 2009-07-10
Thanks - The issue is similar, but not entirely the same.

I don't get the excessively high CPU useage when it occurs and I don't get tearing on the video, it stutters and the audio stutters like Max Headroom on Acid (for those that remember Max Headroom) :-)

---

### Post by lovinglinux on 2009-07-10
I would say pulseaudio, but..

> **PureLoneWolf said:**
> Additionally, Pulseaudio was apt-get purged from my system on the 2nd day of running Ubuntu, so that is not in use or even available on the system.

---

### Post by martinbaselier on 2009-07-10
I've been having the simmilar symptoms for quite a long time now and I can't seem to find the cause. My computer is usually on for a long time. After firefox has been open for a few hours, the sound starts to stutter when playing flashmovies or audiostreams with a flashplayer (like online radio etc). The movie keeps playing fine and there's no high cpu usage.
The problems might be connected.

My audio:
Intel Corporation 82801FB/FBM/FR/FW/FRW (->realtek ALC880)

I've had the problem since intrepid with both adobe flash 9 and 10. 

I haven't got pulseaudio installed, so that's not the problem. I only use alsa and sometimes jack.

Things I noticed so far:
It occurres  quite randomly. Usually I notice it after having used another sound program for some time and then switch back to firefox to watch something on youtube. But that's mainly because that's my normal pattern. I have vlc or songbird open most of the time, playing audio and then switch to firefox to find something and listen to it.

But it can also happen when going from one youtube movie to the next. The few times I experienced that, I noticed the sound starts to echo a little at first, a bit like a hanging cd. It rapidly get worse and I only hear short bleeps of sounds, echoing for a long time. When I stop a movie, the sound keeps playing for several seconds.

The only solution then is restarting firefox. I created an empty profile to see if some settings were corrupt -> no solution.

I used to have the same problem with songbird 1.0, but that's been solved some time. 

I just noticed I have flashplugin-nonfree-extrasound installed, maybe that's causing some problems. I will remove it to see if it makes a difference. 

If that doesn't solve it, next step will be to re-install it and force a different soundsystem: see below. 


I just checked the README
less /usr/share/doc/flashplugin-nonfree-extrasound/README

Here are some points of interest.

* It first tries to detect PulseAudio
* It then checks for Esound:
* Then if checks for ALSA:
* Finally, it checks for OSS:

If everything fails, it falls back to the ALSA driver that's built directly into FlashPlayer 9.

You can force any interface by setting environment variables:
 - FLASH_FORCE_PULSEAUDIO = 1 
 (or) FLASH_FORCE_ESD / FLASH_FORCE_ALSA / FLASH_FORCE_OSS

I will post my testresults later, but others could use this bit of information for their own tests.

---

### Post by martinbaselier on 2009-07-11
Seems like my flash sound problem is solved. I haven't had firefox on for such a long time without sound problems. 

sudo apt-get purge flashplugin-nonfree-extrasound

---

### Post by PureLoneWolf on 2009-07-11
I will purge it like you did and see what happens...thanks very much :)

*EDIT*
Ah... it would appear that this doesn't exist on my PC.

Maybe I should install it...just so I can remove it later ;)

---

### Post by martinbaselier on 2009-07-11
Well it didn't seem to solve my problem after all. Flash sound just crashed again. :(

Just found the bug on launchpad. 
[https://bugs.launchpad.net/pld-linux/+bug/249817](https://bugs.launchpad.net/pld-linux/+bug/249817)

Gonna check if I find anything in there.

current test:
just found a bit of pulse still on my system, removed it to be sure. 
sudo apt-get remove libpulse-browse0

I installed an unstable version from asound:

added the following line to /etc/apt/sources.list
deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main 

got the gpg-key
./getkey.sh B88A1AA8

Updated my system.
apt-get update && apt-get upgrade

getkey.sh contains
gpg --keyserver subkeys.pgp.net --recv $1
gpg --export --armor $1 | sudo apt-key add -

---

### Post by -=hazard=- on 2009-07-11
Same problem with me too, till 30 min ago, check this out [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) The optimization is for firefox or shiretoko there are three ways for doing the job, the best one is the third, the one by installing a script that play the video without the dafault flash player of youtube (that script is only for youtube) then the browser will not lagg anymore, you can use the sound control and cpu wont freak out.

I did 

1.[COLOR=#cc0000][SIZE=4]Removing Conflicting Plugins[/SIZE][/COLOR]

2.[COLOR=#cc0000][SIZE=4]Compiz, Xorg and Graphics Tweaks

[/SIZE][/COLOR]3.[COLOR=#cc0000][SIZE=4]Blocking Flash Content [/SIZE][/COLOR]Already had this one.

4.[COLOR=#cc0000][SIZE=4]Flash Replacements[/SIZE][/COLOR] The Greasemokey script.

.. and seems fine now

It might be helpful because the most videos we watch are on youtube.

-Edited- 
For specified sound problems you can take a look here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Cheerz.

---

### Post by martinbaselier on 2009-07-11
Thanks for the tips, Hazard. That firefox thread is quite good. I already discovered it though. I used the link to ubuntugeeks and implemented their optimizations and also optimized the firefox databases with the script. Now firefox can restart within a couple of seconds with 15 sites opened. 

The problem with replacing flash is compatibility. I've found that many games don't work well in the open source players. And though I use youtube more often than other sites, I don't want to do a complete research each time I want to watch or listen to something on another site.

edit: my conclusion is that there's a bug in the flashplayer which causes this. I'll report it and let adobe fix it.

---

### Post by -=hazard=- on 2009-07-11
> **wojox said:**
> PureLoneWolf

It appears to be a bug that has been reported. Check this out:

[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)


Allready reported --> [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

I hope they fix this.

---

### Post by martinbaselier on 2009-07-16
That's a different problem

---

### Post by martinbaselier on 2009-07-17
I just made a switch from alsa to [oss 4](http://www.opensound.com/) and besides having far better sound quality (I find the difference quite amazing really), I haven't had a flash problem yet. Firefox has been on for 12 hours now without problems, so it's not 100% sure if this is the cure, but probably it is.

---

### Post by igorzwx on 2009-07-18
but USB audio devices are not supported.
It might be a good idea to install the codecs from Medibuntu.
It works well for me (with OSS4)
It seems that all hackers are now busy with Slax...

---

### Post by martinbaselier on 2009-07-18
[USB audio devices support is currently experimental and USB recording is not implemented.](http://wiki.archlinux.org/index.php/OSS)
Medibuntu is quite usefull. I've installed it a long time ago.

---

### Post by igorzwx on 2009-07-18
many newbies have problems with installing OSS4.
they deserve "human treatment".

---

### Post by martinbaselier on 2009-07-19
What do you mean?

---

### Post by igorzwx on 2009-07-19
This, for example:
				**big mistake - gstreamer, alsa, plz help!!!!!**
[http://ubuntuforums.org/showthread.php?t=1216484](http://ubuntuforums.org/showthread.php?t=1216484)
QOUTE:
thanks A LOT igorzwx, your help is being really useful, although i couldn't make it work yet.

what seems to happen is that oss works well in the tests but gnome and gnome applications don't recognize it, as if they were still configured to use alsa. when i open totem, i receive a message saying that gstreamer couldn't be initialized. in preferences-sound, still no option to choose, everything is blank! and it was something i did wrong when installing and uninstalling gst and rhythm from source, because before, i had many options in preferences-sound, including oss.

i'll keep trying, reading wikis and how-tos. if you have an idea, plz tell me. and thank you again!!!
End of QUOTE

I cannot hepl him much.
I have not HDA here.
I have old boxes (IBM of 2003, and a box of 2001)
He managed to make his HDA working!
But gnome aps...

---

