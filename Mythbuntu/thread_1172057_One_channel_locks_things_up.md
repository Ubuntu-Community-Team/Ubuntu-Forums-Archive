---
title: "One channel locks things up"
date: 2009-05-28
forum: Mythbuntu
---

### Post by iitywygms on 2009-05-28
This one is confusing me.  If I tune to channel 4, then press guide, the screen will flicker for a second, then continue to play tv.  But, I can't do anything else from that point on.  No changing channel, no exit, nothing.  I have let it sit for 10 minutes and nothing happens.  The tv screen still plays like everything is normal, but no keyboard or remote control will affect anything.  I have to kill it and restart mythfrontend to do anything.  If I don't use the guide, everything is fine.
I have tried different playback profiles.  Any other suggestions?

Mythfrontendlog shows nothing.
This is the last few lines before I kill it.
2009-05-27 22:41:31.976 Realtime priority would require SUID as root.
2009-05-27 22:41:31.980 New DB connection, total: 4
2009-05-27 22:41:31.981 Connected to database 'mythconverg' at host: 192.168.2.4
2009-05-27 22:41:32.080 Video timing method: USleep with busy wait
2009-05-27 22:41:32.250 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-27 22:41:32.537 AFD: Opened codec 0x85e6560, id(MPEG2VIDEO) type(Video)
2009-05-27 22:41:32.537 AFD: codec AC3 has 2 channels
2009-05-27 22:41:32.538 AFD: Opened codec 0x85e3d80, id(AC3) type(Audio)
2009-05-27 22:41:32.542 Opening audio device 'default'. ch 6(2) sr 48000
2009-05-27 22:41:32.542 Opening ALSA audio device 'default'.
2009-05-27 22:41:32.549 NVP: Enabling Audio
2009-05-27 22:41:32.556 Opening audio device 'default'. ch 2(2) sr 48000
2009-05-27 22:41:32.556 Opening ALSA audio device 'default'.
2009-05-27 22:41:47.195 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml

---

### Post by klc5555 on 2009-05-28
> **iitywygms said:**
>   I have to kill it and restart mythfrontend to do anything.  If I don't use the guide, everything is fine.


"Kill it"? Kill just X (and not a hard reset)? With ctl-alt-backspace or SSH from another machine? If ctl-alt-backspace, then your keyboard is definitely alive. If your keyboard is alive, then it might be that a submerged window has opened underneath mythtv that has arrogated focus to itself from mythfrontend, and all your keystrokes are going to this submerged window. ctl-esc might therefore surface the xfce4 taskbar and you could foreground the submerged window and find out what it's about.  

I don't have your precise problem, but in 9.04 I do get a submerged Update Mangler window occasionally seizing focus from the frontend, which window I then have to foreground and close.

If you have to SSH or hit the Big Red Button to kill it, then none of this applies to you, and something else is going on.

---

### Post by iitywygms on 2009-05-28
By kill it I mean I ssh to it and run top to get the process number. Then run kill that number.
If it matters, xorg is pegged at this time, but I see xorg maxed out on some other channels that do not have this issue.

---

### Post by klc5555 on 2009-05-28
> **iitywygms said:**
> By kill it I mean I ssh to it and run top to get the process number. Then run kill that number.
If it matters, xorg is pegged at this time, but I see xorg maxed out on some other channels that do not have this issue.

Then you might want to test whether you've got a submerged window swallowing up your keystrokes/remote-clicks. If all of X were locking up, I'd expect the playback itself (or at least the video half of it) to freeze.

---

### Post by iitywygms on 2009-05-28
Sounds reasonable.  It does seem like something is opening, but what I don,t know.
How would I go about this?  When I look at top, I see nothing unusual.  And I have no control of myth at this time?

---

### Post by klc5555 on 2009-05-28
> **iitywygms said:**
> Sounds reasonable.  It does seem like something is opening, but what I don,t know.
How would I go about this?  When I look at top, I see nothing unusual.  And I have no control of myth at this time?

Try some of the usual X keyboard shortcuts: maybe ctl-esc from the keyboard, to see if you can access the desktop toolbar; maybe alt-tab to surface a submerged window. Maybe set the frontend up once to run in a window, rather rhan fullscreen, and see whether the guide on ch.4 spawns a second window or just freezes the first. There must be other possibilities.

---

### Post by iitywygms on 2009-05-29
> **klc5555 said:**
> Try some of the usual X keyboard shortcuts: maybe ctl-esc from the keyboard, to see if you can access the desktop toolbar; maybe alt-tab to surface a submerged window. Maybe set the frontend up once to run in a window, rather rhan fullscreen, and see whether the guide on ch.4 spawns a second window or just freezes the first. There must be other possibilities.

Okay I tried as you suggested.  I ran in a windowed mode, and went to that channel.  As soon as I hit guide, the mouse would not respond, the keyboard would not respond.  I could see the mouse previously moving around in the menu bar before I did this.  Trying cntrl esc or other things did nothing.  The tv show kept playing like everything was good.
So I go to my laptop, ssh to it and kill the frontend.  I still see nothing in the error logs???
I am really stumped on this one.

---

### Post by laffinet on 2009-05-29
Maybe run "top" when this happens and see if there are any processes that use up a lot of resources ?

---

### Post by iitywygms on 2009-05-29
I have and xorg is the only thing I see.  It uses whatever is left from mythfrontend.  xorg hogs cpu cycles on other channels but nothing ever locks up except on this one channel.
??

---

### Post by klc5555 on 2009-05-29
> **iitywygms said:**
> I have and xorg is the only thing I see.  It uses whatever is left from mythfrontend.  xorg hogs cpu cycles on other channels but nothing ever locks up except on this one channel.
??

Wow, looks like that channel+guide really is locking up X. I've never seen anything like that before either.

You've already tried different playback profiles; the only additional thing that I can think of to try at the moment would be different versions of the guide --maybe the lowest CPU "Eco" version-- and see whether there's a variant of the guide that doesn't lock everything up when invoked on that channel.

But it's a stumper.

---

### Post by iitywygms on 2009-05-29
I have tried the low eco version.  No joy.
Last night when it did lock, after about five minutes it did return to normal.  I did nothing different.  The logs showed nothing significant.

---

### Post by iitywygms on 2009-06-02
I discovered that turning off sync to v blank in nvidi-settings will fix the hanging guide issue.  Problem with this fix is that I get lots of screen tearing while watching fast moving scenes on tv.
If anyone knows of a fix for the tearing that does not require sync to vblank, please let me know.

---

