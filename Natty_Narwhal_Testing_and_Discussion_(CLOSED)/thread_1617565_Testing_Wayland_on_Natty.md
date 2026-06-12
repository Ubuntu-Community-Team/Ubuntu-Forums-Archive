---
title: "Testing Wayland on Natty"
date: 2010-11-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by meborc on 2010-11-09
Hi again! the last Wayland thread got moved to community and then to reoccurring discussions faster then you can say "unitycompizwayland", so let's try this again :)

Has anyone had success with Wayland on Natty? there is this PPA, but seems to me some dependencies have not been resolved yet - [launchpad.net/~xorg-edgers/+archive/wayland]("http://launchpad.net/~xorg-edgers/+archive/wayland")

With a clean system, what would be the best way to try wayland? install ubuntu server and build up from there with minimal setup and no x-server?

Any success stories?

---

### Post by plun on 2010-11-09
Well... lets make the thread unmovable...:-\"

This i the blueprint för Wayland but it was written during Maverick development but also includes Natty issues.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-easy-wayland-testing](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-easy-wayland-testing)

> Work items for natty-alpha-1:
[bryce] Ensure cairo-gl is available in an ubuntu-x-swat PPA:
[bryce] Ensure libxkbcommon is available in an ubuntu-x-swat PPA:
[bryce] Ensure mesa compiled for wayland is available in an ubuntu-x-swat PPA:

Work items for natty-alpha-2:
[bryce] Ensure wayland is available in an ubuntu-x-swat PPA:
[bryce] Write "startw" script to do the necessary setup & start wayland:

More info:
[http://groups.google.com/group/wayland-display-server/web/building-and-running-wayland](http://groups.google.com/group/wayland-display-server/web/building-and-running-wayland)

---

### Post by cecilpierce on 2010-11-09
I have put it in maverick and so far all i get is:wayland-compositor
DRI2: failed to authenticateSegmentation fault

but im not sure what to do or how to it.
sure would like some help !

Thanks for putting it back here, it got moved 3 times.

PS i put the ppa in natty but nothing got installed ???

---

### Post by plun on 2010-11-09
> **cecilpierce said:**
> 
PS i put the ppa in natty but nothing got installed ???

I viewed package details for the ppa and Nattys packages broke during build.

[https://launchpad.net/~xorg-edgers/+archive/wayland/+sourcepub/1357104/+listing-archive-extra](https://launchpad.net/~xorg-edgers/+archive/wayland/+sourcepub/1357104/+listing-archive-extra)

---

### Post by autocrosser on 2010-11-09
Yes--This should be a sticky--We will be working with it VERY soon......I for one want to test as soon as it is "really" available.......

---

### Post by cariboo on 2010-11-09
There isn't enough here to sticky the thread, but now that it has a better title, that pertains to natty, it should stay here and become similar to the gnome-shell thread. 

As far as I can tell so far it looks like it will be at least a year before Wayland becomes usable, but this, thread should be the place to post problems and work-arounds.

---

### Post by geojorg on 2010-11-09
I think this is a better aprouch to compile Wayland 

[http://grep.tw/blog/?p=1061](http://grep.tw/blog/?p=1061)

---

### Post by muze4life on 2010-11-09
Good luck to the Wayland devs!
To me Ubuntu's transition to Wayland (within a few years) is the best desktop Linux news in a very long time.

---

### Post by meborc on 2010-11-10
> **geojorg said:**
> I think this is a better aprouch to compile Wayland 

[http://grep.tw/blog/?p=1061](http://grep.tw/blog/?p=1061)

OMG! will check it out as soon as I get home to my baby netbook (only intel device I have to test Wayland)
:P

---

### Post by cecilpierce on 2010-11-10
> **meborc said:**
> OMG! will check it out as soon as I get home to my baby netbook (only intel device I have to test Wayland)
:P

I tried, got to compiling wayland and had 2 errors and could not figure it out so i got mad after 3 hours of copy & paste and did make -i but got, DRI2 Segmentation fault when i ran it, iam not to hip on this stuff any more !!!

good luck, let us know how you make it,
cecil

PS heres the deal i get
wayland-compositor 
DRI2: failed to authenticateSegmentation fault

---

### Post by donniezazen on 2010-11-10
> **geojorg said:**
> I think this is a better aprouch to compile Wayland 

[http://grep.tw/blog/?p=1061](http://grep.tw/blog/?p=1061)

Can this be run on an existing ubuntu installation?

Just to make sure, is wayland completely going to replace compiz in natty?

---

### Post by meborc on 2010-11-10
> **soham_1207 said:**
> Can this be run on an existing ubuntu installation?

Just to make sure, is wayland completely going to replace compiz in natty?

this tutorial was for 10.10, but basically should work for 11.04 as well

wayland is to replace X, not compiz

---

### Post by donniezazen on 2010-11-10
> **meborc said:**
> this tutorial was for 10.10, but basically should work for 11.04 as well

wayland is to replace X, not compiz

Mia Culpa - will wayland completely replace x in coming days during natty testing?

---

### Post by DoeRayMe on 2010-11-10
No it wont replace X for awhile yet, at least a year till that happens i would imagine, its a huge change

---

### Post by donniezazen on 2010-11-10
> **DoeRayMe said:**
> No it wont replace X for awhile yet, at least a year till that happens i would imagine, its a huge change

> **geojorg said:**
> I think this is a better aprouch to compile Wayland 

[http://grep.tw/blog/?p=1061](http://grep.tw/blog/?p=1061)

Then what is this tutorial going to do?

---

### Post by autocrosser on 2010-11-10
> **soham_1207 said:**
> Then what is this tutorial going to do?

Allow you to play with Wayland a bit.....I expect that we won't be able to replace X until next testing cycle.....and I also bet the very early code will be quite "fun" to run---BRING ON THE BREAKAGE!!!!!!!!!

---

### Post by suoko on 2010-11-30
hi, 
i tested wayland and was pleased by its behaviour: it's comparable to a moblin install i tried last year.
Isn't it possible for it to be like aiglx so that all X apps will run with no problem ?
Otherwise, a port to wayland of chromium, rhythmbox, gimp, openshot and network manager could probably be enough for most netbooks

---

### Post by quickshade on 2010-11-30
As far as I know all X.org programs should work just fine on wayland, or at least so I've been told by fedora developers. I really want to try it out, having a modern well written display server is really all linux is missing.

---

### Post by nerdopolis on 2010-11-30
Seems they already have X running on Wayland [http://wayland.freedesktop.org/rootless-x-under-wayland.png](http://wayland.freedesktop.org/rootless-x-under-wayland.png)

[http://wayland.freedesktop.org/fullscreen-x-compiz.png](http://wayland.freedesktop.org/fullscreen-x-compiz.png)

I have not yet tried to get X running under Wayland on my box yet...

---

### Post by mttza1 on 2010-12-23
It seams to me that unease they can really strip down the X running under Wayland it will be a REALLY messy option - I mean Wayland is there to remove the mess that is the over-backward-compatibility of X, so wouldn't running an X-Server as a compatibility layer defeat that object?

---

### Post by screaminj3sus on 2010-12-23
> **mttza1 said:**
> It seams to me that unless they can really strip down the X running under Wayland it will be a REALLY messy option - I mean Wayland is there to remove the mess that is the over-backward-compatibility of X, so wouldn't running an X-Server as a compatibility layer defeat that object?

Yeah I was thinking this as well.

---

### Post by snadrus on 2010-12-27
X like TK & Motif become degraded & for historic benefit, but otherwise not part of the default experience. Few apps use X directly, so it may disappear even faster than toolkits designed for developers. Since they're already Linux apps, porting them should be easy. 

Virtualbox or Wine are similar heavy layers for those needing them who don't mind the penalty. I use both but as little as possible. Side note: Virtualbox and Wine both require X under Wayland.

---

### Post by t1497f35 on 2010-12-27
> **screaminj3sus said:**
> Yeah I was thinking this as well.
I think it's a stopgap solution for the next 2-3 years and a reminder that Ubuntu and Fedora are serious about Wayland. Then, when Wayland is good enough and all important apps relying on X get ported to the new graphics stack - X will be dropped and we'll be running pure Wayland. Hm.. doesn't it sound too rosy?..

---

