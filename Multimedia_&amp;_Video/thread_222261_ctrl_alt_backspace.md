---
title: "ctrl alt backspace"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by jrjr on 2006-07-24
I can only perform this once... and ctrl alt f1 as well. If I log back in and try the key combo again my video craps out. It turns into some purplish orange mini columns on just my primary monitor. This is consistent and I can repeat it at will. Reset is the only option. 

ATI drivers in and working. I get good frame rates and the video actually looks awesome. Big desktop works for some users, but not all. Thats another issue. Movies play ok, sound works, etc. 

I did have some issues at install due to being a noob. Maybe I broke something during the process of geting my video working. 

Gigabyte MB
ATI X1600
512 dual channel ram
hyperthreading is on
onboard sound works good

Trying to knock these issues out one at a time.

Please....   some ideas are welcome.

---

### Post by mlind on 2006-07-24
Why do you need to reset Xserver often? Switching between tty's is feature that should work without problems though..

Do you use Xgl or fglrx drivers?

---

### Post by jrjr on 2006-07-24
I don't need to switch a lot. It just doesnt work is all. But if I need to restart X due to making some changes I cannot do it... I have to reboot all the time. Any ideas?

fglrx drivers

---

### Post by jrjr on 2006-07-25
bump

---

### Post by jrjr on 2006-07-25
I just instaled the KDE desktop and would really like to get this working so I could switch back and forth. I cant do it now... the video freezes.

---

### Post by jrjr on 2006-07-26
bump

---

### Post by mlind on 2006-07-26
Does this issue happen with "ati" or "vesa" driver? If it doesn't then fglrx is probably the culprit.. Have you tried searching other threads on the forums for solution?

---

### Post by jrjr on 2006-07-26
Sure, I have spent hours and hours searching both these forums, other disto forums and google. 

Actually this was my first install of Linux. There were some issues during install and setup due to me being a total noob. Maybe im just a noob now. Anyway, I decided to reinstall the OS. I just got all the updates done and now its time to reinstall the ATI driver. 

Maybe this will fix the issue, I will let you know.

Thanks for the response!!

---

### Post by jrjr on 2006-07-26
Things went a lot smoother this time around. I have the big desktop working again and I can switch users, log in and out with no issues. There must have been something tweaked the first time. It wasn't straight forward getting the big desktop working though. 

If you're interested, here's how I did it for my ATI X1600 card, maybe it will help somebody

New Ubuntu install
Did all the updates - 130 of them!

Next I went for the ATI driver
first I did this:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

Then I ran this (not really sure why but it must tell the driver that there are 2 monitors and to use them in the horizontal config)

```
# aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v
# /etc/init.d/xdm restart
```

Next was this:
```
sudo dpkg-reconfigure xserver-xorg
```

At this point I was scratching my head again as I had great video but the monitors were in clone mode. Changing the ATI control panel located in Applications/Accessories did nothing. I changed the setting but it would not stick. 

Next I tried running that with sudo
```

sudo /usr/bin/fireglcontrolpanel
```

That didnt work either

Next I enabled root login, logged in as root, and changed the panel to big desktop.
I logged out of x and back in... no good.
Then I rebooted and voila there it was!!
Yippee! 
Now the sudo command may have worked if I had rebooted, I cant say for sure because all I did was restart X after sudoing the ATI control panel.

Anyway, there you have it... my procedure. Sure hope it works for someone else!!!  

CHEERS to all that have helped me along this far... there is mucho more to learn.

moi'

---

### Post by jrjr on 2006-07-26
Ok well I take it back.. well some of it anyway

I just found out that I am only getting 180 fps with glxgears now. This is a first for this problem.... if its not one thing its another!!

Before reinstall I was almost at 3000 fps

---

### Post by jrjr on 2006-07-27
I had the mesa drivers installed. 
Following this got me back to 3000 fps in glxgears - 

[http://www.ubuntuforums.org/showthread.php?t=195845](http://www.ubuntuforums.org/showthread.php?t=195845)

---

### Post by Thirsteh on 2006-07-27
jrjr, the next time around, you may get a lot more help if you provide X.org's server logs, or any other log that may indicate what the problem is.

---

### Post by jrjr on 2006-07-27
Ok thanks. Everythings seems to be working... good frame rates, dual head, big desktop etc. The ATI control panel disapeared out of the applications menu though... thats odd 

I dont really plan on switching modes, but why did it go away?

edit-

jack@ubuntudesktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by jrjr on 2006-07-27
> **Thirsteh said:**
> jrjr, the next time around, you may get a lot more help if you provide X.org's server logs, or any other log that may indicate what the problem is.

I'm not sure what info I would offer to find out what happened to the control panel. Let me know and I will post it.

---

### Post by jrjr on 2006-07-27
If I use this
/usr/bin/fireglcontrolpanel

The panel opens ok... 
But there is no option ticked for desktop setup.
NONE!

---

### Post by jimmygoon on 2006-07-27
If you are wanting to switch between kde and gnome, why don't you just log out rather than reseting the X server?

---

### Post by jrjr on 2006-07-27
From post #9 of this thread... 

> **jrjr said:**
> Things went a lot smoother this time around. I have the big desktop working again and I can switch users, log in and out with no issues. 

I got that part working so its a non-issue

---

### Post by jrjr on 2006-07-28
.

---

### Post by jrjr on 2006-07-28
.

---

### Post by jrjr on 2006-07-28
.

---

### Post by jrjr on 2006-07-29
.

---

### Post by jrjr on 2006-07-29
.

---

