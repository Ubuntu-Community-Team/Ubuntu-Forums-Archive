---
title: "Not able to Connect to Jack."
date: 2007-10-21
forum: Multimedia Production
---

### Post by CapitanYochua on 2007-10-21
I'm having problems connecting to the JACK server as a client. 
output in message:
[http://paste.ubuntu-nl.org/41592/plain/](http://paste.ubuntu-nl.org/41592/plain/)
Any help?
-Thank you.

EDIT: I'm a Gutsy user.

---

### Post by 5-HT on 2007-10-21
> 
the capture device "hw:0" is already in use. Please stop the application using it and run JACK againLooks like something's already using your capture device and preventing JACK from starting up. I'd try shutting down any running sounds servers and any apps that may be using them. 
cheers,

---

### Post by CapitanYochua on 2007-10-21
How do I go about that?
I tried rebooting my computer, and then tried it in the past. I still would get the error.

---

### Post by CapitanYochua on 2007-10-24
bump.

---

### Post by Stochastic on 2007-10-26
Open up SystemMonitor (in System -> Administration) and see if anything like ESD is running.  If so, kill it, and try jack again.

---

### Post by CapitanYochua on 2007-10-26
I don't see any ESD in my processes in system monitor, but JACK still won't connect. Could it be a problem with JACK's configuration (like connection, or settings)? Or something I have to do with BIOS?

---

### Post by Stochastic on 2007-10-26
post a list of the processing running right before you try to start jack.  is sound working on your computer?  what soundcard do you have? if you run the following command from a terminal what happens ```
jackd -d alsa
```

---

### Post by CapitanYochua on 2007-10-26
```
joshua@joshua-desktop:~$ jackd -d alsa
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

```

[http://www0.dealtime.com/xPF-HP-Pavilion-Desktop-PC-A720N](http://www0.dealtime.com/xPF-HP-Pavilion-Desktop-PC-A720N)
That has my computer's specs. I was able to connect with JACK when I had Feisty. Sound *is* working on my computer.

---

### Post by Stochastic on 2007-10-27
can you post what processes are running right before you try starting jack?

---

### Post by CapitanYochua on 2007-10-27
bonobo activation server
dbus daemon
evolution-alarm-notify
evolution-data-server
evolution-exchange-storage
firefox
firefox-bin
gconfd-2
gnome-cups-icon
gnome-keyring-daemon
gnome panel
gnome power manager
gnome screen saver
gnome-settings-daemon
gnome-vfs-daemon
gnome-volume-manager
mapping-daemon
metacity
nautilus
nm-applet
pulseaudio
python
run-mozilla.sh
script-fu
sh
ssh agent
update notifier
vino-session
x-session-manager

::Yeap, that's all my processes.

---

### Post by Stochastic on 2007-10-27
try killing pulseaudio then trying to start jack

---

### Post by CapitanYochua on 2007-10-27
Yes, it worked. You rock!
-thanks.

---

### Post by Stochastic on 2007-10-28
now if I were you I'd figure out why pulseaudio is running and look into stopping it if that is a suitable action

---

### Post by CapitanYochua on 2007-10-28
It seems it starts from boot up every time. I'm not even sure why or what it does.

---

### Post by Stochastic on 2007-10-28
Like I said, I'd look into what's starting it and see if it's appropriate to remove that setting.  First step would be to go into a different forum section (Multimedia Production probably isn't appropriate) and start asking about how to figure out why it is starting on boot.  Probably looking into its parent process (if there is one) or into your boot files etc..  I'm not too familiar with PulseAudio but I'm pretty sure it's a newer contender in the options for audio servers (ALSA, OSS, JACK, ESD, etc..) so maybe one of your startup programs is now set to use PulseAudio as default.  But that's about all the help I can be to you.

---

### Post by SupraBlur on 2007-11-03
I'm still having the Jack issue on my Gutsy setup and don't have pulseaudio.  My process list is:

bonobo-activation-server
compiz
compiz.real
dbus-daemon
evolution-alarm-notify
evolution-data-server-1.12
evolution-exchange-storage
gconfd-2
gksu
gnome-keyring-daemon
gnome-panel
gnome-power-manager
gnome-screensaver
gnome-settings-daemon
gnome-system-monitor
gnome-vfs-daemon
gnome-volume-manager
gtk-window-decorator
mapping-daemon
mixer_applet2
multiload-applet-2
nautilus
nm-applet
notification-daemon
pidgin
python
run-mozilla.sh
sh
ssh-agent
swiftweasel
swiftweason-bin
trackerd
trashapplet
update-notifier
vino-server
vino-session
x-session-manager

I tried disabling ESD in the sound settings, and killing the mixer_applet (panel volume control) to no avail.  Any other suggestions?  Sound works fine in other apps.

-Ray

---

### Post by SupraBlur on 2007-11-19
So several weeks later I'm still having this same issue.  I'm about to ditch Ubuntu, this is too much work.

-Ray

---

### Post by Stochastic on 2007-11-19
well from my experience firefox and swiftweasel sometimes has host apps and plugins that occupy the sound server.  try shutting swiftweasel down.  If you're ready to toss out ubuntu based on Jack not working I'd suggest installing UbuntuStudio, for the most part it Jack is setup to work out of the box.  It solved many issues I was having with regular ubuntu.

Actually on second thought why don't you start a new thread on your particular problem rather than re-hashing someone else's that has already been solved.

---

