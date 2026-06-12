---
title: "MythVideo Playback Tweaks"
date: 2009-04-16
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-04-16
I recently upgraded one of my frontends to MythBuntu 8.10.  Aside from an MCE remote, all hardware is the same (so I know it's not strickly speaking a hardware issue.)  However, when playing videos from the remote backend, it now has a stutter every 10-15 minutes.  It's only a few stutters, but just enough to be annoying.  Is there some setting that I can adjust to get rid of this again?

---

### Post by newlinux on 2009-04-16
stutters can be caused by a lot of things (audio issues and video issues), so it is probably a configuration issue. Can you post your frontend logs from when it happens? That may help pinpoint which setting to adjust.

---

### Post by Weidbrewer on 2009-04-16
Wow...is it a bad sign that I've posted enough questions over the last few years that I was instantly releaved when I saw your Avatar? ;)

Okay, I'm sure I'll watch something on it over the next few nights...Or, will posting my log from the last time I watched something on it (which was an effected video) work?

---

### Post by itlarson on 2009-04-16
I've been plagued by the same thing using similar hardware.  I can tell you that de-interlace and resolution settings have little effect.  I ran out of time to work on it, and have been living with it, but will revisit it soon.  Is it possible that it is some quirk/bug in the amd or asus hardware?  Anyway- here's the link to my post on the subject:

[http://ubuntuforums.org/showthread.php?t=1103410]("http://ubuntuforums.org/showthread.php?t=1103410")

Props to newlinux for his tireless posting!

---

### Post by Weidbrewer on 2009-04-16
Sorry for the confusion...my sig-line is my backend/server.  The frontend in question is using much older and low-powered equipment.  It was working under 8.04, but I've hit a few snags with the upgrade (to be expected.)  Most everything was worked out except this stuttering.

---

### Post by newlinux on 2009-04-16
> **Weidbrewer said:**
> Wow...is it a bad sign that I've posted enough questions over the last few years that I was instantly releaved when I saw your Avatar? ;)

Okay, I'm sure I'll watch something on it over the next few nights...Or, will posting my log from the last time I watched something on it (which was an effected video) work?

It's not a bad sign :). 

Posting your logs from the last time you had the problem is fine. Hopefully we'll see something in there that leads to some possible fixes.

Playback issues can be really tough to solve. when I first had myth it seemingly took forever to get them right, and I've had a few issues recently that I tweaked to death until solving. One thing I should make sure of - Is This is a combined frontend/backend?

---

### Post by newlinux on 2009-04-16
> **Weidbrewer said:**
> Sorry for the confusion...my sig-line is my backend/server.  The frontend in question is using much older and low-powered equipment.  It was working under 8.04, but I've hit a few snags with the upgrade (to be expected.)  Most everything was worked out except this stuttering.

looks like we were posting at the same time (and I should have read your first post more carefully, it clearly states remote frontend) - what is your frontend hardware and what types of content are your trying to playback? Do you have this problem on your local frontend (to your backend)? And if this is mythvideo you are talking about, are you using mplayer or the internal player or some other player?

---

### Post by Weidbrewer on 2009-04-16
I need to take a look at the hardware later when i'm there....it was put together out of spare parts (Yes, it has and ATI 9200SE card...flogging line starts below.)  I think it has 512+ of ram in it and a so-so single-core processor. Since it's only used for remote play-back, this has not been a problem up until now.   

It is using the internal player (unless something got changed automatatically during the upgrade - didn't think of that.  I doubt it, because the remote is using internal player keybinding.)

Problem does not exist on either of the other two remote frontends, or the combined front/backend.   Combined one and at least one of the other frontends are also running 8.10.

This is happening with videos from the backend (I do very little recording, as my cable provider has a DVR standard.)  Video files are mounted using your kick-*** NFS instructions that I keep bookmarked on all computers. (Flattery generally works.)

Again, frontend worked fantastically under 8.04, so I kno it's possible.  Since it's hooked to my livingroom plasma, it gets the heaviest use out of all my frontends (so, of course, it has the crappiest equipment...)

Hopefully this helps.

---

### Post by nickrout on 2009-04-16
Actually I believe the default for mythvideo is mplayer.

What sort of network connection do you have? I get this kind of trouble when wireless is playing up, so I have gone all wired which is so much better.

If in fact you are using mplayer then try adding > -cache 16384 to the command line.

Anyway, as already mentioned, watch the logs. One good way is to sit on the sofa with your laptop. ssh into the frontend and then run:

```
tail -f /var/log/mythtv/mythfrontend.log
```

The log will scroll past. See if you spot anything during a glitch.

---

### Post by Weidbrewer on 2009-04-16
> **nickrout said:**
> Actually I believe the default for mythvideo is mplayer. 

Yep, but I never liked it, so I've kept every on internal.  Don't know if this one got reverted during upgrade.

>  What sort of network connection do you have? I get this kind of trouble when wireless is playing up, so I have gone all wired which is so much better. 

Wired.

>  Anyway, as already mentioned, watch the logs. One good way is to sit on the sofa with your laptop. ssh into the frontend and then run:

```
tail -f /var/log/mythtv/mythfrontend.log
```

The log will scroll past. See if you spot anything during a glitch.

More or less what I'm planning - thanks for the specific command.  I'll let you know what I find out.

---

### Post by nickrout on 2009-04-16
sorry i see you said upgrade,  not new install, your old default player should still be valid, easy to check though.

---

### Post by Weidbrewer on 2009-04-16
Ha...easy enough to check if I ever get my butt home to where the machine is...

---

### Post by Weidbrewer on 2009-04-17
Okay, here it is:

```
2009-04-17 20:10:16.104 NVP: prebuffering pause
2009-04-17 20:10:03.462 NVP: prebuffering pause
2009-04-17 20:10:04.200 NVP: prebuffering pause
2009-04-17 20:10:05.008 NVP: prebuffering pause
2009-04-17 20:10:05.657 NVP: prebuffering pause

```

Etc.


Does this help us?


EDIT:  The second time it stuttered, it had an additional line:

```
2009-04-17 20:19:16.576 mdb:19, lastbuf:0 skipping granule 0
2009-04-17 20:20:03.621 NVP: prebuffering pause
```

---

### Post by Weidbrewer on 2009-04-17
Additional, the system specs are as follows:

CPU:  768 MHz Celeron
RAM:  502 MB
GPU:  Radeon 9200SE


Yes, I know, very low power - but it has always served the needs of a frontend.

---

### Post by Chunk of Earth on 2009-04-17
Make sure your playback profile in the Playback settings is set to CPU--.

---

### Post by Weidbrewer on 2009-04-17
Where is that setting?  Not finding it.

---

### Post by Chunk of Earth on 2009-04-17
Utilities/Setup
[INDENT]Setup
[INDENT]TV Settings
[INDENT]Playback
[INDENT]Playback Profiles (3/9)
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2009-04-18
OKay, yep...that's what it's set for.   However, remember, this is a MythVudeo issue...I don't watch any TV through this box, if that matters.

---

### Post by joshoekstra on 2009-04-18
> **Weidbrewer said:**
> OKay, yep...that's what it's set for.   However, remember, this is a MythVudeo issue...I don't watch any TV through this box, if that matters.
If you use the internal player, that's the page that controls the settings.

---

### Post by Weidbrewer on 2009-04-18
I will admit that I hadn't read that carefully.  I had not realized that "--" was part of the label.  It had been on CPU+ (And all I saw in both cases was "CPU".)  I changed it over to CPU--, and it is sill stuttering.  Anything else I can try?  

I really don't want to have to downgrade back to 8.04.  That would not be fun.

---

### Post by Weidbrewer on 2009-04-19
Update:  Good news bad news situation.

I back-traced my steps of the upgrade, and realized that I did not have the ATI FGLRX driver installed.  I remembered that I had intentionally deactivated it, and I figured it out again.

With it active, I only got two minor hiccups in an hour.  Couldn't even call them stutters, really.  The problem is that Myth itself does not render correctly.  It displays on the TV all pixlated.  I know that this is because of the card driver, because it displays normally in remote desktop.   An additional issue is that when you hit stop on a video, or it reaches it's end, Myth crashes to the desktop.

So, one problem kinda solved, and an even bigger one presents itself.

EDIT:  Well, it's not pixalating like it was...it was a resolution issue.   But now, when it first boots up, it's way out of whack (Myth GUI) until I exit and restart to let it auto adjust.  Playing with the GUI settings in setup => appearance does nothing.   So, I can get it to display properally...but not without logging in with a laptop so that I can exit and start it again.

---

### Post by Weidbrewer on 2009-04-19
When a video ends and it crashes to desktop, this is the info I get (which doesn't look any different from normal.):

```
2009-04-19 23:27:03.000 TV: Attempting to change from WatchingPreRecorded to None
2009-04-19 23:27:03.249 TV: Changing from WatchingPreRecorded to None


```

---

### Post by newlinux on 2009-04-20
Don't know anything about this crashing problem, but you might want to turn up the verbosiety in your logs to get more information on the crash (mythfrontend -v all -- This will give you a lot of output ).

---

### Post by Weidbrewer on 2009-04-20
Can verbose options be added to the command that nickrout gave me above?

```
tail -f /var/log/mythtv/mythfrontend.log
```

I've been using that so I can keep tabs in real time and like it quite a bit.

So, right now, actually using the ATI driver gives me good play-back performance.  I watched an episode of an hour-long drama yesterday, as well as a full-length movie.  No skips in either.   However, I still get the crash issue.

Also, as mentioned before, no matter what I set the GUI resolution to, it displays wrong when it first boots up (really, really large) and I have to exit and restart.  Hopefully the logs might be able to tell us something.  I'll try to get to that tonight.

---

### Post by newlinux on 2009-04-20
> **Weidbrewer said:**
> Can verbose options be added to the command that nickrout gave me above?

```
tail -f /var/log/mythtv/mythfrontend.log
```

I've been using that so I can keep tabs in real time and like it quite a bit.

So, right now, actually using the ATI driver gives me good play-back performance.  I watched an episode of an hour-long drama yesterday, as well as a full-length movie.  No skips in either.   However, I still get the crash issue.

Also, as mentioned before, no matter what I set the GUI resolution to, it displays wrong when it first boots up (really, really large) and I have to exit and restart.  Hopefully the logs might be able to tell us something.  I'll try to get to that tonight.
you have a couple of options.

1. You could do
```

mythfrontend -v all -l /var/log/mythtv/mythfrontend.log

```
from the command line and that will log to the same file you've been reading with the tail command.

2. You could modify /etc/mythtv/session-settings to change the defualt logging level when you run mythfrontend with the --service option (when you run it from the menu it runs with the --service option).

The first issue you have might be related to the myth problems with the ATI driver, and I don't have any experience with ATI drivers and myth. The second one seems like it might be myth related - hopefully the verbose logs will tell us something, but I'm not terribly hopeful, but that's the first place to start...

---

### Post by Weidbrewer on 2009-04-20
Thanks for the tireless advice once again.  I'll give those log changes a go ASAP and see what we get.

I also realized while working on my wife's computer last night that her's is rocking 8.10 and the same exact gfx card - with no problems.


Grrr.   Looking more and more like I should cut my losses and nuke this installation and go back to 8.04 fresh.  Everything worked there...

But alas, I'm stubborn and want to find a solution to the problem.

---

### Post by Weidbrewer on 2009-04-21
*sigh*  Okay...I give.  I spent another night fighting with this, and long story short - I got nowhere.   The verbose logs just gave me "segmentation error," which has been another endless loop kind of error chase.  I still can't get the resolution issue worked out, either.

Stubbornness is one thing, but this has reached the ridiculous point.  I'm wiping the drive and doing a fresh install of 8.04.  It worked on that before, so I'm just going back to it, and I'm leaving it there until the next LTS release.   Thank you everyone for trying to get this solved for me.

---

