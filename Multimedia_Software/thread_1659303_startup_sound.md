---
title: "startup sound"
date: 2011-01-03
forum: Multimedia Software
---

### Post by kakashi_12 on 2011-01-03
Ubuntu 10.04. I want to change the startup sound and the mail alert sound (incoming mail) for Evolution Mail Client. I go to System > Preferences > Sound, and all I get are themes preset. I do not have option to browse to wav files. I also do not see a browse option in Email Settings. Do I have to change an actual file?

---

### Post by kakashi_12 on 2011-01-04
ping :confused:

---

### Post by matt_symes on 2011-01-04
Hi

> I want to change the startup sound

What startup sound? Do you mean the logon sound when you first logon to Ubuntu and gnome starts up?

Kind regards

---

### Post by kakashi_12 on 2011-01-05
yes

---

### Post by matt_symes on 2011-01-06
Hi

You can change the drums sound by changing the symbolic link in 

/usr/share/sounds/ubuntu/stereo/system-ready.ogg

```
matthew@matthew-laptop:/usr/share/sounds/ubuntu/stereo$ ls -l sys*
lrwxrwxrwx 1 root root 19 2010-10-14 21:39 system-ready.ogg -> dialog-question.ogg
```

You can change the gnome logon sound from System->Preferences->Startup applications. Select Gnome login sound. Select edit and change the --id="" in the command edit box to you desired sound.

These sounds are in *.ogg format. I have no idea if they work encoded as a different type.

I'm not sure how to change the evolution mail sound.

Kind regards

---

### Post by kakashi_12 on 2011-01-10
looks like they do want ogg format. i remember from changing in ubuntu 8. i found the evolution sound change. same location as above for the logon sound (gnome) under preferences menu.

I do not want to change the actual file unless i have to. i just want to select my own. i try input the path by itself (ogg format) and get nothing. i also leave the default value in there (below)
              /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"



and then change just the path and file. still nothing.

Evolution has a default sound. but when i open mail and even send myself mail to test it, i get no sound!

 PS: is anyone else getting a weird encrypted looking like file in their home folder with the word 'fact' in it and a bunch of symbols, then at bottom (invalid encoding)???? Is this recent from an update? looks like a hidden/system file. Or is it a virus?

---

### Post by kakashi_12 on 2011-02-06
when i go to 'edit' the login sound and browse, even though i browse and point to the file, this still changes nothing. it still does not play the sound at login. now just blank. what's weird is that the file that is selected as default... there are 3 files selected AND they are all executables! what the heck? Those aren't sound files?!

---

### Post by kakashi_12 on 2011-02-17
[http://www.youtube.com/watch?v=omByF8hD6EQ](http://www.youtube.com/watch?v=omByF8hD6EQ)

---

