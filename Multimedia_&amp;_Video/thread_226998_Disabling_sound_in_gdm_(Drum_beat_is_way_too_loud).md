---
title: "Disabling sound in gdm? (Drum beat is way too loud)"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by seguso on 2006-08-01
Hi,

Each time I start my laptop, gdm plays a very loud drum beat sound that makes everyone jump off the chair. :-(  My laptop does not have a volume slider and the drum beat is incredibly loud. I need to turn it off. Thanks for any help.

---

### Post by croak77 on 2006-08-01
Open a terminal:

sudo gdmsetup

Accessibility Tab -> Uncheck "Login Screen Ready"

---

### Post by seguso on 2006-08-01
Thank you, but... gdmsetup segfaults at startup! 
Just my luck.

---

### Post by tseliot on 2006-08-01
get to the following menus:

System/Preferences/Sound

Then get to the word "Login" and disable the sound

---

### Post by seguso on 2006-08-01
Thanks, but the sound happens** before** login, unfortunately. I guess I'll have to wait until gdmsetup stops crashing.

---

### Post by tseliot on 2006-08-03
My bad.


Try this:
```

sudo nano -w /etc/gdm/gdm.conf

```

then get to the following section:
```
# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav

```

and make it look like this:
```
# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
SoundOnLogin=[COLOR="Red"]false[/COLOR]
SoundOnLoginFile=/usr/share/sounds/question.wav
```

CTRL+X to exit (save the file)

---

### Post by seguso on 2006-08-03
Thank you very much :D

---

### Post by h3_ on 2008-03-11
Seriously guys, PLEASE remove this sound from Ubuntu or at least make it really easy to disable.

When, as a user, i disable *all* system sounds in the config panel, it might be just my stupid assumption, but I expect *all* sounds to be disabled. 

I've been digging the web for 30min now to find a way to disable. This tamtam sounds drives me crazy since I first booted Ubuntu.

---

### Post by Scoubidou on 2008-05-08
I completely agree with h3_
That sound should not be there or at least by removable from System/Preferences/Sound

Just my 2 cents

---

