---
title: "Movie Player"
date: 2009-11-11
forum: Multimedia Software
---

### Post by nishant.singh28 on 2009-11-11
I am a movie junkie. Recently I decided to switch tu Ubuntu after Karmic supported my laptop (Studio 1555) audio out of the box. But I can't find a suitable movie player. I hate VLC so it is not an option. Mplayer keeps getting stuck playing 720p and 1080p mkv's and mp4's (the formats I use). I have 4GB RAM and 512MB ATI HD 4570 with proper drivers in place. I tried every player available in the Ubuntu Software Center but it all sucks. I used The KMPlayer on Vista but it does not run on Wine. I need something that allows me to have custom keyboard shortcuts and allows me to change the font and size of the subtitles and allows me to resync the subtitles easily. One more thing....I am using the latest version of Mplayer with SMplayer but it gets stuck a lot of times. Please DO NOT SUGGEST ANYTHING THAT IS ALREADY THERE IN THE UBUNTU SOFTWARE CENTER. I have tried all of it.

---

### Post by andrew.46 on 2009-11-12
Hi nishant,

> **nishant.singh28 said:**
> I am using the latest version of Mplayer with SMplayer but it gets stuck a lot of times. Please DO NOT SUGGEST ANYTHING THAT IS ALREADY THERE IN THE UBUNTU SOFTWARE CENTER. I have tried all of it.

Strictly speaking you are actually *not* using the latest MPlayer and SMPlayer. The MPlayer developers recommend the use of their svn repository and the Karmic version of MPlayer is a little way behind that. Have a look at a guide I wrote recently:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package 
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

and perhaps see if this addresses any of the issues you mention?

Andrew

---

### Post by nishant.singh28 on 2009-11-12
> **andrew.46 said:**
> Hi nishant,



Strictly speaking you are actually *not* using the latest MPlayer and SMPlayer. The MPlayer developers recommend the use of their svn repository and the Karmic version of MPlayer is a little way behind that. Have a look at a guide I wrote recently:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package 
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

and perhaps see if this addresses any of the issues you mention?

Andrew

It does not compile....the make command exits with error status 1.

---

### Post by andrew.46 on 2009-11-12
Hi nishant,

> **nishant.singh28 said:**
> It does not compile....the make command exits with error status 1.

I do not wish to hijack your thread here so perhaps if you post on that particular thread and give the exact error message + a little bit of the output before compiling fails?

All the best,

Andrew

---

### Post by rvm4000 on 2009-11-12
> **nishant.singh28 said:**
> I am using the latest version of Mplayer with SMplayer but it gets stuck a lot of times.

Change the audio driver from alsa to pulse.

---

