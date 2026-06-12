---
title: "Dual Monitor/Head; Two Video Cards"
date: 2010-12-11
forum: Multimedia Software
---

### Post by magdon on 2010-12-11
I am running X on ubuntu 10.10. I have 2 identical graphics cards hooked up to 2 identical monitors. The problem is that only 1 card is detected so one monitor is blank. xrandr -q only shows one card/monitor.

So, I forced creation of xorg.conf using "X -configure" as root. Both cards are detected as can be seen from xorg.conf, but now both displays show the same image. I want one big image using both screens. Question: can I achieve this now using xrandr, now that both cards are defined in xorg.conf, or do I need to manually edit xorg.conf. If so, how? What do I need to manually add to xorg.conf to achieve this?

Side question: why did X remove xrandr ability to detect 2 cards?

Help appreciated.

---

### Post by magdon on 2010-12-12
I managed to find a solution that worked for me, but it is ugly. I would bow down to anyone with a better solution. Just in case others are having my same problem, I will post the sequence of steps which ultimately worked for me.

1. Boot into recovery mode as root and run X -configure. This created an xorg.conf.new file which I copied to /etc/X11 as xorg.conf. (There are many posts on how to do this so I wont elaborate).

2. Now if you reboot, this newly created xorg.conf file is used. It sets up both monitors to approximately work as two separate  desktops which can be treated independently. I say approximately because some applets (like This is kind of nice, but not what I wanted. I wanted one big desktop across both monitors.

3. A simple fix to my ServerLayout section in xorg.conf fixed this and introduced another problem. You just add
    Option           "Xinerama" "on"
to that section. 
So my ServerLayout section now looks like:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen1" 
    Screen      1  "Screen0" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option           "Xinerama" "on"
EndSection

4. You are now ready to restart X (CNTRL-ALT-Backspace)

5. Now I have one big desktop and can move windows across monitors. However, THERE IS A BUG IN THE X-SERVER which causes certain applications (QT) to crash X and force restart. This is bad (for me) because one of those apps is emacs which I use heavily. Other apps are virtualbox, skype,...Luckily this is a documented bug. See:

[https://bugs.launchpad.net/xorg-server/+bug/650539](https://bugs.launchpad.net/xorg-server/+bug/650539)

These applications generate the error report:
Xlib:  extension "RANDR" missing on display ":0.0"  
forcing restart of X.

Also, luckily, there is a bug fix available but it has still not been pushed out as a server-update. So you have to install it yourself: 

[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539]("https://launchpad.net/%7Ejared-bunting/+archive/xorg-xserver-650539")

Check out: 
[http://linuxers.org/howto/how-install-any-software-ubuntu-ppa](http://linuxers.org/howto/how-install-any-software-ubuntu-ppa)
If you don't know how to install a bug fix from a PPA (you would be like me in that case).

Now everything works fine, except the annoying error report: Xlib:  extension "RANDR" missing on display ":0.0"  still occurs, but the server does not crash and all applications seem to be working properly.

Good luck...;)

---

### Post by robbie d on 2010-12-12
Glad you have found a solution, this has bugged me (lol) since 10.04, everything worked ok for me up until then. I'll try it tonight on my machine. It doesn't sound too clunky, just like starting with a fresh xorg.conf :)

---

### Post by robbie d on 2010-12-13
hmm didn't work. Oh well nothing new there.

---

### Post by magdon on 2011-01-03
Did you get an xorg.conf file which has entries for both monitors?

---

### Post by BicyclerBoy on 2011-01-03
If you were using an nvidia GPU & nvidia X server then doesn't twinview do this ?

---

