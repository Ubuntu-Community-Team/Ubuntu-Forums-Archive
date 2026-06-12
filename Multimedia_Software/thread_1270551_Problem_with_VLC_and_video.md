---
title: "Problem with VLC and video"
date: 2009-09-19
forum: Multimedia Software
---

### Post by jonnydopemsr on 2009-09-19
Okay well i dont know if the video audio is doing it as well as my speakers are not hooked up yet but here is the deal...

I am running VLC 1.0.1 in ubuntu 9.04 with the latest NVIDIA drivers and for instance when playing ratatouille i will get a choppy video on my 47" LG LCD... i have a 9800GT 512 OC... that should be enough??? but i also have tried to turn off compiz and anything else i saw in forums... any help that would be great...

Thx

Jonny

---

### Post by jonnydopemsr on 2009-09-21
anything? any leads or same issues?

---

### Post by cor2y on 2009-09-21
You say you have the latest drivers so i dont know you might try doing this with compiz installed and see if it helps

Open Compiz Config Settings Manager (System->Preferences->Compiz Config Settings Manager) go to General Options->DIsplay Settings, uncheck Dectect Refresh Rate and manually set your refresh rate to TWICE what your monitor's refresh rate is example if its 60 set it to 120 also check Sync To VBlank in there.
In The Nvida X Server Settings App make sure Sync To VBlank is also checked under XServer XVideo Settings. Under OpenGl Settings make sure Sync To VBlank is NOT CHECKED.

This solves some of the video tearing issues/choppiness also with the latest driver installed make sure vdpau is in use as your decoder , unfortunately this means using mplayer/smplayer and not vlc i am not too sure if vlc has vdpau support yet.
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625) [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa) smplayer/totem-xine with vdpau links to a ppa archive so you dont have to compile it yourself hope this helps.

---

### Post by jonnydopemsr on 2009-09-21
the things i wasnt paying attention to was that i will forsure check that out when i get off work... i'm going to keep my fingers crossed...

thx alot!

let you know tonight sometime...

---

### Post by jonnydopemsr on 2009-09-21
well i tried the first area you spoke of and nothing still samething.... later this week i will try te second thing out to find out.... thx again

---

