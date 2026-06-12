---
title: "Numerous newbie questions"
date: 2011-03-22
forum: Mythbuntu
---

### Post by emunson on 2011-03-22
1. I cannot get mythtv to play music.  It indexed my collection fine but when I start a track it never starts playing.  Most of my music is in mp3.

2. mythtv will not index my existing library of videos.  I have a largish collection that is nfs mounted.  I told the backend where to find the videos on the nfs mount and when I go to watch videos, nothing is available.  The videos are mostly mp4.

3. Not sure of this as I can't get anything to play back but I don't think mythtv is using my ATI 5450  for sound output.  I am running the latest fglrx driver from the hardware manager.  alsamixer doesn't show any available volume control for the card.

Thanks in advance for your help.

---

### Post by Rasa1111 on 2011-03-22
do you have **ubuntu-restricted-extras** installed?

---

### Post by LowSky on 2011-03-22
I hope this helps

> **emunson said:**
> 1. I cannot get mythtv to play music.  It indexed my collection fine but when I start a track it never starts playing.  Most of my music is in mp3.


open a terminal type ```
sudo apt-get install ubuntu-restricted-extras
```


> 
2. mythtv will not index my existing library of videos.  I have a largish collection that is nfs mounted.  I told the backend where to find the videos on the nfs mount and when I go to watch videos, nothing is available.  The videos are mostly mp4.

open videos and press M on the keyboard to pick the option scan for changes, if that doesn't work check that the directory is correct, this isn't on the backend, but the frontend

Utilities/Setup> Setup> Media Settings> Video Settings > General settings 


> 
3. Not sure of this as I can't get anything to play back but I don't think mythtv is using my ATI 5450  for sound output.  I am running the latest fglrx driver from the hardware manager.  alsamixer doesn't show any available volume control for the card.

Thanks in advance for your help.

this is done by the frontend, not the mixer. but you will need to know which output to use.

Utilities/Setup> Setup> General> Audio System (4th page)
Scan for hardware and pick the correct option for sound on Audio output device line.

You can see all options by using this command in a terminal

```
aplay -l

```

---

### Post by emunson on 2011-03-22
> **LowSky said:**
> I hope this helps



open a terminal type ```
sudo apt-get install ubuntu-restricted-extras
```


This didn't help.  Music playback never actually starts.  I am not using a remote and there is no way to get my cursor over the play button.  If I press 'p' it toggles between play and pause but the progress bar never moves and I get no sound.  VLC is able to play any music file in my collection as long as I specify which output hardware to use (see below).

> 
open videos and press M on the keyboard to pick the option scan for changes, if that doesn't work check that the directory is correct, this isn't on the backend, but the frontend

Utilities/Setup> Setup> Media Settings> Video Settings > General settings 


I had already configured all of this properly, still no videos showing up.

the video folder is pointing at /video/Movies.

```

$ mount
...
192.168.1.50:/volume1/video on /video type nfs (rw,user=root,noexec,nosuid,nodev,rsize=1048576,wsize=1048576,addr=192.168.1.50)

$ ls /video/Movies
...
NightmareBeforeXmas.m4v
NoCountryForOldMen.m4v
OBrotherWhereArtThou.m4v
OfficeSpace.m4v
OnceUponATimeInMexico.m4v
OneHourPhoto.m4v
Outsourced.m4v
...

```

There is no file association for m4v listed in the video settings.  Unfortunately, this extension has to stay for my wife's iPad to be able to use the videos.

> 
this is done by the frontend, not the mixer. but you will need to know which output to use.

Utilities/Setup> Setup> General> Audio System (4th page)
Scan for hardware and pick the correct option for sound on Audio output device line.

You can see all options by using this command in a terminal

```
aplay -l

```

I set this and it didn't help at all.  The ALSA default device doesn't point at HDMI out, so when I use VLC to watch/listen to anything I have to tell it to specifically use the HDMI sound hardware.  I believe the ALSA default is pointing at my onboard sound which I have disabled.

---

### Post by emunson on 2011-03-22
I need to add another problem, I cannot search youtube.  I enter text into the input box and hit enter and nothing happens.

---

### Post by emunson on 2011-03-22
youtube now sort of works, probably won't be doing that from myth because I can't seem to quit video playback once started.

If I browse for files directly it finds my movies and will play them, and sound seems to be working.  I haven't tried playing music yet.

I have added another problem, the ATI free driver doesn't work with my TV over HDMI or VGA and the proprietary driver has really terrible playback issues.  I see awful distortion when I try and watch a video that doesn't show the distortion on my desktop.

So my list as it stands now is:

1. MythTV still won't index my movie files, I can get at them via the file browser but giving me entries in the Videos section is what I want.

2. Video playback is awful.  If this can't be fixed I give up and us this machine for something else.

---

