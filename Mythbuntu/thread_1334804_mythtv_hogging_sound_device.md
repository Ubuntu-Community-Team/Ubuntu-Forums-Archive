---
title: "mythtv hogging sound device"
date: 2009-11-22
forum: Mythbuntu
---

### Post by linuxgrrl on 2009-11-22
I have a clean install of mythbuntu 9.10 and added gnome desktop to it.

with prior versions of mythtv, I was able to listen to music on rhythmbox or banshee so long as mythtv wasn't actualy playing TV.

Now, with this version, no music works if mythtv is even open.  My sound device in mythtv is set to "alsa:default".  I have an onboard sound device and everything is set as mythbuntu had it (nothing's been tweaked except volume levels).

Is there a way to get myth to play nicer with other music players?

---

### Post by nuclearwasted on 2010-04-20
Same problem here.
Mythbuntu 9.10 that I added gnome-desktop to.

I made a menu option in mythtv to open xbmc. This worked beautifully for a while.  I don't know what I upgraded (myth? xbmc? pulseaudio?) but now when I open xbmc while mythfrontend is open (whether or not I use the menu item I created), I get no sound in xbmc. Same interaction with other programs too. Having firefox open will tie up the audio for xbmc. 

Menu sounds still play in xbmc, which blows my mind, but no audio in videos, music files don't even try to play.

I just did some more fiddling, and having firefox open doesn't seem to affect myth. and vise-versa. So I'm beginning to think my problem is an xbmc one.

---

### Post by Lepy on 2010-04-20
A few weeks ago, I had a similar problem that seemed to randomly crop up: [http://ubuntuforums.org/showthread.php?t=1443038](http://ubuntuforums.org/showthread.php?t=1443038)

I can't speak for rhythmbox or banshee, but changing xbmc's audio output to the custom device listed in mythtv (for me, alsa:default) allowed me to launch from the myth main menu and have sound. Odd, since "default" used to work fine.

---

### Post by sygin on 2010-04-28
Hi,

I have been using MythTV on 9.10 for the past 6 months. The MythTV front-end stops pulseaudio on startup and resumes it on exit. This is a workaround for a sound issue related to pluseaudio.

The new MythTV in 10.04 will not do this if PulseAudio:default is used for sound output. The problem at the moment is that the pulseaudio driver in the new MythTV that comes with 10.04 has a small bug.

I would stick with 9.10 for a month or so and upgrade when the issue with pulseaudio is fixed. Then you can have sound from many sources at the same time.

Cheers,
Sygin

---

