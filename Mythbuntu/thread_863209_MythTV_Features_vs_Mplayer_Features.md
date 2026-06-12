---
title: "MythTV Features vs Mplayer Features"
date: 2008-07-18
forum: Mythbuntu
---

### Post by maxim99 on 2008-07-18
I was using the Default in-built player to play some videos and I tried to do some things like turn on subtitles, and switch audio channels and such but I was unable to find any keys that did this on the keyboard.

Are these features there and I just couldn't find them?

I switched players to Mplayer and was easily able to find the keys that I wanted in order to switch subtitles, audio channels, do slow-mo and many other features that i'll likely never use. I was able to find what I was looking for, and since then I have used the lirc configs to set up my remote proper to be able to do everything I need.

Comparitively speaking Mplayer seems to be more featureful than the MythTV that's built-in. Given that i'm new to both players i'm not familiar with where they are in development. In addition I don't know how MythTV is integrated into the Mythfrondend. It might be that MythTV has the features i'm looking for just not implemented into the Mythfrontend. 

Personally I like the look and feel of MythTV where it displays the progress of the video in a freindly skinable overlay. However I noticed that while changing the volume while playing a DVD the player seemed to skip and Mplayer did not have this symptom. My system is by no means a power house, but it is atleast 64 bit and should be able to handle playing a DVD and changing the volume. Maybe I just don't understand anything about this application, but i'm learning. It's been very usefult so far.

---

### Post by laga on 2008-07-18
Hi,

you can bring up an OSD menu by pressing "m" in MythTV. If you want a complete list of all available keybindings, look for keys.txt. It's available in /usr/share/doc/mythtv-frontend/keys.txt.gz on my box.

You can also install the mythcontrols plugin to rebind the keys, but keys.txt is probably less painful.

HTH,
laga

---

