---
title: "Gio makes Gnome apps sluggish"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-08-29
Hi,
please first watch the video and see the difference between using Gio (left window) and not using it (right window).
That's why many folks have noticed (unless you've been using Gnome for long enough to get used to this sluggishness thus not paying attention to it any more) that after **creating, changing or deleting a file it usually takes 1 or 2 seconds** for the user (app) to notice this.
Most affected is Nautilus since it's the default file browser and it also handles the desktop.

I tracked this iissue down to gio but the gio developers basically first said this sluggishness is "by design". I asked why, they gave me a reason, I refuted it, then they figured out another reason and I realized they're just trying to fend me off, so I stopped proving, in between one of them eventually gave in that it's an issue but said that he's too busy doing other work.

Since I'm "nobody" for them I hope someone from Canonical either fixes it itself and sends a patch to the gio devs or he convinces them to "fix" this behaviour - basically the easiest way to fix it is to diminish the deliberate delay gio is taking before acting.
I hope it could be fixed in time for Maverick..

---

### Post by ranch hand on 2010-08-29
Ok, that was fun.  Don't see the problem.

Either it is my use of vlc or, as you say, I am just hardend to the deprivations of using gnome.

---

### Post by kahumba on 2010-08-29
Just look **when** Nautilus shows up the new file and **when** does the other app to the right (that is, you can clearly notice the effect of using gio and not using it, respectively). I know that people who are using Gnome for long enough get used to it, but if you're from XP or so you're likely to notice this pretty soon, it's one of those issues that you a user doesn't know how to describe but which makes the general impression about sluggishness. Btw Google is one of the few companies that gives due credit to speed.

---

### Post by Mr. Picklesworth on 2010-08-29
Could you share why this is?

I can see incorporating a delay for the case that many files are changed at the same time. That way it's all communicated in a single update instead of a hundred small updates.

---

### Post by cariboo on 2010-08-29
What is **gio** and why would I want to use it, when doing your experiment the file shows up in nautilus as soon as I press enter.

---

### Post by kahumba on 2010-08-29
> **Mr. Picklesworth said:**
> Could you share why this is?

I can see incorporating a delay for the case that many files are changed at the same time. That way it's all communicated in a single update instead of a hundred small updates.
1) This issue is in gio for quite some time, interestingly enough, I also noticed it's not always equally sluggish for all users, I don't know why.
2) Yes, the gio devs told me your reason, but look, a simple example would suffice: I used windows (which doesn't do this sort of delay) for like 10 years and I never had any issues. Not doing a delay at all is good enough for like 99.99999% cases, for the more paranoid one - one could put like a 0.25 sec delay but certainly not 1-2 seconds cause it's just  a waste of time for no serious reason. Another example: the Linux kernel doesn't do this sort of delay and nobody said it has scalability issues in this regard.
EDIT: 3rd example: Java 7 (which is due this autumn) features filesystem notifications and it doesn't put deliberate delays either, so the "scalability issue" is purely a gio-developer's noble excuse to not do anything about it, sorry if it sounds little harsh but it's true.

@cariboo907
Gio is part of Gtk, it deals with file systems and with notifications to files, among other things.
_**The bad news is that this delay for some reason is not equally long for all users**_ (I got a core i5 with 4 physical cores so my computer is fast thus the issue is in software anyway) which makes it even harder to get rid of this issue once and for all.

---

### Post by ktp on 2010-08-29
> **cariboo907 said:**
> What is **gio** and why would I want to use it, when doing your experiment the file shows up in nautilus as soon as I press enter.

[http://live.gnome.org/GioToDo](http://live.gnome.org/GioToDo)

---

### Post by Mr. Picklesworth on 2010-08-29
> **kahumba said:**
> 
2) Yes, the gio devs told me your reason, but look, a simple example would suffice: I used windows (which doesn't do this sort of delay) for like 10 years and I never had any issues. Not doing a delay at all is good enough for like 99.99999% cases, for the more paranoid one - one could put like a 0.25 sec delay but certainly not 1-2 seconds cause it's just  a waste of time for no serious reason. Another example: the Linux kernel doesn't do this sort of delay and nobody said it has scalability issues in this regard.

Okay, so that kind of delay is quite common practice when handling large quantities of data, especially of this sort. It's a really bad thing if we flood dbus with a lot of signals. Especially bad if, say, six apps are watching for those signals.

I am, of course, assuming they aren't totally crazy and the delay happens in the dbus chunk of things, rather than in each client. Windows's virtual file system &#8212; or maybe just the UIs for viewing files &#8212; may work a bit differently.

Still, I'm sure it's possible that the current delay isn't optimal, or could be tuned at runtime. I suggest you do some benchmarking, (maybe a few graphs ;) ), to beef up your proposal.

---

### Post by kahumba on 2010-08-29
> **Mr. Picklesworth said:**
> 
Still, I'm sure it's possible that the current delay isn't optimal, or could be tuned at runtime. I suggest you do some benchmarking, (maybe a few graphs ;) ), to beef up your proposal.
Sorry that's beyond me, I gave 3 serious reasons why a 1-2 sec delay is highly overrated, and I even put a video so I think for a user reporting an issue I did (more than) enough.
Also, I'm doing something even better, I'm creating a new file browser altogether (which you can see on the video), but it won' be ready any time soon cause I'm a Java dev but the file browser is (being) written in C++ for obvious reasons, which should prove what a modern, quick etc etc file browser should be.

---

### Post by cariboo on 2010-08-29
> @cariboo907
Gio is part of Gtk, it deals with file systems and with notifications to files, among other things.
The bad news is that this delay for some reason is not equally long for all users (I got a core i5 with 4 physical cores so my computer is fast thus the issue is in software anyway) which makes it even harder to get rid of this issue once and for all.

Maybe it works faster for me because my lowly AMD X2 240 has a higher base clock speed then your i5 intel cpu.

---

### Post by kahumba on 2010-08-29
> **cariboo907 said:**
> Maybe it works faster for me because my lowly AMD X2 240 has a higher base clock speed then your i5 intel cpu.
haha good point! accordingly, my app from the video (the right window) probably thinks that I'm running $100 million supercomputer with futuristic chips not yet produced since it reacts literally instantly while the gio solution takes 1-2 seconds on same computer.

---

### Post by ktp on 2010-08-29
> **kahumba said:**
> haha good point! accordingly, my app from the video (the right window) probably thinks that I'm running $100 million supercomputer with futuristic chips not yet produced since it reacts literally instantly while the gio solution takes 1-2 seconds on same computer.

:lolflag:

I had always wondered why it was "little slow"...at least now I know.

---

### Post by ssam on 2010-08-30
can you post a link to the discussion.

its the delay to avoid 100% cpu usage when copying or downloading a file. when a file is changing continuously for a long time you don't want nautilus continually updating its view.

---

### Post by kahumba on 2010-08-30
> **ssam said:**
> can you post a link to the discussion.

its the delay to avoid 100% cpu usage when copying or downloading a file. when a file is changing continuously for a long time you don't want nautilus continually updating its view.
That discussion took place a few months ago on the gtk (or gio, not sure, but I think gtk) mailing list, you can find it if you wish with something like "giomm" , "gtkmm" or so in the title.

And no "when copying a file" you _**don't**_ get a myriad of events, in fact you only get a few of them, **that's what the gio developer(s) said as their first noble excuse** to not fix this issue, then I provided sample code which has proven they/he's wrong and then they switched to another noble excuse so I gave up cause it was obvious they're just trying to find the first best noble excuse to not treat it as an issue. Sorry, I'm not grumpy, if you contributed code and/or bugs to different (open-source/whatever) projects you know that this type of attitude from the devs isn't too seldom.
So the copying issue is non-existent, can you prove the "downloading" issue is true?
Proving it's worth fixing is a lot harder than issuing a random idea why not to fix it, not to mention (as above) that some of these ideas are wrong.

---

