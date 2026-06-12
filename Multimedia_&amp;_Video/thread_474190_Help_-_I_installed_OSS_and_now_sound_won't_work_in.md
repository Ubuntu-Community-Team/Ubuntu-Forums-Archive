---
title: "Help - I installed OSS and now sound won't work in Firefox or Icebreaker"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by JoeLondon on 2007-06-14
This morning the sound was working fine for everything on my system.  My goal now is to get back to that state of affairs.

I think that I was using ALSA before, as I hadn't changed anything drastic soundwise since originally installing Ubuntu (Dapper Drake). My problems began when trying to play Doom 3.  It didn't work with ALSA, so I went to [www.opensound.com](www.opensound.com) and got the free version of OSS for my system (the amd64 .deb package).  I used gdebi to install this package, and I had sound for Doom.  Great!

However, sound no longer worked in Firefox (on youtube) or Icebreaker, and I no longer got the bongo sound at the gdm login screen.  Also, the sound icon in the top right was now disabled.  Going to System -> Preferences -> Sound and pressing play next to the login sound did nothing. VLC still made sound, as did Music Player Deamon.  So I figured I would remove OSS and go back to trying to get ALSA to work with Doom, rather than get OSS to work with everything.

I did this (recklessly) by typing ```
dpkg --purge oss-linux
``` in a terminal window while still logged in.  I got a couple of error messages saying that there were things still using OSS and soundoff could not be run at this time.  This didn't get me back to where I started.

Some other things I tried were (in order):

1. reinstall everything that was installed that came up with a search for "alsa" in synaptic.

2. reinstall and then uninstall oss from runlevel 1 - meant I didn't get the error messages about programs using oss, but didn't acheive anything else.

3. step 1 again

4. reinstall everything that was installed that came up with a search for "sound" in synaptic

I rebooted the machine in between most steps.

I didn't neccessarily expect any of this to work, I just don't really know what I'm doing.  Maybe some kind of config files neccessary for ALSA to work were messed with in the installation of OSS.  Help from anyone who has any idea what to do would be much appreciated.  Thanks.

---

### Post by JoeLondon on 2007-06-14
In fact, the last step did restore sound to firefox and the gdm login screen, and somehow Doom 3 still has sound.

---

