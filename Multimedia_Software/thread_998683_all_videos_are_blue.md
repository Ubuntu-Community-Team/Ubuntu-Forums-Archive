---
title: "all videos are blue"
date: 2008-12-01
forum: Multimedia Software
---

### Post by kevil99 on 2008-12-01
ALL of my media players are playing back all my video files in blue.

every video has a blue hue to it now.i can still watch and see what i have but its blue:confused:

vlc media player
dragon player
mplayer.


any suggestions?

---

### Post by gandaran on 2008-12-01
first set the colour on totem movie player » edit » preferences » screen tab
if this still doesn't work, try this, disable desktop special effects, disable compiz or go to vlc and mplayer preferences, change the video output/driver to x11 or xv

---

### Post by sonicb00m on 2008-12-03
this bug is driving me nuts. i can't understand why it's not sorted. it's been months now.

The quickest fix is to run the nvidia settings manager as it sorts the hue out immediately. But it's very annoying.

---

### Post by uberdonkey5 on 2008-12-17
Preferences worked for me, I just changed hue (to full) as I was watching a vid.

---

### Post by quzomatic on 2008-12-17
have you tried downloading the codecs?

---

### Post by dlfuller on 2008-12-20
What's a simple fix for the nVidia default color hue problem?

There are many recent threads discussing this problem both here and in the nVidia Linux Support Forums <http://www.nvnews.net/vbulletin/forumdisplay.php?f=13> but not many solutions.

I have a new installation of 8.10 using the proprietary hardware driver nVidia accelerated graphics driver (version 177) for a GeForce 8500 GT (rev a1) graphics card.

Displayed colors seem fine for the desktop and most applications. But video color is all screwed up with drastic color shifts (default hue). The strange part is that just opening System > Administration > nVidia X Server Settings immediately corrects the colors.

After quitting a video application the screwed up colors will return when the application is restarted later. Again the step of simply opening the nVidia X Server Settings brings the colors back to normal.

So is there an easy way to fix or automate this instead of dealing with it manually easy time?

---

### Post by shredder12 on 2008-12-20
I am having a similar problem with my system.. I am using Hardy.. and sometimes  a video is played in blue colour.. this is the case with each and every player.. The only solution that i have is to logout and login again.. This fixes the problem but it is really annoying to stop all your running applications and log out.. Well i don't have any desktop effects activated on my system.... And I even have System->preferences->appearence->visual effects  set to NONE... But i do have nvidia propreitary drivers installed.... I am not able to understand what's actually creating the problem??
Any help please..

---

### Post by shredder12 on 2008-12-20
I am having a similar problem with my system.. I am using Hardy.. and sometimes  a video is played in blue colour.. this is the case with each and every player.. The only solution that i have is to logout and login again.. This fixes the problem but it is really annoying to stop all your running applications and log out.. Well i don't have any desktop effects activated on my system.... And I even have System->preferences->appearence->visual effects  set to NONE... But i do have nvidia propreitary drivers installed.... I am not able to understand what's actually creating the problem??
Any help please..

---

### Post by dlfuller on 2008-12-20
Take a look at the NVIDIA Linux Support Forums > NVIDIA Linux <http://www.nvnews.net/vbulletin/>.

Search for "default hue" in recent threads and there are several explanations covering the problem.

---

### Post by crazy ivan on 2008-12-25
>  So is there an easy way to fix or automate this instead of dealing with it manually easy time? 

For automatation: You could rename your video apps and place a script running "nvidia-settings" and e.g. "totem" at the same time.

Anyhow my problem is that in addition to being blue the screen flickers during video playback since update to 8.10. Opening "nvidia-settings" wont fix that..

---

### Post by crazy ivan on 2008-12-25
You could rename your video apps and place a script like "totem"

```

#! /bin/sh
totem $1 &
sleep 1
nvidia-settings &

```

But beware.. The healing effect only works a couple of times :(

Anyhow. In addition to being blue my videos flicker a lot since update to 8.10.. See [ other thread ]("http://ubuntuforums.org/showthread.php?t=824923").. Any ideas??

---

