---
title: "Rhthmbox Crashes When I Change Volume"
date: 2010-07-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-07-03
I notice that Rhythmbox crashes when I change volumes sometimes. Has anyone else seen this? I get no App Report dialog to report this and it silently crashes.

I'd like to pass along a bug report but I have no details other than what I see. Anyone have more details?

---

### Post by Yarui on 2010-07-03
Interesting.  Could you give a little more detail?  How are you changing your volume, with the default applet on the gnome menu bar?  You say it only does it sometimes, have you noticed any pattern?

---

### Post by kyleabaker on 2010-07-03
> **Yarui said:**
> Interesting.  Could you give a little more detail?  How are you changing your volume, with the default applet on the gnome menu bar?  You say it only does it sometimes, have you noticed any pattern?

No pattern that I can tell, otherwise I would have plotted it out. Seems like if I listen for a couple hours, then change the volume from the button in the top right corner of Rhythmbox it always crashes.

If I can create a good test case then I'll share it, but in the mean time.. no one else has seen this bug?

---

### Post by Yarui on 2010-07-03
oh, okay, you mean changing the volume in the application, that sounds more like a rhythmbox bug than what I was imagining.  I thought you meant the system volume, which was a bit remarkable.

---

### Post by kukker32 on 2010-07-03
maybe try install another music player.. one that dosn't screw everything up :P

i have listed som good alternatives..

**Banshee music player**

add this respetory
**deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main**
****
in terminal write
**sudo apt-get install banshee**

[B]
Exaile music player

run theese 3 commands in terminal
[/B]sudo add-apt-repository ppa:exaile-devel/ppa
sudo apt-get update
sudo apt-get install exaile


**Amarok**
run in terminal

sudo apt-get install amarok

personaly i use songbird but that is some kde based bla bla bla.. and i cant find the commands or deb package for it
[B]or otherwise use the software center...
[/B]

---

### Post by Queue29 on 2010-07-03
> **Yarui said:**
> oh, okay, you mean changing the volume in the application, that sounds more like a rhythmbox bug than what I was imagining.  I thought you meant the system volume, which was a bit remarkable.

I've been having this bug since 9.04 (64 bit only), but nobody believes me :(

---

### Post by ssam on 2010-07-03
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/455421](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/455421)
[https://bugzilla.gnome.org/show_bug.cgi?id=533427](https://bugzilla.gnome.org/show_bug.cgi?id=533427)

---

