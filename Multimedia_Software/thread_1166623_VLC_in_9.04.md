---
title: "VLC in 9.04"
date: 2009-05-21
forum: Multimedia Software
---

### Post by nixIT on 2009-05-21
I installed VLC through the repos, and when playing back video files the volume control is in it's own window.  Is there a way to integrate it into the video window?

--nixIT

---

### Post by bhishan on 2009-05-21
Yes, I was also wondering why it is like that. I have a wireless keyboard so I use the shortcut Ctrl+ up or down arrow, but a mouse would be better.

---

### Post by x33a on 2009-05-21
There is an issue with vlc 0.9.9 not integrating the video and control windows.

so you can either use keyboard shortcuts or downgrade to a lower version, or use nvlc (ncurses interface).

---

### Post by alphacrucis2 on 2009-05-22
Install the VLC 1.0 release candidate from Kow's PPA. This fixes the problem with playing vids in the main window.:

[https://launchpad.net/~kow/+archive/ppa]("https://launchpad.net/~kow/+archive/ppa")

---

### Post by Jimmynemo2 on 2009-05-22
FYI, this is the same in the windows version right now too- something about the newest versions, VLC thinks this is a good thing. That or the unintentionally messed it up on both platforms.

(the keyboard shortcuts do still work, fyi)

---

### Post by HappyFeet on 2009-05-22
> **alphacrucis2 said:**
> Install the VLC 1.0 release candidate from Kow's PPA. This fixes the problem with playing vids in the main window.:

[https://launchpad.net/~kow/+archive/ppa]("https://launchpad.net/~kow/+archive/ppa")

That version crashed my computer big time. I'm avoiding it like the plague.

---

### Post by binbash on 2009-05-22
[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

### Post by nixIT on 2009-05-22
thanx, will try these when I get home.

--nixIT

---

### Post by Jimmynemo2 on 2009-05-22
Thanks Binbash- I used that one, and not only did it fix that same issue the OP was having, but the blog that led me through it also had a few other really good tutorials on it, so I apprecaite the link!

---

### Post by bhishan on 2009-05-23
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

Thanks a lot.

---

