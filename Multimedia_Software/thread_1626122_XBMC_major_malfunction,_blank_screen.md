---
title: "XBMC major malfunction, blank screen"
date: 2010-11-19
forum: Multimedia Software
---

### Post by Objekt on 2010-11-19
Today I installed XBMC (version 1.9-11-lucid3 according to the entry in Software Center) but it doesn't work.  When I attempt to run XMBC, I get a black screen - actually, two black screens, as I have two monitors.  I can't switch out of XMBC, so I have to drop to the console (Ctrl+Alt+F1) and then manually stop & restart X.

The only response I get out of XMBC is some kind of sound effect when I press the Escape key.  It does not respond to the keyboard or mouse in any other way.

I installed XMBC by following the instructions on the XMBC wiki:
[http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux]("http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux")

So what's the deal?  I found a few references on the Web to people having a somewhat similar problem, but I'm not even getting a mouse cursor.  Also I can't find any way to kill XMBC.  It's annoying to have to restart X, as I then lose any other program that was open.

---

### Post by bustamelon on 2010-11-22
{Read this whole post before you type anything into console}

to kill xbmc, while in console, do either:

%> ps -ef | grep xbmc
%> kill 1234
(where 1234 is the process ID (PID) of 'xbmc.bin')

OR (less good):
killall -9 xbmc.bin

depending on how xbmc is set up, you might have to do 'sudo kill' instead of just 'kill'.

I also got the black screen today, not sure what caused it or what exactly is going on. Love to hear any other feedback.  I often get a not-so-black screen, where there is still some text showing in xbmc but no response to input.  This is just a black hole.  Can't get in via VNC, but am able to shell in.

---

### Post by bustamelon on 2010-11-23
I seemed to have solved the problem by turning off most of the "sync" settings in the video playback menu.  Didn't make a note of which ones exactly but one of the options was "auto-detect."

Hope that's not totally unhelpful! :P

---

### Post by Objekt on 2010-11-23
> **bustamelon said:**
> I seemed to have solved the problem by turning off most of the "sync" settings in the video playback menu.  Didn't make a note of which ones exactly but one of the options was "auto-detect."

Hope that's not totally unhelpful! :P

That might work, if I got as far as the XMBC menu.

I'm seeing nothing.  Just blackness on both monitors.  Not even a mouse cursor.

That's why I had to drop to console and restart the X server.

---

### Post by Objekt on 2010-11-23
> **bustamelon said:**
> {Read this whole post before you type anything into console}

to kill xbmc, while in console, do either:

%> ps -ef | grep xbmc
%> kill 1234
(where 1234 is the process ID (PID) of 'xbmc.bin')

OR (less good):
killall -9 xbmc.bin

depending on how xbmc is set up, you might have to do 'sudo kill' instead of just 'kill'.

That's helpful, but...how do I get back to the GUI if I kill XMBC at the console?  I don't know how to get back to the GUI from the command line, so I've been just restarting X.

---

### Post by bustamelon on 2010-11-23
Oh, I see.  So, to respond to part 1 of your problems (xbmc won't start so you cant change settings):

- you might try editing your xbmc config files to change the settings manually.  I don't know much of anything about that, I just know it's possible.  I would bet that somewhere on their website they tell you how.

Try this:
[http://wiki.xbmc.org/index.php?title=Advanced_Configuration](http://wiki.xbmc.org/index.php?title=Advanced_Configuration)

As for getting back into X from console:

This brings up a point that I didn't think of before, which is whether you're running XBMC as a standalone desktop solution, rather than alongside Gnome (or whatever).  If Gnome is running in there somewhere, you should be able to use CTRL+ALT+F7 (or maybe F8, I forget) to get you back to the desktop.

...also, I would try disabling the 2nd monitor, just to remove that from the equation -- that can add a lot of complexity.

---

