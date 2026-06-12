---
title: "[SOLVED] Convert flash video to 3g2"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by ctswhole on 2008-03-02
I'm trying to convert .flv videos to .3g2 for use on my cell phone.  I've tried googling around, and searching this forum for an answer.  The best thing I've come up with is WinFF, and the GUI looks like it should convert the video to a format suitable for my phone, but every time I put the .flv video in there for conversion, WinFF says it's "done", but no .3g2 video has been made.  Does anyone have any suggestions or how-to's to convert these videos?

---

### Post by ron999 on 2008-03-02
Hi

I've just converted some YouTube flash videos to 3g2 using WinFF.
It worked OK.

When you load the video into WinFF test it first with WinFF's player.
If the player won't play the video then it probably won't be able to convert it either.

Check that your flash video has a valid file extension such as **.fla** or **.flv**
.
:guitar::guitar:

---

### Post by ctswhole on 2008-03-02
Did you have to do anything special to convert?
I can't get it to convert over here to that format, but I am able to convert to .mpg or .avi.

---

### Post by ron999 on 2008-03-03
Hi
No, I did nothing differently. I just chose the '3g2 for phones' option.
These are the settings in my preset:-

**-acodec aac  -ac 2  -vcodec mpeg4 -s qcif -b 128kb -r 14.985**

---

### Post by ctswhole on 2008-03-03
Hmmm, that's what I have in my preset as well for .3g2.  When I try to convert, a terminal window flashes on screen for a split second, but that's it.  I might have to do some serious digging or serious praying to get this going.  Thanks for the help though!

---

### Post by stooshbunutu on 2008-03-11
phones should handle 3gp aswell now, you can use mobile media converter for that [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

hope this helps

---

### Post by ctswhole on 2008-03-11
My phone doesn't seem to like 3gp, only 3g2.

But as luck would have it, I stumbled on the solution to my problem last night (Thank you StumbleUpon!)  I  couldn't google an answer, but managed to come across a forum post that solved my problem.  I had, at least I thought I had, all the necessary codecs and software installed, but I was missing "faac".  After a quick sudo apt-get install of that, I am now converting videos to .3g2 using WinFF. :)

---

### Post by stooshbunutu on 2008-03-11
gd gd

ps remember to mark your thread as solved using the thread tools menu at the top

---

