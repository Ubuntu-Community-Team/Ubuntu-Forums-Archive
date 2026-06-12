---
title: "Multiple instances of nm-applet"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by speckone on 2006-06-07
I have three instances of nm-applet running whenever I boot up.  I removed nm-applet from my "Autostarted applications", but I still get 3 instances of nm-applet.

```
speckone@speckone-laptop:~$ locate nm-applet
/home/speckone/.config/autostart/nm-applet.desktop
/etc/dbus-1/system.d/nm-applet.conf
/etc/xdg/autostart/nm-applet.desktop
/usr/bin/nm-applet
/usr/share/nm-applet
/usr/share/nm-applet/applet.glade
/usr/share/nm-applet/keyring.png
/usr/share/man/man1/nm-applet.1.gz
speckone@speckone-laptop:~$

```

Any ideas?

---

### Post by angusvitamin on 2006-06-08
i recall from breezy after installing nm-applet. Everytime I closed nm-applet it opens another(few others) up and i would have to do a killall to stop it. thats the time i switched to gtkwiki, except for some reason it doesn't work anymore after the upgrade to dapper.

---

### Post by speckone on 2006-06-08
I don't have any problem with closing nm-applet.  I have 3 instances that start with the desktop.  I can close two of the instances and everything is fine.  How can I find out why all three instances start and what process is starting them?

---

### Post by martinquested on 2006-10-10
I have this problem too: except I get about 17 instances of nm-applet running each time I boot.  Plus, nm-applet does not store my WPA key and I have to paste it in each time before the thing will run.  However, I am fortunately able to "remove" the applet so that I just have one running.

Did anyone find a solution so that just one of them runs when they boot up?

Would be most grateful if you would share it if you did!

Thanks.

mQ

---

### Post by reacocard on 2006-11-07
> **speckone said:**
> I don't have any problem with closing nm-applet.  I have 3 instances that start with the desktop.  I can close two of the instances and everything is fine.  How can I find out why all three instances start and what process is starting them?

I'm having this exact same problem.  Anyone know how to fix this?

---

### Post by mpwoodall1969 on 2006-11-20
Have you guys had any luck with this issue.  I just got everything running, connect to vpn, rdesktop, and all that.  Now I have 4 nm-applets on my desktop.  I killed all but one, rebooted and there they were again.

---

### Post by martinquested on 2006-11-21
I have since moved to a new computer and am running KDE, and knetworkmanager doesn't do that multiples thing.

I read somewhere something about killing all of the instances, saving the desktop status (it's an option somewhere when you switch off), rebooting (they should all be gone) and then starting one of them.  Good luck...

---

### Post by age6racer on 2007-07-23
I'm having the same problem, it has something to do with killing the instance and then starting a new one from the command line. Each time I do that it adds another one to the amount that start with xfce each time I log in.

How can we get this to stop, it's really irritating!

---

### Post by dapayne12 on 2007-08-04
Hi,

I also have this problem, here is a bit more details.

I use Xfce, installed via xubuntu-desktop from the ubuntu install.  At first I wasn't getting any nm-applet so I added it to the startup applications unedr Applications->Settings->autostart applications.  I shortly found out that each time I log in I get the same amount of nm-applets as last time + one more.  I quickli removed it from the startup applications.  I then did "pkill nm-applet" and logged out and in again.  The good news is I did not have the + 1 this time, I just had the same amount as last time.  I then did another pkill nm-applet and restarted, again they came up.  I then did a pkill nm-applet.  This time when I was logging out I selected Save Session for future logins, but when I logged in they were still there.  Playing around I found nm-applet.desktop under ~/.config/autostart, I removed that file but they still come up on restart.  I am out of ideas.

Thanks,

David Payne

---

### Post by noob12 on 2007-08-04
For the Xubuntu / xfce users, this outside thread might help [http://www.nabble.com/Multiple-Instances-of-nm-applet-t4114321.html](http://www.nabble.com/Multiple-Instances-of-nm-applet-t4114321.html)

Everyone check that your startup commands all use the --sm-disable flag.

BTW, the nm-applet man page sucks; nm-applet --help provides minimal clues but at least lists the options.

---

### Post by dapayne12 on 2007-08-04
I agree, the man page for nm-applet is crap.  I managed to get it fixed after poking around with grep in .cache.  My solution is somewhere in that thread to.  Thanks for the reply.

I was going to post how I fixed it.

David Payne

---

### Post by someb0dy on 2007-11-13
What i did was killing all nm-applet's processes, then editing file /home/w0rm/.cache/sessions/xfce4-session-w0rm-laptop:0 and removing nm-applet entry from there. Then I rebooted without saving current session. It helped.

---

