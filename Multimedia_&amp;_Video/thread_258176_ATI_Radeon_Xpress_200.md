---
title: "ATI Radeon Xpress 200"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by liquilife on 2006-09-15
Has anyone found a difinitive solution for this graphics card? I cannot get Ubuntu higher then 640x480 with this card. I've see many confusing hacks and such but nothing that seemed to fix this for everyone. Any updates? Thanks.

Btw, getting a new graphics card is out of the question :)

---

### Post by gzenitsky on 2006-09-15
I have this card in my HP a1130n and have no problems at all with the flgrx driver available in the repositories for Dapper 6.06 LTS. I installed following the instructions in User Documentation and it works perfectly. Runs glxgears and OpenGL screensavers, graphics, etc.

---

### Post by liquilife on 2006-09-15
Thanks, I'll check it out and see what I might have missed.

Your system is very close to mine. I am running the HP a1420n over here. A bit off topic here but are you running Ubuntu and XP on your system under a dual boot?

---

### Post by liquilife on 2006-09-15
Someone please help. I've updated the fglrx drivers from the repository and I am still stuck at the 640x480 resolution. Can anyone please walk me through this? I'm no PC dummy but I'm completely lost in Ubuntu, even more so because of the resolution I'm stuck in.

Any help would be HUGELY appreciated. Thanks!

---

### Post by phunkizm on 2006-09-17
i had the same problem (same video card), and this howto cured it for me.
if you're using amd64, it should work for you too.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

but i'm yet to get OpenGL running with it.. :frown:

---

### Post by liquilife on 2006-09-21
Thanks phunkizm. I found a solution that worked for me at the thread listed below. Everything seems to have been working great for the past week now with no known problems at this point:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by butters671 on 2006-09-27
Hey, i have that card. I am VERY new to linux, as in lets see, 3 days, (don't hate me...yet) and like many newcomers, I am drawn to the xgl compiz eye candy.... for the life of me i can't get the ati card driver installed correctly... also as for the glxgears thing i am hoping there isn't something wrong with this output, as well as the gears looking a little jerky


glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).
peter@peter-laptop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).
peter@peter-laptop:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
bash: Xlib:: command not found
peter@peter-laptop:~$ X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by liquilife on 2006-10-02
Butters.. makes me think of South Park :D

Is your computer 64bit? If it is did you install the 64bit driver? Sorry, that's about the most I can trouble shoot for you. If anything i'll have bumped the topic for you in small hopes someone else can address your issue.

---

