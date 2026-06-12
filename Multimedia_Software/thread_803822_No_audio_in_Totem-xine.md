---
title: "No audio in Totem-xine"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Xecuter on 2008-05-22
Hi!

I'm having trouble with Totem, it's not playing audio anymore, it just stopped all of the sudden.

I've got audio elsewhere, but not in totem. I even got audio in the totem-plugin in firefox.

What's the problem?

---

### Post by erginemr on 2008-05-22
There must be something wrong with the gstreamer codecs, hard to pinpoint though. What is the outcome of the command:
```
dpkg -l gstreamer* | grep ^ii
```
In my system, the attached packages are installed.

You may try your luck with totem-xine, same program but with xine backend:
```
sudo aptitude install totem-xine
```

---

### Post by erginemr on 2008-05-22
Gosh! You already have totem-xine. Sorry, didn't notice, stupid me...:oops:

---

### Post by Xecuter on 2008-05-23
Haha!

Anyone else know?

---

### Post by jocheem67 on 2008-05-23
I've got the same problem, though to me it looks pulse-related. Something with my soundcard being used by another program...I'll keep an eye on this thread...
You don't have two boards by the way ( onboard and an pci one ?? )

---

### Post by Xecuter on 2008-05-23
> **jocheem67 said:**
> I've got the same problem, though to me it looks pulse-related. Something with my soundcard being used by another program...I'll keep an eye on this thread...
You don't have two boards by the way ( onboard and an pci one ?? )

:O 

Yes i do! 

But the strange thing is that i lost audio while i was using totem!

---

### Post by Xecuter on 2008-05-23
I got it working! :D

I started htop and killed pulseaudio! Fixed! ;)

---

### Post by erginemr on 2008-05-23
Great news! But is your solution persistent between sessions?

---

### Post by Xecuter on 2008-05-24
> **erginemr said:**
> Great news! But is your solution persistent between sessions?

No, I'm afraid it's just a temporary solution.
Though it's not hard to run "killall pulseaudio" at login.

---

### Post by Kubureaucrat on 2008-05-25
something similar happens to me on 8.04 on a dell xps 400

might happen only after i have let the computer nap

so when i get back i'm out of luck if i want to be like this guy
:guitar:

---

