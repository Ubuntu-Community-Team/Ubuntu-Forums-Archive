---
title: "How Do I Get a Logitech Webcam Working on Xubuntu 12.04"
date: 2013-01-19
forum: Multimedia Software
---

### Post by kenizl86 on 2013-01-19
I have a Logitech webcam that I got from somebody (there is o model number on it), and I want to be able to use it on Xubuntu 12.04, but I don't really know what to do to get it working? I'm not to Unix/Linux savvy (or at least terminal-wise), so if you could keep the developer jargon to a minimum, I would greatly appreciate it  :)          Thanks!

---

### Post by Toz on 2013-01-19
Does it work (is it recognized) when you plug it in?

To test whether it is, have a look at "Video Devices" in the Preferences section of Skype or install a program like "Video4Linux Control Panel" and see if its picked up (try Preview->Start Preview to see if you get an image).

If not, some log files might help (sorry, this is going to get a little technical). The simplest way is to open a terminal window, plug in the camera, run this command:
```
pastebinit /var/log/syslog
```
...and post back the link that is generated. This will send a copy of your log file to a website that we can view. Hopefully it will contain some diagnostic information.

---

### Post by kenizl86 on 2013-01-30
Here's the link:    [http://paste.ubuntu.com/1591905/](http://paste.ubuntu.com/1591905/)

It looks like the info you are looking for is on line 3891.

Also, here is a screenshot of Video4Linux when I plugged in my webcam (I tried to run the preview thing, but it said: "Failure to start preview process").

---

### Post by Toz on 2013-01-30
In that screenshot, you have an Auto Gain" option. Can you disable that and try the preview again?

Also, if you select Preview->Configure Preview, you should see a LD_PRELOAD environment variable. Make sure the path to v4l2convert.so is correct (change it if it is not). To find the correct path on your system, run this command:
```
locate v42lconvert.so
```

If no luck...


Can you report back what modules are installed?
```
lsmod
```

Also, try running this command in a terminal window, and posting back the text that is displayed:
```
mplayer tv://dev/video0
```

Possibly related bug reports:
- [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/984603]("https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/984603")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/918176]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/918176")

---

### Post by no2498 on 2013-02-02
was just thinking windows

look in the auto start up programs for 
cheese
skype

if you see them turn them off to never auto start

windows has taken over skype and windows turns every thing on to auto start

we can only use 1 program at a time with the cam

hope this helps

john

---

