---
title: "[SOLVED] Rhythmbox vs Firefox - What's going on?"
date: 2008-06-21
forum: Multimedia Software
---

### Post by z.s.tar.gz on 2008-06-21
I have a small problem as far as RB (or FF?) goes.
I listen to music while browsing, and whichever I open first, RB or FF, conflicts with the other. If I start RB first, FF will freeze if I change songs too many times too fast. If I start FF first, RB will freeze if I load a big page. The only way to restart either is to close both out.

I've tried all kinds of stuff on my own, but I don't know how to fix it.
(I'm making an uneducated guess it has to do with priority)

If it can't be fixed, it's nbd, mostly an inconvenience.

I'm using Hardy w/ FF3.
P4 Laptop 2gigs ram

Also, RB lags if I do any scrolling in FF. May just be swamping my old proc.

---

### Post by Mattevt on 2008-06-22
I'm far from an experienced Ubuntu user, so take this post with a grain of salt, or ignore it--either way.

I found that when 2 applications (usually FF an RB) tried to play sound at the same time, the sound would break. When this happened I simply reverted to ALSA:

in terminal:
```
killall pulseaudio
```

That fixed the problem for me. The only downside was that pulseaudio would take over as default when my computer restarted--so I just switched all my audio defaults to ALSA, and haven't had the problem since.

If no one else answers, you might as well try killing pulseaudio, then restarting the offending apps. If that doesn't do it, just restart your computer and pulseaudio will become default again.

---

### Post by z.s.tar.gz on 2008-06-22
thanks, I hadn't thought of that.

---

### Post by sancho panza on 2008-06-23
I too have had this issue with pulseaudio all the time. Amarok and firefox are always hijacking the audio stream and preventing the other from accessing it until I restart both of them. This seems really silly for pulseaudio that was touted as something to be looked forward to in Hardy.

---

### Post by Vivaldi Gloria on 2008-06-27
Fix pulseaudio following one of the following guides:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

I used the second thread to fix all my sound issues but the first thread is newer.

---

### Post by mwsherman on 2008-06-27
Like pretty much everyone else in the ubuntu-verse (and this thread), I'm having issues with pulseaudio in Hardy. However, my reliance on skype and my personal if-it-aint-broke-don't-fix-it philosophy has made me reluctant to follow the steps to fix pulseaudio. I was very excited to see my solution to the Hardy sound problems was as simple as killall pulseaudio. But now I have some hardcore beginner questions--

-If I want to run this command every time my system starts, how do I do that? I did a bunch of searches, and I found information, but they all seemed to be geared for boot level processes, and clearly this command would have to be executed much later. OR, is there a better way to stop pulseaudio rather than killing it every time I boot? I don't know how to change the system settings to stop using pulseaudio...

-What's the advantage of using pulseaudio in the first place?

Thanks!

---

### Post by Vivaldi Gloria on 2008-06-27
> **mwsherman said:**
> -If I want to run this command every time my system starts, how do I do that? 


Try this: Press Alt+F2 and write

```
gksudo gedit /etc/rc.local
```

end then add this line at the end:

```
killall pulseaudio &
exit 0
```

Hopefully this will kill pulseaudio. Let me know if it works for you. If it doesn't work then restore your changes.

---

### Post by ad_267 on 2008-06-27
Try installing the "libflashsupport" package. This solves issues with sound problems in flash. I used to get no sound in flash or rhythbox wouldn't play sound. Installing this solved that issue.

---

### Post by OhioLen on 2008-07-06
> **ad_267 said:**
> Try installing the "libflashsupport" package. This solves issues with sound problems in flash. I used to get no sound in flash or rhythbox wouldn't play sound. Installing this solved that issue.

This worked on my Dell Inspiron 1525n (bought preinstalled with Gutsy, upgraded to Hardy). 

My symptoms: couldn't have Flash audio at the same time as Rhythmbox or any other audio app. Pausing the MP3 I was listening to in Rhythmbox so I could watch a YouTube video was a guaranteed audio kill. 

IF (firefox + flash + audio app) = :-# THEN (sudo apt-get install libflashsupport) = :guitar:

---

### Post by animaniac on 2008-07-06
i had the same problem, seems solved:
[http://ubuntuforums.org/showthread.php?t=850421](http://ubuntuforums.org/showthread.php?t=850421)

---

### Post by shamusl on 2008-07-09
> **animaniac said:**
> i had the same problem, seems solved:
[http://ubuntuforums.org/showthread.php?t=850421](http://ubuntuforums.org/showthread.php?t=850421)

Thanks.

---

### Post by nosfer82 on 2008-07-18
> **ad_267 said:**
> Try installing the "libflashsupport" package. This solves issues with sound problems in flash. I used to get no sound in flash or rhythbox wouldn't play sound. Installing this solved that issue.

thanks mate

---

### Post by z.s.tar.gz on 2008-07-18
thanks. works like a charm.

edit: marking as solved. libflashsupport completely worked.

---

