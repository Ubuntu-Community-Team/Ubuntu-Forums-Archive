---
title: "dvb-t problem (hauppauge wintv hvr 1100)"
date: 2009-05-19
forum: Mythbuntu
---

### Post by spoky99 on 2009-05-19
I'm trying to see work mythbuntu with this card, and... I have some problem.
The firmware is not automatically stored in /lib/firmware
Into mythtv-setup the channel scan goes well only using the france frequenze (is missing the italian frequence)
Using bvb-util I made my own channel.conf, but if i try to make see it from mythtv-setup the scan don't found any channel
If I set manualli frequency and options... also don't found any channel.
For other italian is important reorder the channel list because more mux ave different tv with the same number of channel, you could found more tv at the channel #1 to #5. If you don't reorder the channel number the tv-frontend don't start.

using xine and channel.conf I see the card working well

using mythfrontend... I start seeing the channel, but wen I selected one channel the frondend crasced and now I'm not in able to see any tv.
Every time that I start tv it crash.
starting mythfrontend from terminal I see only this error

2009-05-19 16:32:15.222 TV: Changing from None to WatchingLiveTV
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2009-05-19 16:32:15.237 Realtime priority would require SUID as root.
2009-05-19 16:32:15.247 Video timing method: DRM
2009-05-19 16:32:15.361 XMLParse::LoadTheme using /usr/share/mythtv/themes/ProjectGrayhem/ui.xml
2009-05-19 16:32:18.063 AFD Error: Could not find codec parameters. file was "/media/dati/live/3201_20090519163215.mpg".
2009-05-19 16:32:18.063 Couldn't open decoder for: /media/dati/live/3201_20090519163215.mpg
2009-05-19 16:32:18.064 NVP, Error: JumpToProgram failed.
2009-05-19 16:32:18.064 NVP, Error: Unknown error, exiting decoder
2009-05-19 16:32:18.064 TV: Attempting to change from WatchingLiveTV to None
2009-05-19 16:32:23.420 TV: Changing from WatchingLiveTV to None
2009-05-19 16:32:23.496 DPMS Reactivated.

this are the permission of folder and file
drwxrwxrwx 2 luca mythtv    6 2009-05-19 17:26 live

I don't know how to solve this
someone could help me?

---

