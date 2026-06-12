---
title: "k3b won't preview MP3s when creating audio project"
date: 2008-07-14
forum: Multimedia Software
---

### Post by kortsen on 2008-07-14
k3b has a feature when creating audio projects to preview MP3s. You *should be able to* hilite a track in the project track list and click the play button above the track list window.  What I get is an error message popping up.

[IMG]http://lars.kortsen.googlepages.com/k3b.jpg[/IMG]

My Googling so far has led me to check (and confirm) that artsd is running and kdebase-kio-plugins is installed.

---

### Post by kortsen on 2008-07-14
This problem seems to be related to Xfce (Xubuntu), but with a twist.  I just tried an experiment.  I logged out of my Xfce session and opened a KDE session.  I launched k3b and it happily played previews.  I then closed the KDE session and logged back in to an Xfce session.  THIS TIME kde played previews.  I then reset the computer and booted into an Xfce session.  No previews again.

---

### Post by randomenthusiast on 2009-10-16
I have a similar problem in Ubuntu (Jaunty) trying to preview tracks in K3B.  It won't preview tracks, but it burns fine.  I also have the kdebase-kio-plugins installed, however since I don't have either the KDE or Xfce desktops installed, I have no way of testing that little log in - log out trick.  I wish I knew what the problem was, Google hasn't been very forthcoming with answers on this one.

---

### Post by HappyFeet on 2009-10-16
Does everyone have **libk3b2-extracodecs** installed?

---

### Post by randomenthusiast on 2009-10-16
Wow, it was like you were waiting to respond to my post Happyfeet :P

I do have that package installed, except it's the newer version "**libk3b3-extracodecs**".

---

