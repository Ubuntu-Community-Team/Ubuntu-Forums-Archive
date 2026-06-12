---
title: "Can't get VNC connection to work"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by DJ Barney on 2010-02-03
Hi,

I connected from the Asus EeePC (Jaunty) to my Karmic machine using Remote Desktop - Vinagre to the Vino server over ethernet. However despite getting a connection I could not see the changes I was making - I can control the desktop but the client never updates the screen. It works perfectly connecting to Real VNC on my Windows machine.

I tried installing Real VNC from the package manager but the X vnc module does not load - missing symbol. So I decided to compile from source but the build fails on making the tcp networking part.

I need a solution to control my desktop from the Eee and am confused as to why none of this works. I have tried everything I know of. I have read the README's carefully and I cannot understand why I can control Windows from Ubuntu but not another Ubuntu desktop (well I can but as I said I can't see the changes just a static image).

Please help !

---

### Post by Alasta on 2010-02-04
I think I am having the same issue , interestingly i have three computers all running Ubuntu 9.10 . I can control my laptop no problem at all but my other desktop connected with an ethernet cable to the wi fi router I have no joy . I can control the desktop but I cant see what I am doing on the remote desktop .

---

### Post by DJ Barney on 2010-02-04
I found the solution. Compiz was active on the machine I was trying to control. I turned it off and the screen now updates. Thankyou.

---

### Post by Menthu_Rae on 2010-02-04
You can also run a different VNC server like x11vnc. I have it running with compiz enabled no worries, just be sure to use the -noxdamage flag.

```
x11vnc -usepw -forever **-noxdamage** -nolookup -q -repeat
```

---

### Post by DJ Barney on 2010-02-04
Oh thanks. How easy is that to install ? I might have to try x11vnc if Vino is not fast enough as I am controlling Mixxx - a DJ mixer, so the response has to be fast. Does it require an X11 module ? I tried using the X11 module that comes with Real VNC that I installed through package manager and it is incompatible with my X server which is also installed through the package manager - actually a broken package that needs reporting.

---

### Post by Menthu_Rae on 2010-02-05
> **DJ Barney said:**
> Oh thanks. How easy is that to install ? I might have to try x11vnc if Vino is not fast enough as I am controlling Mixxx - a DJ mixer, so the response has to be fast. Does it require an X11 module ? I tried using the X11 module that comes with Real VNC that I installed through package manager and it is incompatible with my X server which is also installed through the package manager - actually a broken package that needs reporting.

Just:

```
sudo apt-get install x11vnc
```

Dude :D Try it, if you don't like it - don't run it.

---

### Post by DJ Barney on 2010-02-07
Thanks, but the reason I ask is that I have some disabilities and a lack of time to try lots of different versions of VNC.

---

### Post by Menthu_Rae on 2010-02-10
> **DJ Barney said:**
> Thanks, but the reason I ask is that I have some disabilities and a lack of time to try lots of different versions of VNC.

Hey, I'm not sure what your disabilities are - but it's not hard or time consuming. I'm just trying to help you out and stop you from getting frustrated!

Install it with the command above and run it with the command above that!

i.e.

```
sudo apt-get install x11vnc
```

Then from a terminal you can run:

```
x11vnc **-usepw **-forever -noxdamage -nolookup -q -repeat
```

Once you've set the password, you can add it to "Startup Applications" in System > Preferences. Will take all of 2 minutes. :o

---

