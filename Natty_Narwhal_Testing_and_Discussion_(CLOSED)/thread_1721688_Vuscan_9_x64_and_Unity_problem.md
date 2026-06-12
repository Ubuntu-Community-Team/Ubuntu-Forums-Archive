---
title: "Vuscan 9 x64 and Unity problem"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by myoldhouse on 2011-04-04
I have a test system that I just upgraded to Ubuntu 11.04 B1. General system specs are AMD Phenom II X4 940, 8 Gigs of Ram and an Nvidia GeForce 7900GS video card.

I did an online upgrade from 10.10 x64 to 11.04 x64 beta 1 without any particular issues and all my installed programs seemed to transfer OK. I did have some issues with Google Earth but I sorted those out quickly and easily enough.

I use Ed Hamrick's scanner program, VueScan Pro, for a flatbed scanner, an Epson Perfection 4490 PHOTO. Vuescan is currently at version 9.0.28, although I have seen the problems described below in 9.0.26 and 9.0.27 as well.

In order to get the scanner program to work before a native x64 bit version was released (the version 8 series was only x32), I had to run some pretty peculiar kludges swapping out 32 and 64 bit library files on the fly as the program was loading, but it worked. Since version 9 of Vuescan, there is a native x64 version that was compiled under Ubuntu 10.10 that I have been using and it runs without any of the workarounds of the old version 8 under Ubuntu 10.10.

However, something strange is happening now with Ubuntu 11.04 B1. With the Unity shell running, Vuescan 9 starts but does not display an icon for itself in the left hand Launcher bar. It queries the scanner and then just stops running (enters sleep mode). I can keep relaunching Vuescan and it just creates more zombie processes. It doesn't open its GUI window at all. I get the same symptoms if I log in to 11.04 using Ubuntu Classic or Ubuntu Classic without Compiz. But, if I log into 11.04 in Ubuntu Safe Mode, Vuescan works correctly without any problems at all.

Vuescan keeps a log and looking at this log shows no crashes or errors when it hangs. In fact I could not see any difference between the Vuescan log when it failed to open versus when it opened OK in Safe Mode log in.

It seems that something has changed 'under the hood', so to speak, with the way Ubuntu 11.04 expects to get calls to open a GUI. The vuescan program only has three files in total that it installs - an executable named "vuescan" and two support libraries named "vuescan.8ba" and "vuescan.ds" that are in the same directory as the executable. No other files are installed anywhere in the system, it is simplicity itself.

I created a desktop launcher for the program but that made no difference to the outcome except that I could drag the desktop launcher to the Unity Launch bar and have it stick there. Launching from a terminal also produces the same result. Only a Safe Mode log in allows Vuescan to run properly in Ubuntu 11.04.

So, what might Ubuntu 11.04 be looking for from this program (or conversly, what might vuescan be looking for from 11.04)? What is disabled when Ubuntu 11.04 is logged into using Safe Mode?

Any thoughts or suggestions?

Thanks.

---

### Post by VMC on 2011-04-04
I just tried my version of vuescan 9.0.20 and it works perfectly. All you need is that one vuescan file in order to use it.

---

### Post by myoldhouse on 2011-04-04
Are you using the Nvidia proprietary drivers?

I don't have access to any versions of Vuescan earlier than 9.0.26 so I can't test version 9.0.20.

I wonder if some required library for Vuescan is missing when Unity is active. It is strange.

---

### Post by myoldhouse on 2011-04-07
OK. I have found the culprit that causes Vuescan 9.0.xx to not draw its GUI under Unity. If 'Window Decorations' is turned on in Compiz when Vuescan 9.0.xx (64 bit) tries to start, it will fail to launch its GUI window. If I turn 'Window Decorations' off in Compiz, Vuescan 9.0.xx will start and establish its GUI window, without borders of course. I can then turn 'Window Decorations' back on in Compiz and Vuescan 9.0.xx will continue to function normally with proper window decorations. So, as a clumsy workaround, this disabling and re-enabling of 'Window Decorations' will work. I have tested the workaround with all 64 bit versions of Vuescan from 9.0.26 to 9.0.29.

Since the Vuescan 9.0.xx (64 bit) series is compiled by the author (Ed Hamrick) using Ubuntu 10.10, I suspect that the bug that prevents Vuescan from launching is in Natty and the way it has implemented 'Window Decorations' and not in Vuescan itself. I'll file a bug report with the Natty developers.

---

### Post by ronparent on 2011-04-07
I've experienced the same thing on and off as I've iterated thru the various pre-launch releases. Right now Vuescan is working perfectly on my main system an updated 11.04 beta with ATI hd5770 graphics. I currently can't start it in another system with nvidia graphics. Right now I am just sitting tight because who knows what we will see by the RC. I had a simular problem during testing of 10.10 and wrote Ed Hammick about it when it didn't work on the RC (he was upset and expressed some reluctance to continually be dealing with turbulence in Ubuntu behavior). It was working at the final release of 10.10!

I think you are right that something in Natty (or perhaps changes in X) is the culprit. But since Natty is still a work in progress it may be premature to raise the alarm. I think you have some good insight regarding the interaction with compiz and it is probably worth a bug report. I'll be happy to verify the behavior.

---

### Post by VMC on 2011-04-07
Your right, it doesn't work. Wonder what was the difference between the last install and this one. I also can't run the previous versions.

---

### Post by ronparent on 2011-04-08
Ha, ha - changed your tune since last night. :lolflag:

The behavior changes from update to update. I can understand Ed Hammick's frustration - you don't know what to expect from day to day!

I have simular problems to various degrees trying to use FakeRAID on my system since 7.04. You don't know what to expect from release to release. ):P

---

### Post by ronparent on 2011-04-08
Oh,oh. I just ran the update manager with 273 updates. Vuescan still won't load on my system with nvidia graphics. But now I can't log off with Vuescan sleeping - **everything** locks up (fortunately ctrl-alt-backspace still works). Really anoying. But who knows - tommorrow..............

Edit: Tried again on system with ATI graphics. Runs fine on install with default drivers. Won't run on install with ATI proprietary driver. Compiz is not available on any of my natty installs.

---

### Post by myoldhouse on 2011-04-08
> **VMC said:**
> Your right, it doesn't work. Wonder what was the difference between the last install and this one. I also can't run the previous versions.

Try turning 'Window Decorations' OFF in the Compiz Configuration Settings Manager and see if it starts OK after that.

---

### Post by ronparent on 2011-04-10
myoldhouse: Verified. Turning off windows decoration allows Vuescan to display after start.

---

### Post by myoldhouse on 2011-04-13
OK, here is another workaround, although not very good.  :neutral:

Log in to an Ubuntu Classic session. Open the Compiz Configuration Settings Manager (CCSM) and select the Window Decoration plugin. Replace the "Command", which defaults to '/usr/bin/compiz-decorator' with '/usr/bin/metacity --replace'

Close the CCSM, log out then log in again to the Ubuntu Classic session. Vuescan 64bit (now at version 9.0.31) should start normally. This is now pretty much the same as the Maverick (Ubu 10.10) desktop.

I think the only way to actually be able to use Vuescan version 9.x.xx in the full blown Unity interface of Ubu 11.04 would be to put together a launch script that turned Compiz Window Decorations OFF, launched Vuescan, then turned Compiz Window Decorations ON again. This does work manually. The script would probably have to pass the appropriate messages to Compiz via the Dbus, but I don't know how to do this in a script.  :confused:

---

### Post by ronparent on 2011-04-14
I can start Vuescan nromally in natty without proprietary drivers. I need a workaround in both natty installs with proprietary drivers (ATI, nVidia).

---

### Post by VMC on 2011-04-21
VueScan x64 9.0.28 works on Kubuntu Natty. So its obviously a Unity/Compiz issue. Wanted to make sure its not distro related.

---

### Post by myoldhouse on 2011-04-22
Thanks for that confirmation. I'm going to wait for the final release of Natty before I file a bug on this or raise the issue with the author Ed Hamrick.
:KS

I am beginning to think that Vuescan is the culprit. Earlier 32 bit versions of Vuescan (v 8.6.66 and v 8.5.41) from the Vuescan website work OK in Unity with no window decoration or start up issues. Vuescan 9.0.xx (32bit) throws out all kinds of errors and Vuescan 9.0.xx (64bit) has the window decoration problem.

Update - November 7, 2011:

Vuescan 9.0.61 x64 (released Nov 3, 2011) finally fixed this bug with Epson scanners, Unity, Compiz and window decorations on x64 systems. It was a problem with Vuescan not Unity as far as I can tell.

---

