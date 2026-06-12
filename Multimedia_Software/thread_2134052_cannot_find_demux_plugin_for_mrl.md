---
title: "cannot find demux plugin for mrl"
date: 2013-04-10
forum: Multimedia Software
---

### Post by auy2006 on 2013-04-10
&#3657;Hi I'm have a problem I can't play dvd vcd from cd every program.example kaffeine it's show cannot find demux plugin for mrl...I find this in google I find way to solved


sudo apt-get update && sudo apt-get upgrade[COLOR=#333333][FONT=Ubuntu]Install Kaffeine and it's xine engine (Note: xine supports DVB and the gstreamer engine from kaffeine is far from done)[/FONT][/COLOR]

sudo apt-get install kaffeine libxine1 libxine1-all-plugins phonon-backend-xine[COLOR=#333333][FONT=Ubuntu]If you have videos in proprietary formats (or copy protected DVD's) you might need to install the "w32codecs" and "libdvdcss2" packages from the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository.

from [https://help.ubuntu.com/community/Kaffeine](https://help.ubuntu.com/community/Kaffeine)

but I can't  [FONT=UbuntuMono]sudo apt-get install kaffeine libxine1 libxine1-all-plugins phonon-backend-xine it show

[/FONT]Package phonon-backend-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'phonon-backend-xine' has no installation candidate

and I try to find this [FONT=Verdana]problem in google but I do everything it still stay

some people can help me please 

but I just upgrade 12.04 to 12.10 on 12.04 I can play vlc but on 12.10 can't play everything

PS i'm sorry about my [/FONT]language 



[FONT=UbuntuMono]

[/FONT][/FONT][/COLOR]

---

### Post by auy2006 on 2013-04-10
yessss I can solved this use vlc go vlc > open dics> select svcd/vcd

---

