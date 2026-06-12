---
title: "X11 crashes trying twinview"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by LukeKendall on 2007-02-17
I've been reading various posts to learn how to set up a twinview system.
I'm running Ubuntu 6.10, with an nVidia Corporation NV34 GeForce FX 5200] rev 161.
I have a CRT plugged into the VGA output and a DFT plugged into the DVI output.

I managed to get it to the stage where X starts up and drives both displays; clears the background to the smooth grey; I see the mouse pointer; and then X segfaults.

I am perhaps doing something unusual: while most people seem to suggest experimenting with new xorg.conf settings by doing it from the console, it's much more convenient to have a full X session running on another virtual console, with firefox open with tabs on different forums and google search results, then make your change to xorg.conf, flip to a text console and start X on a 2nd display, e.g. with my main gnome session on display :0 I run:

startx -- :1  -dpi 100 -deferglyphs all

I wonder if this is the cause of X crashing?

I'm about to kill off the main X session and lose all my context and just run it from the console.

I'll attach my xorg.conf and log file in case they're helpful.

luke

---

### Post by LukeKendall on 2007-02-17
Well, I'm posting this from another computer.

I stopped gdm and ran startx to try the twinview xorg.conf from the console, but got the sefault and X finished.

Then I copied the old working xorg.conf back and restarted gdm and because I had the CRT plugged in, it tried to start up on the CRT - but kept crashing and trying again. After 90 seconds it gave up, with a warning.  I added a "UseDefaultMonitor" "DFT" to force it to use the LCD screen.  That didn't help either, though the screen tried to come up on the LCD.

So I stopped gdm again.

Somehow though I started X and got a stippled-grey background and a bare xterm. So I tried running wmaker - and it segfaulted!  Then I tried running gnome-wm - and it crashed too!  So I realised it wasn't X crashing, it was the window manager.

I tried running each wm in gdb (by taking local copies of the wmaker and gnome-wm scripts and replacing the "exec" at the end by a call to gdb.  That didn't work - the process seemed to kick off, but then just hang.  I couldn't do anything with gdb, and had to use Ctrl-Alt-Bksp to kill the X session).

I can only imagine some other alteration I made has lead to this sad situation.  I'm at a bit of a loss, but will look into it after I've had some sleep.

luke

---

### Post by LukeKendall on 2007-02-17
> **LukeKendall said:**
> ...

I can only imagine some other alteration I made has lead to this sad situation.  I'm at a bit of a loss, but will look into it after I've had some sleep.

luke

After some sleep, I thought there were a few possibilities:
 [LIST=1]
[*]That I'd copied some old binaries (when I brought across /usr/local from the old PC)
and adjusted PATH so that something from /usr/local/bin was running and crashing.
[*]That I'd brought across my old .profile and it was setting LD_LIBRARY_PATH inappropriately and causing the crashes.
[*]That the old fonts I'd brought across were upsetting the X server.
[/LIST]
Since I'd moved the TTF and CID directories aside to aside-TTF and aside-CID in /usr/share/X11/fonts I thought that was unlikely.

Anyway, from the bare X session with the xterm I tried running synaptic, and it crashed.  So I ran that in gdb and found that it was crashing in libfreetype.  So I ran strace -e open /usr/sbin/synaptic and found that it crashed when it tried to load a font from /usr/share/X11/fonts/aside-CID.  So I moved the directories *well* out of the way and tried again, and sure enough all was basically pretty good again.

Well, apart from me still needing to debug my new script for sourcing /etc/profile and the user's profile before the X session starts, the CRT running at 60Hz instead of 85 Hz, and the GDM login pane appearing half and half on each monitor, that is. :-)

luke

---

