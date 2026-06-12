---
title: "VirtualBox Killed my Sound"
date: 2009-05-07
forum: Multimedia Software
---

### Post by alldaylong on 2009-05-07
Hi all,

I'm brand new to ubuntu, and I love it, however I've been running into some things here and there and having to reinstall, so this is my first time doing the smart thing and attempting to fix an issue before I reinstall.

I am on Ubuntu 9.04 and everything was working perfectly out of the box. Once I installed xfce, I decided I didn't like it and switched back to Gnome (not sure if that has anything to do with this cause the sound still worked when I switched back). Then I installed virtualbox and setup a guest windows XP system. Everything still worked fine when I shutdown yesterday and today my sound doesn't work.

I tried purging the ALSA and reinstalling, I completly removed virtualbox and virtualbox directories using synaptic package manager, removed xfce (didn't like it) using *sudo apt-get remove xubuntu-desktop xfce* and then *sudo apt-get autoremove*.

Still my sound isn't working. I ran *alsamixer* and everything's fine, no channels muted or anything (also checked the gui sound config, everything looks fine). Any suggestions?

---

