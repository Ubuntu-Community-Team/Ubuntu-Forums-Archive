---
title: "no icons &gt; left panel &gt; unity launcher."
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Duncan Williams on 2011-04-19
I have no icons in the left panel, unity launcher.
Titles of apps show and work as does most other things.
I think it is video driver related.
am using all nouveau driver and associated.
can't seem to change to nvidia proprietory drivers.
previous mentions of this problem in other threads has resoved nothing.
_[B]*[screenshot]("http://files.myopera.com/DuncanWilliams/usercss/panel.png")*[/B_]

---

### Post by awam66 on 2011-04-19
Mine are OK except for Firefox which is blank!
I am using Nvidia drivers which have problems of their own. Like blank windows when maximised if another window is open on the desktop. 64bit Amd processor.

---

### Post by eel on 2011-04-19
Hi, same problem here. I see small white triangles and pop-up text saying which icon i am pointing at, but not the icons themselves. It's a bug, see [ launchpad ]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762478"). It's still unassigned, hope someone takes it on soon!

---

### Post by kerry_s on 2011-04-19
You try changing your icons, I noticed in the screenshot, the ubuntu logo is not the right 1.

---

### Post by eel on 2011-04-19
> **kerry_s said:**
> You try changing your icons, I noticed in the screenshot, the ubuntu logo is not the right 1.

Tried, not working (was also not using unity theme)

---

### Post by Duncan Williams on 2011-04-19
so like,wat'z the solution?

---

### Post by eel on 2011-04-19
> **Duncan Williams said:**
> so like,wat'z the solution?

so like, there is none right now that i know of...

---

### Post by Duncan Williams on 2011-04-19
ok, thanks.
I am still loving ubuntu natty unity with no icons in the left column and will wait for icons when they arrive, I suppose.

---

### Post by eel on 2011-04-19
yeah i'm sort of trying to do the same (:

---

### Post by Duncan Williams on 2011-04-19
also > tried to watch dvd movie > no encrypted drivers in movie player > no works in vlc > downloading `restricted extras' to see if works then.

---

### Post by cariboo on 2011-04-19
Run the libdvdcss install script in /usr/share/doc/libdvdread4:

```
sudo install-css.sh 
```

---

### Post by oasick on 2011-04-19
[http://ubuntuforums.org/showthread.php?t=1726841&highlight=unity+icons](http://ubuntuforums.org/showthread.php?t=1726841&highlight=unity+icons)

same problem...

---

### Post by Duncan Williams on 2011-04-22
I was doing well with the nouveau drivers that offered themselves in `additional drivers' as `experimental 3d drivers for nvidia cards'.
Could boot into unity, the only real issue was `no icons in launcher' at 1920 by 1024 (on 24" aoc monitor).

Then a few days back `nvidia drivers for 3d support' showed up in `additional drivers' so I installed it. 

After a few boots it sorta worked and then would only come up in 640 by 480 mode.

So I removed the nvidia drivers in `additional drivers'.

Now I am (I think) using nouveau drivers, but I can't set my resolution past 1024 by 1080.

How can I get the system to re-read the monitor and video card again or set to original default. or just get the thing to the right resolution (1920 by 1024)

---

### Post by eel on 2011-04-24
> **cariboo907 said:**
> Run the libdvdcss install script in /usr/share/doc/libdvdread4:

```
sudo install-css.sh 
```

I assume this solution is about the dvd watching, not the icons not showing?

---

