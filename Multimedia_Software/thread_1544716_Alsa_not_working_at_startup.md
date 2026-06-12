---
title: "Alsa not working at startup"
date: 2010-08-02
forum: Multimedia Software
---

### Post by Peter7K on 2010-08-02
Hello.  My audio was working just fine up until today, when I was working on some audio production stuff.  I did QjackCtl, and also ran pulse-jack so I could use another app not in jack.  Now, upon a boot up, there is no gnome-volume-control-applet or gnome-volume-control running.  When I run gnome-volume-control it says there is no sound device (without Jack running).  When I do it with Jack and Pulseaudio running (doing QjackCtl and pulse-jack), gnome-volume-control shows info about jack, but no hardware.
 I have sound, I just can't affect it volume-wise, etc.

When I run pacmd I get this:

$ pacmd
Daemon not responding.


When I close QjackCtl I then get an error in a window that says merely:

Waiting for sound system to respond.

It's like it's hanging up or something.  Anyone know what I screwed up?  Thanks.

---

### Post by Peter7K on 2010-08-03
After some more testing it seems like the sound does function, I just have zero control over the volume or muting it, etc.  Also, when I run "pavucontrol" it says "Connection refused."  :(

EDIT: Solved!  Deleted .pulse folder in home and works fine on reboot.

---

### Post by isbiyanto on 2010-08-08
ok...

---

### Post by Nabo00o on 2011-02-16
I too did have this problem and got really annoyed, thankfully it was easy to fix with the .pulse folder deletion. What I wonder though is wether there is a faster way to change between normal audio and pulse-jack than simply restarting every time? Could we maybe instead use a command to restart pulse audio? 

Thanks for helping me anyway!

---

### Post by moongya on 2011-03-13
have the same prob, but do not have .pulse folder under home. help

---

