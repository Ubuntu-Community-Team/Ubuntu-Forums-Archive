---
title: "I broke my nvidia driver :("
date: 2008-10-26
forum: Multimedia Software
---

### Post by frendofthedevil on 2008-10-26
So yesterday I was playing WoW and decided to see how recent my video driver was.  From there I decided it would be a good idea to update it, as there was a much newer driver available. I was following this thread: [http://ubuntuforums.org/showthread.php?t=797270]("http://ubuntuforums.org/showthread.php?t=797270")
but managed to mess it up.  I overlooked the write down the directions part, and it brought me to the "command prompt" without me knowing what to do next... from there I shut down the computer because I was stuck, and I havent gotten things to work since.  I messed around with a few nvidia guides until I found envyng, and got that to run.  It claims to have installed the latest driver, but I dont seem to have the ability to watch movies (without terrible skipping), and WoW wont start up due to not being able to find a suitable display device.  But, everything else works perfectly.  So my guess is that something is wrong with the 3d rendering in the driver, but I don't know how to fix it.  I hate to break down and ask for help, but I literally spent 6 hours trying to fix this last night and I cant keep that up...  Any help would be very much appreciated.

The graphics card is an NVIDIA 8600gt in an Inspiron 1520 running Ubuntu Hardy Heron... I'm sure there's more relevant information but I am too drained to think of it :/ .

---

### Post by darthshak on 2008-10-27
There is nothing to fear

Write the following instructions this time :)
First, do a clean wipe of whatever you got off envy:
```
sudo apt-get remove --purge nvidia*
```
Next, do ```
sudo apt-get install build-essential
``` -> This is necessary for the drivers to compile a kernel interface for your drivers.

Next, go to the nvidia website, download the latest drivers
-> Press Ctrl+Alt+F1 to go to the terminal
-> Close your display manager : ```
sudo /etc/init.d/gdm stop
```
-> Go to the directory where you downloaded the driver. Log in as admin. ```
sudo su
```
->```
sh <driver_file_name>
```
Once you're done, ```
sudo reboot
```

---

### Post by frendofthedevil on 2008-10-27
Perfect!  Thanks a ton, it was the purge nvidia that I hadn't tried before.  Its my first go  with gnu-linux so I'm slowly learning.  Thanks again :)

---

