---
title: "Screen darkens on boot, shutdown and VLC"
date: 2008-04-28
forum: Multimedia Software
---

### Post by bertilow on 2008-04-28
I've got a screen brightness problem in Hardy Heron. For some reason the screen brightness goes way down on boot - somewhere when the hardware drivers are being loaded. It remains very dark at the log-in screen (but it's possible to log in if you squint). When the desktop is fully loaded the full brightness comes back automatically. When the computer is shutting down, the brightness goes down again. When the brightness is down, the laptop keys for brightness don't work. Once the brightness comes back, they start working.

I could live with that - I use passwordless auto-login anyway, so I don't really need to see anything before the desktop is loaded. But unfortunately the same thing happens at other times as well. If I change anything about "Monitor & Display" in the KDE Control Center, the screen goes dark again. And if I start VLC, the screen goes dark again. (No such problem - yet - in Kaffeine, but Kaffeine is not really very usable...)

I can always get the brightness up again using the Power Management applet (touching the brightness settings there wakes things up again), but that is no real solution.

I saw this the first time with one of the beta realeases of the Hardy Live CD. It's still there in the final realease. I never saw anything like this on older versions of Ubuntu or Kubuntu.

I have a Lenovo 3000 C22 laptop. I'm on Kubuntu Hary Heron 8.04. I did a fresh install.

What could I do to fix this? (I've seen that others here have somewhat similar brightness problems, but no one seems to have exactly the same situation.)

---

### Post by toemos on 2008-05-21
hey mate

i had the same problem with VLC, i fixed it by turning off the window transparency. I never noticed it with the log in screen or when shuting down.

hope this helps :)

---

### Post by bertilow on 2008-05-21
> **toemos said:**
> i had the same problem with VLC, i fixed it by turning off the window transparency. I never noticed it with the log in screen or when shuting down.

Window transparency? Is that a setting in VLC or somewhere else? Maybe it's a Compiz thing. I don't use Compiz (or anything similar). And I use Kubuntu.

BTW: The same dimming also happens when I start Virtual Box - or rather when I start a virtual OS in Virtual Box. Actually the dimming occurs at least three times (maybe more) during a boot of Windows Vista in Virtual Box. If I try to do something else while Windows is booting on another desktop, I constantly have to use the Power Manager applet to get the screen brightness back. :(

---

### Post by davey.moore on 2008-05-27
I have the exact same problem as you.
It happens since I upgraded to Hardy.

I don't have kubuntu though, just regular ubuntu, but I do use compiz and transparencies.

Same problem as you... gets dark at login, logout, when i start video, and when i start VirltualBox.

However it can't be linked to Kubuntu/Ubuntu, or Compiz (as you don't use), or to a specific video player, as it happens to me with all that i have tried...

---

### Post by jaygo on 2008-09-12
I only experienced this with VLC, while running it in fullscreen, and only recently. 

In KDE, I quick-fixed it by going to system settings > window behavior > translucency > use translucency/shadows = uncheck + apply.

It'd be nice to find a permanent solution but for now I'll just avoid VLC in fullscreen.

GLHF

---

### Post by ublackwhiteu on 2008-10-08
same problem here
ubuntu 8.04 Hardy Heron on a Lenovo 3000 C200 notebook.

can't solve this issue with vlc. if someone has an idea, please answer.



I solved the darkness at startup by writing a script for xbacklight:

install xbacklight (synaptic)

create a file with this content:
```
#!/bin/bash
xbacklight -set 50
xbacklight = 100
```


save the file as lighter.sh

make it executable:

```
chmod +x /PATHTOFILE/lighter.sh
```

and ad it to the startup programs through the main menu.



when the desktop loads, the screen will become bright again. 


(but the darkness of bios, grub and log-in remains)

---

### Post by openseastar on 2010-01-24
Hi guys,

I don't have any trouble on startup, but while watching a movie with VLC 1.0.2 and ubuntu 9.10, the screen goes dark every 5 minutes, and I have to move the mouse to avoid this.
Using any other program than VLC media player, I don't have this issue, so it doesn't come from my power settings...
Can anyone help?
Thanks

---

