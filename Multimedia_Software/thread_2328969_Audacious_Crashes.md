---
title: "Audacious Crashes"
date: 2016-06-26
forum: Multimedia Software
---

### Post by kc1234 on 2016-06-26
To start with, I'm new to the forums, so please forgive me if this is the wrong place for this.

But anyway, I have been running Lubuntu for 3 or 4 years now and just did a fresh install of Lubuntu 14.04 and Audacious crashes as soon as I right click on it. 
I added the ppa to install Audacious 3.7 from here: [http://www.webupd8.org/2015/11/audacious-37-released-available-in-ppa.html](http://www.webupd8.org/2015/11/audacious-37-released-available-in-ppa.html)
When I run apt-get install audacious in the terminal, it says something about broken packages and is never installed. So I removed the ppa and installed Audacious 3.4.3-1 again. 
I ran it from the terminal and I get this:


WARNING: Audacious seems to be already running but is not responding.

** (audacious:2644): CRITICAL **: Error creating UI<ui/mainwin.ui>: Failed to open file '/usr/share/audacious/ui/mainwin.ui': No such file or directory

(audacious:2644): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(audacious:2644): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault (core dumped)

If anyone could help it would be much appreciated, I ran Audacious 3.7 on my previous install without any problems and would like to do so in my new one 
Thanks in advance to anyone who responds

---

### Post by ajgreeny on 2016-06-26
Try removing or renaming the configuration for audacious in **~/.config/audacious** and see if that helps; perhaps there is some problem with your config.

---

### Post by kc1234 on 2016-06-26
I just tried removing it, thinking maybe Audacious would make a new one, but I still get the same error in the terminal. Also I removed the Audacious folder in ./config and reinstalled and the only error I get when I run Audacious from the terminal is that it cannot connect to pulse audio, it seems as thought the problem lies with the winamp interface

---

### Post by mc4man on 2016-06-26
try starting from terminal with this, maybe something will show up relevant
audacious -V

As far as the web8 version - have you used the MuseScore  ppa?, if so then you'll have issues with other packages that have qt5 deps

---

