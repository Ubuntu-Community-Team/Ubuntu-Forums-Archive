---
title: "Nauitlus is seriously slow"
date: 2010-06-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-06-24
latest updates to nautilus render it useless. when opening directory it takes about 15 to 20 seconds to show folders, and forget about navigating to different directories, nautilus grays out and I have to force quit.

---

### Post by sparker256 on 2010-06-24
> **tad1073 said:**
> latest updates to nautilus render it useless. when opening directory it takes about 15 to 20 seconds to show folders, and forget about navigating to different directories, nautilus grays out and I have to force quit.

I am seeing the same behaviour.

Bill

---

### Post by Sam on 2010-06-24
Same here.

EDIT: It only hangs on local folders (not on remote ones like sftp). They have the (new) "Ubuntu One disabled/enabled" information bar and I suspect this slows down everything.

---

### Post by philinux on 2010-06-24
> **Sam said:**
> Same here.

EDIT: It only hangs on local folders (not on remote ones like sftp). They have the (new) "Ubuntu One disabled/enabled" information bar and I suspect this slows down everything.

I have ubuntu-one disabled in startup but the syncdaemon still starts.

---

### Post by pressureman on 2010-06-24
Nautilus seems to ignore double-clicking folders. I can right-click, open a folder, but even that is quite slow to refresh.

Isn't there some way to remove or completely disable Ubuntu One? I don't want it at all, and it's starting to get in my way now.

---

### Post by kslen on 2010-06-24
Aye, same behavior here.

To remove ubuntuone-client and its baggage, check out this guide:
[https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

---

### Post by ranch hand on 2010-06-24
I hate to remove things in testing but I did remove Ubuntuone on my 2 main installs.  I use this as a production OS and that is just crippling.

Kind of interesting to watch in my other installs though.  Really screws nautilus.

Does anyone that uses Ubuntuone have more than one install?  It would be interesting to know if it is worse or the same if you use it as opposed to just having it installed.

There is no way I am hooking up to something like that.  Too paranoid, and likely too silly, but there it is.

---

### Post by tad1073 on 2010-06-24
> **Sam said:**
> Same here.

EDIT: It only hangs on local folders (not on remote ones like sftp).  They have the (new) "Ubuntu One disabled/enabled" information bar and I  suspect this slows down everything.

> **kslen said:**
> Aye, same behavior here.

To remove ubuntuone-client and its baggage, check out this guide:
[https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)


yup, the enable/disable option that was in nautilus is what was causing the problems.

---

### Post by kslen on 2010-06-24
ranch hand: I followed the guide above and it didn't harm my system in any way. Nautilus is not locking up anymore and browsing between directories with lots of content feels snappier.

If you want to undo the changes the guide suggest, there's a section that covers that as well.

It is true what you say in regards to testing, but I time is scarce and I need my files to be accessible within at least a fairly reasonable time frame. :p

Good luck to ya in any case. :)

---

### Post by indigoblue on 2010-06-25
I ran update manager this morning, and after the update, Nautilus seems to be faster than it was yesterday. Also, the double clicking works now. (I didn't remove Ubuntu One, and the Enable/Disable thing is still there.)

It still takes a bit to open Nautilus itself, but there's a definite increase in browsing speed, if anyone wants to go back to having Ubuntu One.

---

### Post by dino99 on 2010-06-25
yesterday was a pain but now its normal (installed but not activated)

---

### Post by Speed_arg on 2010-06-25
Nautilus is always slow.

---

### Post by tad1073 on 2010-06-25
problem still exists when browsing nautilus as root.

---

### Post by QQi on 2010-06-27
> **tad1073 said:**
> problem still exists when browsing nautilus as root.

yes, same here (gksu nautilus)

---

### Post by lkjoel on 2010-06-28
There is a similar problem at [http://ubuntuforums.org/showthread.php?t=1513079&page=2](http://ubuntuforums.org/showthread.php?t=1513079&page=2)
I hope that helps!

---

### Post by jerrylamos on 2010-06-28
> **Speed_arg said:**
> Nautilus is always slow.

Pcmanfm on Lubuntu and Debian CD live is quite quick.  I haven't tried it on meerkat.

Hmmm.  It's on Synaptic.  Let me try it out on meerkat.

Jerry

---

### Post by jerrylamos on 2010-06-28
> **jerrylamos said:**
> Pcmanfm on Lubuntu and Debian CD live is quite quick.  I haven't tried it on meerkat.

Hmmm.  It's on Synaptic.  Let me try it out on meerkat.

Jerry

Just tried it.  Swift for me.  I don't know if it will do what you want.

Jerry

---

### Post by Speed_arg on 2010-06-29
> **jerrylamos said:**
> Pcmanfm on Lubuntu and Debian CD live is quite quick.  I haven't tried it on meerkat.

Hmmm.  It's on Synaptic.  Let me try it out on meerkat.

Jerry

Yes, im using PCMANFM (with lubuntu). Very good. Its dissapointing that ubuntu is actually slower than windows 7 by far.

---

### Post by ranch hand on 2010-06-29
> **Speed_arg said:**
> Yes, im using PCMANFM (with lubuntu). Very good. Its dissapointing that ubuntu is actually slower than windows 7 by far.
I like Lubuntu and pcmanfm myself.

I do not care to compare an OS that works with an MS product.  No I do not have Win 7.  I will not pay for something that gathers information on me or insults me with stupid messages when I want to change my wallpaper.  What that boils down to is that I am not disappointed by the comparitive speed of two, unrelated OS'.

There are things that disappoint me about Ubuntu.  If I had MS on here there would be things that disappointed me.  If I had a Mac OS it would be the same.

I do not think it really fair, or really realistic to compare any of them to each other.  What is important is to compare each against your expectations of an OS.  If they do not match up well, use the one that does.

---

### Post by taavikko on 2010-06-29
> **Speed_arg said:**
> Its dissapointing that ubuntu is actually slower than windows 7 by far.

You're basing this notation on devel-release?

quoting my cousin who used kubuntu 9.10 for a while "I didn't know programs could start so fast"
And with genuine amazed look on his face.

---

### Post by VMC on 2010-06-29
> **ranch hand said:**
> ...I do not care to compare an OS that works with an MS product.  No I do not have Win 7...
There are things that disappoint me about Ubuntu.  If I had MS on here there would be things that disappointed me.  If I had a Mac OS it would be the same.

I do not think it really fair, or really realistic to compare any of them to each other.  What is important is to compare each against your expectations of an OS.  If they do not match up well, use the one that does.

> **taavikko said:**
> You're basing this notation on devel-release?

quoting my cousin who used kubuntu 9.10 for a while "I didn't know programs could start so fast"
And with genuine amazed look on his face.

My old time friend Dell Optiplex GX260, P4, 2.65 GhZ died suddently. I was using Ubuntu at the time and was cussing Ubuntu for the display going dark. Little did I know at the time, but my PC was under cardiac arrest. I launched Windows XP ( a trusted friend - heavily optimized), soon it too failed. Finally around noon, it died for good. I tend to keep things way past their prime..then again, I'm way past my prime also :(

On my birthday I bought a new PC that came with Windows 7. At first I thought it was great, then as time wore on, and the excitement of a new PC, I installed Maverick. Wow. The startup blew away Windows 7. Also Windows brings the desktop to the forefront quickly, but thats a misconception. It took 30 seconds or more for things to settle down, before it was totally usable. Then there is that derelict program design to slow down any Microsoft product down and to its knees....Anti-virus.

At any rate, if I was still using my old 32bit P4, it was a toss up as to which was faster, XP or Ubuntu. Now with my new 64-bit dual core, and nVidia chip, things fly using Ubuntu amd64.

---

### Post by Speed_arg on 2010-06-29
> **taavikko said:**
> You're basing this notation on devel-release?

quoting my cousin who used kubuntu 9.10 for a while "I didn't know programs could start so fast"
And with genuine amazed look on his face.
All versions of ubuntu (at least from 9.04, the first version I tried) 

[QUOTE=VMC]My old time friend Dell Optiplex GX260, P4, 2.65 GhZ died suddently. I was using Ubuntu at the time and was cussing Ubuntu for the display going dark. Little did I know at the time, but my PC was under cardiac arrest. I launched Windows XP ( a trusted friend - heavily optimized), soon it too failed. Finally around noon, it died for good. I tend to keep things way past their prime..then again, I'm way past my prime also 

On my birthday I bought a new PC that came with Windows 7. At first I thought it was great, then as time wore on, and the excitement of a new PC, I installed Maverick. Wow. The startup blew away Windows 7. Also Windows brings the desktop to the forefront quickly, but thats a misconception. It took 30 seconds or more for things to settle down, before it was totally usable. Then there is that derelict program design to slow down any Microsoft product down and to its knees....Anti-virus.

At any rate, if I was still using my old 32bit P4, it was a toss up as to which was faster, XP or Ubuntu. Now with my new 64-bit dual core, and nVidia chip, things fly using Ubuntu amd64.[/QUOTE]

I have had 10x more problems with Ubuntu than with Windows. I am not a fanboy of none, I am just objective. In windows you install, download drivers or use the ones from the CD, install, restart a couple of times, and everything just works. In ubuntu, you may be lucky and everything works out of the box, or it just won't work. Actually, all issues I had with ubuntu where with video, and with many different PC's. Either the display driver wouldnt appear in hardware drivers, or it didnt allow me to go further 800x600, or the screen was just black. After hours of googling and trying several xorg.conf configurations, I tried Lubuntu and display worked fine (Allthough resolution still sux, up to 1024x768, in windows I can choose a custom one (1330x768)).

You are now going to hate me because I said the work Microsoft, and say stuff like its hardware vendors fault. I don't think a use will care (neither the user should) about whose fault is, it should just work.

Going back to the topic, Windows 7 is faster than Ubuntu, but Windows XP is like 5x faster ubuntu. Its just that the applications it uses are so bad optimized (mozzilla, fspot, nautilus, evolution, open office, etc etc)

---

### Post by cariboo on 2010-06-29
@Speed_arg

Is it just Ubuntu that runs slow on your hardware, or do all distro's run slow?

---

### Post by Speed_arg on 2010-06-29
> **cariboo907 said:**
> @Speed_arg

Is it just Ubuntu that runs slow on your hardware, or do all distro's run slow?

Havent tried a wide range of distros, but lubuntu is very fast (faster than XP)

---

### Post by jerrylamos on 2010-06-29
> **Speed_arg said:**
> Havent tried a wide range of distros, but lubuntu is very fast (faster than XP)

Ditto.  PCmanfm file manager and Chromium on lubuntu are quite noticeably fast.

Jerry

---

### Post by indigoblue on 2010-06-30
> **Speed_arg said:**
> Its dissapointing that ubuntu is actually slower than windows 7 by far.

Really? That's strange. I wonder what kind of magical Windows product you're using because 2000, XP, Vista, and 7 are all dinosaurs. Especially Vista.

Ubuntu is miles ahead with speed.

---

### Post by vkontakte on 2010-07-01
> **cariboo907 said:**
> @Speed_arg

Is it just Ubuntu that runs slow on your hardware, or do all distro's run slow?
I think his computer suffers from that well known IO bug (I don't remember it's index).

---

### Post by lkjoel on 2010-07-03
> **indigoblue said:**
> Really? That's strange. I wonder what kind of magical Windows product you're using because 2000, XP, Vista, and 7 are all dinosaurs. Especially Vista.

Ubuntu is miles ahead with speed.
I'm using 10.04, and I have the same problem with speed.
I finally figured out that there was an evil process that was taking too much ram.
The process is good by nature, but it takes way too much ram.
I killed it, and everytime my system is slow, I kill it, and I run LinuxEssentials.
It suddenly becomes much faster.
The process is "polkitd". I saw it take 2.8GB out of 2.9GB.
Not good.

---

### Post by x-shaney-x on 2010-07-04
I'm also finding nautilus very slow in many ways.
When opening nauty, the window appears but the contents take a while to load in.
When minimizing, it pauses halfway through the animation (with compiz and not just flashy anims, even the standard minimize effect plugin).
The same goes for closing the window, it starts fading then pauses before finally closing.

The rest of the meerkat desktop has no such problems.
ALL other apps respond fast and all other animations are smooth with no pauses.
Incidentally, I did disable compiz to check and nautilus was just a slow and clunky.

Removing everything ubuntu one related did help a lot but it still has problems.

---

### Post by lkjoel on 2010-07-16
> **x-shaney-x said:**
> I'm also finding nautilus very slow in many ways.
When opening nauty, the window appears but the contents take a while to load in.
When minimizing, it pauses halfway through the animation (with compiz and not just flashy anims, even the standard minimize effect plugin).
The same goes for closing the window, it starts fading then pauses before finally closing.

The rest of the meerkat desktop has no such problems.
ALL other apps respond fast and all other animations are smooth with no pauses.
Incidentally, I did disable compiz to check and nautilus was just a slow and clunky.

Removing everything ubuntu one related did help a lot but it still has problems.
Try purging nautilus, and before you restart, or log out, reinstall it.
If you log out, or restart before, then you will need to use recovery mode, or KDE

---

### Post by x-shaney-x on 2010-07-16
I discovered eventually the nautilus slowness was down to two things:

1.  UbuntuOne.  Was every component was completely removed it speeded up a lot but it still had problems.
2.  The global app menu in unity makes nautilus slow to start up.  Doesn't slow other apps down though.

---

### Post by lkjoel on 2010-07-16
> **x-shaney-x said:**
> I discovered eventually the nautilus slowness was down to two things:

1.  UbuntuOne.  Was every component was completely removed it speeded up a lot but it still had problems.
2.  The global app menu in unity makes nautilus slow to start up.  Doesn't slow other apps down though.
So is it fixed?

---

### Post by x-shaney-x on 2010-07-16
Not on my comp.
I did a clean install from a maverick daily the other day (netbook edition) and still just as slow until I removed ubuntuone again.

Still a delay when opening with appmenu enabled but to bad really.

---

### Post by MarkieB on 2010-08-02
no longer participating in ubuntuforums.org

---

### Post by aviramof on 2010-08-02
Is there any hope that we would finally see nautilus 3.0 in maverick?

---

### Post by ranser on 2010-08-06
Yes, it seems in Maverick will be implemented Gnome 3.0. I hope it won't be the same user-experience as with KDE 4.0.

---

### Post by ranch hand on 2010-08-06
> **ranser said:**
> Yes, it seems in Maverick will be implemented Gnome 3.0. I hope it won't be the same user-experience as with KDE 4.0.
I think this is unlikely as the release of G3 has been put off to March in 2011.

---

