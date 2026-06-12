---
title: "Dueling screensavers"
date: 2013-08-17
forum: Mythbuntu
---

### Post by donb21 on 2013-08-17
After using the MythBuntu control center to change the system role to "ubuntu", two screensavers are running (Gnome and xscreensaver).  Which one should I turn off and how?  Here's a capture of the settings:

[http://users.zoominternet.net/~dlbrett/ScreenCapture_313.jpg](http://users.zoominternet.net/~dlbrett/ScreenCapture_313.jpg)

Note - Clicking "OK" turns it off, but it comes back on the next reboot.

---

### Post by ajgreeny on 2013-08-17
I have no idea which one comes by default with mythbuntu, but I assume gnome-screensaver is the default with normal ubuntu.  Personally I believe that xscreensaver is the better of the two; it is much more configurable that gnome-screensaver, which allows you to set the actual saver graphics, but not much else.  I use xscreensaver on my xubuntu machine and choose the glslideshow to show a folder of chosen photographs from my many thousands of photos on the machine, something you can not do in the GSS any more.

As you can guess probably, my suggestion is to use xscreensaver, even in your gnome/unity system, and if it is possible without also removing some needed packages, I would uninstall gnome-screensaver.

---

### Post by donb21 on 2013-08-18
From what I've read, a lot of people agree with you about preferring xscreensaver, so I removed gnome-screensaver.  Not sure if I lost anything else; I may have since the background changed, but at least the contention is gone.  Another thing happened after the switch-over...a keyboard appeared; not sure what it's for.  I'll start another thread for it.  Thanks for the suggestions.

Capture of desktop after removing gnome-screensaver:
[http://users.zoominternet.net/~dlbrett/ScreenCapture_314.jpg](http://users.zoominternet.net/~dlbrett/ScreenCapture_314.jpg) 

Command used to remove screensaver:
sudo apt-get remove [COLOR=#000000]gnome-screensaver


[/COLOR]

---

### Post by ajgreeny on 2013-08-18
You can easily see what was removed along with gnome-screensaver by running command ```
grep -iw remove /var/log/dpkg.log.1 && grep -iw remove /var/log/dpkg.log
```and seeing what was removed at the same time as gnome-screensaver, give or take a second or two.

In my opinion this is a very good reason for using synaptic package manager which would show you clearly what else will be removed.  The terminal does tell you too, but perhaps not as easily understood as the pop-up that synaptic gives you.

---

