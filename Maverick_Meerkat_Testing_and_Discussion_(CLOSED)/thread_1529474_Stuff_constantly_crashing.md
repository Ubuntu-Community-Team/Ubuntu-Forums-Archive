---
title: "Stuff constantly crashing?"
date: 2010-07-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-07-12
I have 10.10 alpha 2 +updates installed on [eee box b202](http://event.asus.com/eeepc/microsites/eeebox/en/specifications.html), and I notice very often stuff crashing.

Usually it is "..." program crashes (nothing?), then I click close, and then "applet.py" crashes, and this can sometimes repeat several times in a loop.

I've had update manager 'crash', even though most of these crashes do not interfere with any programs, and they keep running fine.

When testing liveusb, I had screenshot program crash (stopped it from crashing by adding 3 second timeout before taking screenshot).

Anyone else having crashes, or just my install?

I have 60gb ocz ssd (firmware 1.6, brand new), and I've heard on their forums some are having [problems with linux](http://www.ocztechnologyforum.com/forum/showthread.php?74708-Vertex-1.6-fails-to-read-data-on-Linux) not working well on it (my 9 month old 60gb vertex firmware 1.3 works fine on another computer).

Yes I know it's alpha, but I don't remember having this many crashes when testing previous ubuntu versions. So I'm just wondering if others are having similar crashes or something wrong with my hardware setup.

---

### Post by VMC on 2010-07-12
I opened "top" and notice the crashing occurs just after that update-manager opens up. I forgot to remove its startup.  I never use that program. I prefer using aptitude to update my system.

 I usually remove that using the "System> Preferences >Startup Applications" - Update Notifier. Among several other applications including ubuntuone - which I will never use.

Now I no longer have those crashes. So the Python script must be related to the update-manager.

---

### Post by sgage on 2010-07-12
Yes, Update Manager is quite flaky these days. I also have gPodder crashing on me frequently - that is to say, the crash notification comes up, but the app still keeps working.

---

### Post by scradock on 2010-07-12
> **andrewabc said:**
> 

Usually it is "..." program crashes (nothing?), then I click close, and then "applet.py" crashes, and this can sometimes repeat several times in a loop.

Yes I know it's alpha, but I don't remember having this many crashes when testing previous ubuntu versions. So I'm just wondering if others are having similar crashes or something wrong with my hardware setup.

Yes, there was a missing file reference or something, and any python script calling GObject crashed. It's supposed to be fixed now..... (lp #603919)

---

### Post by ELD on 2010-07-12
I was getting hundreds of pop ups telling me something kept crashing again and again, was so annoying!

---

### Post by cariboo on 2010-07-12
I had the same problem this morning on My Compaq mini 110, until I did the updates, except for a rhythmbox crash that was my own fault, everything else has been running great since.

---

### Post by kyleabaker on 2010-07-12
This started for me a couple days back. I'm updating now (as I do daily) to see if its fixed. In the meantime, I just selecting ignore future crashes of this version after trying to report them once. Most were already reported by the time I saw them though.

---

### Post by ranch hand on 2010-07-12
I may have a hard time booting (I just love plymouth) but once booted I have little trouble even with boinc cranking my cpus right to the top, multiple stuff working on 6 desktops.

---

### Post by andrewabc on 2010-07-13
Turned on computer.
...
applet.py
update manager

all 'crashing'. I must have clicked close like 10 times.

Hopefully todays update does fix the problem like others here say it might.

---

### Post by kerry_s on 2010-07-13
:lolflag:

that got me when i installed unity a couple of days ago.
it was like windows pop up hell, if i didn't know better i would have thought i installed a virus.

:lolflag:

---

### Post by SevenMachines on 2010-07-13
In general i'd say, have apport disabled (i thought this was done automatically to be honest), at least early on in a testing phase
/etc/default/apport:
enabled=0

and when you want to generate crash reports/popups, force apport to start before crashing
$ sudo service apport start force_start=1

---

