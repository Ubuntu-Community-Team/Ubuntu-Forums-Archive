---
title: "xorg.conf and video problems in 11.04"
date: 2011-09-05
forum: Multimedia Software
---

### Post by AliPM on 2011-09-05
I have an Elonex Webbook, which has a native screen resolution of 1024*600, and for the year or so I've had it I've used 9.04, then 9.10, then 10.04, without too many problems. 

Now I have 11.04 I can't manually change the desktop panel size, it seems the usage of the **xorg.conf** file has changed (it's no longer in /etc/X11/)

The website webbookblog.com showed me how to change the panel size, but the last upgrade it covered was 9.10.

Can anyone tell me how to do what I need to to use my laptop? At the moment I have to use an external monitor.

Thanks!

---

### Post by BicyclerBoy on 2011-09-07
The xorg.conf can be used, it is just not required in 10.10 or 11.04.

Your netbook uses VIA unichrome graphics & I imagine the problem is this driver is not working/availalble for 11.04.
This would explain your current problem.

The VIA Unichrome is/was supported by openchrome & closed VIA driver..It is the least supported video hardware in Linux..
Unichrome support has been dropped/removed in mesa recently..

I can only find the driver package for 10.04..

---

### Post by AliPM on 2011-09-12
Thanks for the reply.

In the past I managed to get it working ok just by writing a new xorg.conf file (as per the instructions on webbookblog).

I've reinstalled 9.10, repeated what worked before but it doesn't change the desktop size to 1024x600. I'm just stuck with the scrolling-lines effect, and no display without an external monitor.

Is there something I need to do to tell Linux where the xorg.conf file I wish to use is located?

---

### Post by BicyclerBoy on 2011-09-12
You can read/post the Xorg log file ...
/var/log/Xorg.0.log

This should reveal if the xorg.conf file is used & what is wrong with it or the driver etc..

Did your netbook originally (new) have a custom linux setup ?

---

### Post by martinkea on 2011-12-22
I have exactly the same problem, am desperately seeking a solution to it, no real idea though how to sort it. is it something to do with screen resolution, or is it something to do with drivers or other settings - i just don't know.
would very much appreciate some help.

---

