---
title: "ubuntu 11.4:  banshee too buggy"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kswenson on 2011-04-22
I'm using Banshee for the first time with 11.4 beta2...
   what a disaster.

There are so many bugs I almost can't isolate one to report on launchpad!
Are others having this issue?

---

### Post by KegHead on 2011-04-22
Hi!

Can you be a little more specific?

Also, can you post your computer specs?

Ram, etc.

KegHead

---

### Post by teachop on 2011-04-22
> **kswenson said:**
> I'm using Banshee for the first time with 11.4 beta2...
   what a disaster.

There are so many bugs I almost can't isolate one to report on launchpad!
Are others having this issue?
I didn't find Banshee to work properly either, but I cannot help except to say me too.  Because I chickened out and left that for other beta testers, putting rhythmbox on my natty instead.

---

### Post by kswenson on 2011-04-22
I posted one bug here:
  [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/769006](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/769006)

Other than that, there were many times when Banshee was using 100 CPU and hanging if I press stop, pause, play, forward, back too often.
It's not doing that any more which make me think it had something to do with importing my music...
   but my music appeared to be imported at the time fully.

There have also been some glitches in playback.
Things seem to be running more smoothly now.


I have a fairly modern machine (dell xps m1330):
=> lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)

---

### Post by screaminj3sus on 2011-04-22
banshee works fine for me.

---

### Post by KegHead on 2011-04-22
Hi!

Just curious:

Could you type "top" in your terminal when you're playing music and post?

KegHead

---

### Post by screaminj3sus on 2011-04-22
10% cpu while playing with the default banshee 2 package. 4% cpu usage using the daily ppa (2ghz core2 duo.)

---

### Post by KegHead on 2011-04-22
Hi!

It's in beta!

When was the last time you updated:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Just thinking out loud!

KegHead

---

### Post by gnomeuser on 2011-04-22
I've tried to make the bugreporting against Banshee a little easier:

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

Bugs filed on distribution bug trackers have a really hard time making it upstream so please file bugs on bugzilla.gnome.org

---

### Post by donniezazen on 2011-04-22
Ideally at this point of time use minimum number of addons while most of the bugs are being resolved.

---

### Post by VinDSL on 2011-04-22
> **kswenson said:**
> There are so many bugs I almost can't isolate one[...]

Are others having this issue?

> **kswenson said:**
> (T)here were many times when Banshee was using 100 CPU and hanging [...]

> **KegHead said:**
> Just curious:

Could you type "top" in your terminal when you're playing music and post?

For the sake of discussion...

Banshee has worked well enough for me.  It's definitely a step up from Rhythmbox, in form and functionality.  

The only 'problem' I've had with Banshee has to do with incorporating it into my Conky script.  And, it's a matter of timing.

Banshee is slow to start/stop, at times, and if I don't feed wait states into Conky, Banshee will start up in 3 instances.  And, it will require 3 stabs to get it to shut down.  Other than that, it works fine.

This, of course, is a 'problem' with Banshee and Conky not playing well together.  One, or the other, usually ends up with a black eye or bloody nose.  :)

With Rhythmbox, you can specify -nostart, on the command line, in scripts, and so forth.  This allows Conky to 'look' at the player's status, without actually opening a new instance of the program.

Banshee has such no matching feature, and this is the source of my 'problem'.  When things are finalized, I'll need to create a suitable workaround, but it certainly would make life easier if the devs would simply add a -nostart type feature to its CLI.

Anyway...

As far as mem & cpu are concerned, Banshee is as well behaved as any player that I've used.

Here's a screenie:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-22-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-apr-2011.png")[/INDENT]


I would post a 'top', but I find 'system monitor' more visually pleasing.

What I do is setup the 'system monitor' prefs to mimic 'top'.

IMO, all that matters is 'resident memory', e.g. ram usage (especially on this 1 GB machine).

As you can see, Banshee is using 86.7 MB ram and 4% cpu - a mere pittance of the limited resources on this machine.

If Banshee is using 100% of your resources, I would start looking elsewhere for the answer - perhaps your sound card drivers, et cetera.   ;)

---

### Post by andymion on 2011-04-22
> **kswenson said:**
> I posted one bug here:
  [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/769006](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/769006)

Other than that, there were many times when Banshee was using 100 CPU and hanging if I press stop, pause, play, forward, back too often.
It's not doing that any more which make me think it had something to do with importing my music...
   but my music appeared to be imported at the time fully.

There have also been some glitches in playback.
Things seem to be running more smoothly now.


I have a fairly modern machine (dell xps m1330)


I think the problem comes in when importing a large library (like in first use). Banshee was extremely slow and kept graying out for about the first ten minutes or so after logging in for the first time. This happened in a WUBI installation as well as an upgrade from a native install of 10.10 on the same machine. 

top says I'm only using 4% CPU now, and haven't had an issue after the "busy" icon in the lower left corner of the banshee window went away.

If there's a problem, it may just be in how aggressive Banshee is in processing new files. Has anyone else noticed a similar pattern?

---

### Post by screaminj3sus on 2011-04-22
> **VinDSL said:**
> For the sake of discussion...

Banshee has worked well enough for me.  It's definitely a step up from Rhythmbox, in form and functionality.  

The only 'problem' I've had with Banshee has to do with incorporating it into my Conky script.  And, it's a matter of timing.

Banshee is slow to start/stop, at times, and if I don't feed wait states into Conky, Banshee will start up in 3 instances.  And, it will require 3 stabs to get it to shut down.  Other than that, it works fine.

This, of course, is a 'problem' with Banshee and Conky not playing well together.  One, or the other, usually ends up with a black eye or bloody nose.  :)

With Rhythmbox, you can specify -nostart, on the command line, in scripts, and so forth.  This allows Conky to 'look' at the player's status, without actually opening a new instance of the program.

Banshee has such no matching feature, and this is the source of my 'problem'.  When things are finalized, I'll need to create a suitable workaround, but it certainly would make life easier if the devs would simply add a -nostart type feature to its CLI.

Anyway...

As far as mem & cpu are concerned, Banshee is as well behaved as any player that I've used.

Here's a screenie:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-22-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-apr-2011.png")[/INDENT]


I would post a 'top', but I find 'system monitor' more visually pleasing.

What I do is setup the 'system monitor' prefs to mimic 'top'.

IMO, all that matters is 'resident memory', e.g. ram usage (especially on this 1 GB machine).

As you can see, Banshee is using 86.7 MB ram and 4% cpu - a mere pittance of the limited resources on this machine.

If Banshee is using 100% of your resources, I would start looking elsewhere for the answer - perhaps your sound card drivers, et cetera.   ;)
What theme is that?

---

### Post by VinDSL on 2011-04-22
> **screaminj3sus said:**
> What theme is that?
Oh, my!  Let's see...

I'm always playing around with the look n' feel of Ubuntu.  :)


**Dependencies:**
[INDENT]Equinox-Theme Engine for GTK+ 2.x
Official Themes for Equinox GTK Engine
Faenza Icon Theme
Faenza F-Dark Icon Theme
Faenza F-Dark Color Icon Theme
Faenza F-Dark Gnome Icon Theme
Faenza-Dark Extras
Faenza Icons Mono
Faenza Color Meta Package
[/INDENT]


**Custom Theme Settings:**
[INDENT]Controls:  Equinox Evolution Dawn
Colors:  Default
Windows Border:  Ambiance (Ubuntu)
Icons:  F-Darkest-Color-One-Black-Gnome
Pointer:  DMZ (Black)[/INDENT]

**CCSM:**
[INDENT]Image Loading:  Uncheck all (defeats top panel Drop Shadow shading)
[/INDENT]


**Ubuntu Unity Plugin (CCSM):**
[INDENT]Hide Launcher:  Never
Backlight Mode:  Backlight Always Off
Panel Opacity:  0.0000
Launcher icon size:  32[/INDENT]

**Widgets on right-side (combination of):**
[INDENT]Conky
conkyForecast
Lua[/INDENT]

Er...


I *think* that's about it...  :D

---

### Post by PaulW2U on 2011-04-23
> **kswenson said:**
> I'm using Banshee for the first time with 11.4 beta2...
   what a disaster.

There are so many bugs I almost can't isolate one to report on launchpad!
Are others having this issue?
Well at least you got it to run!

On a brand new Natty installation using today's daily build banshee was one of the first applications that I tried. It closed within two seconds of opening. I also tried a build from the banshee ppa, same again.

So I filed a bug report, [https://bugs.launchpad.net/bugs/769545](https://bugs.launchpad.net/bugs/769545) but as banshee hasn't worked for me on 10.04, 10.10 and now 11.04 I doubt I'll see any progress. Strange how banshee works on other distributions though. :confused:

[COLOR="Navy"]Edit: It seems the bug is not in banshee but a one year old bug with many duplicates to confirm it should have been fixed by now. See [https://bugs.launchpad.net/bugs/529714](https://bugs.launchpad.net/bugs/529714)[/COLOR]

---

