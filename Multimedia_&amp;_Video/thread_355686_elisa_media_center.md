---
title: "elisa media center"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by zekopeko on 2007-02-07
anybody managed to install it on edgy?

i tried getting it by following this instructions:

[https://core.fluendo.com/elisa/trac/wiki/Packages](https://core.fluendo.com/elisa/trac/wiki/Packages)

but synaptic reports this error

E: /var/cache/apt/archives/libpigment0_0.1.3-1ubuntu1_i386.deb: trying to overwrite `/usr/lib/pigment-0.1/gstreamer/libpgmrendersink.so', which is also in package pigment

---

### Post by zekopeko on 2007-02-08
::bumpy::

---

### Post by philn on 2007-02-12
This is weird, where did you find that "pigment" package? There are only libpigment0 and libpigment-dev

---

### Post by zekopeko on 2007-02-12
sorry i don't get it.

i have elisa and libpigment0 in synaptic using the guide in the link above.
now i have elisa installed but the problem is i get segmentation faults.

---

### Post by philn on 2007-02-12
> **zekopeko said:**
> sorry i don't get it.

i have elisa and libpigment0 in synaptic using the guide in the link above.
now i have elisa installed but the problem is i get segmentation faults.

What video drivers are you using?

---

### Post by zekopeko on 2007-02-13
i'm using the ones from the ENVY script. i belive its 9746 or something like that.

Geforce 6200

---

### Post by barney_1 on 2007-02-13
I don't have any help to offer you.  But I did want to thank you for post because this is the first I have heard of Elisa.  I installed from the repo in the guide you posted.  It's up an running well on my Feisty system.  There doesn't seem to be any support for DVD ISO files but the project looks promising!

Thanks!

---

### Post by zekopeko on 2007-02-13
^^^ 

glad i could help. i just removed every file of pigment and elisa from my computer (before going by the guide i tried to compile it and that probably left a lot of trash)

now it works like a charm

---

### Post by olavjunior on 2007-03-06
I used the pagage from their website, but uinstalled it reght afterwards. Elissa's the worst program I've tried in Linux by now. It's really just a beta, I know. I know media-centers tend to use much resorses, but Elisa was unusable!

---

### Post by Sir Frederic on 2007-04-06
doesn't work for me right now. grr. crashes when opening.

---

### Post by philn on 2007-04-10
Yes we are aware that current Elisa branch (0.1.x) has usability and ergonomy issues. We are currently working on a new software architecture that will allow us to fix these problems and implement some really nice usecases like the ones you can see there: [https://core.fluendo.com/elisa/trac/wiki/UseCases](https://core.fluendo.com/elisa/trac/wiki/UseCases)

That new branch will be available by the month of July.

---

### Post by hotani on 2007-04-25
Maybe I got lucky, but the Edgy version of Elisa installed on my Feisty machine and ran. It has some issues, but I am very impressed with it so far. It is the most promising non-TV media center for Linux I've found, and I will be eagerly following its development in the coming months.

It took me a while to figure out how to tell it where my video files lived, but from what I have read, this will soon be a part of the config section.

As much as I despise using MythVideo, I do like that I can configure it so everything plays through VLC which has had the most success playing the variety of formats in my collection (mostly downloaded TV shows, and a good bit of HD content--most players will choke on a 720 or 1080p mkv file).

Keep up the good work. Elisa is filling an important need on the linux desktop: an easy-to-use media center without the hassels of TV cards, backend servers, CLI configurations, etc...

---

### Post by MetalMusicAddict on 2007-04-25
Guys. FYI right from the [Fluendo site]("https://core.fluendo.com/elisa/trac/wiki/Packages"). They have Edgy/Feisty repos.

**Edgy Eft**
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) edgy main

**Feisty Fawn**
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main

---

### Post by fonzie on 2007-06-02
Got the same issue here. What do you mean you erased every pigment of file? Can you be a bit more specific because here after a while it crashes.

thx

---

