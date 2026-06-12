---
title: "Banshee Won't Shut Down Properly"
date: 2011-05-26
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2011-05-26
Hello,

Whenever I close Banshee by clicking the 'x' in the upper left-hand corner; the player moves to the next track and keeps on playing, just without a GUI.  I had this problem in Rhythmbox as well.  I'm also having the same problem with Software Center.

It certainly looks like the UI/Window Manager is not always sending the application 'kill' signal to the running process.  I'm currently using Gnome 2.x / Ubuntu Classic.  I haven't tried this in Unity yet; but I suspect I will have the same problems there as well.

Has anyone else had this problem; and is there a work-around???





Thanks Hannibal

---

### Post by beew on 2011-05-26
Yeah, that is an odd bug (design?), if you pause first and click the x it will shut down.

It used to be that you can click quit in the tray icon but there is no tray icon in Unity unless you whitelist the application.

---

### Post by coljohnhannibalsmith on 2011-05-29
> **beew said:**
> Yeah, that is an odd bug (design?), if you pause first and click the x it will shut down.

It used to be that you can click quit in the tray icon but there is no tray icon in Unity unless you whitelist the application.

Thanks for your reply,

Here's what I guess is happening.  I think, based on the behavior I've observed, that the UI/Window manager 'is' probably sending "a" kill signal, but not the correct one with a high enough priority; so that the kill signal that gets sent get's interrupted by a process with a higher priority, and then just goes to sleep indefinitely.  I think a way of checking this would be try it in a variety of window managers.  That would either isolate the problem to a specific window manager; or point to the Linux kernel.  I suspect this is not an Ubuntu problem per se...  I've also read that historically the Linux kernel has been developed without the benefit of a versioning control system.  I don't know if this is still the case; but if it is, it's a disaster waiting to happen....




Hannibal

---

### Post by pbhill on 2011-11-12
I have been noticing a higher level of CPU activity than normal and I attribute it to Banshee running in the background. I have to "kill" Banshee in order to stop it.

---

### Post by achelis on 2012-12-12
Did any of you find a fix for this ?

Or do I have to launch a terminal and do killall banshee everytime I want to close it :/

---

### Post by coljohnhannibalsmith on 2013-03-14
Rythmbox has the same problem.

Hannibal

---

### Post by mc4man on 2013-03-14
This threads a bit old, probably should of been closed.
Anyway this isn't an issue, purely design.

If you close the window (X) while playing, RB, Banshee window will exit but the app will continue on, accessible  from thru sound menu
If you close the window (X) while paused the they will  quit

To quit while playing only "Quit" from the app menu will actually do so (or Ctrl+q
"Quit" from the unity quicklist is mis-named, should be "Exit"

---

### Post by coljohnhannibalsmith on 2013-03-16
Thanks,

I think I understand now.

Hannibal

---

### Post by oldos2er on 2013-03-16
Old thread closed. Anyone who still has questions, please start a new thread.

---

