---
title: "XBMC Breaks MCE Remote that worked inside Ubuntu"
date: 2012-08-31
forum: Multimedia Software
---

### Post by TheFu on 2012-08-31
[SIZE=3]**Short version:**[/SIZE]
* MCEUSB remote works - all keys, back, ok, arrows, suspend/power, enter ... play video, play music .. .all work
* **Install XBMC and the remote only partially works inside** it. Basically, **just the arrows.**
* Outside XBMC, the remote sends expected keyboard commands and those work as expected for video, images and music playback controls.

[SIZE=3]**Longer version:**[/SIZE]

A little background.
Built a new XBMC box a few weeks ago using an E350N MB and E350d APU with ATI 6310 GPU.
* Installed fresh Ubuntu 12.04.1 desktop x32 - fully patched as of today.
* Installed all my favorite tools - ntp, ssh, fail2ban, VLC,  gqview and replaced all the default apps with those as makes sense.
* Installed ATI proprietary GPU drivers to get hardware codec support for video and audio. Worked fantastically on 1080i content and everything lower in VLC.  Totem choked - no HW decoding support.  Oh - the "post release" ATI drivers always failed to install. Had to drop back to the older version - well, I assume they are older - can't tell in the GUI (Driver updates) which versions is which because the GUI is dumbed down too much. Release numbers or even dates would help folks!
* Plugged in a USB MCE remote and tested.
** left, right, up, down, OK, enter, back, suspend/power, de-suspend **all worked. **I was shocked, but happy.
** Pressing the green W-button starts Rhythmbox - unexpected, but nice.
* Installed XBMC
* Setup a few video sources local and network with all the different file types -  avi, xvid, flv, mkv, mp4, mpeg2, ... wmv ... 
* Tested using the MCEUSB remote and only the enter and arrow keys work.
**** "OK", power/suspend, "Back" keys do not work!!!!!**  All the other keys probably don't work either, but those 3 are hit more than any others.

**The difference that broke the remote is XBMC, nothing else.**  I specifically did not load lirc this time because in the install last week, I did and that broke the suspect/power key.  Last week, tried following a guide for the same APU, but a different MB.  Suspend/power didn't work, but most other keys did. The suspend/power key would try to do something and get stuck somewhere that  needed a cntl-C to continue. That isn't any good for an XBMC box without a keyboard connected.

This install is into a fresh different partition. No cross contamination.

a) is there a way to get XBMC to stop screwing around with the keys?
or
b) does anyone have a working keymap for mceusb remotes that xbmc will honor?

It would be really nice if the remote worked well in and out of XBMC.

Thanks in advance.

---

### Post by TheFu on 2012-09-02
**Solved.  **Looks like **User Error.**

Started over with lirc.
* purged it
* reinstalled
All the buttons are working now.  Must have been user error.

I'm pretty certain that the text menu system selected the remote device after the one I intended the first time. The 2nd time, it just worked.  Of course, this was after I'd tried to manually correct the errors in the lircd.conf myself further complicating things.

Just to be clear, every button is working as expected now just by 
a) purging the lirc package
b) reinstalling and 
c) reconfiguring lirc.  

I probably could have just used **dpkg-reconfigure** and been done.

---

