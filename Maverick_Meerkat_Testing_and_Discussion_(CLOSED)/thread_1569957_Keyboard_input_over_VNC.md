---
title: "Keyboard input over VNC"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by retrow on 2010-09-07
I have been using Ubuntu 10.10 since alpah-1 and one of the features that has always worked fine for me was the VNC server/viewer. Since updating to 2.6.35.20, the keyboard inputs via VNC have stopped working completely. 

When you try to hit any alphanumeric key for inputting text or command to an application, it causes the application window to minimize or completely crash. When you are actually using that machine, you can use the keyboard just fine - the input problem is only when you are using a VNC over SSH.

Anyone having similar problems or knows of workarounds?

---

### Post by aaronwball on 2010-09-08
Howdy,

I have the same problem. I installed maverick meerkat on my test server at home (that REALLY helps find bugs fast) and have noticed the same issue.
Buckle down for lots of information (or lack thereof perhaps)! 
;)

Everything in the installation of vnc4server worked well.
I ran vncpasswd alright. 
After creating an ssh tunnel (5901), I run vncserver :1. The vnc server starts with no errors. I connect to localhost:5901 and everything connects fine. I can click through menus and run programs fine until I need to input anything with the keyboard.

If for instance I am in terminal, upon typing anything, terminal crashes. If I have the desktop selected and type something (to select a folder by letter for instance), nautilus crashes. 
Interestingly enough, if I try to run something (alt + f2), the run window comes up, nautilus crashes (along with the window), and nautilus restarts (window no longer up). 

Here is the error I am receiving taken from my ~/.vnc/hostname :1.log file
**When I try to input into a terminal window, I get...**

(nautilus:3011): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

Gdk-ERROR **: Failed to get keymap
aborting...


**When I try to input anything into nautilus (run window, the file manager, etc), I get...**

Gdk-ERROR **: Failed to get keymap
aborting...
Initializing nautilus-gdu extension

(nautilus:3011): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Now, some more interesting stuff...

When I don't have gnome-session set to execute on vnc display creation (vncserver :1), I get the typical grey screen of nothingness with a terminal window. When I input keyboard text into the terminal window, it crashes. Not sure if that's gnome since I didn't specify "gnome-session &" in my xstartup file.

Also tried running as root.

**Here's my xstartup...**

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
gnome-session &





Thoughts anyone?

---

### Post by Bachstelze on 2010-09-16
Same problem here on tightvnc. Probbly GTK-relatd because of the message and that it doesn't happen on non-GTK apps.

---

### Post by Bachstelze on 2010-09-17
By the way, a workaround is to just use ssh -X instead of VNC. Might not be convenient depending on what you want to do, though.

---

### Post by andy.stallwood on 2010-09-18
I am having the same problem, so I have created a bug under vnc4server - [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/642120](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/642120). It may be that this isn't actually a bug in vnc, but I don't have the knowledge to know what it is, so hopefully it'll get moved if appropriate.

---

### Post by cabbrick1243 on 2010-09-24
This bug is also at [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/638686?comments=all](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/638686?comments=all)

---

