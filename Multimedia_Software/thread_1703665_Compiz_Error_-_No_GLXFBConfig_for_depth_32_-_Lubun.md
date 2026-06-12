---
title: "Compiz Error - No GLXFBConfig for depth 32 - Lubuntu"
date: 2011-03-09
forum: Multimedia Software
---

### Post by travlemon on 2011-03-09
Hello Everyone,

I've been Googling this issue, and can't seem to find a solution that works for my machine.  I installed Lubuntu 10.10 on a Thinkpad R40 and I like it a lot!  The only thing really lacking so far is the nice look that Compiz would give the desktop, so I can say "ooh" and "aah!".  

_**Problem:**_ When I try to test Compiz, I run in the terminal: ```
compiz --replace
```
When I do this,  Compiz appears to run, but I get no window borders and cannot move the windows.  I also get a strange terminal screen (in addition to the terminal I used to run the command) in the top left hand corner.  That terminal will go away when I press CTRL+C to kill the command.  My original terminal window shows this output:

```

compiz (core) - Warn: No GLXFBConfig for depth 32

Launching fallback window manager
```

_**What I've tried to fix it:**_ So far, I installed the compiz fusion icon and set Emerald as the default decorator.  I also tried the Gnome and KDE decorators just for kicks.  They all failed, so I put it back to Emerald.  

Also, I generated xorg.conf (I understand 10.10 doesn't include it by default anymore?) via the command ```
sudo Xorg -configure
```.  It generated xorg.conf.new in my home folder, so I renamed it to xorg.conf and moved it to /etc/X11.

At the suggestion of a Compiz thread I found, I edited all values for all instances of "Depth" in the "Screen" section to be 24.  This apparently worked for quite a few other people, but not quite for me.  Is there another way to make sure I'm forcing 24 bit mode?

One last note:  the graphics card in the laptop, as reported by Lubuntu, is an ATI Radeon Mobility 7500.  I had the regular Gnome version of Ubuntu on it and the effects ran quite smooth for it being an older laptop, so that gives me hope that I can get this working.

Any help on this one is much appreciated, I love my Compiz!

---

### Post by travlemon on 2011-03-11
> **travlemon said:**
> Hello Everyone,

I've been Googling this issue, and can't seem to find a solution that works for my machine.  I installed Lubuntu 10.10 on a Thinkpad R40 and I like it a lot!  The only thing really lacking so far is the nice look that Compiz would give the desktop, so I can say "ooh" and "aah!".  

_**Problem:**_ When I try to test Compiz, I run in the terminal: ```
compiz --replace
```When I do this,  Compiz appears to run, but I get no window borders and cannot move the windows.  I also get a strange terminal screen (in addition to the terminal I used to run the command) in the top left hand corner.  That terminal will go away when I press CTRL+C to kill the command.  My original terminal window shows this output:

```

compiz (core) - Warn: No GLXFBConfig for depth 32

Launching fallback window manager
```_**What I've tried to fix it:**_ So far, I installed the compiz fusion icon and set Emerald as the default decorator.  I also tried the Gnome and KDE decorators just for kicks.  They all failed, so I put it back to Emerald.  

Also, I generated xorg.conf (I understand 10.10 doesn't include it by default anymore?) via the command ```
sudo Xorg -configure
```.  It generated xorg.conf.new in my home folder, so I renamed it to xorg.conf and moved it to /etc/X11.

At the suggestion of a Compiz thread I found, I edited all values for all instances of "Depth" in the "Screen" section to be 24.  This apparently worked for quite a few other people, but not quite for me.  Is there another way to make sure I'm forcing 24 bit mode?

One last note:  the graphics card in the laptop, as reported by Lubuntu, is an ATI Radeon Mobility 7500.  I had the regular Gnome version of Ubuntu on it and the effects ran quite smooth for it being an older laptop, so that gives me hope that I can get this working.

Any help on this one is much appreciated, I love my Compiz!

I switched to a distro with Openbox as the desktop, and that seems to work much better with Compiz for my laptop.  They seem so similar, I'm perfectly fine with the change!

---

### Post by venikfi on 2011-06-05
I've got the same problem!!

---

### Post by travlemon on 2011-06-08
> **venikfi said:**
> I've got the same problem!!

Hello,

If you're not too invested into Lubuntu, and are able to try another OS, you could try installing Peppermint.  It's Ubuntu-based and is similar to Ubuntu, but Compiz seems to work on it.  I haven't done much testing, but everything seemed to configure without a problem.

I gave up on the issue and moved to another OS, so I never found a solution.  Perhaps it may work on Lubuntu 11.04?

---

### Post by kerry_s on 2011-06-08
if compiz is what you where after, then lubuntu is not the right distro. only 1 window manager can be used & lubuntu is built around openbox.

---

### Post by travlemon on 2011-06-28
> **kerry_s said:**
> if compiz is what you where after, then lubuntu is not the right distro. only 1 window manager can be used & lubuntu is built around openbox.

Thanks for responding.  I've been meaning to come back here and update this thread, as I have solved this.  Or rather, Lubuntu 11.04 solved it for me.

After quite a bit of time had passed, I had forgotten about my Lubuntu-Compiz craze.  Then Lubuntu 11.04 was released and Compiz works great on it now.  I installed the compiz packages (compiz, compiz settings manager, compiz fusion extra plugins, fusion icon, etc).

I ran fusion-icon and set Compiz as the window manager, and set GTK+ as the window decorator.  Then I reloaded the window manager, and presto chango...Compiz was working fine. 

The only problem I had was getting Lubuntu to use Compiz as the default Window manager without the clunky method of autostarting fusion-icon.  It really isn't too hard, and it was only a problem because I didn't know what was going on.  However, I made a video on how to set Compiz as your default window manager, and explain why it doesn't work when changing it in the Desktop Session Settings application.  

Here are the links to the videos (it's a 2 parter):

Part 1 - [http://www.youtube.com/watch?v=7PRXBOV7Fqs](http://www.youtube.com/watch?v=7PRXBOV7Fqs)
Part 2 - [http://www.youtube.com/watch?v=tuxv3FtgqBw](http://www.youtube.com/watch?v=tuxv3FtgqBw)

I hope this helps!

---

