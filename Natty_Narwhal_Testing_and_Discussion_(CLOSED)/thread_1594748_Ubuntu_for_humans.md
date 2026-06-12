---
title: "Ubuntu for humans?"
date: 2010-10-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-10-12
So, Gimp was removed because it was too advanced, but MM has OO Drawing, a video editor, a remote desktop viewer, a terminal server client, and OO Spreadsheet. Then there are preferences and administration: Passwords & encryption keys, network proxy, and keyboard input methods. Blimey! What humans are using this? Not your average ones that Ubuntu is directed at, I'm sure.

Then there is the audio issue which stopped me using Ubuntu since Karmic:
I have an LFE channel (subwoofer) on my laptop that I cannot control independently nor combined for the volume. Bugs were raised but the reply was to shift the blame to upstream changes. I have been using Debian since, and these changes are not in Squeeze.

Apart from regular releases, I see no advantages of Ubuntu over Debian. Even Debian Squeeze will have a live CD and a graphical installer.

Any chance of having a better ranges of apps in NN, and sort the audio out.

---

### Post by 23meg on 2010-10-12
> **phenest]So, Gimp was removed because it was too advanced, but MM has OO Drawing, a video editor, a remote desktop viewer, a terminal server client, and OO Spreadsheet. Then there are preferences and administration: Passwords & encryption keys, network proxy, and keyboard input methods. Blimey! What humans are using this? Not your average ones that Ubuntu is directed at, I'm sure.[/quote]

GIMP was not removed because it was "too advanced" said:**
> Then there is the audio issue which stopped me using Ubuntu since Karmic:
I have an LFE channel (subwoofer) on my laptop that I cannot control independently nor combined for the volume. Bugs were raised but the reply was to shift the blame to upstream changes. I have been using Debian since, and these changes are not in Squeeze.

What is the bug report for this? "Upstream" could be referring to PulseAudio or ALSA rather than Debian.

> **phenest]Any chance of having a better ranges of apps in NN,[/quote]

Of course said:**
> and sort the audio out.

Not unless a bug report has been filed and triaged.

---

### Post by ronacc on 2010-10-12
Ubuntu for humans? where ever did you get that idea ? Ubuntu is for furry little woodland creatures .

---

### Post by caryb on 2010-10-12
> **ronacc said:**
> Ubuntu for humans? where ever did you get that idea ? Ubuntu is for furry little woodland creatures .

Ronacc Thanks for the best laugh I have had for a while :-)


Cary

---

### Post by ubunterooster on 2010-10-12
> **ronacc said:**
> Ubuntu for humans? where ever did you get that idea ? Ubuntu is for furry little woodland creatures .
Or elegant sea creatures :D

---

### Post by ranch hand on 2010-10-13
> **phenest said:**
> So, Gimp was removed because it was too advanced, but MM has OO Drawing, a video editor, a remote desktop viewer, a terminal server client, and OO Spreadsheet. Then there are preferences and administration: Passwords & encryption keys, network proxy, and keyboard input methods. Blimey! What humans are using this? Not your average ones that Ubuntu is directed at, I'm sure.

Then there is the audio issue which stopped me using Ubuntu since Karmic:
I have an LFE channel (subwoofer) on my laptop that I cannot control independently nor combined for the volume. Bugs were raised but the reply was to shift the blame to upstream changes. I have been using Debian since, and these changes are not in Squeeze.

Apart from regular releases, I see no advantages of Ubuntu over Debian. Even Debian Squeeze will have a live CD and a graphical installer.

Any chance of having a better ranges of apps in NN, and sort the audio out.
You have a bad attitude here.  There is nothing wrong with Ubuntu.

I have kernel 2.6.35 (from liquirix) Squeeze, by the way, and it boots faster than any of my Ubuntu installs and shuts down in less than 5 seconds.

---

### Post by phredbull on 2010-10-13
> **ranch hand said:**
> There is nothing wrong with Ubuntu.
I like using Ubuntu, a lot, but I *definitely* wouldn't say that!
:lol:
I also find the choice to remove the image editor and include a video editor to be puzzling. 
:confused:
But whatever, I'll just uninstall it.

---

### Post by Slug71 on 2010-10-13
> **ranch hand said:**
> You have a bad attitude here.  There is nothing wrong with Ubuntu.

I have kernel 2.6.35 (from liquirix) Squeeze, by the way, and it boots faster than any of my Ubuntu installs and shuts down in less than 5 seconds.

Is Plymouth working better for you now Ranch Hand? I know you had some trouble with Lucid.

---

### Post by ranch hand on 2010-10-13
> **Slug71 said:**
> Is Plymouth working better for you now Ranch Hand? I know you had some trouble with Lucid.
Plymouth has made it impossible to use 10.04.  It is better in 10.10.

10.10 will boot (usually) with no splash.  It still will not shut down reliably at all.

When it does shut down it takes over 3 minutes.

Debian doesn't use a splash generator at all and boots very fast.  I do not have bootchart on here so I won't make any claims but the bugger is very quick.  I do not have time to hardly blink on shut down.

Better yet, if I "improve" something that has a bad effect on booting, the logs actually get written which is something that plymouth will not do.

---

### Post by Slug71 on 2010-10-13
> **ranch hand said:**
> Plymouth has made it impossible to use 10.04.  It is better in 10.10.

10.10 will boot (usually) with no splash.  It still will not shut down reliably at all.

When it does shut down it takes over 3 minutes.

Debian doesn't use a splash generator at all and boots very fast.  I do not have bootchart on here so I won't make any claims but the bugger is very quick.  I do not have time to hardly blink on shut down.

Better yet, if I "improve" something that has a bad effect on booting, the logs actually get written which is something that plymouth will not do.

Strange, mine is the opposite. My maverick install wont shut down reliably at all whereas no trouble with 10.04. It usually freezes as it attempts to log out of X. Every now and again it will get to Plymouth and then freeze and even rarer it will actually shut down.

---

### Post by ranch hand on 2010-10-13
> **Slug71 said:**
> Strange, mine is the opposite. My maverick install wont shut down reliably at all whereas no trouble with 10.04. It usually freezes as it attempts to log out of X. Every now and again it will get to Plymouth and then freeze and even rarer it will actually shut down.
That is what happens when you keep beating a dead horse, or more correctly, patching a very bad program to try to fix it.

Every patch really does improve things.  For some hardware.  Makes it worse for a smaller sample of hardware.

In my case the "improvements" to Plymouth in 10.04 have excluded my box completely.  Just too unreliable.  Sounds like 10.10 is getting close to that for you.

---

### Post by Slug71 on 2010-10-13
Really hoping it will be working nicely in 11.04.

---

### Post by cariboo on 2010-10-13
I have to ask, aren't the open source ATI drivers good enough for most day to day usage, and don't they solve most of the plymouth problems?

I'm almost tempted to buy an ATI graphics card to test it out.

---

### Post by ranch hand on 2010-10-13
I would not recommend hoding your breath.  If it improves on yours it will be getting worse for others.

It should longer even be seen as base code.  It is a ragged quilt of patches.  Poor thing needs put out of its suffering.

Most OS' that have been using it have dropped it for that very reason.

My boot speeds in 10.04 testing, before plymouth, were dropping.  They were below 25 seconds on this desktop.  Right before plymouth came in I was getting 21 to 22 second boot time with password login.

In 10.10 it has improved from 10.04.1 to the pint that I can get 32 to 34 second boot times.

I really need to time Debian (kernel 2.6.35), password login, no ureadahead, no splash (don't have that with Plymouth on my hardware).  I am sure that it is in the low 20s.

Bootchart there works like it does on some of my Ubuntu installs.  Not at all.  I can actually time things all by myself.

---

### Post by Simian Man on 2010-10-13
> **ranch hand said:**
> you have a bad attitude here.  There is nothing wrong with ubuntu.

> **ranch hand said:**
> 10.10 will boot (usually) with no splash.  It still will not shut down reliably at all.

When it does shut down it takes over 3 minutes.

Lol.

---

### Post by ranch hand on 2010-10-13
> **Simian Man said:**
> Lol.
There is nothing wrong with Ubuntu.

I am sure that everything is design intent.  Everything is good.

---

### Post by Reiger on 2010-10-14
> **cariboo907 said:**
> I have to ask, aren't the open source ATI drivers good enough for most day to day usage, and don't they solve most of the plymouth problems?

I'm almost tempted to buy an ATI graphics card to test it out.

For me they are. Evergreen might not be quite there yet; but my 4500 series (laptop) and 4800 series (desktop) cards run fine. Definitely come a long way since Intrepid there (where the 4800 would not boot to X reliably without some cursing and cajoling); compositing et all works...

---

### Post by zekopeko on 2010-10-14
> **ranch hand said:**
> There is nothing wrong with Ubuntu.

I am sure that everything is design intent.  Everything is good.

I'm seeing a lot of snarky comments but no links to bug reports from you. I guess it's business as usual for you.

---

### Post by Slug71 on 2010-10-14
> **ranch hand said:**
> That is what happens when you keep beating a dead horse, or more correctly, patching a very bad program to try to fix it.

Every patch really does improve things.  For some hardware.  Makes it worse for a smaller sample of hardware.

In my case the "improvements" to Plymouth in 10.04 have excluded my box completely.  Just too unreliable.  Sounds like 10.10 is getting close to that for you.

[http://ubuntuforums.org/showthread.php?t=1595812](http://ubuntuforums.org/showthread.php?t=1595812)

Something for you to play with.
Someone has made a Plymouth Manager.

---

### Post by MishaAct on 2010-10-14
> **zekopeko said:**
> I'm seeing a lot of snarky comments but no links to bug reports from you. I guess it's business as usual for you.
I stopped making launchpad bugs because it's just plain useless in most cases and only steals my time

---

### Post by TNT1 on 2010-10-14
> **phenest said:**
> 

Any chance of having a better ranges of apps in NN, 

That's odd... Linux, and especially ubuntu derivatives are the only OS's out their that come with any "apps" as part of the initial install... And then they even give you an entire internet full of apps in the software center. What more do you want? A human to come and install everything for you, and use your pc for you?

---

### Post by ranch hand on 2010-10-14
> **zekopeko said:**
> I'm seeing a lot of snarky comments but no links to bug reports from you. I guess it's business as usual for you.
The bugs are there,  I am not updating them.

Plymouth is supposed to write logs.  It does not do this.

You file a bug, they ask for error logs.  They do not exist.

This is a very convenient way to prove there is no problem but not conducive to getting things fixed.

---

### Post by ranch hand on 2010-10-14
> **Slug71 said:**
> [http://ubuntuforums.org/showthread.php?t=1595812](http://ubuntuforums.org/showthread.php?t=1595812)

Something for you to play with.
Someone has made a Plymouth Manager.
A manager for the boot manager.  Interesting concept.

Has it fixed your shutdown problems?

---

### Post by perspectoff on 2010-10-14
I'm a Cyborg. I actually interact closely with my computers.

Real humans merely hunt antelope and pick berries and talk about meaningless politics.

---

### Post by TNT1 on 2010-10-14
> **perspectoff said:**
> I'm a Cyborg. I actually interact closely with my computers.

Real humans merely hunt antelope and pick berries and talk about meaningless politics.

Come here, we hunt a heck of a lot more than anteslopes, including berry pickers:)

---

### Post by zekopeko on 2010-10-14
> **ranch hand said:**
> The bugs are there,  I am not updating them.

Plymouth is supposed to write logs.  It does not do this.

You file a bug, they ask for error logs.  They do not exist.

Then you report a bug about Plymouth not generating error logs.

> This is a very convenient way to prove there is no problem but not conducive to getting things fixed.

This is a very convenient way to bitch but it won't fix the problem if you don't talk to someone and provide the appropriate info.

---

### Post by Slug71 on 2010-10-14
> **ranch hand said:**
> A manager for the boot manager.  Interesting concept.

Has it fixed your shutdown problems?

Havent given it a try yet, will later today.

---

### Post by ranch hand on 2010-10-14
> **zekopeko said:**
> Then you report a bug about Plymouth not generating error logs.



This is a very convenient way to bitch but it won't fix the problem if you don't talk to someone and provide the appropriate info.
This was done some time ago.

---

### Post by ranch hand on 2010-10-14
> **Slug71 said:**
> Havent given it a try yet, will later today.
I will await a report with bated breath.

---

### Post by 23meg on 2010-10-14
> **MishaAct said:**
> I stopped making launchpad bugs because it's just plain useless in most cases and only steals my time

Reporting bugs is a [necessary condition]("http://en.wikipedia.org/wiki/Necessary_and_sufficient_condition") of them getting fixed (except accidentally or as a side effect of some other fix), not a sufficient condition.

> **ranch hand]The bugs are there, I am not updating them.[/QUOTE]

Why not? Is there no new information you can add to them? Or because it would actually help towards fixing the issues you've been ranting about? 

[QUOTE=ranch hand]
Plymouth is supposed to write logs. It does not do this.

You file a bug, they ask for error logs. They do not exist.

This is a very convenient way to prove there is no problem but not conducive to getting things fixed.[/QUOTE]

Right, because the people who developed and integrated Plymouth have a vested interest in shipping and putting their names under inferior code, and because of that, they're deliberately not fixing log-related bugs. Makes a lot of sense. 

Except, you know, I've seen [at least one such bug]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/527715") fixed. Since you haven't filed one, you're all talk.

[QUOTE=ranch hand said:**
> A manager for the boot manager.  Interesting concept.

Except that Plymouth is not a "boot manager". It doesn't "manage" your boot process. It takes (from KMS drivers) and hands over (to X) the optimal video mode during boot, fills up your screen during boot and shutdown, and pops in when you need to handle volume decryption or fsck.

---

### Post by ranch hand on 2010-10-14
I seem to get notices of a lot of bugs dealing with Plymouth for someone that hasn't filed any.

---

### Post by 23meg on 2010-10-14
> **ranch hand said:**
> I seem to get notices of a lot of bugs dealing with Plymouth for someone that hasn't filed any.

So you subscribed to bug mail? That's useful.

---

### Post by ranch hand on 2010-10-14
I am only subscribed to bugs that I have reported or commented on.

---

### Post by k3lt01 on 2010-10-14
Lads, stop the grumbling.

RH, you have my utmost respect but sheez you let people pull your chain to much.

mgunes, you also have my utmost respect but why continue an argument that isn't helpful to fixing the actual issue. RH won't change his mind. I know that, he knows that, I would have thought you would have known that. After all we have all been here long enough to sort of know how the other works.

No back to regular programming.

---

### Post by lisati on 2010-10-14
> **k3lt01 said:**
> Lads, stop the grumbling.

+1. We are at risk of having a thread closure here.

---

### Post by ubunterooster on 2010-10-15
> **k3lt01 said:**
> Lads, stop the grumbling
  "Ubuntu for humans"

Grumbling; Human nature. ;)

---

### Post by ronacc on 2010-10-15
this is the development and TESTING forum , aren't we SUPPOSED to bitch moan and whine about whats wrong ?:lolflag:

edit : as a note , I also sometimes get notices about bugs I have neither reported , joined or commented on ,and on occasion the same notice 20 times .

---

### Post by zekopeko on 2010-10-15
> **ronacc said:**
> edit : as a note , I also sometimes get notices about bugs I have neither reported , joined or commented on ,and on occasion the same notice 20 times .

[https://bugs.launchpad.net/launchpad/+filebug](https://bugs.launchpad.net/launchpad/+filebug)

Go crazy.

---

### Post by ronacc on 2010-10-15
> **zekopeko said:**
> [https://bugs.launchpad.net/launchpad/+filebug](https://bugs.launchpad.net/launchpad/+filebug)

Go crazy.

I am well aware of how to file bugs . As far as going crazy , I can't ,I am already there .

---

### Post by 23meg on 2010-10-15
> **k3lt01 said:**
> why continue an argument that isn't helpful to fixing the actual issue. RH won't change his mind. I know that, he knows that, I would have thought you would have known that. After all we have all been here long enough to sort of know how the other works.

You're right; I shouldn't have posted, and I'm wrong to have cared about the quality of discourse here at all (no sarcasm intended).

---

### Post by 23meg on 2010-10-15
> **ronacc said:**
> edit : as a note , I also sometimes get notices about bugs I have neither reported , joined or commented on ,and on occasion the same notice 20 times .

You can figure out why you received a certain bug notification by reading the notice at the end of it, that goes something like

> You received this bug notification because you are a direct subscriber of the bug.

or

> You received this bug notification because you are subscribed to $PACKAGE / $PROJECT.

---

### Post by k3lt01 on 2010-10-15
> **mgunes said:**
> You're right; I shouldn't have posted, and I'm wrong to have cared about the quality of discourse here at all (no sarcasm intended).The point of my post was to get you, not RH, to lighten up. You can care about the quality of the discourse but you took the quality down a few pegs in that part of the discussion. No one should have to keep justifying themselves like RH did to you.

I could say alot more but I am biting my tongue and I don't want to have to do it any harder.

---

### Post by 23meg on 2010-10-15
[QUOTE=k3lt01]The point of my post was to get you, not RH, to lighten up. You can care about the quality of the discourse but you took the quality down a few pegs in that part of the discussion. No one should have to keep justifying themselves like RH did to you.[/QUOTE]

I agree, except the "justifying themselves" part. If someone is making hundreds of posts despising the work of others on an anecdotal basis with next to no technical information, without having filed a single bug report, and with language that violates the CoC (not that I care much about that part, but others do), "justifying themselves" is an understatement regarding what they should be expected to do. But if collectively they're not, and this forum is perceived as a dumping ground for such behavior, that's fine.

---

### Post by k3lt01 on 2010-10-15
> **mgunes said:**
> I agree, except the "justifying themselves" part. If someone is making hundreds of posts despising the work of others on an anecdotal basis with next to no technical information, without having filed a single bug report, and with language that violates the CoC (not that I care much about that part, but others do), "justifying themselves" is an understatement regarding what they should be expected to do. But if collectively they're not, and this forum is perceived as a dumping ground for such behavior, that's fine.RH has been a good member, IMHO anyway. As for the rest of what you said I am thinking back to a discussion you and I had about the word "insane" and the context in which it was used by one of us (not me). This is a case of the pot (you) calling the kettle (RH) black. I don't understand why you can't see that.

May I suggest if you want to converse with me anymore on this matter you take it to PMs, just like you should have with RH before the slanging match started.

---

### Post by 23meg on 2010-10-15
> **k3lt01 said:**
> RH has been a good member, IMHO anyway.

I didn't say he was a "bad member". I'm not into singling out people; I'm talking about the acceptability or not of *behavior*, and that should apply to everyone.

> **k3lt01 said:**
> As for the rest of what you said I am thinking back to a discussion you and I had about the word "insane" and the context in which it was used by one of us (not me). This is a case of the pot (you) calling the kettle (RH) black. I don't understand why you can't see that.

I had [explained my use of that word]("http://ubuntuforums.org/showpost.php?p=9178988&postcount=1690") to you, and you had [said]("http://ubuntuforums.org/showpost.php?p=9179099&postcount=1692") you didn't know it could be used that way. Thanks for the ad hominem based on one invalid example.

[QUOTE=k3lt01]May I suggest if you want to converse with me anymore on this matter you take it to PMs, just like you should have with RH before the slanging match started.[/QUOTE]

No, I'm not going to take it to PMs, since it's not a private issue concerning one person, but I agree that this already horribly off-topic thread is starting to drift into meta-discussion which is better suited to Forum Feedback & Help. We should let that branch die, and if anyone is interested in discussing aspects of behavior I outlined in the last post any further (I'm not), they can start a thread there.

---

### Post by ronacc on 2010-10-15
Since NN doesn't actually exist yet ( officially anyway ) how can anything we discuss here be ON topic ?

---

### Post by 23meg on 2010-10-15
> **ronacc said:**
> Since NN doesn't actually exist yet ( officially anyway ) how can anything we discuss here be ON topic ?

Good point.

---

### Post by k3lt01 on 2010-10-15
First I am going to apologise to Lisati, I had no intention of this going this way.

> **mgunes said:**
> I didn't say he was a "bad member". I'm not into singling out people; I'm talking about the acceptability or not of *behavior*, and that should apply to everyone.May I suggest you live up to your own standards then.

As for everything else you said, again.
You did single out one person and you are still going on with it with another who called you up on it.

What you think is invalid doesn't matter in this case. What does matter is the lack of self accountability.

You talk of technical information yet you use words that have nothing to do with the topic at hand. Whether you explained your use of a word is neither here nor there what remains is your usage was and still is incorrect. We discussed it, **_privately_** and even though I disagree with you I left it at that so I didn't raise the ire of the UbuntuForums mods. RH has expressed himself in his own way, just like you did back then, if you have difficulty with that then the problem is not RHs.

You talk of behaviour standards yet you don't care about violations of the CoC which we are all apparently bound to! What standards should we live up to? the CoC's or yours?

Delete this or move it if you want, I'm not posting this matter anywhere else, not will I respond anymore to you. You could have nipped this in the bud early on but you chose to escalate it now you want others to take it somewhere else when you yourself wouldn't.

---

### Post by 23meg on 2010-10-15
Feel free to use the "Report abuse" button to report my posts that violate the CoC, or that you think are otherwise problematic. That's what I'll do in the future for posts in the vein I outlined in post #43, since I feel my time and energy are not well spent on dealing with them any longer.

---

### Post by psusi on 2010-10-15
> **phenest said:**
> So, Gimp was removed because it was too advanced, but MM has OO Drawing, a video editor, a remote desktop viewer, a terminal server client, and OO Spreadsheet. Then there are preferences and administration: Passwords & encryption keys, network proxy, and keyboard input methods. Blimey! What humans are using this? Not your average ones that Ubuntu is directed at, I'm sure.

Well, let's see:

Open Office... yea, nobody writes documents or uses spreadsheets... oh and of course EVERYBODY speaks english and lives in the US, so who needs keyboard and input methods.  And who needs to manage their passwords or configure a network proxy?  Of course, those take up how much space again?  Oh... hardly anything?

:roll:

---

### Post by Elfy on 2010-10-16
After reports and reading the whole thread, this has drifted so far off topic into the realsm of who can beat who the hardest with the largest stick I am closing it.

---

