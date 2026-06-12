---
title: "Kaffeine, subtitles and libxine 1.1.10"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by montag on 2008-02-21
Hi,
I'm having a strange behavior from Kaffeine since the last update of libxine (from the backports)

Usually when I wanted to watch a video (movie.avi), and in the same folder was present a subtitle file with the same name (movie.srt), Kaffeine simply played the file enbling automatically subtitles.

After the upgrade of libxine, under the same conditions, Kaffeine (or better, Xine) says:
> 
The specified file or url was not found. Please check it. (/home/vitto/movie.avi#subtitle:/home/vitto/movie.srt)Followed by:

> Resource can not be opened (/home/vitto/movie.avi#subtitle:/home/vitto/movie.srt)

And then Kaffeine welcome window opens up.

But if I try to move or rename the subtitle file, movie file plays nicely.

It seems something related to the handling of filename of movie AND subtitle.

Time to open a bug?

---

### Post by roshan18 on 2008-02-23
Hi,

I am having the same problem with Kaffeine since today morning. For quite a few hours now, I have been searching the net for the available solutions and trying them out, but none of them have worked. I guess the problems to which the solutions were given didn't match the problem I am having.

Now, I found a post which I feel describes the same problem I am having.
I regularly update my computer by selecting "all" the updates that Ubuntu recommends; I don't check "what" the updates. A day or 2 back I had updated my computer. On noticing this post, I realized libxine must have been updated.

So, its a conflict of "version number". In fact, "latest" version number. Is there any solution for this?
I had suffered a similar "latest" version incompatible problem before.
The result of all this is : I am thinking whether its necessary to continue upgrading all the softwares as and when any update is available :-(

---

### Post by Poborskiii on 2008-02-23
I have the same problem already from my own backport of libxine 1.1.9 (and later 1.1.10) from hardy to gutsy a month ago.

---

### Post by montag on 2008-02-23
Ok, good, I'm not only one suffering this problem... ;)

Has someone already opened a bug at launchpad about that?

---

### Post by pinta_vodki on 2008-02-23
Yep, got same problem today after updating... I can't live without subtitles!!

---

### Post by pinta_vodki on 2008-02-23
Ok, I got this sorted out. The bug was fixed in kaffeine 0.8.6, just go to [http://kaffeine.homelinux.com/](http://kaffeine.homelinux.com/) and follow the instructions how to install the latest version. =))

---

### Post by montag on 2008-02-23
It seems that Kaffeine 0.8.6 will be officially backported soon to Gutsy:
[https://bugs.launchpad.net/gutsy-backports/+bug/186482](https://bugs.launchpad.net/gutsy-backports/+bug/186482)

But it's strange, the problem appeared after upgrading libxine, not kaffeine...

---

### Post by siddartha on 2008-02-26
Done. The new kaffeine is ok and solves the subtitles problems.

---

### Post by james_xxx on 2008-03-08
OK, there is a new Kaffeine that I did upgrade to, but when I did that, it removed libxine entirely, and Kaffeine could hardly play anything.

I still see no upgrade for libxine that goes with the new Kaffeine.

I got off on the wrong foot with Gutsy from the very beginning.

---

