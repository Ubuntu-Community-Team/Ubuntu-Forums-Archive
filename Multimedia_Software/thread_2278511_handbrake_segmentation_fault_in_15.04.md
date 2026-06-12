---
title: "handbrake segmentation fault in 15.04"
date: 2015-05-17
forum: Multimedia Software
---

### Post by slgtheindividual on 2015-05-17
Every time I try to start a queue in handbrake it just closes, when I run it from terminal it says "segmentation fault". For some reason I can use it for single files but as soon as I add more than one file to the queue and go to start the queue it just closes. I tried adding the nightly snapshot PPA doing a complete purge and reinstalling but this doesn't solve the problem.

I'm running ubuntu 15.04.
If any further information is required please let me know.


Thank you in advance

---

### Post by Rob Sayer on 2015-05-17
Have you tried here?

[https://forum.handbrake.fr/](https://forum.handbrake.fr/)

---

### Post by slgtheindividual on 2015-05-17
thank you I've just had a look on the forums, I tried uninstalling ffmpeg as this helped somebody with the same issue, but no luck, I will post on that forum with my issue too, but if anybody on here can help that would also be appreciated, my activity log can be found here: [http://pastebin.com/jfZp5FAi](http://pastebin.com/jfZp5FAi) I will leave this thread open so that if I get a solution from either here or the handbrake forum I can update and mark as solved for anybody who has this problem in the future.

---

### Post by mc4man on 2015-05-17
I don't use HB but installed on 15.04 & queued up 3 files with no issue.
Typically a segfault will create a crash report, maybe have a look in /var/crash/
If one is there > r.click on the .crash > open with Report a ... > Details button.  That may give you some idea on the crash

---

### Post by slgtheindividual on 2015-05-17
Got the answer from over at the handbrake forums, apparently the recommended PPA is this one [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots)
and then I just had to remove handbrake and reinstall handbrake-gtk. [COLOR=#333333][FONT=Lucida Grande]Just a note, that when I tried to install handbrake-gtk I got a dependecies error, so I installed handbrake and then handbrake-gtk, which proceeded to remove handbrake before installing with no error. Thank you for the help.[/FONT][/COLOR]

---

