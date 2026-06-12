---
title: "Problems playing music library in Banshee"
date: 2009-12-06
forum: Multimedia Software
---

### Post by judith_sw on 2009-12-06
Hi,

I finally managed to get my imported music library working with Banshee last night ... I was delighted, as I has totally failed with Rhythmbox in Mandrivan and Xubuntu. 

This morning it doesn't work any more ... the play sign doesn't go green, tracks get a red cross on them when I try to play. No warnings come up.

Just to summarise: all music was imported via an external hard-drive and is stored in the Music folder. The format is .m4a, as this is from an iPod library. 

Is there any way I can get this working?

Thanks!!!

---

### Post by sdowney717 on 2009-12-06
banshee has major bugs
i tried it with video podcasting and get cpu 100%, random shutdowns x server errors, etc...

people say good things about exaile, i tried it and it works
[http://www.exaile.org/](http://www.exaile.org/)

they builtin shoutcast radio also works well

here is a ppa
[http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu)


[http://www.exaile.org/downloads](http://www.exaile.org/downloads)

---

### Post by judith_sw on 2009-12-06
Thanks - downloading it now. I'll let you know how I get on!

---

### Post by judith_sw on 2009-12-06
Yes it works - thank you!

One additional little question ... the main volume on the computer keeps defaulting back to mute. I am using alsamixer and can change the setting either in the window or via a command lne ("alsamixer -c 0"), but I cannot save it. I used "alsactl store" in Mandriva, but it won't let me do this in Xubuntu :-(

---

### Post by sdowney717 on 2009-12-06
there is bound to be a configuration file for this that stores that setting 

try looking in this
run 'gconf-editor'

---

### Post by sdowney717 on 2009-12-06
have you checked here
sound preferences?

---

### Post by second.exodous on 2009-12-06
> **judith_sw said:**
> Hi,

I finally managed to get my imported music library working with Banshee last night ... I was delighted, as I has totally failed with Rhythmbox in Mandrivan and Xubuntu. 

This morning it doesn't work any more ... the play sign doesn't go green, tracks get a red cross on them when I try to play. No warnings come up.

Just to summarise: all music was imported via an external hard-drive and is stored in the Music folder. The format is .m4a, as this is from an iPod library. 

Is there any way I can get this working?

Thanks!!!
It looks like you've already moved on, but I had the same problem with Banshee.  Right click one of the tracks that is xed out and see where Banshee thinks it is, it might think it's on your external drive.

I had my backup drive plugged in when I started up Banshee but before I moved everything to my /home/music directory and it linked everything on my external drive.

So to sum up check where Banshee thinks the track is by right clicking a xed out track and go to properties and if it thinks it's somewhere besides your music folder.  If it thinks it's on the external drive it's just easier to remove all your media from Banshee and then import your /home/music folder again.  Make sure you remove everything from Banshee before re-importing from /music or you'll still have a lot of dead files.

I've been using Banshee since 8.10 and this last update to 9.10 messed up like I said above.  Besides that I have really enjoyed Banshee and recommend it to all *buntu users.

---

### Post by judith_sw on 2009-12-07
Hi,

Still no luck on saving the sound settings. I cannot find a preferences menu in 9.04. There are options to change the sound in the panel, but these are the master setting defaults to 00 when restarting. I can change these setting by using "alsamixer -c 0", but when I try "sudo alsactl store" the response is:

E: core-util.c: Home directory /home/judith not ours

Any ideas???

---

