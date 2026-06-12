---
title: "Resolution Issue @ login screen"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SolvedSnake on 2010-09-21
Ubuntu has set my resolution to an extremly high setting. I could change it back to what I want on the desktop ( 1024x768 ), but how can I change it back on the login screen? (before logging in to GNOME)

I tried searching around on google, but people say that Ubuntu now automatically configures it or something.
Does that mean I can't change the login resolution?

---

### Post by tormod on 2010-09-21
See III.5 on [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by DevHead on 2010-09-21
I'm having this same issue.

I feel like I shouldn't have to do something just to make the resolution correct.  Never had to before.  Now with Maverick, it's starting to look that way. :(

---

### Post by antiram on 2010-09-21
gnome-display-properties has a button for systemwide settings, but systemwide save doesn't work. it works on fedora 14 with a monitors.xml file in /etc/gnome-setting-daemon/. maybe the file is located elsewhere in ubuntu (/usr/lib or share or so). 

easiest for now is a xrandr command in /etc/xprofile (new file, don't forget chmod +x)

---

### Post by SolvedSnake on 2010-09-23
Okay, I have found a solution.

I opened up a terminal 

```
cd /etc
sudo mkdir gnome-settings-daemon
cd gnome-settings-daemon
sudo mkdir xrandr
gnome-display-properties

```

And now make default works!

---

### Post by DevHead on 2010-09-23
Seems to work for me too (fingers crossed).

---

### Post by antiram on 2010-09-23
works and reported here
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/646076](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/646076)

---

### Post by oasick on 2010-09-23
> **SolvedSnake said:**
> Okay, I have found a solution.

I opened up a terminal 

```
cd /etc
sudo mkdir gnome-settings-daemon
cd gnome-settings-daemon
sudo mkdir xrandr
gnome-display-properties

```

And now make default works!

thank you! now works :)

---

### Post by tormod on 2010-09-23
> **antiram said:**
> works and reported here
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/646076](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/646076)

awesome, thanks a lot!

---

### Post by jaycee23 on 2010-10-02
> **SolvedSnake said:**
> Okay, I have found a solution.

I opened up a terminal 

```
cd /etc
sudo mkdir gnome-settings-daemon
cd gnome-settings-daemon
sudo mkdir xrandr
gnome-display-properties

```And now make default works!

Another happy chappy. Worked for me with the RC release. My graphics card is in my sig if anyone's interested

---

