---
title: "Investigating mysterious network traffic (an process not showing up)"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by legalguy on 2009-07-30
Just a couple of info questions.  Running Jaunty, no user apps running.

I just noticed a lot of download traffic in my system monitor applet.  Opening it up (gnome-system-monitor), it showed only gnome-system-monitor awake and using CPU.

I wanted to find out what was going on (suspected malware).  I remembered there was a program called ntop, but it failed to load with a bunch of errors.

I fired up wireshark, found the offending ip address [http://204.152.191.39/](http://204.152.191.39/) and it is mirrors.kernel.org.  Which is good, looks like a normal update.

Questions
1)  What do you all use to check out or keep track of your traffic?  I would like something that doesn't use a lot of resources to keep an eye on my connection when I'm not around.

2)  Why didn't gnome-system-monitor see the process id?  I checked preferences, there's nothing in there about ignoring some processes.

3)  I really like having the gnome-system-monitor in the panel, I have it set to graph the CPU and network.  But it uses a lot of resources.  Any know of an applet that does about the same thing but doesn't use so much? 
Thanks in advance...

---

### Post by superprash2003 on 2009-07-30
firestarter has a small box which shows the list of active connections,blocked connections etc

---

### Post by martinbaselier on 2009-07-30
Use top within a terminal to view your processes and their cpu/memory usage. It doesn't look so nice but it's much faster.

---

