---
title: "Will they eventually have live iso for nvidia users?"
date: 2010-11-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by efflandt on 2010-11-26
I just got into natty with Nov 23 iso.  The sources.list change and dist-upgrade from maverick didn't work due to dependency conflicts (maybe only works with fresh maverick with no updates).  This is the earliest I have gotten into a development version, so I am not expecting everything to be sorted out yet, months before release.

The first thing I noticed booting the natty iso live from usb stick (which I have not seen mentioned here) is that **nothing in X works with default nouveau driver**, all the panels and applets crash leaving you with just an empty background image (not sure how to report that to launchpad).  And you cannot install nvidia drivers using the iso, even with persistent data.  The iso does work fine with Intel video and even old legacy ATI X1300 desktop (without even using nomodeset).

Install works with nouveau from the iso, so I was able to do a regular install from one usb stick to another.  Then I booted recovery mode to **sudo apt-get install nvidia-common**, but did not realize I also needed to **sudo nvidia-xconfig**.  There were still some issues with X, probably due to apt related compressed package processes choking the system, which have since been fixed with updates to some apt packages (not easy to find in Synaptic with Quick search stuck on Reindexing).  Maybe the apt glitch explains why regular installation took so long.  Everything seems to be stable now (I am posting from it).

Since my nvidia GT 430 is so new that lspci does not even show its model, I did some peeks and vbios dumps sent to nouveau developers per [http://ubuntuforums.org/showthread.php?t=1595037](http://ubuntuforums.org/showthread.php?t=1595037) which hopefully will help them advance nouveau.

I have not looked at all of the posts of people having trouble booting the live maverick iso, because I have not had that problem.  And I know that would be a low priority at this point for natty.  But eventually defaults need to be considered, and whether booting to a blank or text screen and not knowing what to do would discourage new users.  It is easier to add something to a working system.

---

### Post by kahping on 2010-11-26
Not sure what you're asking here. Are you asking if a stable working nouveau will be included with Natty, or that the proprietary nVidia drivers will?

Updates to the proprietary drivers depends on the company (nVidia, in this case) so it's more a matter of waiting for nVidia to release a version that works on Natty. It's also proprietary which means it's not freely redistributable and so won't be a part of the .iso. That's why Ubuntu has Jockey: to optionally download and install proprietary drivers for you after you've installed Ubuntu

As for nouveau, it's probably too early in development so things'll get better later.

**Note:** I don't use nVidia so please take my words with a pinch of salt. ;)

---

### Post by cariboo on 2010-11-26
The only system I've having any strangeness with, has an intel graphics chipset. 4 other systems with different cards, 6600GT, 8400GS, 9400GT and 210GT, all work well with Nouveau and Nvidia drivers.  The system with the 210GT does lock up on occasion when using the nouveau drivers, with the latest nvidia-current (260.19.21) drivers, it's rock solid.

---

### Post by autocrosser on 2010-11-26
Hmmm--granted I use a older set of cards (9800GT pair) in SLI--all I need to do is the nomodeset & I'm in even with the new iso......I've been planning to update my cards this next year, so that should be interesting.......

---

### Post by VMC on 2010-11-26
> **efflandt said:**
> I just got into natty with Nov 23 iso.  The sources.list change and dist-upgrade from maverick didn't work due to dependency conflicts (maybe only works with fresh maverick with no updates).  This is the earliest I have gotten into a development version, so I am not expecting everything to be sorted out yet, months before release.

The first thing I noticed booting the natty iso live from usb stick (which I have not seen mentioned here) is that **nothing in X works with default nouveau driver**, all the panels and applets crash leaving you with just an empty background image (not sure how to report that to launchpad).  And you cannot install nvidia drivers using the iso, even with persistent data.  The iso does work fine with Intel video and even old legacy ATI X1300 desktop (without even using nomodeset).

Install works with nouveau from the iso, so I was able to do a regular install from one usb stick to another.  Then I booted recovery mode to **sudo apt-get install nvidia-common**, but did not realize I also needed to **sudo nvidia-xconfig**.  There were still some issues with X, probably due to apt related compressed package processes choking the system, which have since been fixed with updates to some apt packages (not easy to find in Synaptic with Quick search stuck on Reindexing).  Maybe the apt glitch explains why regular installation took so long.  Everything seems to be stable now (I am posting from it).

Since my nvidia GT 430 is so new that lspci does not even show its model, I did some peeks and vbios dumps sent to nouveau developers per [http://ubuntuforums.org/showthread.php?t=1595037](http://ubuntuforums.org/showthread.php?t=1595037) which hopefully will help them advance nouveau.

I have not looked at all of the posts of people having trouble booting the live maverick iso, because I have not had that problem.  And I know that would be a low priority at this point for natty.  But eventually defaults need to be considered, and whether booting to a blank or text screen and not knowing what to do would discourage new users.  It is easier to add something to a working system.

Todays live-daily (11/26) was the first time I got a panel. Its very tiny and almost hidden. You have to move your mouse all the way to the top. Even so, Compiz keeps crashing as before.

Here's one trick to get a simi normal desktop. After you select Try ubuntu, and you get the urple screen, do a C+A+F1 then ```
sudo service gdm restart
```. It should bring you back to the selection once again. Then select Try Ubuntu once more. This time you should have a desktop. Strange but it at least works. The problem is Compiz. See if this [bug repor]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677506")t fits you situation

---

### Post by sparker256 on 2010-11-27
With todays daily live build (11-27-10) I made a new live usb and it booted to the desktop and everything looked fine except that the time settings button for clock preferences was greyed out. I am running a 9800GT nvidia card so it is starting to look it is almost ready for me to install. I was not going to install until the daily live was working as well as I have seen on previous versions.

Bill

---

### Post by efflandt on 2010-11-27
With nouveau it was a compiz issue.  That is what crashed on the Nov 23 iso and immediately after installation.  I could not follow VMC's compiz bug link, because even while logged into lauchpad in it says: "Sorry, you don't have permission to access this page."

Even with nvidia drivers if I try to enable Normal visual effects, it works fine that session, but something "Unknown" does not close properly when logging out or shutting down, and next boot the panels are there, but all applets crash.  Most of them come up when clicking the dialogs to restart them except sound and network.  At that point visual effects have reverted to None and clicking anything on that locks up X.  But restarting gdm from a console brings everything back to normal like it never happened and is completely stable as long as I leave desktop effects set to None. Would this be relevant:

```
Nov 25 23:09:46 localhost kernel: [ 3312.943818] polkit-gnome-au[1445]: segfault at 68 ip 00007f04df5318a8 sp 00007fff6f4c6120 error 4 in libglib-2.0.so.0.2703.0[7f04df50a000+e8000]
Nov 26 04:08:32 localhost kernel: [  274.103710] polkit-gnome-au[1435]: segfault at 48 ip 00007fc903bf88a8 sp 00007ffffa02da80 error 4 in libglib-2.0.so.0.2703.0[7fc903bd1000+e8000]
Nov 26 21:40:05 localhost kernel: [ 6000.026458] polkit-gnome-au[2109]: segfault at 28 ip 00007fd98cac48a8 sp 00007fffc6d0ffb0 error 4 in libglib-2.0.so.0.2703.0[7fd98ca9d000+e8000]
```I'll try zsync and see how the latest iso is working.

PS: Tried the Nov 27 iso and it mostly works except for a minor issue with applets in upper right. GNOME_FastUserSwitchApplet and GNOME_IndicatorApplet crash when booted live.  But if you go to a console and **sudo restart gdm**, you can "Try Ubuntu" again and everything comes up normally.  However, after rebooting with persistent data those errors kept coming up regardless of restarting gdm.  If I selected to remove those from the panel, no errors on subsequent boots, but I only ended up with nm applet and clock in upper right panel (no sound, shutdown, etc).  Since I loop mounted casper-rw from another system and removed everything in /home/ubuntu/.gconf/apps/panel/ everything seems to come up perfect on a couple of reboots.  So it is almost there, just something about the sequence of events starting gdm on initial boot.  Anyway natty iso is working with nouveau now even with my unrecognized GT 430:

```
01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device 0828
    ---
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
```

---

### Post by VMC on 2010-11-27
Success! Todays [daily-live]("http://cdimage.ubuntu.com/daily-live/current/") 11/27/2010 worked. Finally.

Edit: I missed Sparker's reply. I'm using  GeFore 6150SE nForce 430.

---

