---
title: "HDA intel: sound trouble... I think I'm gonna cry soon :P"
date: 2009-09-09
forum: Multimedia Software
---

### Post by gukke on 2009-09-09
Ok, so I bought this laptop: HP dv-3 2140. My sound doesn't work and it drives me insane. I have spent 10 hours + on googling and troubleshooting to fix this problem. 
I am new to Linux (been using it for a week or so) but I think I've managed to do the basic troubleshooting for a problem like this: 
ALSA-mixer is not muted and detects the sound card (HDA intel) and I have reinstalled Ubuntu to unsure that my "tinkering" is not a factor...
 I've also followed the instructions of this thread (adding some lines of text in some file called alsa.conf or something like that) :

[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

but it didn't help.


So, what I'm trying to do now is to install the latest ALSA-drivers (alsa-driver, alsa-lib and alsa-utils, all of the latest version: 1.0.21). I came across some instructions on how to do this:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65078](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65078)

I did exactly like that (except for replacing "1.0.19" with "1.0.21" which is the current version) and everything was going great until I came to

cd ~/alsa-utils-1.0.19
./configure                 < ---- THAT STEP
make
sudo make install

because I got an error when I wrote ./config, the last to lines read:

[B]checking for new_panel in -lpanelw... no
configure: error: panelw library not found[/B]

So it seems like the computer can't find something called new_panel in -lpanelw... whatever that is, and because of that an error occurs and I can't **make** the file ='(

So if anyone of you know how to fix or circumvent this particular problem (or the general no-sound-problem... perhaps installing the 1.0.21 alsa-drivers isn't even a way to solve this...?) I would be very, very grateful! (actually I'm grateful that you've even bothered to read this wall of text..)

:guitar:

---

### Post by nabukadnetsar on 2009-09-11
Have you tried this link? It may solve your problem with panelw.

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

---

