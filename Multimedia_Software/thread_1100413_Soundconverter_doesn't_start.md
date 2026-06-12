---
title: "Soundconverter doesn't start"
date: 2009-03-19
forum: Multimedia Software
---

### Post by CK05 on 2009-03-19
Hi all, 

I've installed Sound Converter on 8.10 using the Add/Remove Application. 

However, after it's installed whenever I try to open it, Sound Converter just hangs on the panel saying "Starting Sound Converter". Then the window disappears, no program. No error message. 

Any ideas on what I'm doing wrong? Google doesn't return anything and I tried searching here. 

Cheers.

---

### Post by gandaran on 2009-03-19
do you have the ubuntu-restricted-extras installed?

---

### Post by CK05 on 2009-03-20
Thanks for taking the time to reply. I didn't have it installed, but I do now and it works fine. 

Thank you very much.

---

### Post by bob12564 on 2009-07-07
I just discovered this thread.  

I just installed SoundConverter on Intrepid and I have the same problem.  I see "Starting SoundConverter" on the task bar and then it just disappears after a few seconds.  And, yes, I do have the ubuntu-restricted-extras installed and I've had them for months and they're working.

Any ideas?

Thanks!

---

### Post by mc4man on 2009-07-07
> Any ideas?
Try starting soundconverter from a terminal, there won't be much output, maybe something useful will show up. (or it may just say segmentation fault which isn't much help

---

### Post by bob12564 on 2009-07-08
I'm a newbie with terminal commands.  How would I invoke it from a terminal window?

---

### Post by mc4man on 2009-07-08
Applications -> accessories -> terminal, then just type soundconverter into it and press enter.
(odds are the output won't be of much help ,but copy and paste into reply

Ex (blue will be different for you
> [COLOR="Blue"]doug@doug-laptop[/COLOR]:~$ soundconverter
SoundConverter 1.4.3
  using Gstreamer version: 0.10.18, Python binding version: 0.10.11
  using gio
  using 2 thread(s)


Edit:
I'm not big on gstreamer apps, but if output is of no use then try this instead as terminal command

```
soundconverter  --gst-debug-level=3
```

---

### Post by bob12564 on 2009-07-09
I ran it from the terminal as you suggested and it looks like the version of SoundConverter in the repository is corrupt.  Can that be?


SoundConverter 1.3.2
Traceback (most recent call last):
  File "/usr/bin/soundconverter", line 43, in <module>
    import pygtk
  File "/var/lib/python-support/python2.5/pygtk.py", line 41
    dir = os.getcwd()
                    ^
TabError: inconsistent use of tabs and spaces in indentation

---

### Post by mc4man on 2009-07-09
can't be of too much help, what I'd try (in no particular order

Open up synaptic, search 
```
python-gobject
```
mark for reinstall and apply (maybe reinstall sc at same time

Install a different version of sc, they're all the same anyway, you can use jaunty, karmic versions (assuming your on intrepid

(( when I posted before I was on hardy, must of grabbed the karmic version from packages.ubuntu at some point (SoundConverter 1.4.3

[http://packages.ubuntu.com/search?searchon=names&keywords=soundconverter](http://packages.ubuntu.com/search?searchon=names&keywords=soundconverter)


go to home folder -> .gstreamer-0.10 and rename registry.i486.bin to registry.i486.bin.bak and try sc again

While initially soundkonverter can be a bit mysterious, it has better capabilities than soundconverter

---

