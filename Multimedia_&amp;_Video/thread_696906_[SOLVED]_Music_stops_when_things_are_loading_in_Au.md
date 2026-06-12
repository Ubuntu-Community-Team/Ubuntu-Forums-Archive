---
title: "[SOLVED] Music stops when things are loading in Audacious since backport"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by tghe-retford on 2008-02-14
Today, I noticed that Audacious had upgraded in Gutsy to 1.4.5. However - a problem has appeared. When I play music, the sound will stop if my computer is also doing something else, ie. if Firefox is loading a webpage or if Synaptic is searching for a program in the repositories.

It only happens with Audacious. The problem is, it supports a lot of file formats that I like to listen to which means I cannot simply change programs.

My personal thoughts are that it is either a bug or buffer under-run, but I wouldn't know how to diagnose for either. I ran Audacious from the command line and nothing appeared when the problem occurred, so I suspect it may be the latter (ie. my PC cannot keep up with the updated Audacious).

Any help would be appreciated. Thanks in advance.

---

### Post by xc3RnbFO8P on 2008-02-14
Sometimes it helps to compil it:

> [http://ubuntuforums.org/showthread.php?t=680736](http://ubuntuforums.org/showthread.php?t=680736)

---

### Post by tghe-retford on 2008-02-14
Sorted it. Turns out a option I changed to make it work with the last edition caused problems with this latest version. Upping the buffer size stopped the sound skipping.

Marking as solved...

---

### Post by peterx14 on 2008-02-17
I'm noticing the same problem, but I don't recall previously changing any options myself. Can I ask what your buffer size is? Mine is currently showing as 3000, but I do notice it stopping sometimes when firefox is displaying a busy page.

---

### Post by tghe-retford on 2008-02-17
> **peterx14 said:**
> I'm noticing the same problem, but I don't recall previously changing any options myself. Can I ask what your buffer size is? Mine is currently showing as 3000, but I do notice it stopping sometimes when firefox is displaying a busy page.
My buffer size is 100. It was set to just 1 on the previous version because of a problem where the end of the song would be cut off, and lowering the buffer size allowed the song to play in full but didn't cause skipping in Firefox.

Since the backport upgrade, the low buffer size caused sound to skip, so raising it fixed the problem. Try raising it in steps of 500 or so and get Firefox to reload a busy page after you have upped the buffer size to see if the problem has been fixed.

That's all I can suggest at the moment.

---

### Post by peterx14 on 2008-02-17
Will do -- thanks for the reply!! :D

---

