---
title: "wicd needs python-urwid"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by beckx020 on 2010-02-19
Ok, I followed the instructions at 
[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)
But I got errors. I have no idea what to ignore or not. But I don't know how to fix it either.

So, try to install wicd from the synaptic package manager andit says it depends on python-urwid but it is not installable.

So....  I have no network manager now and no wicd and no internet.

How do I fix this?

---

### Post by northd_tech on 2010-02-19
Have you tried this terminal command?

```
**[FONT=Courier New][B][B]sudo apt-get install **[/B]python-urwid[/FONT][/B]
```That seems like the most straightforward way (unless you run into other problems).  You might also try unistalling wicd until after the python thing is fixed.  Then try to install wicd from the Synaptic Package Manager again.

Of course, if you don't have a cabled ethernet connection, then you will probably need to download some .deb (Debian package) files from another computer and install those from a USB stick or something similar.

I had just installed wicd last Friday, and I don't remember any problems under Jaunty 9.04.  I did need to restart the computer after installing to see my WiFi connection points though.

edit:  What version of ubuntu are you running?  That will affect what .deb packages you will need to locate.  Here is the wicd package for ubuntu 9.04 though:

[http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)

Here are links to that python widget:

[http://packages.ubuntu.com/search?keywords=python-urwid](http://packages.ubuntu.com/search?keywords=python-urwid)

---

### Post by beckx020 on 2010-02-19
I have 9.10 so it's Karmic?  That's probably the whole problem that the instruction are not setup for it.  Or maybe it's just not included in the remix version.  I'll try the install on the command line that you showed.  I guess if it doesn't work I'll start over again.

Thank you.  I'll try this again.

---

### Post by 2hot6ft2 on 2010-02-19
> **beckx020 said:**
> I have 9.10 so it's Karmic?  That's probably the whole problem that the instruction are not setup for it.  Or maybe it's just not included in the remix version.  I'll try the install on the command line that you showed.  I guess if it doesn't work I'll start over again.

Thank you.  I'll try this again.

Here's the download page for the karmic wicd
[http://packages.ubuntu.com/karmic/all/wicd/download](http://packages.ubuntu.com/karmic/all/wicd/download)

---

### Post by beckx020 on 2010-02-20
Thank you. I messed something up bad.  So I reinstalled.  Wicd installed fine and is working now. Hopefully I won't mess up anything else.

---

