---
title: "HD/ Full screen video 'stutters'"
date: 2010-08-17
forum: Multimedia Software
---

### Post by DeTeReR on 2010-08-17
I'm new to Ubuntu and I've been having some problems with videos / games:

When running videos at certain resolutions the framerate drops to a few fps (the audio is fine):


[LIST]
[*]In youtube videos, if it is NOT fullscreen, then the video plays smoothly up to 420p.
[/LIST]

[LIST]
[*]If it IS fullscreen, then the resolution needs to drop to 240p to play smoothly.
[/LIST]


[LIST]
[*]Using BBC iplayer "normal" resolution runs fine, but HD is always stuttery.
[/LIST]

[LIST]
[*]I cannot get a framerate over ~10fps in Team fortress 2 (using wine)
[/LIST]

What DOES work is "normal" resolution videos playing fullscreen in VLC.

When I boot my machine in Win XP, all of the above work fine. 

My computer is a core 2 duo 2.13GHz
Graphics: Nvidia 7950 GT, running NVidia  drivers version 256.
Gnome: 2.30.2
Ubuntu 10.04

Is there anything that can be done to fix/ improve this?
Is there something really obvious that I can have missed?

---

### Post by sticky_icky on 2010-10-28
**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

