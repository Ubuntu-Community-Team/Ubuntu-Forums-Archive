---
title: "Monitor gone completely black."
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by Rusty Bicycle on 2008-03-04
I've got a bit of a problem: my monitor has gone black for no reason that I'm able to discern and I can't get it back to normal again.

My computer is an old IBM NetVista so the monitor isn't separate from the computer itself.

What happened is that I was reading the news online, left to get lunch, and when I came back to check my e-mail the screen was completely black.  Thinking that it had gone to sleep or some such I tried moving the mouse around and tapping the space bar, but to no avail.  I tried turning off the computer and turning it back on again, likewise achieving nothing.  I noticed that while I couldn't see anything on the screen itself, I was able to do things like open a terminal and use it to run commands.  I just couldn't see anything.

After doing this I noticed that the screen wasn't entirely dead: I could see something like a shadow of what I'd normally see on the screen if I did something like open a terminal or a menu.  Basically it looks like a slightly different shade of black, as if the monitor is changing colors but not emitting any light.

I'm not sure the monitor itself is busted though: When I turn on the computer or exit my session to get to the login screen, the monitor turns itself right for about a second, then goes black again.

I've tried restarting X and that gets me nowhere.  I tried to run *dpkg-reconfigure xserver-xorg* but being unable to see very well I wasn't able to follow any of the prompts, so I just manually shut down the computer.

Anyone have any idea what's going on here?  Any help you could send my way would be _greatly_ appreciated.

---

### Post by kaens on 2008-03-04
Do you have a livecd to try booting from?

---

### Post by Rusty Bicycle on 2008-03-05
I tried booting from a LiveCD and the same thing happened, no light coming out of the monitor.  :(

---

### Post by Zayne on 2008-03-05
While it wasn't on Ubuntu, I had this same issue with an LCD monitor.

Same problem. Just went dark, literally black one day. After a while I noticed it was possible to see shadows of things if you looked hard enough. Tried a ton of different things.

Eventually found out the backlight in the monitor was not functioning. I got it to turn on a few more times, then it burnt out.

I don't know if this is the same problem but.. something to think on.

---

### Post by Rusty Bicycle on 2008-03-05
I was wondering if that was it myself...  I found some instructions for fixing an LCD monitor online and if they work I'll make sure to mention it.  I've included the link below in case anyone who has the same problem finds their way to this thread.  Thanks to both of you for your help!

[http://www.inventgeek.com/Projects/BacklightFix/overview.aspx](http://www.inventgeek.com/Projects/BacklightFix/overview.aspx)

---

