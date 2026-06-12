---
title: "Need a network monitoring solution"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by z3nhakr on 2012-01-08
Hey guys! I probably put this thread in the wrong place so feel free to move it. Im looking for a multi-platform network monitoring (not managment) solution. All of the machines on my network either run ubuntu or windows so it has to run on both and it needs to be accessable from some sort of control panel preferably a webpage. All i want it to do is show running processes with pids and system load information such as cpu load, ram used, hdd free, etc. but it cant control because i keep my security tight. Btw before you ask, i already tried google and all i could get was some spysoftware crap :p

---

### Post by firedragoneater on 2012-01-08
Hi,
if all you want to do is monitor the computers process's and HDD usage etc, try Webmin - [http://webmin.com/](http://webmin.com/).

It's free and should do everything you need. It has a web control platform, so if you wanted you could even open it up to the internet.

Hope this helps,
J.K.F

---

### Post by z3nhakr on 2012-01-08
this should work if i can compile it with the dependencies so it is easier to install on windows. do you know if it is a separate web-page/server per machine or can i see all the machines on one page?

---

### Post by firedragoneater on 2012-01-08
I'm afraid that I think it is separate as it runs on a local web server.

---

### Post by z3nhakr on 2012-01-08
:( err
OK then. any other suggestions?

---

### Post by debd on 2012-01-08
dstat is the no.1 choise for monitoring any and everything in a linux box. but don't know if that's cross platform.
....
[look here]("http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html#public")   the page's pretty painful on the eyes. . .[URL="http://www.xymon.org/xymon/help/about.html"]
[/URL]

---

### Post by MasterGamerJK on 2012-03-20
Problem Solved: [http://www.xymon.com/](http://www.xymon.com/)

---

### Post by mikaelcrocker on 2012-03-20
I would say it would depend on what it is you want to do.

If you're wanting to looking at trends such as inodes, disk space, load, memory and such, you could go with munin. It's super easy to setup. I've also used scout, which is also good and quick and writing your own plugins in ruby isn't too bad either.

If you're wanting more granularity I would go with new relic.

Hope it helps

---

