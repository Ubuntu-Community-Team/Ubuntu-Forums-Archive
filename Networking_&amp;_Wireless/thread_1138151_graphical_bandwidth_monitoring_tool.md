---
title: "graphical bandwidth monitoring tool"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by spip on 2009-04-26
Hello,

I am looking for a real-time graphical bandwidth plotting utility that will run on Linux and X Window, although it doesn't matter if it uses a widget API (gtk, etc) as long as I can still export the display to an X Server such as Cygwin or Xming.  Since I need to export the display, the app can't take the form of a control panel in a desktop environment (kde/gnome/etc) or something like that.

I haven't been able to find one so far.

My needs are really simple.  I just want to see a real-time graph of the bandwidth usage (Tx/Rx) on a single interface.  I need the graph to capture the last fews seconds/minutes/hours of activity, which means all the console applications that just display the current usage snapshot (iftop, bwm-ng, etc) won't do.  If it is able to recognize bandwidth usage for a specific IP-to-IP conversation and have one plotline per conversation, even better.

I've searched around a fair amount.  Most applications I found are either console based or web-server based.  The console based ones usually only offer a current snapshot (no history) and the web ones aren't real-time, typically generating data that later gets compiled into a report.  I've also tried etherape thinking it might do this, but it doesn't.  bmon is the closest, but is text display.

I've examined the applications on the following pages to not avail:
   [http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html#public](http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html#public)
   [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)
   [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

I hope I'm missing something!  Would appreciate any pointers to existing apps.  I might write one if there really isn't anything, but I just find it hard to believe.

Thank you.

---

