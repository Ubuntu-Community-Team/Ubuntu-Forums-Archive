---
title: "[SOLVED] DVD playback vob files"
date: 2008-10-20
forum: Multimedia Software
---

### Post by prabath_fun on 2008-10-20
Hi,
   I have installeded Mplayer in Ubuntu 8.10 and try to play DVD (contains 2 folders Audio_ts and Video_TS (contains vob files of video)) with 5.1 Dolby surround supported, just by right click on GUI and selected play DVD.  Nothing played.
   Further, I tried by playing individual files. I got video and Audio but not 5.1 Dolby surround after setting video and audio settings with lot of combinations. I enabled also 5.1 speakers setting as well and un-muted surround option. No improvement.
   
  Only for playing DVDs, I am rebooting my PC to windows. If I get it solved, Then, I completely shift to Ubuntu Linux.

   Please suggest me the settings for Mplayer / some other player with following features
   1. without setting video and audio options for different file formats, It has to play like Windows Media player 10/11 (plays DVD, CD, DIVX, etc.,) without any setting changes. At least by installing some packages.
   2. 5.1 surround support, at least by installing some supporting drivers.
   3. Continuous DVD playback.
   4. Menu playback. (I could not able to play menu. Can able only file by file).

My Motherboard is D102GGC2 with inbuilt 5.1 supports.
   Realtek ALC883 High Definition Audio.
   Integrated ATI radeon x300 based graphics.
   ATI Radeonexpress 200 chipset.

   Please suggest me some points.
With advanced Thanks,
Prabath

---

### Post by ne0h on 2008-10-20
MPlayer should work fine. Anyway, try VLC [http://www.videolan.org]("http://www.videolan.org"). If its works, then something wrong with your MPlayer installations.

---

### Post by prabath_fun on 2008-10-20
I have instalded by downloading package by package. Can you provide repo to add it in synaptic.

With thanks,
Prabath

---

### Post by Brain-free on 2008-10-20
No need to add repos. Go to Add/Remove in Applications and type "vlc" or "videolan", I'm not sure which. Then install it.

---

### Post by prabath_fun on 2008-10-21
I got message that, Cannot install vlc-nox and some other packages and start Synaptic for VLC media player installation.
  Please help me.
Prabath

---

### Post by prabath_fun on 2008-10-21
I got message that, Cannot install vlc-nox and some other packages and start Synaptic for VLC media player installation.
  Please help me.
Prabath

---

### Post by clancymf on 2008-10-21
what does 

```
sudo apt-get install vlc
```

tell you?

---

### Post by prabath_fun on 2008-10-22
Finally, I installded by downloading package by package from packages.ubuntu.com.
   Now, VLC player is playing from DVD menu and I can able to jump menus and play movie.
   But,
   1. Picture is not smooth, getting small squares (Say 4-8 pixel forms a square) instead of smooth picture. 
   2. Audio also not so clear. somthing like clipped in levels.
   3. How to set for 5.1 surround speakers?
   4. I installded from hardy link from packages.ubuntu.com. How to update? That is one more link is available - hardy-update. I have to download package by package? 
   5. Further, How to update vlc player alone?
Please help me.
Prabath

---

### Post by clancymf on 2008-10-22
Why are you going to the internet to install packages?  This is the old windows way of thinking...

Use synaptic, apt-get, add/remove, etc...

I think it will solve most of your problems.

what did ```
sudo apt-get install vlc
``` respond back with?

---

### Post by prabath_fun on 2008-10-25
Hi,
   I uninstalded VLC player installded package by package and restarted PC. 
   Then, I tried "sudo apt-get install vlc" in terminal. It downloaded 3 packages "vlc-nox", "vlc-pluguns" and "vlc" and installded. Then, restarted PC.
   Still, Picture is not blurred. Under preferences -> audio -> File -> No of output channels, I set to 6. But, still, I believe that alsa need to be set for 5.1 channel.
[COLOR="Blue"] Prabath[/COLOR]

---

### Post by prabath_fun on 2008-10-28
Any update on this, please.......

---

### Post by prabath_fun on 2008-12-16
[COLOR="DarkGreen"]Hi,
   I got 5.1 channel surround sound through steps I described in the thread [http://ubuntuforums.org/showthread.php?t=845784.:p](http://ubuntuforums.org/showthread.php?t=845784.:p)[/COLOR]
   [COLOR="Purple"]I got VLC player also working with smooth picture in normal mode. If, I switch to full screen mode, then I feel some frames were missing for approximatly 1-2 seconds. This is noted down by observing the slight jump in movements in picture. 
   I feel that, I am missing some video settings, some where. Please indicate me, by the way where I can do the settings.[/COLOR]

[COLOR="DarkGreen"]With advanced thanks,
Prabath[/COLOR]

---

### Post by prabath_fun on 2008-12-18
[COLOR="Sienna"]Frame missing problem got solved by disabling visual effects from right click on desktop -> Visual effects -> none.[/COLOR]

---

