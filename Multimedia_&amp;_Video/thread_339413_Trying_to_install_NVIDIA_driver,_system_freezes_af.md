---
title: "Trying to install NVIDIA driver, system freezes after I stop GNOME"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by jbayone on 2007-01-15
I'm trying to uninstall the currect video driver that I have, then reinstall an older one, but everytime I stop GNOME, my system locks up on "running local scripts."  I've tried waiting for a few minutes to see if it was just taking a while; I can ctrl-alt-delete to restart and that seems to respond but nothing else.  

Is there an easier way to go about this?  I've been having the "system freezes, but mouse can move" problem for a few days.  It only takes about a minute, maybe less for this to occur.  I've got a GeForce 4ti 4200.  Any suggestions would be appreciated.

---

### Post by scrooge_74 on 2007-01-15
How are you stopping Gnome?

Are you using the instructions from this site? 

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by jbayone on 2007-01-15
sudo /etc/init.d/gdm stop

---

### Post by scrooge_74 on 2007-01-16
try running in recovery mode

---

### Post by jbayone on 2007-01-17
I was able to install the driver in recovery mode, but it didn't help the problem.  I don't know what else to try.

---

### Post by Fitzy_oz on 2007-01-17
> **jbayone said:**
> I'm trying to uninstall the currect video driver that I have, then reinstall an older one, but everytime I stop GNOME, my system locks up on "running local scripts."  I've tried waiting for a few minutes to see if it was just taking a while; I can ctrl-alt-delete to restart and that seems to respond but nothing else.  

Is there an easier way to go about this?  I've been having the "system freezes, but mouse can move" problem for a few days.  It only takes about a minute, maybe less for this to occur.  I've got a GeForce 4ti 4200.  Any suggestions would be appreciated.

Use the GLX Legacy driver for the 4200ti, I'm pretty sure when I tried to install the propritary driver it told me to use the legacy driver anyway.

sudo apt-get install nvidia-glx-legacy i think is the correct command.

---

### Post by jbayone on 2007-01-17
Do I need to uninstall anything I've already done?  If so, how would I go about that?

---

### Post by Fitzy_oz on 2007-01-17
> **jbayone said:**
> Do I need to uninstall anything I've already done?  If so, how would I go about that?

I don't think so, apt-get should take care of that for you...
It's probably easier to do it via synaptic package manager.  Do a search nvidia and select the package - Once installed just run sudo nvidia-glx-enable in the terminal and reboot.  Should be right after that./

---

### Post by jbayone on 2007-01-17
I wouldn't be able to do this with synaptec because I everything freezes right after I login.

---

### Post by Fitzy_oz on 2007-01-17
> **jbayone said:**
> I wouldn't be able to do this with synaptec because I everything freezes right after I login.

ahhh i see what's happening here.

Kill the Xserver by pressiing ctrl+lt+f1.

Type the following - dpkg-reconfigure -phigh xserver-xorg (I have had to run this so many times that I remember it off the top of my head)

Set your graphics driver to "nv" and then rtestart.  You should have gnome back, then follow the process above.  :)

---

### Post by jbayone on 2007-01-18
That didn't work either.  Same results-the picture is weird looking and it freezes right after login.

---

### Post by Fitzy_oz on 2007-01-18
> **jbayone said:**
> That didn't work either.  Same results-the picture is weird looking and it freezes right after login.

run sudo dpkg-reconfigure -phigh xserver-xorg and take it back to vga and try again.  If possible, can you paste your /etc/X11/xorg.conf file here for us to look at...

---

### Post by jbayone on 2007-01-18
When I did run sudo dpkg-reconfigure -phigh xserver-xorg, I only had the option to select the resolution, not any option for drivers.

---

### Post by Fitzy_oz on 2007-01-18
> **jbayone said:**
> When I did run sudo dpkg-reconfigure -phigh xserver-xorg, I only had the option to select the resolution, not any option for drivers.  Maybe try the loest possible resolution.  Try typing the following also: sudo init 1.  Then startx.....  See if it starts under the root user

---

### Post by scrooge_74 on 2007-01-18
If you are having problems to boot , maybe boot from a Live CD and then go to your xorg.conf file on the HD and change the driver to nv so you can start back from the beginning

---

### Post by jbayone on 2007-01-20
No luck booting from the live CD either.  Gnome seems to start, then gives some weird scrambled display.  How can I post my xorg.conf on here from the command line?  I'm on another comptuer right now and have no way of getting on the internet on the computer with the problem.

---

### Post by jbayone on 2007-01-21
I've got it fixed now.  I have no idea what was wrong, I was getting errors like "HAL failed", "runlevel failed".  I was able to boot from the live cd after changing the resolution to 800x600, then reinstalled and was able to install the nvidia driver and set up twinview.  Thanks guys.

---

