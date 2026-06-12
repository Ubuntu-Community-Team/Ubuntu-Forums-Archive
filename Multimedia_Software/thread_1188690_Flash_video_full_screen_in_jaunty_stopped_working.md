---
title: "Flash video full screen in jaunty stopped working"
date: 2009-06-16
forum: Multimedia Software
---

### Post by kelt65 on 2009-06-16
Is anyone else having this problem? If I try a full screen flash video using the plugin, it goes full screen for an instant then goes back.

Full screen flash works fine with vlc.

I can't remember when this stopped working, but it definitely worked when I first upgraded to Jaunty ...

This is using the proprietary nvidia driver.

Starting firefox from a terminal doesn't show anything interesting, nor does the error console ...

---

### Post by alan.lamielle on 2009-07-07
I've been running Jaunty since before its official release (since late November I believe...).  Full screen flash videos have never worked for me since I first started running Jaunty.

I see the same behavior as you do: the video is played full screen for less than a second before restoring to the in-browser window.

To me it seems like something is stealing focus of the video and causing the full screen window to close.  However, I'm not even sure where to begin debugging this.  Like you said, we get no error/warning messages anywhere.  This may be because it isn't actually a bug with the flash plugin or firefox.  The problem exists between applications and interactions/focus of the X windows.  Just a guess...

Is anyone else seeing this behavior?  I'd love to find a decent size group and start narrowing down what may be causing this and find a fix.  It's quite frustrating when I can't watch flash videos full screen, but I've ignored so far.

---

### Post by samb63 on 2009-07-19
I had this problem, reading this thread prompted me into figuring out a solution (well, a work-around at least).

If I choose System -> Preferences -> Windows and uncheck the 'Window Selection: Select windows when the mouse moves over them' option, then full-screen flash works again.

I guess that's a bug.

---

### Post by alan.lamielle on 2009-07-19
I have focus-follows-mouse ('Select windows when the mouse moves over them') enabled as well.  I tried what you suggested and discovered that it works for me as well.  Additionally, after you mentioned this, I tried some experiments with moving my mouse to various places right after I clicked 'full screen' in a youtube video.  I found that if I move the mouse to the far right of the screen, the video stays full-screen.  So it does appear that it is a focus issue, possibly focus-follows-mouse is selecting the browser window and causing the full-screen window to close.

Another thing that I discovered about a week ago is that if I disable compiz, this behavior stops and full-screen flash works as expected.  So maybe the proper fix for this should be in the compiz code related to the focus-follows-mouse option.

I'm a developer myself, but I've not had to debug anything like this, therefore I'm not quite sure where to start.  Maybe someone who is more familiar with this code could help us out with this.

---

### Post by kelt65 on 2009-07-31
> **samb63 said:**
> I had this problem, reading this thread prompted me into figuring out a solution (well, a work-around at least).

If I choose System -> Preferences -> Windows and uncheck the 'Window Selection: Select windows when the mouse moves over them' option, then full-screen flash works again.

I guess that's a bug.

This fixed it. THANKS!

---

### Post by alan.lamielle on 2009-07-31
> **kelt65 said:**
> This fixed it. THANKS!

Great, I'm glad this fixes things for you too.

I've submitted a bug report on Launchpad ([https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/407573](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/407573)).  Let's hope we can get this resolved in a more proper fashion.

---

