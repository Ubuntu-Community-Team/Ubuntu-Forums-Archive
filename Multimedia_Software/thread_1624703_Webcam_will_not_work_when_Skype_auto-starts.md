---
title: "Webcam will not work when Skype auto-starts"
date: 2010-11-18
forum: Multimedia Software
---

### Post by tlfcbb on 2010-11-18
When i set skype to load on start up my webcam will not work. However if I manually start it after booting up the system it works fine. I am not using ciaro dock but am using docky. My webcam is a Logitech.  This can be anoying as I would sometimes forget to turn Skype on manually. Any ideas would be greatly appreciated?

---

### Post by tlfcbb on 2010-11-22
Bump - Is no one else having this problem?

---

### Post by tlfcbb on 2010-11-25
Bump, Giving this one last try in case anyone can help.

---

### Post by Goldfissh on 2010-11-25
Have you tried re-installing Skype? I actually have no idea, but I felt bad that you had no replies :D

---

### Post by BigD77 on 2010-11-25
> **tlfcbb said:**
> Bump - Is no one else having this problem?

I can't get my webcam to work on Skype either.  I downloaded a program called Cheese, which the webcam shows up, but all I get are still pictures even when I try video.  At least I know the webcam works.

---

### Post by gordintoronto on 2010-11-25
Sorry, I don't understand why you need to start Skype on startup.

Perhaps the problem is timing: Skype starts running before the webcam has completely "initialized."

By the way, Logitech has made many webcams, which are very different from each other. Perhaps if you said *which* Logitech webcam you have, it might be useful.

---

### Post by MZ250Supa5 on 2010-11-25
I too am unable to get my webcam to work on Skype, though everything seems fine when I open Cheese to check that everything is working.

---

### Post by tlfcbb on 2010-11-26
Thanks for all the replies guys. 

Goldfissh - I have tried re-installing skype but it makes no difference.

 gordintoronto - I think you may be right that it is a timing problem.  When I manually start skype after turning the computer on the webcam works without a problem.  The reason I want it to auto start is that if I do not intend to use it I don't always remember to turn it on (If another member of the family turns the computer on they never remember to start Skype).  This means no one can contact me when I am on-line. I am in work at the moment so cannot get the model of the webcam but it does work well in Ubuntu when Skype is started manually.

Again thank you all for your replies.

---

### Post by Protocol84 on 2010-12-05
I am having this same issue and this is basically what I have found out. 

When Skype installs the menu links point to ~/skype.sh which contains the code:

#/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 && skype

to get the webcam to work properly.

The problem en lies when you either just type skype into a terminal, or you have restarted and your computer remembers a skype instance from your last session but does not load skype up with the above arguments to make the webcam work.

If you don't have the "remember my desktop session" option enabled you can add skype to your startup pointing to the above script (if it is not there you can just make it) to enable the webcam.

I am still trying to figure out how to make it use the arguments when it is recalled from my last session.

---

### Post by ocwo92 on 2010-12-05
> **Protocol84 said:**
> #/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 && skype

You may want to modify the script to avoid the export and replace the above with the following line:

```
XLIB_SKIP_ARGB_VISUALS=1 skype
```

With this workaround, my daughter's webcam worked in skype. On my own computer (using some Logitech 4000-ish webcam), I had to enter the following instead:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"
```

---

### Post by Protocol84 on 2010-12-05
I Left the code alone as that was how skype had put it and I do not know that much about syntax.

---

