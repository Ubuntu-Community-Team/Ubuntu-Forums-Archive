---
title: "Audacity doesn't have menu"
date: 2010-10-21
forum: Multimedia Software
---

### Post by kingofmakai on 2010-10-21
Hello every body. I have a problem with Audacity and need your help.
I installed Audacity from Software center and launched it but it didn't have menu like this.
[IMG]http://ca6.upanh.com/14.1006.19248773.Odk0/screenshotaudacity.jpg[/IMG]
I tried to lauch it in Terminal and here is output in Terminal:
```

Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
no more csLADSPA plugins

```
Can you help me fix this problem. Thankyou so much!

---

### Post by sanderd17 on 2010-10-21
I have the problem too, this happens also with Golly, I'll look for a bug on launchpad, maybe there's a fix.

---

### Post by sanderd17 on 2010-10-21
There is already a thread about it: [http://ubuntuforums.org/showthread.php?p=10005362]("http://ubuntuforums.org/showthread.php?p=10005362")

I suggest further discussion will happen on the other thread.

---

### Post by formerWindowsUser on 2011-01-10
On all four of my computers, with Ubuntu 10.10 installed, Audacity had a menu.  A few days ago I tried out the Unity interface by using Synaptic and installing ubuntu-netbook and unity (not sure) on my main computer.  Everything seemed to be normal until I tried running Audacity today.  Now the menu bar is gone!

I tried uninstalling ubuntu-netbook and unity and the menu bar is still gone.  The other three computers have essentially the same software as my main (except for ubuntu-netbook and unity) and are fine.

I put the gnome-applet-globalmenu 0.7.10 in the panel and the Audacity shows up there.

I hope this helps someone find the cause/solution.:)

---

### Post by mikeg9b on 2011-01-17
I had the same problem.  I suspect the problem arose because I downloaded the Ubuntu Netbook Edition and then switch to the regular Gnome Ubuntu.

Here's what fixed it for me:

[http://www.techytalk.co.cc/2010/12/ubuntu-maverick-10-10-no-menu-bar-in-some-apps/](http://www.techytalk.co.cc/2010/12/ubuntu-maverick-10-10-no-menu-bar-in-some-apps/)

Basically, it amounts to removing the package: appmenu-gtk

---

### Post by formerWindowsUser on 2011-01-17
I did the same thing (downloaded the Ubuntu Netbook Edition and then switch to the regular Gnome Ubuntu).

Tried the fix and it got my menus back. We'll see if this is the "real" fix. Thanks:p

---

### Post by MarkoCro on 2011-03-03
> **mikeg9b said:**
> I had the same problem.  I suspect the problem arose because I downloaded the Ubuntu Netbook Edition and then switch to the regular Gnome Ubuntu.

Here's what fixed it for me:

[http://www.techytalk.info/ubuntu-maverick-10-10-no-menu-bar-in-some-apps/](http://www.techytalk.info/ubuntu-maverick-10-10-no-menu-bar-in-some-apps/)

Basically, it amounts to removing the package: appmenu-gtk

Link has changed from co.cc to info domain:
[http://www.techytalk.info/ubuntu-maverick-10-10-no-menu-bar-in-some-apps/](http://www.techytalk.info/ubuntu-maverick-10-10-no-menu-bar-in-some-apps/)

---

