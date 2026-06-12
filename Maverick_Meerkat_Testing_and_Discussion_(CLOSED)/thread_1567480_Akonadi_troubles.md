---
title: "Akonadi troubles"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2010-09-03
Anyone else experiencing Akonadi issues? It is slowing down all my dolphin operations. I had to kill it, otherwise I wouldn't be able to work.

Any solution? Any way to disable it?

---

### Post by ranch hand on 2010-09-03
Use Gnome.

---

### Post by lovinglinux on 2010-09-03
> **ranch hand said:**
> Use Gnome.

Thanks, but that is not a solution. I prefer KDE 1000 times over Gnome.

---

### Post by buzzmandt on 2010-09-03
haha, you funny ranch hand.  Some of us prefer not to use gnome. (uh oh, gnome vs kde, let's hope not)

there is a setting to not use akonadi.  I just let it run for a while and now it's fine.

---

### Post by lovinglinux on 2010-09-03
> **buzzmandt said:**
> haha, you funny ranch hand.  Some of us prefer not to use gnome. (uh oh, gnome vs kde, let's hope not)

there is a setting to not use akonadi.  I just let it run for a while and now it's fine.

I have disabled Strigi and Nepomuk already, but I couldn't find the akonadi option.

---

### Post by ktp on 2010-09-03
> **ranch hand said:**
> Use Gnome.

never disappointing...:lolflag:

---

### Post by buzzmandt on 2010-09-03
true, would have been dissapointed if he hadn't posted it lol.

---

### Post by buzzmandt on 2010-09-03
> **lovinglinux said:**
> I have disabled Strigi and Nepomuk already, but I couldn't find the akonadi option.

click K menu and in the search field type akonadi. there'll be about 4 options for ya, and akonadi configuration should be there.

edit:  alternately you can press alt+f2 and type akonadi there and scroll through the options that come up and select configuration.

---

### Post by lovinglinux on 2010-09-03
> **buzzmandt said:**
> click K menu and in the search field type akonadi. there'll be about 4 options for ya, and akonadi configuration should be there.

I already did that. The problem is that I get no options. Everything is greyed. I will go through each menu to see if I can find it.

---

### Post by lovinglinux on 2010-09-03
Never mind. I guess I need some sleep. I was looking in the System Settings instead of the menu.](*,)

---

### Post by ranch hand on 2010-09-03
Sleep, at times, is the best tool to use when fighting with your box and OS.

---

### Post by lovinglinux on 2010-09-04
> **ranch hand said:**
> Sleep, at times, is the best tool to use when fighting with your box and OS.

You won't believe [what I just did]("http://ubuntuforums.org/showthread.php?t=1567598").

---

### Post by lovinglinux on 2010-09-04
It seems is not only akonadi. Dolphin is unusable. Everything takes ages, even accessing a file context menu.

---

### Post by ktp on 2010-09-04
> **lovinglinux said:**
> You won't believe [what I just did]("http://ubuntuforums.org/showthread.php?t=1567598").

i am sure everyone has done that.  I just wish shutdown/restart was smart to save the user.

---

### Post by seeker5528 on 2010-09-04
Dolphin seems plenty quick on my system, AMD Athlon(TM) XP2200+, 768MB RAM.

I'm running it from Gnome at the moment, but system monitor does show that nepomuk and akonadi are running, don't know if it is the default or something I did, but when I run systemsettings and go to dekstop search it show that strigi file indexing is disabled.

You might try disabling desktop effects, just to see if that somehow makes a difference.

Other than that you might start dolphin from the command and see if any errors are displayed at the command line and look through log files, .xsession-errors, /var/log/syslog, Xorg.0.log.

Don't know how useful gdb would be if dolphin is not actually crashing, but you could run dolphin from gdb by typing:

```
gdb dolphin
```

Then when you get the gdb command prompt type:

```
set args --nofork
run
```

Later, Seeker

---

### Post by lovinglinux on 2010-09-04
> **seeker5528 said:**
> Dolphin seems plenty quick on my system, AMD Athlon(TM) XP2200+, 768MB RAM.

I'm running it from Gnome at the moment, but system monitor does show that nepomuk and akonadi are running, don't know if it is the default or something I did, but when I run systemsettings and go to dekstop search it show that strigi file indexing is disabled.

You might try disabling desktop effects, just to see if that somehow makes a difference.

Other than that you might start dolphin from the command and see if any errors are displayed at the command line and look through log files, .xsession-errors, /var/log/syslog, Xorg.0.log.

Don't know how useful gdb would be if dolphin is not actually crashing, but you could run dolphin from gdb by typing:

```
gdb dolphin
```

Then when you get the gdb command prompt type:

```
set args --nofork
run
```

Later, Seeker

Is not crashing. The problem is that it takes time to open a context menu and to drag and drop files, which I do a lot. Looks like it has something to do with previews, since I don't get video previews anymore. Perhaps is because medibuntu is not available yet.

---

### Post by dagrump on 2010-09-04
Just edit your source list & use karmic's repo or lucid. It works fine. One of the first things I do is edit my source list.

******************
For medibuntu...

---

### Post by lovinglinux on 2010-09-04
> **dagrump said:**
> Just edit your source list & use karmic's repo or lucid. It works fine. One of the first things I do is edit my source list.

******************
For medibuntu...

I tried that already, but got errors.

---

### Post by dagrump on 2010-09-04
Strange, I just did it earlier today. I think it grumbled abit, but it worked as I installed various items.
I'm using Karmic's repo.

---

### Post by seeker5528 on 2010-09-04
> **lovinglinux said:**
> Is not crashing. The problem is that it takes time to open a context menu and to drag and drop files, which I do a lot. Looks like it has something to do with previews, since I don't get video previews anymore. Perhaps is because medibuntu is not available yet.

I get video previews and it doesn't look like I have anything all that significant that is coming from medibuntu, I'm at work though so I only have a few videos in mpeg format to test with. If you do want to load stuff from medibuntu, it is the lucid stuff you want to install. 

The mplayer and libavcodec stuff is newer in the maverick repositories, w32codecs doesn't seem to make much difference these days for the 32 bit systems, w64codecs seems kinda pointless if you are on a 64 bit system.

For me all that leaves is aacgain and libdvdcss2. So far I haven't had much luck attempting to add replaygain information to aac files, but you never know, it could happen.

Later, Seeker

---

### Post by lovinglinux on 2010-09-14
Fixed dolphin by deleting the config files.

---

