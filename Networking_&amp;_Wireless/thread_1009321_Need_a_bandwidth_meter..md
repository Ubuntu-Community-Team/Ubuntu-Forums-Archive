---
title: "Need a bandwidth meter."
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by MadnessRed on 2008-12-12
Hi, my ISP are complaining about excessive use, what I would really appreciate is a program which basically logs my internet usage.

ideally I would like to know how much I am using each day, and what programs use the internet the most.

Is there a program like this?

---

### Post by gpsmikey on 2008-12-12
Assuming you are going through a router, you might check out the "Tomato" firmware -- they have it for a number of different routers.  It can show you all sorts of throughput and bandwidth information  - realtime, last hour, this month etc.  I have an older Linksys WRT54G with it on it and it works quite well.

mikey

---

### Post by cb34 on 2008-12-12
haven't tried it yet, but i'm about to.. found some app in Synaptic called:

bwm-ng

description says:

small and simple console-based bandwidth monitor
Bandwidth Monitor NG is a small and simple console-based live bandwidth
monitor.

Short list of features:
  * supports /proc/net/dev, netstat, getifaddr, sysctl, kstat and libstatgrab
  * unlimited number of interfaces supported
  * interfaces are added or removed dynamically from list
  * white-/blacklist of interfaces
  * output of KB/s, Kb/s, packets, errors, average, max and total sum
  * output in curses, plain console, CSV or HTML
  * configfile
---

then there's writing some custom script to output all the info u want from netstat or something similar to a file maybe ?? just an idea.

also i dont know about logging, but with conky on the screen u can see all programs running, internet connections, speed, ports etc. good to hunt down things running on the system, and see things happening in realtime.. but there must be a way to send that info to a file for review later...hmmmm.. or netstat info to a file...??

---

### Post by cb34 on 2008-12-12
ehh.. that bwm-ng program is some small little program that just shows active connection speeds.. not what i think you're lookin for..

purge..lol

bcuz im interested in something like this also.. i did some searching and found this.. havent tried it yet.. just linkin you with an idea. :)

called Nnetstat

[http://www.google.com/search?q=Nnetstat](http://www.google.com/search?q=Nnetstat)

cya

EDIT-> interesting page i just found.. thought i'd share. :)
[http://www.linuxjournal.com/article/6882](http://www.linuxjournal.com/article/6882)

---

### Post by MadnessRed on 2008-12-14
Many thanks for all your responses, I will look at the progs you suggested and let you know how to go.

---

### Post by Junkieman on 2009-03-10
Sorry to do this, but *bump*.

Has anyone found a bandwidth monitor that actually persists previous bandwidth usage data, so that you can see the total usage for a given period? 

I need some way to track how much bandwidth I'm using per month, there are many great monitoring tools out there, but can only find real-time monitors, none that keep a history of usage.

---

### Post by binbash on 2009-03-10
did you check vnstat ?

---

### Post by smeerbartje on 2009-03-10
> **binbash said:**
> did you check vnstat ?

Indeed, [vnstat]("http://humdi.net/vnstat/") is the best! Install by typing 'sudo apt-get install vnstat'. After installation you need to create a local file where all the data is stored in. Works perfect! It even offers some nice [statistics]("http://humdi.net/vnstat/cgidemo/")!

---

### Post by bgiannes on 2009-03-10
take a look at Webmin there is a metering tool in there.  Assuming your Ubuntu Box is the only device connected to the WAN

if not updating the firware in your router is the way to go, i use dd-wrt.

---

### Post by aragorn2909 on 2009-03-12
or there is bandwidthd

---

### Post by create.vibe on 2009-03-24
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

---

