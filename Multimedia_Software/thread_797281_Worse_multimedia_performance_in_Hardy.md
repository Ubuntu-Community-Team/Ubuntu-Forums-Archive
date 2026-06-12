---
title: "Worse multimedia performance in Hardy?"
date: 2008-05-17
forum: Multimedia Software
---

### Post by kristianz on 2008-05-17
I recently upgraded to Hardy, and immediately noticed how sound would skip (sometimes slightly, sometimes rather severely) when switching between virtual desktops.

Anyone else experience the same?

---

### Post by fcorourke on 2008-05-17
I too have noticed that I made a big mistake in thinking Hardy a LEAP forward. Should have stayed with 7.10 as it actually worked, sound video. Everything that Ubuntu can do [do not go to US Patent office & expect to SEE anything-- working on it]--- also a better browser in Firefox 2.xxx --- I think we are the Firefox 3 testers -- like it or not. -- I can see nothing that Hardy does better --- OH it does have a higher number --- is that supposed to make you feel better? It would take a 50 page "Sticky+ to fix all the little things that did work. IT is updating like crazy. My last "UPDATE" removed the ability to play DVD's.... Way too go.

    Fred

---

### Post by 4Orbs on 2008-05-17
I'm not gonna bash Ubuntu for offering a free OS that incorporates the newest stuff available, even if it is not completely bug free. I experienced the same multimedia bugaboo's as you, tried to fix them and finally gave up... on the standard Ubuntu. So I did a new install of Xubuntu, followed the Comprehensive Multimedia sticky thread item-by-item and it works flawlessly. Xubuntu is a whole different animal than Ubuntu and I suggest you give it a try. Not as an addition to Ubuntu, but as a clean install all by itself. Do I miss the desktop effects? Not one bit.

---

### Post by prshah on 2008-05-17
> **kristianz said:**
> I recently upgraded to Hardy, and immediately noticed how sound would skip (sometimes slightly, sometimes rather severely) when switching between virtual desktops.


Switching desktops etc, especially with compiz running is an intensive job, and will cause interruptions unless your graphics is setup correctly. Eg, if you are using the (default) vesa driver, you will not get best graphics performance, this will in turn degrade performance elsewhere.

Do you have an Intel onboard graphics card? If that is the case, then the default hardy install is not (usually) optimized for it.

If you have an intel onboard graphics card, post back for correct optimization.

Otherwise, some more config details will be helpful; eg. RAM, etc

---

### Post by fcorourke on 2008-05-17
Does Firefox 3 work? I can not get all pages to display or work correctly. I had fixed DVD playing until the last update -- it fixed my sound [none] and I can not even watch a video -- not really true I can watch the individual files with no sound. Why are updates going backwards?

Frec

---

### Post by 4Orbs on 2008-05-17
If you are asking me if Firefox 3 works in Xubuntu, the answer is yes. But it is noticeably slower than Seamonkey. Maybe 2 or 3 seconds slower per page load on dsl connection. Firefox 3 got quicker for me as soon as I removed the "Latest Headlines" link up in the toolbar, but I don't think that is any real problem. There are just some bugs left to work out by the developers. For the record, simply doing a fresh install of Ubuntu fixed some of the problems I could not solve. But now I am running Xubuntu and have no regrets. Honestly, its so much leaner and cleaner and can be customized plenty. A great foundation for adding new goodies one at a time. As for the multimedia. I strongly recommend following the Comprehensive Multimedia how-to sticky thread on this forum. That is all that was necessary to get all my audio/video stuff working. Vlc is the default dvd player and opens in fullscreen mode with full volume. Mplayer plays my mkv video with subtitles from an external hdd and gxine plays the avi video and subs. I believe the xine library makes a difference in the ability do play dvd, not sure though. Streaming video and flash work fine in Firefox 3 (again the how-to sticky thread was the only instruction I followed)

---

### Post by fcorourke on 2008-05-17
Thanks :-)  === I have to run to work. But will give it a shot. I can just not understand why once I had it working --- an update knocked it out. Why have threads to fix things when standard updates are going to kill the time you spent fixing it in the first place?? Why fix anything, like it as it is -- sounds too much like Vista & SP1 update. Ill planned and not really thought out. I run both platforms & am truly thinking of building an Intel Mac. I need/want a faster machine and just as well give myself another option. Good fast machine cost over $1,000 for all basic parts -- so why not make it a 3 way machine. I used to love my Mac years ago & it ran circles around IBM DOS. Just no business compatibility in files. Thanks anyway for the advice, I just woke up early today and wanted to finish seeing a DVD i bought & no longer can without going into windows. Which I was/am trying to ditch. Maybe will for a Mac/Windows/Linux machine. I already know which will run the smoothest :-(

    Fred

---

### Post by Fixxxer on 2008-05-17
> **kristianz said:**
> I recently upgraded to Hardy, and immediately noticed how sound would skip (sometimes slightly, sometimes rather severely) when switching between virtual desktops.

Anyone else experience the same?

I experienced that, sound would skip alot, and not just when switching desktops but also when opening menus etc. I fixed it by adding my user to the pulse-rt group. No skipping whatsoever anymore! The solution was suggested in a bug report for pulseaudio I think. Give it a try, hope it works for you too.

---

### Post by kristianz on 2008-05-17
> **prshah said:**
> Switching desktops etc, especially with compiz running is an intensive job, and will cause interruptions unless your graphics is setup correctly. Eg, if you are using the (default) vesa driver, you will not get best graphics performance, this will in turn degrade performance elsewhere.

Do you have an Intel onboard graphics card? If that is the case, then the default hardy install is not (usually) optimized for it.

If you have an intel onboard graphics card, post back for correct optimization.

Otherwise, some more config details will be helpful; eg. RAM, etc

I noticed that music skips with Amarok (my music player of choice) and Rhythmbox, but not sound in VLC or Totem. I tried changing output plugin in Amarok from "autodetect" to "pulseaudio" (which I believe is what Hardy uses), and ... I thought it helped at first, but now it's skipping again when I move about, so maybe it was just a fluke.

Actually it's not just switching desktops that produces skipping, sound also skips (but less so) when Alt-TABing between windows on the same desktop.

I'm not running composite WM, just a very plain Gnome with ATI proprietary driver. 1 GB RAM, CPU is Athlon 64+ 3500+, so it *should* be able to play back music smoothly... RAM usage and CPU usage are both low.

The following applications skip:
Amarok (using PulseAudio, it produces an error when selecting ALSA)
Rhythmbox (no setting for sound server, but I presume it uses PulseAudio as set in Gnome sound settings)

The following does not skip:
VLC (no skipping with ALSA or with PulseAudio)
Totem (no setting)
Audacity (set to use ALSA for playback, no option to use PulseAudio)

Seeing as some apps produce skipping and some don't should give a clue to where the problem is, but it doesn't seem to lie with ALSA vs. PulseAudio (Amarok skips with PA, VLC doesn't). Any ideas how I can narrow it down?

---

### Post by kristianz on 2008-05-17
> **Fixxxer said:**
> I experienced that, sound would skip alot, and not just when switching desktops but also when opening menus etc. I fixed it by adding my user to the pulse-rt group. No skipping whatsoever anymore! The solution was suggested in a bug report for pulseaudio I think. Give it a try, hope it works for you too.

Nope, didn't work. Thanks for the suggestion, though.

---

### Post by mgmiller on 2008-05-17
Here is what fixed the skipping for me.  I got this from another thread, but I forget which one.

1) sudo apt-get install --reinstall pulseaudio (don't know if absolutely necessary)

2) gksudo gedit /etc/pulse/daemon.conf ( I would suggest making a backup of this file before you edit it.)

3) replace the lines containing "high-priority" and "nice-level" with
Code:

high-priority = yes
nice-level = -15

and the lines containing "default-sample-rate", "default-fragments" and "default-fragment-size-msec" with
Code:

default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10

4) log off and log in

---

### Post by kristianz on 2008-05-23
Thanks for the suggestion. It didn't make any difference, unfortunately. The skipping is still there in Amarok (but not VLC, which also uses PulseAudio) when I move about the desktop.

---

### Post by mgmiller on 2008-05-23
Here is the absolutely latest info on fixing sound skipping in Hardy:
[http://ubuntuforums.org/showthread.php?p=4928900]("http://ubuntuforums.org/showthread.php?p=4928900")

---

### Post by Zorael on 2008-05-23
Blanket advice for everything: from what I understand Pulse takes some (in cases noticeable) cpu time, so you could try to disable it and see if things improve.

---

### Post by cor2y on 2008-05-23
Ever since playing around with the Beta version of Hardy i have learned my lesson.
DON'T DO UPGRADES ONLY CLEAN INSTALLS.
This sorted out like 85% of my hardy problems when i tried the beta and later the full version, from not being able to install the closed source nvidia drivers to audio/video problems and system freezes.
The others were the incomplete install of Pulse Audio in Hardy, to some kernel errors for the Beta and some kernel problems with virtualbox in the final version.

---

### Post by 47_MasoN_47 on 2008-05-23
I've noticed that videos don't look as clear on mine after going to 8.04.  DVDs also seem to have trouble playing for some reason.  I haven't had any problems with sound skipping though.

---

### Post by Rob-e on 2008-05-23
> **mgmiller said:**
> Here is what fixed the skipping for me.  I got this from another thread, but I forget which one.

1) sudo apt-get install --reinstall pulseaudio (don't know if absolutely necessary)

2) gksudo gedit /etc/pulse/daemon.conf ( I would suggest making a backup of this file before you edit it.)

3) replace the lines containing "high-priority" and "nice-level" with
Code:

high-priority = yes
nice-level = -15

and the lines containing "default-sample-rate", "default-fragments" and "default-fragment-size-msec" with
Code:

default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10

4) log off and log in

this actually fixed it for me, except first it broke it...
i reinstalled the package, and backed up the config file, made those changes, loged off and on and it broke it more (some error came up when playing a movie)
so i reverted to my backed up file, loged off/on and it was still broken. i restarted and now it works

soooooo install that package and restart works :confused:

---

### Post by mgmiller on 2008-05-23
This line seems to have a big influence depending on your sound card and system specs.  

```
default-fragment-size-msec = 10
```

10 worked for me, but in the thread located here: 
[http://ubuntuforums.org/showthread.php?p=4928900]("http://ubuntuforums.org/showthread.php?p=4928900")

This number has been changed to 5.

Read the thread I linked to if you are still having sound problems.

On one older system I have, the only thing that worked was going into System > Preferences > Sound and in the devices tab, changing everything from "Autodetect" to alsa.  This effectively uses asla instead of pulse audio for pretty much everything.  

This should only be looked at as a temporary work around, as, in the very near future, everything is going to use pulse audio.  I understand there are kernel level fixes already in hardy proposed that fix this as well as other problems.

---

### Post by mgmiller on 2008-05-23
> **cor2y said:**
> Ever since playing around with the Beta version of Hardy i have learned my lesson.
DON'T DO UPGRADES ONLY CLEAN INSTALLS.


For some hardware and software combinations, that is a true statement.  But in my vast experience :roll:(of upgrading all of 2 systems that I built, one with ATI video and one with Nvidia), you can do upgrades pretty much painlessly.  Look at my signature line to see how far I've gotten with one of my machines without doing a reinstall.  My other one started with a clean install of 6.06 and has been upgraded right along to 8.04.

Admittedly, some of the earlier upgrades required a fair amount of tinkering to get working correctly, but the last 2 (from 7.04 to 7.10 to 8.04) have been damn near perfect.

---

### Post by kristianz on 2008-05-24
> **cor2y said:**
> DON'T DO UPGRADES ONLY CLEAN INSTALLS.


Well, I know that's how they do it in Windows country, but for me that is simply out of the question. A properly designed OS should never have to be reinstalled.

---

