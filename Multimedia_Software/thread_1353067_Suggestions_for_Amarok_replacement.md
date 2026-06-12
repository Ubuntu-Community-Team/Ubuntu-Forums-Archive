---
title: "Suggestions for Amarok replacement?"
date: 2009-12-12
forum: Multimedia Software
---

### Post by doug-M on 2009-12-12
Okay I tried to give the 2.x version of Amarok a fair try but I can't stand it. 

So going forward I'm looking for suggestions for a new music player. Features of interest are:
- Simple management of large mp3 collections.
- Song queue (preferably add from within music player or from file system)
- Multi platform (Linux and windows)
- Easy to turn random play on/off
- In the repositories so it is easy to keep up to date
- Easy way to show recently added music.
- mp3 player (iPod etc.) integration a plus.

I really liked Amarock 1.x, it was fabulous, the rediscover your music was absolutely right. I was very excited when they said 2.x would be multi-platform. Unfortunately I can't stand the new UI, that big applet window that I can't remove is horrible. None of he features I loved in 1.4 are there and it sounds like the devs aren't planning on doing much for the things I am interested in.

So what do you use? Any other suggestions for players I should look at.

amarock 1.4 - I'm tempted to go back for a while and see what the landscape looks like when this dies.

atunes - only other cross platform one I have found so far but doesn't appear to be in repositories.

Gmusicbrowser - sounds promising but not cross platform.

---

### Post by balaknair on 2009-12-12
Try this PPA if you really want to stick with Amarok 1.4, not cross platform though

[https://launchpad.net/~bogdanb/+archive/amarok14](https://launchpad.net/~bogdanb/+archive/amarok14)


Other notable linux options- Juk, Banshee, Exaile and Listen

Cross platform players-
Songbird- Based on Mozilla, extensible with loads of extensions. Best of the lot in many ways, but I've found Amarok to be better(especially with the ease of adding songs to queue). Not in the repos but there a few PPAs on Launchpad for testing builds(may not be stable).

aTunes- very very good, just wish it wasn't so resource hungry, being a Java app.

The only app that I can think of which fulfills pretty much all the requirements you state is jajuk
[http://www.jajuk.info/index.php/Main_Page](http://www.jajuk.info/index.php/Main_Page)

It's cross-platform and available in the repos.

---

### Post by cascade9 on 2009-12-12
Exaile is meant to work on windows from 0.3.1 

[http://www.exaile.org/wiki/index.php?title=Microsoft_Windows](http://www.exaile.org/wiki/index.php?title=Microsoft_Windows)

Should do everything you want with the iPod plugin. 

Jajuk was horrid, very slow in my experience.

---

### Post by michaelzap on 2009-12-12
> **cascade9 said:**
> Exaile is meant to work on windows from 0.3.1
+1 for Exaile. It's what I started using after Amarok devoured itself. I actually like MediaMonkey best on Windows, however (I just mount the same shared mp3 server on both platforms).

---

### Post by Raffles10 on 2009-12-12
Amarok is one of the saddest stories in Linux. When I first used it a couple of years ago I thought it was amazing, the best music app' in Linux & Windows. How they made such a balls up of it is incredible, turning a silk purse into a sow's ear. :(

+1 Exaile.

---

### Post by doug-M on 2009-12-12
I'm not finding Exaile in the repositories. 

I gave jajuk a quick try. It seems pretty good, certainly better than Amarok 2.x. The fonts are a bit funky and some of the controls seem a little weird:
- You seem to have to drag things into the queue, there doesn't seem to be any other way to queue up stuff (right click/double click etc).
- The right click menu on the control panel is a little too busy

I agree, it is really sad what happened to Amarok, the devs seem to be doing a whole bunch of work but from what I see the results are not very usable.

---

### Post by michaelzap on 2009-12-12
> **doug-M said:**
> I'm not finding Exaile in the repositories.
That's odd. It should be in the repos from at least Intrepid forward. You should probably add the Exaile PPA anyway so that you get the latest version:
[http://www.exaile.org/downloads](http://www.exaile.org/downloads)

---

### Post by SuperSonic4 on 2009-12-12
Stagnation is good for nobody - after all if you don't progress you end up with gnome

---

### Post by Uncle Spellbinder on 2009-12-12
> **michaelzap said:**
> That's odd. It should be in the repos from at least Intrepid forward. You should probably add the Exaile PPA anyway so that you get the latest version:
[http://www.exaile.org/downloads](http://www.exaile.org/downloads)

Yep. I have the PPA repo in my sources.list as such:

```
#### Exaile
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43CBFCC0
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main
```

The finest player I've used in Linux.

---

### Post by Uncle Spellbinder on 2009-12-12
> **SuperSonic4 said:**
> Stagnation is good for nobody - after all if you don't progress you end up with gnome

:roll:

---

### Post by Raffles10 on 2009-12-12
> **SuperSonic4 said:**
> Stagnation is good for nobody - after all if you don't progress you end up with gnome

Amarok 2 is progress ? :o

---

### Post by Ron F. on 2009-12-25
This is tough. I was an Amarok user for several years, until the 2.* revolution. Since then I have never been completely happy with anything. I have tried Exaile, Banshee, Rhythmbox, Songbird, Listen, Quod Libet, GMPC & GMPD, Audacious, aTunes, Jujuk, and probably a few I have forgotten. 

I listen to a lot of music ... an awful lot. Right now in fact, I am listening to an incredible display of raw talent: Jeff Beck playing Nadia (live) using Exaile again since, it was being mentioned here.

The problem with each of these music managers/players, is that they all do something wonderful, but then suck at something else, Exaile is no exception.

The perfect, or nearly perfect music player does not exist, does not remotely exist. Some players have good OSD support, some don't, some have great searching, others wonderful context displays, some can fade out a playing track when it is paused, or fade in a track when play begins - some players will never support that. Some players are good at supporting multiple music sources, and will show only available tracks ... others cannot handle that. MSD support, CD ripping, etc.

I guess they all suck. My greatest angst is directed at Songbird, who before perfecting a passable music player, want to go on and do video player support - like I am ever going to supplant VLC with Songbird........right. 

So, in the end, my solution is this:
I am most comfortable with Jajuk. It looks ugly as sin, but on balance it works well, and it gives lots of love to Linux users. I give it a B. Nobody gets an A today.

For ripping CDs, my choice is controversial: I run dBpoweramp under WINE. I do this because it produces the most accurate tagging, and it works very well under WINE. I have ripped well over a thousand CDs by my own hands, and tried every conceivable solution available under Linux. In the end I went back to a Windows solution for this task.

Ah... now we are on to "Goodbye Pork Pie Hat." You will have to excuse me...

---

### Post by kung fu buntu on 2010-06-21
I know this thread is old, but this was one of the most relevant when I searched for amarok in the title.

I'm compelled to share the good news :)

copy-paste from what I typed here: [http://ubuntuforums.org/showthread.php?p=9493407#post9493407](http://ubuntuforums.org/showthread.php?p=9493407#post9493407)


There seems to exist a **[COLOR="Red"]faithful replacement to amarok 1.4 for KDE4[/COLOR]**.
It seems good so far, but I just installed it 1 hour ago.

[http://pana.bunnies.net/](http://pana.bunnies.net/)
[http://pana.bunnies.net/](http://pana.bunnies.net/)
[http://pana.bunnies.net/](http://pana.bunnies.net/)

I think this needs all the support (users, advertisement, coders) that it can get in order to live and prosper (including encouragement to the developer).
I've heard of other "clones" as well, like cuberok or clementine... but Pana seems to be the real thing :D


If you like Pana, I would suggest to add it to your signature:
**[http://pana.bunnies.net/](http://pana.bunnies.net/) [COLOR="Red"]An Amarok 1.4 clone for KDE4.[/COLOR]**

---

### Post by SZVSZ on 2010-08-10
> **Raffles10 said:**
> Amarok is one of the saddest stories in Linux. When I first used it a couple of years ago I thought it was amazing, the best music app' in Linux & Windows. How they made such a balls up of it is incredible, turning a silk purse into a sow's ear. :(

god, this is so true. they took something that was near perfect, and destroyed it. There's not even a trace left of what I originally loved about Amarok. Amarok 2.0 is so full of mindless, ugly gimmickry, like they are trying to compete with itunes on eye candy or something. I don't understand any of it - why the huge, ugly play control buttons at the top of the screen? Why the dumb "information" window in the centre of the screen (where the playlist should be)? Why can't I create folders to group my podcasts, like I could in 1.4? It's just very, very, sad - an act of software vandalism, almost.

---

### Post by wkulecz on 2010-08-10
I'm running Amarok 1.4 on 64-bit 10.04 (my wife actually is the main user).  The instructions are toward the end of this thread:

[http://ubuntuforums.org/showthread.php?t=1400314&page=2](http://ubuntuforums.org/showthread.php?t=1400314&page=2)



> Stagnation is good for nobody - after all if you don't progress you end up with gnome 
Things like Amarok hit a level of functionality that completely solve the problem.  Further "improvements" are counter-productive.  Different is not better, better is better, Amarok 2 is not only very different, its mcuh worse in doing the job of being an unobtrusive music player and management system.

I'd be thrilled with Amarok 1.4 simply ported unchanged to new versions of Ubuntu in the repos.

I find the fact that with Gnome I can still effectively use RedHat 5 and Ubuntu 10.04 systems as opposed to the KDE flavor of the day where everything seems randomly moved around at every "upgrade".

---

### Post by nothingspecial on 2010-08-10
You ought to try guayadeque

Links in my sig

---

### Post by SZVSZ on 2010-08-12
> **nothingspecial said:**
> You ought to try guayadeque

Links in my sig

thanks for the suggestion :)

---

