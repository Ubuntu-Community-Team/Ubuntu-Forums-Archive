---
title: "Green Screen in Kaffeine/Myth... Sometimes?"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Pennycook on 2007-10-22
Had a look around on Google and in the forums and can't find an answer to this, and am not even sure where to start troubleshooting. >.<

I've recently put a fresh install of Gutsy on my desktop, and I'm running into some issues with video files and MythTV.  Sometimes when I open files (or MythTV) I get sound but a green screen with lines across it, sometimes I don't.  In the case I do get a green screen, restarting X tends to fix it, but doing that every time is a bit of a hassle.

I never had the problem under Feisty, and the only thing that I can think of that I did differently was try to install DVD support following the Ubuntu Guide for Feisty.

The first time I saw the screen was following trying to play a DVD (a "proper" one) when I got an error about gnome (confusing because I'm running Kubuntu).

Does anybody have an ideas about potential fixes, or a file that may contain information about why it's crashing?

Any help would be greatly appreciated, as Ctrl+Alt+Backspacing every time I want to watch TV is just silly.  Cheers.

---

### Post by Hirs on 2007-10-23
The same here, I don't know what is the cause, as seems random. I get a green screen on every application that uses the xvideo extension

A more handy workaround is to switch to a terminal and get back to X (ctrl+alt+F1 then alt+F7)

Possibly is related to the nvidia driver, btw are you using the binaty drivers?

---

### Post by Pennycook on 2007-10-23
I'm using the restricted Nvidia driver.

---

### Post by Gidon on 2007-11-20
It's a problem with the nvidia drivers.  I'm not sure if it's a recognized issue.  One way to fix it is to change your refresh rate.  I change mine from 60hz to auto then back again and the video then plays fine.  It's not ideal but at least you don't have to restart X.

---

### Post by BatPenguin on 2007-11-28
Thanks for this tip, great. I've been going crazy trying to fix the various sync options in the nvidia-settings. Switching to a terminal and back is a really nice solution to this.

Any idea if the new beta driver fixes this?

---

