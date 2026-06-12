---
title: "simple graphical real time bandwidth monitor?"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by h2z on 2009-12-18
Is there such a thing? 
I've tried both Wireshark and EtherApe but I wasn't able to get what I want. Closest thing was Firestarter's "Active Connections" window.

In windows, something like this was an integral part of "Tiny Personal Firewall 2.0.15"

[IMG]http://http://robert.feldhousen.com/freeware/tpfirewall2015a.jpg[/IMG]

[http://robert.feldhousen.com/freeware/tpfirewall2015a.jpg](http://robert.feldhousen.com/freeware/tpfirewall2015a.jpg)

---

### Post by jerrrys on 2009-12-18
don't use one, but is this what your looking for?

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by h2z on 2009-12-18
Thanks for that link, it's hard to choose from such a long list, I was hoping someone with experience with either of those would comment here...

---

### Post by ajgreeny on 2009-12-18
Iuse one of the websites to check my download speeds etc, but for a note of my downloads and uploads I use vnstat, but have it in a small shell script I wrote to show me in a text file what the last month's daily usage has been.

Install vnstat, if it's not there by default (I can't remember) and then use this script for the output.  Simple but very effective.
```
#!/bin/bash
vnstat -d > /tmp/$
gedit /tmp/$
```

---

### Post by h2z on 2009-12-18
That's also not what I was looking for...I'll try to explain by means of an example;

I have a youtube video playing, in a single tab firefox instance. What I want to know is the _current_ up/down stream, I really don't care about statistics.

---

### Post by smo0th on 2009-12-18
Right click on the top screen bar, select Add to panel.., System monitor, right click on the recently added addon, Preferences.., select network ant that's it!

An easy click, click, click solution, although it doesn't provide numbers unless you drag the mouse over the little monitor space.

---

### Post by ajgreeny on 2009-12-18
OK, you could still use **vnstat** in the terminal with the -l option ```
vnstat -l
```which will give you output like this
> Monitoring eth0...    (press CTRL-C to stop)

   rx:       0.00 kB/s     0 p/s            tx:       0.00 kB/s     0 p/s
Note, I did this with no network activity, hence the zeros shown in rx: and tx:

---

### Post by h2z on 2009-12-18
Still same as the previous suggestions. How about an app that shows the speeds for each running program's connection?

---

### Post by ajgreeny on 2009-12-18
Sorry, no idea.  I'm not even sure I understand what exactly it is you want, but perhaps that's just my way of working; I usually have just one thing downloading at a time, not many different files or streams, and I am more interested in the overall network download speed, not how it's shared between applications.

---

### Post by h2z on 2009-12-18
I have pidgin with 3 different protocols, irc, firefox and web radio running at the same time usually. What I want to know is the speed (along with destination:ip) of _each_ of those apps...

---

