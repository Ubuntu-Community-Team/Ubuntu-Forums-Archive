---
title: "Suspend Xscreensaver when invoking XBMC (Kodi) from MythTV"
date: 2015-01-24
forum: Mythbuntu
---

### Post by philled on 2015-01-24
I have got Kodi v14 (was XBMC) installed on my MythTV v0.27 frontend. When watching a video in Kodi the screensaver kicks in and blanks the screen, and the way to unblank it is to press a key on the keyboard (IR remote won't unblank it). This probably happens because the MythTV frontend has Xscreensaver enabled and it gets "pinged" every so often by MythTV frontend to ensure it doesn't kick in when watching a recording. When watching something on Kodi that "ping" doesn't happen.

I invoke Kodi from library.xml as follows (which I got from [http://ubuntuforums.org/showthread.php?t=1919731](http://ubuntuforums.org/showthread.php?t=1919731)):

   <button>[INDENT][FONT=courier new]<type>Kodi</type>
        <text>Kodi</text>
        <description>Launch Kodi</description>
        <action>EXEC /usr/bin/xbmc</action>
    [/FONT][/INDENT]
[FONT=courier new]</button>[/FONT]

I would have thought this was a very common issue with a simple solution, and I've found other people with the same issue (eg [http://www.serkey.com/ubuntu-script-to-disable-xscreensaver-momentarily-bddpje.html](http://www.serkey.com/ubuntu-script-to-disable-xscreensaver-momentarily-bddpje.html)) but, sadly, no solution.

Is there a way of putting Xscreensaver on hold when invoking Kodi, and then re-enabling it when exiting Kodi back to MythTV frontend?

---

### Post by Dennis N on 2015-01-24
It is easy to disable xscreensaver. Open the xscreensaver settings dialog, and in the mode selection box, select "Disable screen saver". Then it will not be the cause of any screen blanking. But, screen blanking can also be instigated by the power manager, or the DPMS system for the monitor. DPMS = Display Power Management System.

Read about DPMS: 

[http://www.computerhope.com/jargon/d/dpms.htm](http://www.computerhope.com/jargon/d/dpms.htm)

---

### Post by philled on 2015-01-24
> **Dennis N said:**
> It is easy to disable xscreensaver. Open the xscreensaver settings dialog, and in the mode selection box, select "Disable screen saver". Then it will not be the cause of any screen blanking.
Sorry, perhaps I didn't explain the problem correctly. I'm looking for a way of doing this seamlessly with no user intervention. This is a MythTV box so people shouldn't need to use keyboards or mice to do any of this.

---

### Post by Dennis N on 2015-01-24
Why don't you uninstall any screensavers? Do you need them? 
There are other screensavers that might be present too, besides xscreensaver: light locker, and gnome screensaver come to mind. I don't know which Mythbuntu might have installed.

---

### Post by lionsnob on 2015-02-27
Hi -

I'm also having this issue. Anyone come up with a solution? Kodi fades to black after ten minutes regardless of LIRC input.

---

### Post by Lester_Burnham on 2015-02-28
At the desktop select Applications>Settings>Screensaver. Change Mode: "blank screen only" to Disabled.

---

### Post by lionsnob on 2015-03-04
> **Lester_Burnham said:**
> At the desktop select Applications>Settings>Screensaver. Change Mode: "blank screen only" to Disabled.

Thanks Lester - but wouldn't that disable the screensaver? I believe the OP and I are both looking to keep screensaver settings as-is and use Kodi.

---

### Post by uteck on 2015-03-05
I found some posts that talk about using the --hearbeat-cmd flag, but Kodi does not support it.  Found a script at the Arch wiki that says it will stop Xscreensaver while Kodi is runnng;
[https://aur.archlinux.org/packages/kodi-prevent-xscreensaver/](https://aur.archlinux.org/packages/kodi-prevent-xscreensaver/)

---

### Post by Lester_Burnham on 2015-03-05
Hi,
I'm pretty sure Kodi dims the display still even with the screensaver disabled at the desktop.

Give it a try and change it back if no good.

Lester

---

### Post by uteck on 2015-03-06
Lester,
That is the built in screensaver in Kodi, Xscreensaver is a separate app designed for desktop use.  So in this case it will kick on while watching something because it is not detecting any activity and is not aware that a video is playing.

---

### Post by khPWXxF on 2015-03-06
So you want Mythtv and Kodi to screensave their respective menus but not media?
 
Mythtv should do that itself.
 
Does a ‘vanilla’ Kodi screensave properly or is the problem that starting via Myth ‘poisons’ the Kodi screensave mechanisms?
 
Have you raised this issue with the Kodi community? 
 
Would it all work if you trigged Mythtv from Kodi (can you?) or had an initial script which chose either Myth or Kodi?
 
If you google ‘kodi screensaver inhibit’ you’ll find this:
 
[http://www.mstuttle.com/2010/07/08/disable-ubuntu-screensaver-when-xbmc-starts/](http://www.mstuttle.com/2010/07/08/disable-ubuntu-screensaver-when-xbmc-starts/)
 
Does that help?
 
Phil

---

### Post by luwrust on 2015-06-11
There is also an add-on - [http://sourceforge.net/projects/osscreensavermanager/](http://sourceforge.net/projects/osscreensavermanager/) .  Just install it to Kodi and linux screen saver will be automatically disabled when Kodi is started and re-enabled upon exit.

---

