---
title: "ubuntu-extras-keyring??"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-09-26
Just got updates & there was a "ubuntu-extras-keyring" optional in Synaptic---question is--where is the repo that the keyring is for? Any ideas anyone?:confused:

The doc states that: 

ubuntu-extras-keyring (2010.09.17) maverick; urgency=low

  * initial version that includes the signing key for extras.ubuntu.com

 -- Michael Vogt <michael.vogt@ubuntu.com>  Tue, 21 Sep 2010 09:35:42 +0200

---

### Post by cariboo on 2010-09-26
There has been an extra repository started for stand-alone apps, that are submitted after the final freeze. The apps have to be self-contained and not depend on any  libraries, to qualify.

---

### Post by kerry_s on 2010-09-26
yeap, thats for that extra repo that only has 1 thing currently.

---

### Post by ranch hand on 2010-09-26
Good Gods man!  Are you really still using Synaptic?  It has, we have been informed, no features real users would have any use for.

Get with the program.

---

### Post by ktp on 2010-09-26
> **ranch hand said:**
> Good Gods man!  Are you really still using Synaptic?  It has, we have been informed, no features real users would have any use for.

Get with the program.

:lolflag:

---

### Post by kerry_s on 2010-09-27
> **ranch hand said:**
> Good Gods man!  Are you really still using Synaptic?  It has, we have been informed, no features real users would have any use for.

Get with the program.

:lolflag: i don't think i have ever opened the software center more than once & have never opened it after that.

---

### Post by M4570D0N on 2010-09-27
> **ranch hand said:**
> Good Gods man!  Are you really still using Synaptic?  It has, we have been informed, no features real users would have any use for.

Get with the program.

¿Cuál es tu problema con synaptico...brah? [IMG]http://forums.nasioc.com/forums/images/smilies/mad.gif[/IMG]














Ok, I'll show myself out now. :lol:

---

### Post by autocrosser on 2010-09-27
> **ranch hand said:**
> Good Gods man!  Are you really still using Synaptic?  It has, we have been informed, no features real users would have any use for.

Get with the program.


YEAH!!!  And I Still Understand Aptitude also :P ---Software Centre flat leaves me cold---smells like wet mackerel....:confused::rolleyes::rolleyes:

---

### Post by lonniehenry on 2010-09-27
I would rather use synaptic than Software Center.  Better view of what will be installed and what problems may arise.  Software Center doesn't always work and doesn't let me know why it fails.

---

### Post by philinux on 2010-09-27
> **autocrosser said:**
> Just got updates & there was a "ubuntu-extras-keyring" optional in Synaptic---question is--where is the repo that the keyring is for? Any ideas anyone?:confused:

The doc states that: 

ubuntu-extras-keyring (2010.09.17) maverick; urgency=low

  * initial version that includes the signing key for extras.ubuntu.com

 -- Michael Vogt <michael.vogt@ubuntu.com>  Tue, 21 Sep 2010 09:35:42 +0200

From here.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/645436](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/645436)

---

### Post by MacUntu on 2010-09-27
> **ranch hand said:**
> It has, we have been informed, no features real users would have any use for.

If you'd change "real users" to "average users" I'd sign that statement.

---

### Post by Locke_99GS on 2010-09-27
I agree completely. I use aptitude on the server, which IMO is far better than the clunky synaptic. (and synaptic requires a DE?) On the desktop and laptop, I've been finding myself using the Software Centre more and more, mostly because I don't really care what else is going on, so long as it works.

Desktops are for the pr0ns, not inspecting dependency versions. Get with it people.

---

### Post by ronacc on 2010-09-27
> **MacUntu said:**
> If you'd change "real users" to "average users" I'd sign that statement.

there are no "average" users in linux , "average" users swallow what MS gives them and don't dare use that evil "open source" stuff .

---

### Post by MacUntu on 2010-09-27
> **ronacc said:**
> there are no "average" users in linux
That's utterly wrong. ;)

---

### Post by clhsharky on 2010-09-27
If we are not real, are we virtual?

---

### Post by ronacc on 2010-09-27
> **clhsharky said:**
> If we are not real, are we virtual?

no , you're a figment of your own imagination .

---

### Post by kansasnoob on 2010-09-27
> **ranch hand said:**
> Good Gods man!  Are you really still using Synaptic?  It has, we have been informed, no features real users would have any use for.

Get with the program.

Spot on as usual!

I hope I don't get in trouble for saying so but Synaptic is my work horse!

When I can't figure things out I let Synaptic do it for me.

OTOH Lucid works great for me so I have three years to get involved, stay involved, and make sure Ubuntu keeps working for me :)

I try through Ayatana when I can, and I certainly file and post to bug reports, but what we need is a somewhat knowledgeable end user to get involved at the UDS level.

It can't be me! But I understand it can be done via social networking. All the screaming in the world makes no difference unless it's heard by the right ear(s) :)

If we're only going to shout back and forth here at the forums we'll have /dev/null effect on the outcome :D

---

### Post by IanW on 2010-09-28
> **ronacc said:**
> no , you're a figment of your own imagination .

"cogito | grep sum" :P

---

### Post by dino99 on 2010-09-28
my choices:

- synaptic to know wich packages are added to repo
- update-manager to see comments about each package before upgrading

for the main packages (gcc, xserver, grub) i come here to know about bad experience if any, before applying myself the rotten stuff if i dont care

---

### Post by cariboo on 2010-09-28
I've been using synaptic for as long as I've been using Debian (about 10 years), even when it isn't included in the default install any more, it will be the first thing I install. 

The Software Center is a wonderful application, but it just doesn't feel right to me. Fortunately, there are still a few devs that stand up for us more experienced users. :)

---

### Post by benjamimgois on 2010-09-30
> **kerry_s said:**
> yeap, thats for that extra repo that only has 1 thing currently.

Strange, i'm using Maverick RC and the extras repository do not show up here. How can i add it ?

---

### Post by doctordruidphd on 2010-10-01
Is this the correct line to add ot /etc/apt/sources.list for the extras repository? I don't seem to be getting any 404 errors with it, so far.

## Ubuntu extras repository
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

---

