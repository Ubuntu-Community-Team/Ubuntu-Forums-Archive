---
title: "Entire GUI seems sluggish"
date: 2010-07-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by clivejo on 2010-07-02
I don't know if its me going too fast, but my entire system GUI seems to be reacting very slow since the system update today.  For example the drawing of the system menus, application menus, opening web pages.

I have Compiz + Emerald installed and have also noticed the window titles are not transparent like they used to be.  They now have a white background.   I wonder are these two issues related and is anyone else having similar problems?

---

### Post by ronacc on 2010-07-03
try restarting compiz .

---

### Post by alexan on 2010-07-03
**glxinfo |grep direct**
Give "yes"?


also this:
post the result of:

**cat /var/log/apt/history.log |tail**

---

### Post by indigoblue on 2010-07-03
Have you done an update more recently than 18 hours ago when you posted this? I had a problem with Emerald as well, where the window borders were off and it might have been similar, but that was fixed with an update.

Also, it was slow a few days ago, but both Nautilus and menus, etc, are faster now, so I would just suggest an update.

---

### Post by omgbots on 2010-07-03
I'be had the same issue.  For me, it seems to have corresponded with the update a few days ago to libcairo2 1.9.10.  Also, Update Manager since that upgrade is now unbearably slow.  Back to using command-line apt.

---

### Post by russianbandit on 2010-07-05
I've also seen the same thing for the past week. The whole UI is slow and Update Manager takes ages to rebuild dependencies. Any resolution on this?

---

### Post by Harry33 on 2010-07-26
The sluggishness and incorrect rendering of buttons, progress bars etc. are said to be due to the nvidia proprietary drivers.
Even the version 256.35-0ubuntu2 is not fully compatible with the new 1.9 branch of cairo (newest one is libcairo2_1.9.12-1).

However, the problems can be fully avoided and overcome by changing the themes. You need to open the manager (Appearance).
Then choose to customize the theme you are using, pick up Controls named "Mist". Save the theme and you are done. ;)

Mist does not use color blends nor gradients, which are the main reasons for the troubles in cairo.

---

### Post by gnomeuser on 2010-07-26
Maverick generally has been slower than Lucid for me since day one, but the last few days it has gotten to the point of the entire desktop stalling for up to a minute at the time.

It's very weird indeed.

---

### Post by jpeddicord on 2010-07-26
What Harry33 said.

I got fed up with the slowness and started digging around a bit -- turns out Ambiance and Radiance are causing problems and draw very slowly. Try picking another theme and see if it helps. I'm using Shiki-Brave (Murrine) and things have sped up ten-fold. Measure the performance between different themes in GtkPerf.

---

### Post by mc4man on 2010-07-26
Haven't noticed any appreciable  slowness w/ Ambiance on nvidia, maybe a hair slower. (other than performance expected from p4 3.4

Did however decide awhile ago the 256 drivers are not that well suited to an agp card (7800 GS OC here), so have reverted to using the 195 nvidia-current (Xserver 1.8 comp.

Don't have high hopes of the 195 being offered as one of the restricted driver choices so obviously only a temporary thing. 
( though am certainly going to try rebuilding the 195 to work with the final Xserver version.

---

### Post by Artoo on 2010-07-27
I'm guessing it's the bug reported here: [https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/595845](https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/595845)

Changing theme to human (from ambiance) helped a lot - though it's still there. It was also apparent in AWN from repository, especially on loading, but resorting to awn-testing ppa resolved the issue.

---

### Post by Harry33 on 2010-07-27
Artoo,

Actually the bug #595845 is about the issue where opening and using either update manager or synaptic will take up to 100% CPU load.
This issue concerns both Lucid and Maverick and both NVidia and Ati graphics cards.
This does not seem to have much to do with libcairo2 package,
which is in lucid 1.8.10 and it does not have slowdown issues at all. And yet, it seems that Ati does not suffer from slowdowns either. The problematic libcairo2 is 1.9 branch and only with NVidia graphic cards.
This issue is well described here (bug #605979):
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/605979](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/605979)
So it seems, this is a NVidia driver issue.

---

### Post by recluce on 2010-07-28
Launchpad makes it official now: there is nothing wrong with libcairo - and if your system gets sluggish - scr** you. As long as it works on the developers machines, all is well.

So we seem to get three alternatives: use Nouveau and forget about decent graphics performance, throw away our Nvidia cards or throw away Ubuntu. 

As things stand, I might as well discontinue beta-testing Maverick and look for another distribution once Lucid gets too old. A sorry state of affairs.

---

### Post by cariboo on 2010-07-28
> **recluce said:**
> Launchpad makes it official now: there is nothing wrong with libcairo - and if your system gets sluggish - scr** you. As long as it works on the developers machines, all is well.

So we seem to get three alternatives: use Nouveau and forget about decent graphics performance, throw away our Nvidia cards or throw away Ubuntu. 

As things stand, I might as well discontinue beta-testing Maverick and look for another distribution once Lucid gets too old. A sorry state of affairs.

How about waiting until the final release, until you throw your hands in the air and claim you're quiting. There is still approx. 2½ months to go.

---

### Post by SunnyRabbiera on 2010-07-28
> **cariboo907 said:**
> How about waiting until the final release, until you throw your hands in the air and claim you're quiting. There is still approx. 2½ months to go.

Indeed, its an alpha so issues are bound to happen

---

### Post by crjackson on 2010-07-29
> **SunnyRabbiera said:**
> Indeed, its an alpha so issues are bound to happen

Seriously, it's an Alpha.  It's been doing so well for me it seems like it's just a few package upgrades rather than a release.  I'm sure that'll change down the road, but it's an ALPHA!

---

### Post by recluce on 2010-07-29
> **cariboo907 said:**
> How about waiting until the final release, until you throw your hands in the air and claim you're quiting. There is still approx. 2½ months to go.

Since the bug has been marked "invalid", how likely is it to be fixed by then (or ever)?

---

### Post by ranch hand on 2010-07-29
All they are talking abput is where the problem lies;
> 
Changed in gtk2-engines-murrine (Ubuntu):
status:     Confirmed &#8594; Invalid 

They seem to take the cairo problem fairly seriously, including an Ubuntu only patch to deal with what appears, to them, to be a bug in the Nvidia driver.

Interesting problem anyway.

---

### Post by Harry33 on 2010-07-29
I made an interesting test. I installed the maverick-64bit version of libcairo2 (1.9.12-1) into a lucid-64-bit machine with an Ati graphics card (HD 2600 Pro).
And what did I find, GTK-themes are now suffering some sluggishness. Not nearly as bad as with NVidia card, but still.
And yes, using theme controls "MIST", no sluggishness at all.

I would not call this a bug in NVidia drivers anyway. An issue, yes. After all recent NVidia drivers (256.35) are older than the recent libcairo2. So what actually have happened is that libcairo2 developed into a direction, where it ended up being fully incompatible with NVidia drivers. Chicken or the egg?

---

### Post by ranch hand on 2010-07-29
> **Harry33 said:**
> I made an interesting test. I installed the maverick-64bit version of libcairo2 (1.9.12-1) into a lucid-64-bit machine with an Ati graphics card (HD 2600 Pro).
And what did I find, GTK-themes are now suffering some sluggishness. Not nearly as bad as with NVidia card, but still.
And yes, using theme controls "MIST", no sluggishness at all.

I would not call this a bug in NVidia drivers anyway. An issue, yes. After all recent NVidia drivers (256.35) are older than the recent libcairo2. So what actually have happened is that libcairo2 developed into a direction, where it ended up being fully incompatible with NVidia drivers. Chicken or the egg?
That may be some good information to pass on.  A comment on that bug?

---

### Post by recluce on 2010-07-29
> **ranch hand said:**
> All they are talking abput is where the problem lies;

They seem to take the cairo problem fairly seriously, including an Ubuntu only patch to deal with what appears, to them, to be a bug in the Nvidia driver.

Interesting problem anyway.

I wish you were right. However, take a look at bug 601220, which concerns libcairo2:

```
 Changed in cairo (Ubuntu): 
status: 	New &#8594; Invalid 
```

This is the reason for my pessimism as far as upcoming releases of Ubuntu and the NVidia drivers are concerned.

---

### Post by philinux on 2010-07-29
> **recluce said:**
> I wish you were right. However, take a look at bug 601220, which concerns libcairo2:

```
 Changed in cairo (Ubuntu): 
status: 	New &#8594; Invalid 
```

This is the reason for my pessimism as far as upcoming releases of Ubuntu and the NVidia drivers are concerned.

Invalid only means they don't have enough info. Be pessimistic when it goes to won't fix.

---

### Post by jpeddicord on 2010-07-29
> **recluce said:**
> I wish you were right. However, take a look at bug 601220, which concerns libcairo2:

```
 Changed in cairo (Ubuntu): 
status: 	New &#8594; Invalid 
```

This is the reason for my pessimism as far as upcoming releases of Ubuntu and the NVidia drivers are concerned.

The reporter marked their own bug as invalid. This is hardly an indication of anything official.

---

### Post by Harry33 on 2010-07-30
> **jpeddicord said:**
> The reporter marked their own bug as invalid. This is hardly an indication of anything official.

Exactly,
the bug #601220 is about claiming that new libcairo2 (1.9 branch) causes incorrect rendering of buttons, progress bar, etc. where gradients are used. But this issue can only be seen with NVidia proprietary drivers, not with Ati.
So, here we are again, chicken or egg.;)

The sluggishness (high CPU usage) is totally another issue and it can be seen on both NVidia and Ati graphic cards, whatever driver is used.

---

### Post by mc4man on 2010-07-30
> chicken or egg
whichever is the nvidia 256 drivers
(or if not for all 256 users then hardware+256

---

### Post by Harry33 on 2010-08-01
Well the newest pre-release 256.44 did not change this buggy situation anyway.
One might wonder, however, what is the situation seen from the developers point.
Ubuntu developers related to libcairo2 claim this is a nvidia issue.
Well do we actually know, are other linux distros affected, those that use libcairo2 1.9 branch with nvidia hardware?
And, after all, do nvidia developers know about this "ubuntu" issue?

---

### Post by kj74 on 2010-08-01
> **Harry33 said:**
> Well the newest pre-release 256.44 did not change this buggy situation anyway.
One might wonder, however, what is the situation seen from the developers point.
Ubuntu developers related to libcairo2 claim this is a nvidia issue.
Well do we actually know, are other linux distros affected, those that use libcairo2 1.9 branch with nvidia hardware?
And, after all, do nvidia developers know about this "ubuntu" issue?

It might be good idea to ask what Nvidia driver developers think about this issue. Some of them are active at this [web]("http://www.nvnews.net/") forum.

---

### Post by Harry33 on 2010-08-01
> **kj74 said:**
> It might be good idea to ask what Nvidia driver developers think about this issue. Some of them are active at this [web]("http://www.nvnews.net/") forum.

Sure, I know.
But, in order to give a constructive feedback, you need to be a libcairo developer, indeed.
If it is true that nvidia proprietary drivers read new cairo (1.9) incorrectly, you should be able to pinpoint how does this happen.
And I am not one.

---

### Post by Intrepid Ibex on 2010-08-01
Not reproducible with Arch (linux). I'm not exactly 100% sure where am I _supposed to_ experience all these "incorrect rendering of buttons, progress bar, etc. where gradients are used" as Harry33 it described (nor does the desktop feel 'sluggish') but either way I'm using the proprietary Nvidia driver 256(.44), libcairo 1.9(.12), Gnome 2.30(.2) and Compiz (0.8.6)/Emerald (0.8.4).

Q.E.D. this is not an Nvidia issue (in the sense that the 256.x series Nvidia drivers break Cairo) but a Ubuntu or/and Debian based patching issue. I'd be excited to toy around with all those libcairo/libcairo's dependencies patches with Ubuntu and Debian but I don't have either of those distros and have no other plans of touching them so I can't provide the name of the exact patch that would cause this issue - it sure would be dangling fun to take the credit for at least that, tough ;).

**E:** Tried with the Ubuntu Ambiance theme from AUR (Arch User Repository, think of it as an Arch Linux's Launchpad.. only you build every single package from source) - no difference, still as fast and non-incorrectly rendered buttons as always.

---

### Post by MarkieB on 2010-08-02
no longer participating in ubuntuforums.org

---

### Post by kj74 on 2010-08-02
> **MarkieB said:**
> don't hold your breath - I've witnessed what I now know is a cairo bug - possibly the bug you see, corrupt renders - in amd64 nvidia from Lucid Beta, it initially looked as though it was openoffice, then I noticed in in FirstClass - now in Maverick it seems to appear in various cairo renders

needless to say, the 'pillar to post' business is par for the course :p

That's not same bug.

---

### Post by Harry33 on 2010-08-02
> **Intrepid Ibex said:**
> Not reproducible with Arch (linux). I'm not exactly 100% sure where am I _supposed to_ experience all these "incorrect rendering of buttons, progress bar, etc. where gradients are used" as Harry33 it described (nor does the desktop feel 'sluggish') but either way I'm using the proprietary Nvidia driver 256(.44), libcairo 1.9(.12), Gnome 2.30(.2) and Compiz (0.8.6)/Emerald (0.8.4).

Q.E.D. this is not an Nvidia issue (in the sense that the 256.x series Nvidia drivers break Cairo) but a Ubuntu or/and Debian based patching issue.
...

Well here we are again in this "Ubuntu" mess.
So many packages are patched and repatched that it's damn hard to say what is causing what.
But, nvidia proprietary drivers are not open source, so at least one cannot patch them.
This suggests the bug is actually elsewhere.
There are different suggestions around, some claim it is cairo, some point fingers on gtk-themes.

Just tell me this.
Why am I seeing serious sluggishness with Maverick's nvidia-current_256.44, libcairo_1.9.12 and with any gnome theme (clearlooks, human, sand ...). It takes about 3-5 sec to open subdirectories in the directory .thumbnails with Nautilus.

And then tell me this.
Why I do not see any sluggishness if I change the "Controls" of any theme to "Mist".
Any other "Controls" in the list cause sluggishness.

---

### Post by Intrepid Ibex on 2010-08-02
I actually installed Maverick today and tried to build libcairo2 without those two patches the package has and to update emerald. Well, sad to say as a try it stayed (and I'm a goddamn _Arch_ user) (took like 5 hours overall before I gave up). First off dealing with the xorg-edgers PPA and 'standard' repositories through Synaptic was _pure_ pain because of those nice dependency errors. Doing stuff as Synaptic wanted me to took like 2 hours off my time. Why? Because Ubuntu has to be idiot-proof and apparently there's no need to have the slightest opportunity to break this shield. In Arch/pacman all the dependencies can be ignored with a simple "-d" flag.

When I (thought I) finally got all the packages set up I decided to go for Gnome shell to look into this cairo-or-whatever-issue a bit closer. Well, I tried both the outdated one you can get from the 'standard' repos and the one from the [PPA](https://launchpad.net/~ricotz/+archive/testing) but apparently I couldn't get either gnome-shells to open up.

Finally I tried to build libcairo2 without the two patches it's build against but apparently Maverick's repos are missing some packages I'd need in order to do so.

Well, maybe I'll try again tomorrow with Lucid ;).

[QUOTE=the Ubuntu Installation Welcome Screen]
Whether you're new to Ubuntu or a long-time user, we're sure there is something you will enjoy.[/QUOTE]- Oh, I'm sorry.

---

### Post by Harry33 on 2010-08-02
> **Intrepid Ibex said:**
> ...
Well, of course after trying both the outdated one you can get from the 'standard' repos and from the PPA but apparently I couldn't get either gnome-shells to open up.


Yeah, those outdated gnome-shells are troublesome.
However, the maverick official repo version works after one workaround.
I have made a bug report on this one:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/611262](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/611262)

So gnome-shell does not know where the mozilla javascript library is (=libmozjs.so).
As a workaround the file /usr/lib/xulrunner-1.9.2.8/libmozjs.so
must be copied into the directory /usr/lib/
or a symlink has to created into the directory /usr/lib/

---

### Post by Harry33 on 2010-08-03
Those interested may also want to take a look at one Launchpad bug report and one FreeDesktop Bugzilla bug report:
[https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/612614](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/612614)
[https://bugs.freedesktop.org/show_bug.cgi?id=29368](https://bugs.freedesktop.org/show_bug.cgi?id=29368)

---

### Post by Intrepid Ibex on 2010-08-03
Ok, now I've experienced two other issues in Arch with nvidia 256.x and libcairo 1.9.x. The whole desktop is actually a bit 'wider' than with Nouveau, while there's also a rendering issue *or-whatever-fancy-word-I'm-supposed-to-use* with the 'Window selection' in the panel where the selection color is brighter with the nvidia proprietary driver than with nouveau.

Here's screenies of my desktop with: [[COLOR="Blue"]nvidia[/COLOR]](http://img694.imageshack.us/img694/841/nvidiam.jpg), [[COLOR="Blue"]nvidia with compiz[/COLOR]](http://img834.imageshack.us/img834/4020/nvidiacompiz.jpg) and [[COLOR="blue"]nouveau[/COLOR]](http://img138.imageshack.us/img138/986/nouveaut.jpg).

Also [[COLOR="Blue"]here's[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/612614) the original message I posted in Launchpad ([[COLOR="Blue"]and here's a straight link[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/612614/comments/13)).

So there is indeed an issue with Nvidia 256.x and cairo 1.9.x.

**E:** But to find something positive it is a very good thing that even Lucid refused to cooperation so I don't need to bang my head against my keyboard no longer.. not that it'd matter anymore in the sense that I had a working one (this message was written with an on-screen keyboard) (just kidding).

---

### Post by Harry33 on 2010-08-04
Please take a look at the bug #605979:

[https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/605979](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/605979)

and especially Aaron Plattners reply.
As many of you know Aaron is a developer of nvidia drivers.

---

### Post by Harry33 on 2010-08-04
More news about the sluggishness in package libcairo2 with nvidia proprietary drivers.
In maverick repos there is a new libcairo2_1.9.14-1ubuntu1 package with a patch to fix slow progress bar on cards that do not implement server-side gradients.

---

### Post by Harry33 on 2010-08-04
I have now tested the new update, libcairo2_1.9.14-1ubuntu1, and it seems to have fixed all incorrect rendering issues and also the desktop sluggishness issues so far.:p

---

### Post by Intrepid Ibex on 2010-08-04
I guess that makes this topic [SOLVED]..

---

### Post by durand on 2010-08-04
Not fixed here, using libcairo2-1.9.14_1 and I still get this sluggishness. Everything's fully updated.

---

### Post by psyke83 on 2010-08-04
> **durand said:**
> Not fixed here, using libcairo2-1.9.14_1 and I still get this sluggishness. Everything's fully updated.

Your version is from xorg-edgers? Judging from the changelog, it doesn't include the fix.

Edit: Maybe not. Xorg-edgers has version 1.9.14-1 for Lucid only. if you're on Maverick, you should have the patched version (1.9.14-1ubuntu1) from the main repository.

---

### Post by Intrepid Ibex on 2010-08-05
You also need to (re)boot..

---

### Post by durand on 2010-08-05
Thanks, I didn't realise that the ubuntu1 bit made all the difference. It seems to be working well now.

---

