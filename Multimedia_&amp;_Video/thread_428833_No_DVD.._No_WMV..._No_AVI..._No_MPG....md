---
title: "No DVD.. No WMV... No AVI... No MPG..."
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by funky_D on 2007-04-30
hi everybody, i did this tutorial:

[COLOR="DarkRed"] Enabling Multimedia in Feisty (HOW-TO)
Video/audio codec, flash, mp3, dvd playback, and win32 Codec install for Feisty Fawn for beginners. If your a new user, copy and paste commands into the terminal, should be relatively easy from that point forward.

For mp3, etc.
Open up Add/Remove programs from your Application bar.

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)

    * "GStreamer ffmpeg video plugin"
    * "GStreamer extra plugins"
    * "GStreamer plugins for aac, xvid, mpeg2, faad"
    * "GStreamer plugins for mms, wavpack, quicktime, musepack"


Then go to Other subsection of Add/Remove and find

    * "Ubuntu restricted extras"

For Flash support

While under the "Other" section enable

    * "Macromedia Flash plugin"



For DVD Playback and Win32 Codecs

Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
Code:

$gksudo gedit /etc/apt/sources.list

to open it in the GUI text editor

or

Code:

$sudo vim /etc/apt/sources.list

to open it in the Vim command line text editor

Add the following lines to add the Medibuntu repository to the file:


Quote:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:

Code:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:

In a terminal execute the following command:

Code:

sudo apt-get update

Now you can install libdvdcss2 and w32codecs using the following command:
Code:

sudo apt-get install libdvdcss2 w32codecs[/COLOR]

and i still can't view videos... i can hear the audio of the video, but all i see is a black screen.... any suggestion? 
many thanks....

---

### Post by veloce on 2007-04-30
You could try "easy ubuntu" it's a program to set up all that stuff.  I used it on edgy, don't know if it works with feisty.

---

### Post by FoolsGold on 2007-04-30
What are you using to play the videos? Totem?

Search the repositories for vlc (or VideoLAN), install that and try loading some stuff into it. You'll at least be able to view a lot more stuff I hope.

---

### Post by funky_D on 2007-04-30
yes, i'm using totem... neither firefox can play the videos...i will try vlc
many thanks

---

### Post by funky_D on 2007-05-01
VLC does the same thing. Plays audio, but not the video. I guess it is important to say that the window resizes as if the video was actually playing.. but all i see is black.

bug?... any workaround?

many thanks

---

### Post by Gina on 2007-05-01
I think the problem could be graphics card related.  I'm running Totem in Feisty with no problem having installed GStreamer libraries and w32codecs from Medibuntu much as described above.  I'm running it sucessfully on both desktop and laptop.  Both use ATI graphics.

---

### Post by funky_D on 2007-05-01
i will try with medibuntu...
many thanks

---

### Post by killer_tank on 2007-05-01
OK this is kinda weird i think i have everything working fine with totem-xine.

have installed the new intel video driver package. everything in this laptop in intel first thing i did was get rid of the broadcom wireless card and replace with a intel one. i get everything setup including dvd playback tested with many diffrent dvd's. and the moment i turn on the desktop effects totem starts crashing.  anyone run across this yet?  chipset is a 945gm express i think.

any idea's would be appreciated am at loss here.

everything works perfectly in fedora core 6 but i just hate rpm's and multimedia setup is nightmare. Really wanted to switch to ubuntu but its looking like i am going to have to go back.

---

### Post by Frihet on 2007-05-03
Confirmed turning on desktop effects immediately causes Totem to crash when playing an MP3. Turn desktop effects off and all is well.

---

### Post by killer_tank on 2007-05-03
update

I have tried mplayer,plain xine, and totem-gstreamer all have the same problem.

Once i turn on desktop effects the crashs are perment in my install(turning off effects does not fix for me)seems to require a reinstall to get playback back. It seems to be related to the new intel driver. the i810 seems to work fine just the effects are slow and i cant get 1280x800 screen rez.

doing some more testing tommrow at work when i get some free time.

---

### Post by amiga_os on 2007-10-30
libdvdcss2 from Medibuntu with Gutsy...

dvd - hearing audio, but video is black

this is the case in totem-gstreamer, totem-xine, gxine, xine-ui, vlc... and mplayer doesn't even play!

Playing encrypted DVDs required a little fiddling, but worked fine on this laptop under Dapper, Edgy and Feisty... Gutsy it's all fallen flat on it's face.  To be quite honest, Gutsy has seen a fair few new bugs appear.

Let's hope the Heron is hard enough to squish them!

---

### Post by brothermalcolm on 2007-10-30
> **killer_tank said:**
> update

I have tried mplayer,plain xine, and totem-gstreamer all have the same problem.

Once i turn on desktop effects the crashs are perment in my install(turning off effects does not fix for me)seems to require a reinstall to get playback back. It seems to be related to the new intel driver. the i810 seems to work fine just the effects are slow and i cant get 1280x800 screen rez.

doing some more testing tommrow at work when i get some free time.

Hi I've got exact same problem here, and I think I've narrowed it down to the video driver as the root cause.

If using server-xorg-video-i810 driver (default out of box) then I can only get 1024x768 res at max.
If instead I use xserver-xorg-video-intel (as suggested by [https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29) ) then I can fix the resolution problem after running the xserver-xorg autodetect script, but then I lose the ability to open any videos (every common filetype crashes, every common vid player crashes)  

Is it going to be a choice of proper-res and no vids to watch or watch vids at wrong res ???

acer travelmate 6231 laptop
i945 chipset 
celeron M520 proccessor
i950 intel graphics media accelerator

---

