---
title: "[SOLVED] Flash videos break Ubuntu"
date: 2008-07-08
forum: Multimedia Software
---

### Post by JonahRowley on 2008-07-08
I like to watch flash videos (particularly hulu), however on 8.10 they're doing something...  funny.  They'll work fine for a while, but suddenly everything will slow to a crawl.  The video will drop to less than 1 frame per second (though the sound still plays).  Firefox hangs.  Everything else is also significantly slowed.  Even trying to start up gnome-terminal to kill firefox was so slow, it took about a minute.

When it first happens, Firefox along with X consume 100% CPU.  If you pause it quickly, Firefox continues to consume about 40% CPU for a while and everything remains sluggish.  Eventually the CPU utilization will go down and things are fast again.  If you start the video again, it will play normally for a while and then the problem will happen again.

I'm using 8.10 x86 with Compiz on an NVidia 7900GS and an ASUS A8V-VM SE with an AMD64 3500+.  I've tried to change just about every variable in this situation to narrow the problem to one thing, but nothing I change fixes the problem.  I've tried the following:

[list]
[*]Switch to Swiftfox.  No change.
[*]Downgrade to Firefox 2.  No change.
[*]Disable all Firefox extensions.  No change.
[*]Switch to Opera.  No change.
[*]Upgrade to the Flash 10 beta.  No change.
[*]Disable Compiz.  No change.
[*]Upgrade NVidia drivers.  No change.
[*]Close all other Firefox tabs (including Javascript-heavy google apps).  No change.
[*]Close every single application but Firefox.  No change.
[/list]

The only thing I haven't checked is using the nv driver.  I would rather not do that, I really enjoy the Compiz effects and the things are much smoother with the nvidia driver.  I'm about to try that though, I'll reply with my findings.

So has anyone else experienced this?  Does anyone know how to fix it or how I might diagnose the problem?

---

### Post by wolfen69 on 2008-07-08
why not switch to firefox2?

---

### Post by JonahRowley on 2008-07-08
> **wolfen69 said:**
> why not switch to firefox2?

I tried that already.  I also tried Opera just to be sure.  No change at all.

I've now tried switching to the nv driver.  No change.  I've honestly run out of ideas here.

---

### Post by acirilo on 2008-07-09
> **JonahRowley said:**
> I tried that already.  I also tried Opera just to be sure.  No change at all.

I've now tried switching to the nv driver.  No change.  I've honestly run out of ideas here.

i'm having the same kidda of problems

---

### Post by JonahRowley on 2008-07-09
> **acirilo said:**
> i'm having the same kidda of problems

Well I have good news for you.  I've solved the problem.  It was simpler than I had thought.  My CPU was overheating.  I failed to mention is about 90 degrees in this room.

I hadn't thought it was the CPU overheating because the same problem doesn't happen on Windows.  However, thanks to X's supreme inefficiency, playing a flash video really burns up the CPU cycles and heats up the CPU more.  Also, I think Windows might handle the overheating situation better.  I know it's overheated while playing flash videos before without any problems.

Since I don't have air conditioning, my solution is to take the side panel off my case and aim a nice big box fan at it.  Bad news is it vibrates my whole desk.  Good news is it keeps my feet nice and cool.

Hope you solve your problem.  Look into installing lm-sensors and monitoring your CPU temps.  Your problem could be the same as mine.

---

### Post by JonahRowley on 2008-07-09
An amusing update.  Did you know box fans have rather...  unshielded motors?  Putting the fan more or less right next to my Wifi router kills network connectivity.  Nothing is ever simple...

---

### Post by acirilo on 2008-07-10
> **JonahRowley said:**
> Well I have good news for you.  I've solved the problem.  It was simpler than I had thought.  My CPU was overheating.  I failed to mention is about 90 degrees in this room.

I hadn't thought it was the CPU overheating because the same problem doesn't happen on Windows.  However, thanks to X's supreme inefficiency, playing a flash video really burns up the CPU cycles and heats up the CPU more.  Also, I think Windows might handle the overheating situation better.  I know it's overheated while playing flash videos before without any problems.

Since I don't have air conditioning, my solution is to take the side panel off my case and aim a nice big box fan at it.  Bad news is it vibrates my whole desk.  Good news is it keeps my feet nice and cool.

Hope you solve your problem.  Look into installing lm-sensors and monitoring your CPU temps.  Your problem could be the same as mine.


ahhh... i'm an idiot.. turned out i had major packet loss from my box to router but not from router to internet.... my wireless router is upstairs... and i wasn't getting good signal... so i moved my tower from UNDER the desk to ON the desk.. now.. i have smooth videos.

---

