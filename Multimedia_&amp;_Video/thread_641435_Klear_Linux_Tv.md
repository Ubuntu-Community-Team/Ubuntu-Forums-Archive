---
title: "Klear Linux Tv"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by JoeDaPro on 2007-12-15
Ive bought a WinTv USB adapter for my computer, but on windows its just terrible, crashes as soon as you open it, so im trying to get klear on linux, but i get this error.
[IMG]http://img167.imageshack.us/img167/7949/screenshotklearerror1qt4.png[/IMG]

Whats up :(?

---

### Post by fsando on 2007-12-17
I see the same. I went through a lot of trouble several months ago without any luck. You can download those files it asks for (as I remember they are on the klear site or you can get directions from there).

I downloaded them and put them in klear's config folder (as far as I remember) but never succeeded in getting anywhere, probably didn't try hard enough.

I suppose they contain some kind of signal configuration / station identification. At least it appears from those t-,s-,c-zap files that they take very specialized knowledge to create. Maybe klear only works in a few situations or with some stations.
What I just did: Deleted the 
~/.klear/klear.conf
Restarted klear and got a configuration dialog. Two things that are very telling 
1. "scanning is not yet implemented"
2. In the dropdown menu only a few locations are present
What exactly it means I don't know but to me it spells "alpha" and needs some serious tweaking (or luck) to get it up and running.
MINOR UPDATE:
I downloaded various channels.conf files from klear.org, and repeatedly restarted klear (frequently deleting the klear.conf as it gives a "first start" config dialog) right now it shows channels in config dialog on "first" start, subsequent starts get past the initial error and hang on the splash screen (I have to kill it from system > admin > system monitor) so still no functionality. I'm inclined to believe that the problem is rather with some dependencies in Ubuntu - the errors could be a missing library or something? Maybe one should file a bug report or at least post in klear's forums.

---

