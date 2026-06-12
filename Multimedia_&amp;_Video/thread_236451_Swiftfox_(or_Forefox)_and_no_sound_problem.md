---
title: "Swiftfox (or Forefox) and no sound problem"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by mkljun on 2006-08-14
It took me a day to figure this one out. 
There were two solutions that worked for me.

I run Swiftfox which I manulay downloaded from Swiftfow web page.
As (like firefox) it is not capable to handle ESD I tried to disable it first

$ ps ax | grep esd
  978 pts/1    SL     0:00 /usr/bin/esd -nobeeps
  980 ?        Ss     0:00 /usr/bin/esd -nobeeps
$ kill -9 978

And I went to System-Preferences-Sound and unchecked "Enable software sound mixing"

So now only one application at a time could use /dev/snd. And sound in Swiftfox (Flash, Real audio, ...) worked. But later I came accross a package alsa-oss

$ sudo aptitude install alsa-oss
$ aoss /home/user/swiftfox/swiftfox &

I also enabled EDS again and everything works now. (Multiple programs can play sound at once). 

Btw: it is possible to run every application with aoss prefix.

Hope this one helps somebody!

Other sound problems solutions:
[http://ubuntuforums.org/showthread.php?t=187752&highlight=sound+flash](http://ubuntuforums.org/showthread.php?t=187752&highlight=sound+flash)
[http://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once](http://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once)
[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

---

