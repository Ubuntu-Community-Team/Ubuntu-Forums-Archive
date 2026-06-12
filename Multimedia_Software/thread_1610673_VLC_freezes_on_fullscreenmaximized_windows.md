---
title: "VLC freezes on fullscreen/maximized windows"
date: 2010-11-01
forum: Multimedia Software
---

### Post by beew on 2010-11-01
Hi, I am having a strange problem with VLC which didn't exist before (possibly due to some updates) When viewing a video file (say an .avi file so it has nothing to do with flash)in maximized windows or full screen, playback becomes very slow and sometimes freezes momentarily (with the screen turning grey) On the other hand, if I open the same file in a small screen and then strech it out to the size of a maximized windows everything is fine.
I don't notice anything extraordinary in terms of cpu or memory usage (from running top in the terminal) when this happens.

This problem only happens with VLC, Banshee has no problem playing these same files in full screen. I use Compiz, disabling Compiz  stops VLC from freezing but it still seems a bit sluggish in full screen. Moreover, this is a new problem, as I used to be able to play videos with VLC in full screen AND with Compiz on. 

I am running Ubuntu 10.04. VLC is working fine in 10.10 on the same machine.

Any hint or suggestion for solving this problem would be appreciated.

---

### Post by beew on 2010-11-01
bump!

---

### Post by aloisam on 2010-11-02
and what if you check off "unredirect fullscren windows" in compiz config settings manager?

---

### Post by beew on 2010-11-02
> **aloisam said:**
> and what if you check off "unredirect fullscren windows" in compiz config settings manager?

It is always unchecked.

---

### Post by aloisam on 2010-11-02
> **beew said:**
> It is always unchecked.

sorry for my bad english. You should CHECK that option..

---

### Post by beew on 2010-11-02
Hi,

I tried checking it and it made no difference. :(

---

### Post by beew on 2010-11-04
Bump??!!

---

### Post by beew on 2010-11-05
bump!!

---

### Post by beew on 2010-11-19
I tried to maximize vlc's screen in the terminal and here are the error messages

> VLC media player 1.1.4.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x9be967c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb76400d4, 0xb7640048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1288795805)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:7357): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
swScaler: pal8 is not supported as output pixel format
[0xa1a020c] swscale scale error: could not init SwScaler and/or allocate memory
bee@beelaptop:~$ vlc
VLC media player 1.1.4.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x84bc67c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb75680d4, 0xb7568048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1289443067)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:9563): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[mpeg4 @ 0x87df5b0]Invalid and inefficient vfw-avi packed B frames detected
swScaler: pal8 is not supported as output pixel format
[0x89b90ec] swscale scale error: could not init SwScaler and/or allocate memory

Any idea please?

---

### Post by beew on 2010-11-20
bump!

---

### Post by beew on 2010-11-23
bump!

---

### Post by phillo on 2010-12-13
bump also

---

### Post by trooperchix on 2011-01-11
bump!

---

### Post by beew on 2011-01-23
bump again!

---

### Post by trooperchix on 2011-01-24
This seemed to work for me.  I get jumpy screen sometimes and on some movies it still freezes, but for the most part [this]("http://ubuntuforums.org/showthread.php?t=1604475&highlight=vlc+broken") worked.

---

### Post by beew on 2011-01-26
I don't think it is the same problem. I have deleted the .vlc folder many times, that didn't help.

But thanks for the reply, it is really frustrating to have posted a question for months and it seems that noone pays any attention.

---

### Post by wiggie on 2011-02-16
Dude, I feel for you. I have a similar problem. It doesn't run slow but it freezes once in a while when in full screen, and I think it has something to do with CPU usage. It didn't happen before though.

It was so annoying and consistent that I decided to look into it. No answer yet.

---

### Post by sosostris on 2011-07-01
I experienced the same problem. My Vlc player froze the system on certain videos. For example when playing the following yt video through vlc my system froze after about ~6min. 
[LIST]
[http://www.youtube.com/watch?v=y3Vc-cL9lTM](http://www.youtube.com/watch?v=y3Vc-cL9lTM)
[/LIST]

When starting vlc player like this:
```

vlc --ignore-config

```

The video plays as expected. I have tested this solution for 2 different videos so far, that refused to play without error before.

Although I am not really satisfied with this solution, since it completely ignores vlc configuration and hardly tells anything about the cause of the problem, at least I am able to use vlc again it seems.

---

### Post by Bill Gates Foundation on 2012-03-07
still frozen on 12.04

edit:

fixed 12.04

>          In Tools > Preferences > Video > Output change the Default to X11, save and restart vlc.
 


---

### Post by Driger on 2013-01-16
Thank you! Works perfectly for me

---

### Post by johanzebin on 2013-10-08
Great, many thanks, that was exactly my problem after upgrading to Debian GNU/Linux 7.

---

