---
title: "Sound setting not respected"
date: 2008-11-19
forum: Multimedia Software
---

### Post by liquid.silver on 2008-11-19
I am running ubuntu 8.10. I find the sound that plays after login a tad annoying and it's not for me. So i preceded to set the login sound to disabled in the sound preferences. However, when i restart, the original sound still plays. I even tried setting the login sound to something else, but that didn't help.

This is getting really annoying when i turn my laptop on at work and bongo drums noises emerge from my speakers... any advice would be appreciated.

---

### Post by robertyou on 2008-11-19
Which one are you referring to?

For the one that plays immediately when login screen shows up, you can disable it from 
> System -> Administration -> Login Window -> Accessibility

The other one you described plays after you log in as the desktop is loading.
> System -> Preferences -> Sound -> tab "Sounds" -> under "Alerts and sound Effects" 

---

### Post by liquid.silver on 2008-11-19
I was referring to the latter, "after login". and i disabled it in exactly the place you referred to, but it didn't work.

however, i was looking at some other settings, namely sessions (preferences>sessions) and i stumbled upon "gnome login sound", disabling this fixed my problem and the login sound doesn't play anymore.

as far as i am concerned, this is still a bug and therefore i'm not going to mark this thread as solved (is that right?). what if i want to play a different sound after login? it doesn't work then... i can only choose to play the default or nothing it seems...

---

### Post by MaX on 2008-11-19
> **liquid.silver said:**
> I was referring to the latter, "after login". and i disabled it in exactly the place you referred to, but it didn't work.

however, i was looking at some other settings, namely sessions (preferences>sessions) and i stumbled upon "gnome login sound", disabling this fixed my problem and the login sound doesn't play anymore.

as far as i am concerned, this is still a bug and therefore i'm not going to mark this thread as solved (is that right?). what if i want to play a different sound after login? it doesn't work then... i can only choose to play the default or nothing it seems...

So report it in launchpad, complaining here does nothing.

---

### Post by liquid.silver on 2008-11-19
Hm... sorry, didn't mean to complain, just thought maybe i was overlooking something and someone here could help.

Had a look at launchpad, seems there is already a bug open on this: [http://bugs.launchpad.net/bugs/277203](http://bugs.launchpad.net/bugs/277203)

---

### Post by robertyou on 2008-11-19
There seem to be an extreme way to solve your problem..
someone suggested to just remove the audio files.

In this thread:
[http://ubuntuforums.org/showthread.php?t=93785](http://ubuntuforums.org/showthread.php?t=93785)

Worth give it a try, but I would back up the files in case it might cause some error message.

Edit:

To be exact, the file you need to remove is

> /usr/share/sounds/ubuntu/stereo/dialog-question.wav

You have to do this as root, open up a terminal:
```

cd /usr/share/sounds/ubuntu/stereo/

```
```

sudo mv ./dialog-question.wav ./dialog-question.backup

```
..above commands just rename the file to "dialog-question.backup"

---

### Post by liquid.silver on 2008-11-20
Thanx, but you really didn't need to tell me how to rename a file :)

Or you can just do what i stated in a previous post: disable the "gnome login sound" in preferences>sessions. I think that's a much better work-around.

---

