---
title: "Miro not working with 2.7 Python update"
date: 2010-12-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-12-12
Anyone else having a problem with Miro after the update to Python 2.7?

I'm getting:```
dean@linux:~/Desktop$ miro
/home/dean/.themes/Nuvola-Light-Blue-Gray/gtk-2.0/gtkrc:558: error: unexpected identifier `menue', expected character `:'
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 269, in <module>
    startapp()
  File "/usr/bin/miro.real", line 226, in startapp
    startup(props_to_set)
  File "/usr/bin/miro.real", line 166, in startup
    application = load_frontend(globals(), locals(), att)
  File "/usr/bin/miro.real", line 142, in load_frontend
    _temp = __import__(frontend, globals_, locals_, ['application'], -1)
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py", line 47, in <module>
    from miro.frontends.widgets.application import Application
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/application.py", line 57, in <module>
    from miro.frontends.widgets import dialogs
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/dialogs.py", line 42, in <module>
    from miro.frontends.widgets import style
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/style.py", line 40, in <module>
    from miro.frontends.widgets import imagepool
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/imagepool.py", line 42, in <module>
    from miro.plat.frontends.widgets import widgetset
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/widgetset.py", line 39, in <module>
    from miro.plat.frontends.widgets import webkitbrowser
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/webkitbrowser.py", line 58, in <module>
    class WebKitEmbed(webkit.WebView):
AttributeError: 'module' object has no attribute 'WebView'

```

---

### Post by ronacc on 2010-12-12
yep same here , you found it, do the honors and I'll confirm .

---

### Post by autocrosser on 2010-12-12
Sounds good----here's the bug: [https://bugs.launchpad.net/ubuntu/+source/miro/+bug/689319](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/689319)

---

### Post by ronacc on 2010-12-12
confirmed and me too'd , good timing , I was out all morning and when I got back your post was 1 min old :D

---

### Post by autocrosser on 2010-12-12
Wow--I'm just getting ready to venture out---Christmas stuff & all that.......looks like there are not many Miro users here.......

I really like the science channel on Miro......

---

### Post by ronacc on 2010-12-12
LOL I'm one of those disgusting people that gets their Christmas shopping done by Thanksgiving .

---

### Post by autocrosser on 2010-12-12
Ya--just a couple of final things here--then I hide 'til after the New Year......:D:D

---

### Post by mc4man on 2010-12-12
A tmp 'workaround' is to remove or mv to a .bak /usr/lib/python2.7/dist-packages/webkit/_init_.py

Then miro will open, though at least here the window border is buried under unity's top panel bar. (can be moved w/ ALT+click

I would think an update should be forthcoming at some point

---

### Post by autocrosser on 2010-12-12
Very good catch!!!  I created a "unused" folder & stuck the webkit there---Miro starts up right afterwards, so it looks like we wait for a update....I "me too'd" the webkit bug & provided a link to the Miro bug.

I'm bummed that I was using the new Miro 3.5.1 & now needed to move back to the older Miro 3 due to this one......I might try building Miro from source to get 3.5 back---or contact the PPA & see if they want to build it with Python2.7.....

---

### Post by ronacc on 2010-12-12
just for grins I d/l'd the source from LP to see what would happen trying to local build it , the build script dies looking for something that isn't in the repos , they must have made some adjustments for it to build under Ubuntu .

---

### Post by ronacc on 2010-12-12
update , found a ppa for natty/miro , the build there 3.5.1 was only uploaded 2 hrs ago so its fresh , seems to run fine without hiding /usr/lib/python2.7/dist-packages/webkit/_init_.py .
 the ppa is     ppa:brian-rogers/ppa

---

### Post by mc4man on 2010-12-12
> found a ppa for natty/miro , the build there 3.5.1 
Interesting - was curious to see how he adapted to build on natty, (the ubuntu natty miro builds are a bit different than ubuntu maverick builds of miro

turns out he's using python 2.6 which is why "seems to run fine without hiding /usr/lib/python2.7/dist-packages/webkit/_init_.py ."

---

### Post by autocrosser on 2010-12-12
Hmmm--good workaround for the moment--I was missing my ESO-cast!!!!!

ronacc--you should try some of the science stuff on Miro--The Hubble-cast & ESO-cast are very good......

---

### Post by ronacc on 2010-12-12
I've been getting hubble cast for awhile , listening to one of the 365 days of astronomy audio podcasts right now , I'll give  ESO a try .

added ESO to my feeds .

---

