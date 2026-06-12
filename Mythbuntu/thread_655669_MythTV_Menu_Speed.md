---
title: "MythTV Menu Speed"
date: 2008-01-01
forum: Mythbuntu
---

### Post by Tteddo on 2008-01-01
A few months ago I built a new MythTV box, 2800XP 1 Gig ram, etc w/MythBuntu, that was an upgrade from my old machine from 2004 1700XP 1Gig ram, Fedora Core 4. The old one ran ok, I just decided to redo it because I had a nicer video card to put in it and the old machine didn't have the right AGP slot.
Well, the new machine, while I am in the menu system of mythtv is really slow most of time. For instance just navigating from "Watch TV" to " Watch Recordings" by hitting the down key there is at least a 1 second delay. If I am in the recordings section picking out something to watch it is even slower.
My old machine worked fine with regards to this, was quite snappy.
I have tried renicing mythtv but it didn't seem to help. Makes no difference whether   it is doing nothing, or recording 2 shows at once, it has the same slowness. I was running KDE, and today I switched to XFCE to see if that would help and it made no difference.
Anyone have any ideas what could be going on?

Oh, and during regular playback of videos, or live TV (like CNN with the scroll on the bottom) there is no stutter at all.

---

### Post by superm1 on 2008-01-02
> **Tteddo said:**
> A few months ago I built a new MythTV box, 2800XP 1 Gig ram, etc w/MythBuntu, that was an upgrade from my old machine from 2004 1700XP 1Gig ram, Fedora Core 4. The old one ran ok, I just decided to redo it because I had a nicer video card to put in it and the old machine didn't have the right AGP slot.
Well, the new machine, while I am in the menu system of mythtv is really slow most of time. For instance just navigating from "Watch TV" to " Watch Recordings" by hitting the down key there is at least a 1 second delay. If I am in the recordings section picking out something to watch it is even slower.
My old machine worked fine with regards to this, was quite snappy.
I have tried renicing mythtv but it didn't seem to help. Makes no difference whether   it is doing nothing, or recording 2 shows at once, it has the same slowness. I was running KDE, and today I switched to XFCE to see if that would help and it made no difference.
Anyone have any ideas what could be going on?

Oh, and during regular playback of videos, or live TV (like CNN with the scroll on the bottom) there is no stutter at all.
Sounds like you have the opengl theme painter turned on without a video card that has full opengl drivers installed.

Either setup proprietary drivers, or turn off opengl theme painter.

---

### Post by Tteddo on 2008-01-02
It was running the restricted drivers, it's an ATI Radeon 9550...In making sure it was, I borked it all up and now it won't go into X (I have a custom xorg.conf dual heads, etc...). No biggie.
So, while I am fixing that, where do I find the OpenGL Theme Painter? I poked around and there is no OpenGL section in the Settings section like my other machines.
Maybe I am misunderstanding what you said.

---

### Post by superm1 on 2008-01-02
> **Tteddo said:**
> It was running the restricted drivers, it's an ATI Radeon 9550...In making sure it was, I borked it all up and now it won't go into X (I have a custom xorg.conf dual heads, etc...). No biggie.
So, while I am fixing that, where do I find the OpenGL Theme Painter? I poked around and there is no OpenGL section in the Settings section like my other machines.
Maybe I am misunderstanding what you said.
Settings->Appearance is where the theme painter option is.

---

### Post by Tteddo on 2008-01-02
Well, I got the dual head setup working again with XFCE. I don't see anything in any of the menus about OpenGL though, altho oddly the menus in Myth are working fast at the moment. It's happened before, then been slow the next day.
On my other machines (all running Gnome and Compiz) there is a menu entry under preferences called GL Desktop where you can turn that off and on, but my MythTV box doesn't have that. Not running compiz on that either.
Maybe it's not an option in XFCE?
I have the one setting in MythTV Setup where you can pick OpenGL or Qt set to Qt, but it's been set to that all along.

Is there a command that I could use to tell if OpenGL is being used?

---

### Post by .gurkburk on 2008-03-30
Im having the same problem, around 1 second lag between every reaction in the menu-system.
I simply thought that this was the way myth behaved, but if I can get that lag out the way, id love my htpc even more.
Im running a nvidia 5200 128mb, im not using the restriced drivers (using restricted drivers in regular ubuntu just resulted in black screen whatever I tried, so im not anxious to "go there").

Any ideas how to get rid of the lag?

Im not having any lag while actually playing movies or large dvd-iso's, just in the menu's.

And, sidenote: Its an miniITX-card with a builtin unichrome-card (altough im using the PCI-nvidia, and nothing is plugged in to the unichrome and bios/boot goes through pci aswell).

---

### Post by Tteddo on 2008-03-30
Actually mine has been fine since my last post. It's not a hardware issue, as my old machine was fine.
To recap, I crashed X and in the process of getting it back I also switched to XFCE. I am still running the ATI restricted drivers, and that machine is all up to date too, including all the MythTV updates.
It must have been something with the video driver I am guessing. I had the restricted drivers with a PCI nVidia on my sister's machine and it worked ok.
I know this probably doesn't help much.....

---

### Post by .gurkburk on 2008-03-30
Well, I was pretty much sure it was a drivers-issue already, which kindof sucks, as I cant get anything to work with my nvidia-card :/
I bought this card just so that I would have an "easy time" in linux, nvidia sounded good enough with some forum reading...
Well, I cant get restricted drivers to work, I have a post in the ubuntu-multimedia section about it and no-one seems to have an idea how to get nvidia-drivers to work with an 5200.
Sucks to be me I guess ;-)

And, If I go into apperance, and select opengl instead of qt, I go from 1 second lag to about 5-10 second lag (menus even load ontop of eachother, the first one taking 10-15 seconds to 'fade').

Guess its my pci-card that sucks, or the fact its an itx, with unichrome+5200PCI, something in that mix just makes linux go nuts ;-)

---

### Post by Tteddo on 2008-03-30
I don't know if this will help, but one of my machines wouldn't work at all with MythTV unless I had:
Option  "VideoOverlay" "on" 
in the device section.

I just found an old copy of my xorg.conf with 2 GeForce 4 MX 4400's if you want to take a peek at it. I had 2 monitors, one the TV, the other a workstation with 2 different displays setup.

---

