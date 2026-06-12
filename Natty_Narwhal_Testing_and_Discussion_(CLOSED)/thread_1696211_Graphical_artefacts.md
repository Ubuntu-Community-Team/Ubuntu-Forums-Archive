---
title: "Graphical artefacts"
date: 2011-02-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-02-27
Haven't found any other thread about this so I'm opening a new one.

When I open a menu I get graphical glitces, also metacity decorator is corrupted.

This issue appeared with Xorg 1.10 (from its first rc release),
it is reproducible with different graphic drivers (ati, nouveau, nvidia, gma500, vesa, vbox),
it is present with metacity and with metacity compositor, only with compiz activated is no more present.

Any suggestions?

this is a video with the problem: [http://dl.dropbox.com/u/1338581/artefacts.ogv](http://dl.dropbox.com/u/1338581/artefacts.ogv)
and bug report: [https://bugs.launchpad.net/xorg-server/+bug/726369](https://bugs.launchpad.net/xorg-server/+bug/726369)

---

### Post by PaulW2U on 2011-02-27
> **lucazade said:**
> Haven't found any other thread about this so I'm opening a new one.

When I open a menu I get graphical corruption, some artefacts.. it seems video memory is not clean or has some issue.
This issue appeared with Xorg 1.10 (from its first rc release) and it is present in a virtual machine and also using a Nvidia or Intel gfx card so it seems not related to graphic drivers.

I haven't found any bug report on Launchpad, don't know if it is related to pixman or to other component. Any suggestions?

this is a video with the problem: [http://dl.dropbox.com/u/1338581/artefacts.ogv](http://dl.dropbox.com/u/1338581/artefacts.ogv)

I'm not sure if any of this is related but on a newly booted PC, if I log in and open an application, say Opera, the main program window will for a very short time consist of "noise". By that I mean hundreds of vertical lines before the window detail is displayed. I've also been messing about converting my installation from Ubuntu to Xubuntu and back again. When I log in I see either my previous log in screen or a bright flash of colour momentarily. I'm not sure when this started happening but I don't see anything like this when using Lucid or Maverick. I'm using the Classic Desktop without effects.

Excellent video by the way. :)

---

### Post by fflopes on 2011-02-27
> **lucazade said:**
> Haven't found any other thread about this so I'm opening a new one.

When I open a menu I get graphical corruption, some artefacts.. it seems video memory is not clean or has some issue.
This issue appeared with Xorg 1.10 (from its first rc release) and it is present in a virtual machine and also using a Nvidia or Intel gfx card so it seems not related to graphic drivers.

I haven't found any bug report on Launchpad, don't know if it is related to pixman or to other component. Any suggestions?

this is a video with the problem: [http://dl.dropbox.com/u/1338581/artefacts.ogv](http://dl.dropbox.com/u/1338581/artefacts.ogv)

I have the same behaviour on my ATI HD3200.

---

### Post by macroshaft on 2011-02-27
I have been experiencing this for some time now on my laptop (Nvidia graphics) but haven't mentioned it because I have had other more pressing issues to deal with. Natty was doing so well for a while but all the problems seem to be creeping out of the woodwork since the new X stack was introduced.

---

### Post by ronacc on 2011-02-27
> **PaulW2U said:**
> I'm not sure if any of this is related but on a newly booted PC, if I log in and open an application, say Opera, the main program window will for a very short time consist of "noise". By that I mean hundreds of vertical lines before the window detail is displayed. I've also been messing about converting my installation from Ubuntu to Xubuntu and back again. When I log in I see either my previous log in screen or a bright flash of colour momentarily. I'm not sure when this started happening but I don't see anything like this when using Lucid or Maverick. I'm using the Classic Desktop without effects.

Excellent video by the way. :)

I was getting the same thing using the nouveau driver but haven't had it since the  Nvidia-current became avaiable for 1.10.rc2 xorg .

---

### Post by lucazade on 2011-02-27
At least i'm not the only one.. I'll open a bug.
I hope final xorg 1.10 release will not have this issue because is not nice!

---

### Post by lucazade on 2011-02-28
openend a new bug report:
[https://bugs.launchpad.net/xorg-server/+bug/726369](https://bugs.launchpad.net/xorg-server/+bug/726369)

I've linked the bug to Xorg server, don't know if I should link to any other projects.

---

### Post by cariboo on 2011-02-28
> **ronacc said:**
> I was getting the same thing using the nouveau driver but haven't had it since the  Nvidia-current became avaiable for 1.10.rc2 xorg .

I had the same behavior when using the nouveau drivers.

---

### Post by ronacc on 2011-02-28
something new and interesting has popped up since my last post . after updates late sunday two strange things are happening , my top panel which I have set to fully transparent comes up grey with thin white vertical stripes on bootup but if I go to properties and set the panel backgroun to "system theme" and then back to solid color it turns transparent again .  and when typing a message in the message window on this forum I cannot place the cursor with the mouse and   the arrow keys cause erratic jumps in the cursor and sometimes vertical lines to be drawn .

---

### Post by lucazade on 2011-03-22
some news... it looks like it is related to XServer with no backfill functionality

[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)
"This PPA contains a variant of the xserver with background initialization disabled. This will result in background corruption (video garbage) in windows or new objects, however it also gives a performance boost, and on some drivers the corruption isn't noticeable."

This is imho a major issue for natty release because it affects "Classical Session"

I've updated bug report: [https://bugs.launchpad.net/xorg-server/+bug/726369](https://bugs.launchpad.net/xorg-server/+bug/726369)

---

### Post by doctordruidphd on 2011-03-22
Similar issues here, running kde/kubuntu, with nvidia-current.

Most applications (including gtk) work fine, but if I run GIMP, and close an image, I get the noise and video corruption, or sometimes a crash, from which ALT-SYSRQ-REISUB is the only escape. The other thing that seems to trigger the problem is changing display colors.

---

### Post by wolfgangmcq on 2011-03-22
The same thing was happening to me, too. Try System>Preferences>Appearance, Visual Effects tab, choose none. That worked for me.

---

### Post by cariboo on 2011-03-22
> **wolfgangmcq said:**
> The same thing was happening to me, too. Try System>Preferences>Appearance, Visual Effects tab, choose none. That worked for me.

Natty doesn't have a Visual Effects tab on the Appearance Window.

---

### Post by wolfgangmcq on 2011-03-23
> **cariboo907 said:**
> Natty doesn't have a Visual Effects tab on the Appearance Window.
Oh. Karmic does. Sorry!

---

### Post by lucazade on 2011-03-25
Fix released!

Changes:
 xorg-server (2:1.10.0-0ubuntu2) natty; urgency=low
 .
   [Chase Douglas]
   * patches/500_xi2.1.patch: Process ownership properly when activating an
     async passive grab (LP: #733483)
 .
   [Bryce Harrington]
   * 217_revert_bgnonevisitwindow.patch: Cherrypick from upstream. Drops
     recent change that inhibits drawing backfill for non-bg-None windows.
     This causes a regression on -ati (at least) where menus and other
     windows display graphical corruption briefly.
     (LP: #726807)

---

